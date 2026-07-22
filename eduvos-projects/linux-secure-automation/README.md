# Securing SME Infrastructure: Linux Permissions & Automated Disaster Recovery

![Status: Completed](https://img.shields.io/badge/Status-Completed-success)
![Course: Higher Certificate](https://img.shields.io/badge/Course-Higher_Certificate-blue)
![Focus: OS Configuration & Scripting](https://img.shields.io/badge/Focus-OS_Configuration_&_Scripting-orange)

## 📌 Project Overview
Designed and provisioned a dual-node Ubuntu virtual environment to demonstrate critical Linux system administration and disaster recovery protocols. The project proves how to mitigate internal security risks by enforcing strict access control lists (ACLs) via the command line. Furthermore, it details the development of an automated, redundant backup script engineered with active email alerting to detect and report silent data failures in small-to-medium enterprise (SME) environments.

## 🏗️ Architecture & Environment
The project environment consists of locally hosted virtual machines simulating an enterprise Linux deployment:
*   **Hypervisor:** Oracle VirtualBox 7.1.8
*   **Operating System:** Ubuntu 24.04.1 LTS
*   **VM Instance 1 (Linux2030):** Primary administration and scripting environment (3GB RAM, 60GB Virtual Disk)
*   **VM Instance 2 (PSG2024):** Secondary isolated instance (3GB RAM, 25GB Virtual Disk, NTFS partition)

## 💻 Technologies Used
*   **Operating System:** Linux (Ubuntu 24.04.1 LTS)
*   **Virtualisation:** Oracle VM VirtualBox
*   **Scripting & Alerting:** Bash / Shell Scripting, `mailutils`
*   **CLI Tools:** `nano`, `chmod`, `sort`, `mv`, `pwd`
*   **Troubleshooting Concepts:** Recovery Mode, `initramfs` diagnostics

## 🚀 Key Implementations
*   Enforced the Principle of Least Privilege by applying strict absolute file permissions (`chmod 700`) to sensitive backup directories, preventing unauthorised user access to critical data.
*   Developed an automated disaster recovery script (`backup.sh`) featuring dual-destination redundancy to mitigate localised storage failures.
*   Integrated automated email alerting (`mailutils`) into the backup lifecycle to ensure IT administration is immediately notified of silent backup failures, reducing Mean Time to Detect (MTTD) for data loss events.
*   Diagnosed and resolved simulated boot-level system failures, demonstrating rapid service restoration capabilities for enterprise Linux endpoints.

## 🛠️ Setup & Deployment Instructions
To replicate this environment and test the shell scripts:

### Prerequisites
*   Oracle VirtualBox 7.1.8+ installed on the host machine.
*   Ubuntu 24.04.1 LTS ISO image.

### Step-by-step Setup
1.  **Provision Virtual Machines:**
    *   Deploy VM 1 (`Linux2030`) with 3GB RAM and a 60GB virtual disk. Install Ubuntu 24.04.1 LTS.
    *   Deploy VM 2 (`PSG2024`) with 3GB RAM and a 25GB NTFS virtual disk.
2.  **CLI File Operations:**
    *   Navigate to the home directory and execute the foundational file management and sorting commands to organise the `Wildlife` directory.
    *   Restrict access using `sudo chmod 700 ~/Backup`.
3.  **Executing the Backup Script:**
    *   Install mail utilities: `sudo apt-get install mailutils`
    *   Create the script: `nano ~/backup.sh`
    *   Make the script executable: `chmod +x backup.sh`
    *   Run the script: `./backup.sh`

## 📄 Project Documentation & Media
*   [`backup.sh`](scripts/backup.sh) - The primary shell script handling dual-destination backups and email alerting.
*   [`ITLXA0-22-Formative_Assessment.pdf`](docs/ITLXA0-22-Formative_Assessment.pdf) - Full documentation of CLI operations, OS configurations, and script testing.
*   **Video Demonstration:** [Insert Unlisted YouTube Video Link Here] - A walkthrough explaining the diagnosis and recovery of Linux boot halts.

## 🔐 Relevance to Security Awareness Training
When consulting for small business owners, the most devastating threat is rarely a sophisticated foreign hacker—it is "silent failure" and insider risk. By demonstrating how a simple `chmod 700` command prevents unauthorised staff from snooping through sensitive HR backups, I can make the Principle of Least Privilege immediately tangible. Furthermore, showing a script that emails the IT team the exact second a backup fails helps business owners understand why "set it and forget it" data recovery policies routinely destroy companies during a ransomware attack. 

## 📜 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
