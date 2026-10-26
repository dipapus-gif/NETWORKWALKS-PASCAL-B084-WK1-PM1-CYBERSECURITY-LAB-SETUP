# NetworkWalks Week 1 Task: Virtualization & Kali Linux Network Configuration

## 📌 Project Overview
This project documents the setup and configuration of a virtualized lab environment using *Oracle VirtualBox* and *Kali Linux, completed as part of the **NetworkWalks* Week 1 practical task under the mentorship of *Waqas Karim*.

The goal of this task is to configure a custom NAT Network, adjust hardware resource allocations, set up shared folders, and configure static IPv4 networking via CLI inside Kali Linux.

---

## 🛠️ Infrastructure & Environment Setup

* *Hypervisor:* Oracle VM VirtualBox Manager
* *Virtual Machine Name:* KALI NETWORKWALK
* *Operating System:* Kali Linux (64-bit)

---

## ⚙️ Key Configurations Implemented

### 1. Custom NAT Network Creation
* Configured a dedicated isolated internal network named NatNetwork.
* *IPv4 Prefix:* 10.0.0.0/24
* *DHCP:* Enabled on the network scope.

### 2. Hardware Resource & System Allocation
* Allocated *2048 MB RAM* base memory.
* Set boot order sequence: Floppy, Optical, Hard Disk.
* Enabled *I/O APIC* and *Hardware Clock in UTC*.
* Enabled *Nested Paging* under Hardware Virtualization settings.

### 3. Network Interface Attachment
* *Adapter Type:* Intel PRO/1000 MT Desktop (82540EM)
* *Attached To:* NAT Network (NatNetwork)
* *Promiscuous Mode:* Allow All
* *Virtual Cable:* Connected

### 4. Shared Folder Integration
* Configured machine folder mapping to facilitate file transfers between host and guest OS (C:\Users\User\Downloads).
* Granted *Full Access* and enabled *Auto Mount*.

### 5. CLI Static Network Configuration (Kali Linux Terminal)
* Configured connection Wired connection 1 with static addressing:
  * *IP Address:* 10.0.0.2
  * *Netmask:* /24 (255.255.255.0)
  * *Gateway:* 10.0.0.1
  * *DNS:* 8.8.8.8
* Used nmcli to modify and bounce the connection interface:
  ```bash
  sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
  sudo nmcli connection down "Wired connection 1"
  sudo nmcli connection up "Wired connection 1"
