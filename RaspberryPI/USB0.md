# USB0

Enable usb0 interface for rpi4

Reference: https://www.hardill.me.uk/wordpress/2019/11/02/pi4-usb-c-gadget/

## Prepare on Boot

- Add `dtoverlay=dwc2` to the /boot/config.txt
- Add `modules-load=dwc2` to the end of /boot/cmdline.txt
- Create file `ssh` on /boot

## Customization

- Add `libcomposite` to /etc/modules
- Disable DNSStubListener in `systemd-resolved` (https://unix.stackexchange.com/a/516808)
```bash
mkdir -p /etc/systemd/resolved.conf.d
cat << EOF > /etc/systemd/resolved.conf.d/noresolved.conf
[Resolve]
DNSStubListener=no
EOF
systemctl restart systemd-resolved
rm -rf /etc/resolv.conf
cat << EOF > /etc/resolv.conf
nameserver 127.0.0.1
```

- Add `nameserver 127.0.0.1` to `/etc/resolv.conf` for fallback to use `dnsmasq`

- Install `isc-dhcp-server` for next step (Ubuntu)
- Add `denyinterfaces usb0` to /etc/dhcpcd.conf
- Install `dnsmasq`
- Create `/etc/dnsmasq.d/usb` with following content

```bash
cat << EOF > /etc/dnsmasq.d/usb
interface=usb0
dhcp-range=10.255.0.2,10.255.255.6,255.255.255.248,1h
dhcp-option=3
leasefile-ro
EOF
```

- Create `/etc/dnsmasq.d/dns`
```bash
server=1.1.1.1
server=1.0.0.1
```

- Install `ifupdown` (Ubuntu)
- Create `/etc/network/interfaces.d/usb0` with the following content
```bash
auto usb0
allow-hotplug usb0
iface usb0 inet static
address 10.255.0.1
netmask 255.255.255.248
```

- Create `/root/usb.sh`
```bash
#!/bin/bash
cd /sys/kernel/config/usb_gadget/
mkdir -p pi4
cd pi4
echo 0x1d6b > idVendor # Linux Foundation
echo 0x0104 > idProduct # Multifunction Composite Gadget
echo 0x0100 > bcdDevice # v1.0.0
echo 0x0200 > bcdUSB # USB2
echo 0xEF > bDeviceClass
echo 0x02 > bDeviceSubClass
echo 0x01 > bDeviceProtocol
mkdir -p strings/0x409
echo "NONAME1234567890" > strings/0x409/serialnumber
echo "NONAME" > strings/0x409/manufacturer
echo "RPI4 USB" > strings/0x409/product
mkdir -p configs/c.1/strings/0x409
echo "ECM network" > configs/c.1/strings/0x409/configuration
echo 250 > configs/c.1/MaxPower
# Add functions here
# see gadget configurations below
# End functions
mkdir -p functions/ecm.usb0
HOST="00:dc:c8:e7:99:20" # "HostPC"
SELF="00:dd:dc:eb:6d:a1" # "BadUSB"
echo $HOST > functions/ecm.usb0/host_addr
echo $SELF > functions/ecm.usb0/dev_addr
ln -s functions/ecm.usb0 configs/c.1/
udevadm settle -t 5 || :
ls /sys/class/udc > UDC
ip link set dev usb0 up
```

- Enable rc.local `systemctl enable rc.local`
- Make /root/usb.sh executable with `chmod +x /root/usb.sh`
- Add `/root/usb.sh` to /etc/rc.local before exit 0 (I really should add a systemd startup script here at some point)

- Create file `/etc/systemd/system/startup-script.service`
```bash
[Unit]
Description=RPI4 USB Startup Script
After=network.target

[Service]
ExecStart=/root/usb.sh
Type=oneshot
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```
- sudo systemctl daemon-reload
- sudo systemctl enable startup-script.service
