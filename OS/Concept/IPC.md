# IPC

- `Inter-process communication` are the mechanisms provided by an OS for processes to mange shared data.

## Approaches

- File
  - A record store on disk, or a record synthesized on demand by a file server, which can be accessed by multiple processes
- Signal
  - Asynchronous System Trap or Interrupt
  - A system message sent from one process to another, not usually used to transfer data but instead of used to remotely command the partnered process
- Socket
  - Data sent over a network interface, either to a different process on the same computer or to another computer on the network
  - Stream-oriented ([TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)) or Message-oriented ([UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol))
- Unix domain socket
  - Similar to an internet socket, but all communication occurs within the kernel
  - Domain sockets use the file system as their address space
  - Processes reference a domain socket as an [inode](https://en.wikipedia.org/wiki/Inode)
  - Multiple processes can communicate with one socket
- Message queue
  - A data stream similar to a socket, but which usually preserves massage boundaries
  - OS is allowed multiple processes to read and write to the message queue without being directly connected to each other
- Anonymous pipe
  - A unidirectional data channel using standard i/o
  - Data written to the write-end of the pipe is buffered by the os until it is read from the read-end of the pipe
  - Two-way communication between processes can be achieved by using two pipes in opposite directions
- Named pipe
  - A pipe that is treated like a file
  - Instead of using standard i/o as with an anonymous pipe, processes write to and read from a named pipe, as if it were a regular file
- Shared memory
  - Multiple processes are given access to the same block of memory, which creates a shared buffer for the processes to communicate with each other
- Massage passing
  - Allows multiple programs to communicate using message queues
  - Commonly used in concurrency models
- Memory-mapped file
  - A file mapped to RAM and can be modified by changing memory addresses directly instead of outputting to a stream
