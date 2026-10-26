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
  sudo nmcli connection up "Wired connection 1"<img width="587" height="388" alt="Screenshot 2026-10-25 233505" src="https://github.com/user-attachments/assets/1334e745-3522-401c-8110-101849e3ad39" />
<img width="587" height="388" alt="Screenshot 2026-10-25 233010" src="https://github.com/user-attachments/assets/5d725ed4-311a-4c3c-8b6d-fd37f4a6d731" />
<img width="960" height="504" alt="Screenshot 2026-10-25 232943" src="https://github.com/user-attachments/assets/d27e698d-fbea-4887-a79b-48c44aed7d8a" />
<img width="960" height="504" alt="Screenshot 2026-10-25 211316" src="https://github.com/user-attachments/assets/368377d8-07bd-4b86-b74d-aa06c210010c" />
<img width="960" height="504" alt="Screenshot 2026-10-25 211118" src="https://github.com/user-attachments/assets/5f1f0787-724b-468f-b1d8-7875af3a4e93" />
<img width="960" height="504" alt="Screenshot 2026-10-25 211032" src="https://github.com/user-attachments/assets/e9ca4664-496d-44c3-a276-ab3cb9ce6687" />
<img width="1920" height="892" alt="VirtualBox_KALI NETWORKWALK_25_10_2026_23_28_15" src="https://github.com/user-attachments/assets/5961b8ac-9fd1-4f6d-be8f-9cd391b32b6d" />
<img width="1920" height="892" alt="VirtualBox_KALI NETWORKWALK_25_10_2026_23_22_44" src="https://github.com/user-attachments/assets/00f36244-f9d5-483c-aa26-705aee2e31bf" />


