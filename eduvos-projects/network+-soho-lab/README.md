# Network+ Practical: Subnetting & Virtual SOHO Infrastructure

![Status: Completed](https://img.shields.io/badge/Status-Completed-success)
![Course: Higher Certificate](https://img.shields.io/badge/Course-Higher_Certificate-blue)
![Focus: Network Engineering](https://img.shields.io/badge/Focus-Network_Engineering-orange)

## 📌 Project Overview
This project demonstrates foundational network engineering skills by designing, calculating, and deploying a Small Office/Home Office (SOHO) network environment. It covers physical infrastructure (UTP cable fabrication), logical addressing (IPv4 /28 subnetting), and the configuration of a virtualized peer-to-peer Windows workgroup using static IP addressing and centralized DNS resolution. It also includes practical troubleshooting of domain name resolution failures.

## 📑 Table of Contents
- [Architecture & Topology](#-architecture--topology)
- [Technologies Used](#-technologies-used)
- [Key Implementations](#-key-implementations)
- [Setup & Configuration Instructions](#-setup--configuration-instructions)
- [Project Documentation & Media](#-project-documentation--media)
- [License](#-license)

## 🏗️ Architecture & Topology
The project simulates a remote office network leveraging a `192.168.1.66/28` address space.

*   **Network Workgroup:** `REMOTE-2025`
*   **Subnet Mask:** `255.255.255.240`
*   **DNS Server:** `10.16.0.10`
*   **Node 1 (VM1):** `OFFICE-PC1` (Windows 8.1) — Assigned First Usable Host IP `192.168.1.65`
*   **Node 2 (VM2):** `OFFICE-PC2` (Windows 10) — Assigned Last Usable Host IP `192.168.1.78`

## 💻 Technologies Used
*   **Networking:** IPv4, CIDR Subnetting, ICMP (Ping), DNS Resolution
*   **Hardware:** UTP Cabling, RJ45 Connectors, Crimping Tools
*   **Virtualization:** Oracle VM VirtualBox
*   **Operating Systems:** Windows 8.1, Windows 10
*   **Configuration:** Static IP Assignment, Windows Workgroup Management

## 🚀 Key Implementations
1.  **Physical Cabling:** Created a functional UTP straight-through cable to standard specifications (TIA/EIA-568) for physical network connectivity.
2.  **Subnet Architecture:** Calculated critical subnet parameters for a `/28` CIDR block, defining the network address, broadcast address, and valid host ranges to prevent IP conflicts.
3.  **Virtualized SOHO Deployment:** Provisioned and networked two Windows virtual machines, placing them in an isolated workgroup with manually configured static IP addresses based on the calculated subnet block.
4.  **Connectivity & DNS Troubleshooting:** Verified peer-to-peer routing using ICMP echo requests and diagnosed a simulated Domain Name System (DNS) resolution failure, identifying the root cause of hostname connectivity issues and proposing a remediation strategy.

## 🛠️ Setup & Configuration Instructions
To replicate the virtual network environment:

### Prerequisites
*   Oracle VirtualBox 7.0+
*   Windows 8.1 and Windows 10 ISOs

### Step-by-step Setup
1.  **Virtual Machine Provisioning:**
    *   Deploy VM1 (Windows 8.1) and name it `OFFICE-PC1`.
    *   Deploy VM2 (Windows 10) and name it `OFFICE-PC2`.
    *   Ensure both VMs are connected to the same `Internal Network` in VirtualBox settings.
2.  **OS Configuration:**
    *   Join both machines to the workgroup: `REMOTE-2025`.
3.  **Network Configuration (IPv4):**
    *   Open `ncpa.cpl` (Network Connections) on each VM.
    *   Set the IP of `OFFICE-PC1` to `192.168.1.65` and subnet mask to `255.255.255.240`.
    *   Set the IP of `OFFICE-PC2` to `192.168.1.78` and subnet mask to `255.255.255.240`.
    *   Set the Preferred DNS server on both to `10.16.0.10`.
4.  **Verification:**
    *   Open Command Prompt and ping each machine by IP and Hostname to verify routing and DNS behavior.

## 📹 Project Demo
[▶ Watch: UTP Straight-Through Cable Tutorial](https://youtu.be/9F41N_NPfTU)
*    Step-by-step demonstration of stripping, arranging, and crimping a straight-through UTP cable.

## 📄 Project Documentation & Media
The following assets are included in the repository to document the project execution:
*   [Network+ Write-Up.pdf](docs/)
  - Complete tables showing the breakdown of the 192.168.1.66/28 subnet.
  - Visual proof of static IP assignment, workgroup configuration, and successful ICMP pings.
  - Analysis of the hostname resolution failure and recommended solutions.
 
 

Add Network+ SOHO Lab Project
