# Endpoint Access Control & Cross-Platform Security Administration

![Status: Completed](https://img.shields.io/badge/Status-Completed-success)
![Course: Higher Certificate](https://img.shields.io/badge/Course-Higher_Certificate-blue)
![Focus: System_Administration](https://img.shields.io/badge/Focus-System_Administration-orange)

## 📌 Project Overview
Configured a secure, cross-platform enterprise environment bridging a Windows 10 host and an Ubuntu 24.04.2 virtual machine[cite: 7]. Enforced strict endpoint access controls by eliminating world-readable directories, applying sticky bits to shared folders, and implementing aggressive password aging policies[cite: 7]. Validated system interoperability by securely mapping remote file systems via RDP and automating critical system updates through scheduled cron jobs[cite: 7].

## 🏗️ Architecture & Environment
The project relies on a bridged networking architecture allowing the virtualised Linux machine to exist on the same physical subnet as the host[cite: 8].

*   **Host OS:** Windows 10[cite: 7]
*   **Guest OS:** Ubuntu 24.04.2 LTS (Hostname: `alpha`, 4GB RAM, 25GB Virtual Disk)[cite: 7]
*   **Hypervisor:** Oracle VM VirtualBox 7.0+[cite: 7]
*   **Network Mode:** Bridged Adapter[cite: 7]
*   **Linux Network Config:** 
    *   Static IP: `192.168.68.51/22`[cite: 7]
    *   Gateway: `10.1.1.101`[cite: 7]
    *   DNS Server: `10.1.1.110`[cite: 7]

## 💻 Technologies & Tools Used
*   **Operating Systems:** Ubuntu Linux, Windows 10[cite: 8]
*   **Networking:** CLI Static Routing, `/etc/hosts`, `/etc/netplan`[cite: 7]
*   **Cross-Platform Tools:** Remmina (RDP Client), Wine (for executing `.exe` binaries)[cite: 7]
*   **User & File Management:** `chage` (Password aging), `chmod` (Sticky bit/Permissions)[cite: 7]
*   **Automation & System Tools:** Bash Scripting, Crontab, `hdparm` (Disk performance), `init` (Runlevels)[cite: 7]

## 🚀 Key Implementations
*   Provisioned a static IPv4 network configuration via Netplan YAML, establishing local hostname resolution (`/etc/hosts`) to bypass external DNS dependencies between the Linux and Windows environments[cite: 7].
*   Secured user endpoints by provisioning a new identity (`fblack`), stripping world-readable permissions from the home directory (`chmod o-r`), and enforcing strict password lifecycles (14-day maximum, 30-day inactivity lockout) using the `chage` utility[cite: 7].
*   Applied the "sticky bit" (`chmod +t`) to a shared reports directory, restricting file deletion rights exclusively to the file creators to prevent accidental or malicious data loss[cite: 7].
*   Established an authenticated Remote Desktop Protocol (RDP) session from Ubuntu to Windows using the Remmina client, securely mounting the local Linux filesystem to the Windows host[cite: 7].
*   Automated routine security patching by engineering an executable Bash script (`update`) and scheduling it to execute autonomously via a granular `crontab` configuration[cite: 7].

## 🛠️ Setup & Configuration Instructions

### Prerequisites
*   Oracle VirtualBox installed on a Windows 10 host[cite: 7].
*   Ubuntu 24.04.2 Desktop AMD64 ISO[cite: 7].

### Step-by-step Setup
1.  **VM Initialisation:**
    *   Create a new VM allocating 4096MB (4GB) RAM and a 25GB virtual hard disk[cite: 7].
    *   Set the Network Adapter to **Bridged Adapter**[cite: 7].
    *   Install Ubuntu, setting the hostname to `alpha`[cite: 7].
2.  **Network Configuration:**
    *   Use the CLI to assign a static IP. Update the `/etc/netplan/` YAML file with the IP (`192.168.68.51/22`), Gateway (`10.1.1.101`), and DNS (`10.1.1.110`)[cite: 7].
    *   Apply the configuration via `sudo netplan apply` and update `/etc/hosts` with the IPs and hostnames of both machines[cite: 7].
3.  **Interoperability:**
    *   Enable RDP on the Windows host[cite: 7].
    *   Install Remmina on Ubuntu: `sudo apt install remmina remmina-plugin-rdp`[cite: 7].
    *   Connect to Windows and map the local Linux folder via Remmina's shared folder settings[cite: 7].
4.  **User & Permissions Setup:**
    *   Add user: `sudo adduser fblack`[cite: 7].
    *   Remove world-read permissions: `sudo chmod o-r /home/fblack`[cite: 7].
    *   Set policies: `sudo chage -E 2030-10-10 -m 7 -M 14 -I 30 -W 7 fblack`[cite: 7].
    *   Apply sticky bit to reports: `chmod +t ~/reports`[cite: 7].
5.  **Automation Setup:**
    *   Create `update` script containing `sudo apt update && sudo apt upgrade -y`[cite: 7].
    *   Make executable: `chmod +x update`[cite: 7].
    *   Add to crontab via `crontab -e`: `0 5 1 10 5 /home/username/update`[cite: 7].

## 📄 Project Documentation
*   [`ITLIA0-44-Formative_Project.pdf`](docs/ITLIA0-44-Formative_Project.pdf) - Complete academic submission documenting static IP assignment, IAM policy enforcement, automated patching via crontab, and cross-platform RDP configuration.

## 🔐 Relevance to Security Awareness Training
When training staff on password policies, telling them they "must change it every 14 days" often sounds like arbitrary IT punishment. In this project, I configured the exact backend tools (`chage`) that enforce these lifecycles. During a workshop, I use this backend knowledge to tell a practical story: these lockouts aren't designed to annoy staff; they mathematically close the window of opportunity for an attacker who might have compromised a password without the user's knowledge. Showing how easily a folder can be locked down (`chmod o-r`) or protected from deletion (`chmod +t`) also reinforces why saving sensitive data on public desktops is a massive risk. It bridges the gap between "annoying company policy" and "active threat defence."

## 📜 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
