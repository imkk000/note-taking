# AWS EC2
- Pricing comparison:
    - https://instances.vantage.sh/
- Elastic Compute Cloud = Infrastructure as a Service
- Knowing EC2 is fundamental to understand how the Cloud works
- It mainly consists in the capability of:
    - Renting virtual machines (EC2)
    - Storing data on virtual drives (EBS)
    - Distributing load across machines (ELB)
    - Scaling the services using an auto-scaling group (ASG)

## Sizing and configuration options
- OS
- CPU
- RAM
- Storage space:
    - Network-attached (EBS & EFS)
    - Hardware (EC2 Instance Store)
- Network Card: speed of the card, public IP Address
- Firewall rules: Security Group
- Bootstrap script (configure at first launch): EC2 User Data

## EC2 User Data
- It is possible to bootstrap our instances using an EC2 User Data script
- Bootstrapping means launching commands when a machine starts
- That script is **only run once at the instance first start**
- Used to automate boot tasks such as:
    - Installing updates
    - Installing software
    - Downloading common files from the internet
- Runs with the **root user**

![ec2](./Images/ec2_user_data.png)

## EC2 Instance Types
- https://aws.amazon.com/ec2/instance-types/
- `t2.micro` is part of the AWS free tier (up to 750 hours per month)
- Naming convention: m5.2xlarge
    - m: instance class
    - 5: generation (AWS improves them over time)
    - 2xlarge: size within the instance class

### General Purpose (T/M/A)
- Great of a diversity of workloads such as web servers or code repositories
- Balance (networking, compute, memory)

### Compute Optimized (C)
- Great for compute-intensive tasks that require high performance processors:
- Use cases:
    - Batch processing workloads
    - Media transcoding
    - High performance web servers
    - High performance computing (HPC)
    - Scientific modeling and machine learning
    - Dedicated gaming servers

### Memory Optimized (R/X/z/High Memory)
- Fast performances for workloads that process large data sets in memory
- Use cases:
    - High performance, relational/non-relational databases
    - Distributed web scale cache stores
    - In-memory databases optimized for BI (Business intelligence)
    - Applications performing real-time processing of big unstructured data

### Storage Optimized (I/D/H)
- Great for storage-intensive tasks that require high, sequential read and write access to large data sets on local storage
- Use cases:
    - High frequency online transaction processing (OLTP) systems
    - Relational and NoSQL databases
    - Cache for in-memory databases (Redis)
    - Data warehousing applications
    - Distributed file systems
