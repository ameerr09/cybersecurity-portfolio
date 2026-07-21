# Detecting Network Intrusions and Brute-Force Attacks: Enterprise Security Lab

![Status: Completed](https://img.shields.io/badge/Status-Completed-success)
![Course: Higher Certificate](https://img.shields.io/badge/Course-Higher_Certificate-blue)
![Focus: Security_Operations](https://img.shields.io/badge/Focus-Security_Operations-red)

## 📌 Project Overview
Engineered an isolated enterprise network environment using Windows Server 2022 and Kali Linux to execute and subsequently defend against targeted cyber attacks[cite: 3, 4]. Executed offensive reconnaissance, stealth scanning, and brute-force credential attacks to compromise a misconfigured FTP service[cite: 4]. Deployed Snort as a host-based Intrusion Detection System (IDS), authoring custom detection rules and rate-limiting logic to successfully intercept and log the malicious network traffic[cite: 4].

## 🏗️ Architecture & Lab Topology
The environment operates on an isolated virtual network (`192.168.20.0/24`)[cite: 3]:
*   **Target Machine (Domain Controller & FTP Server):** Windows Server 2022 (`DC.ignite.net`) `192.168.20.1`[cite: 4]
*   **Attacker Machine:** Kali Linux `192.168.20.2`[cite: 4]
*   **Network Gateway/DNS:** `192.168.20.1`[cite: 3]

## 💻 Technologies & Tools Used
*   **Offensive Security:** Kali Linux, Nmap, Metasploit Framework, Custom Wordlists[cite: 3]
*   **Defensive Security:** Snort (Intrusion Detection System), Wireshark (Packet Analysis)[cite: 3]
*   **Vulnerability Management:** Tenable Nessus Essentials[cite: 3]
*   **Infrastructure:** Windows Server 2022, Active Directory, IIS (FTP Services), Windows Defender Firewall[cite: 3]

## 🚀 Key Implementations
*   Captured and analysed network traffic in Wireshark during Nmap reconnaissance sweeps, applying targeted display filters (`tcp.flags.syn == 1` and `tcp.flags.fin == 1`) to isolate specific scanning behaviours[cite: 4].
*   Brute-forced administrative credentials on a purposefully misconfigured IIS FTP server using Metasploit's `ftp_login` module alongside custom dictionary lists[cite: 4].
*   Executed a Tenable Nessus basic network scan against the domain controller, identifying medium-severity (CVSS 5.0) web server vulnerabilities and detailing patching prioritisation[cite: 4].
*   Authored custom Snort IDS logic (`local.rules`) to flag inbound FTP connections and stealth `FIN` scans[cite: 4]. 
*   Implemented event thresholding (`detection_filter: track by_src, count 5, seconds 5`) within Snort to prevent alert flooding and log exhaustion[cite: 4].

## 🛠️ Setup & Configuration Instructions
To replicate this security lab environment:

### Prerequisites
*   A hypervisor (VirtualBox or VMware)[cite: 3].
*   ISOs for Windows Server 2022 and Kali Linux[cite: 3].

### Lab Initialisation
1.  **Target Provisioning (Windows Server):**
    *   Install Windows Server 2022, rename the machine to `DC`, and assign the static IP `192.168.20.1`[cite: 4].
    *   Promote the server to a Domain Controller for the `ignite.net` forest[cite: 4].
    *   Install IIS and configure an FTP site named "IGNITE" bound to port 21 (No SSL, Basic Authentication, Read/Write permissions)[cite: 4].
    *   Configure Windows Defender Firewall to allow File/Printer Sharing and inbound TCP Port 21 traffic[cite: 4].
2.  **Attacker Provisioning (Kali Linux):**
    *   Install Kali Linux and assign the static IP `192.168.20.2` via `/etc/network/interfaces`[cite: 4].
3.  **Execution & Scanning:**
    *   Run Wireshark on the Windows Server to begin packet capture[cite: 4].
    *   From Kali, execute host discovery and full port scans: `nmap -sn 192.168.20.0/24` and `nmap -p- 192.168.20.1`[cite: 4].
    *   Execute a stealth FIN scan from Kali: `nmap -sF 192.168.20.1`[cite: 4].
    *   Run a Nessus Basic Network Scan targeting `192.168.20.1`[cite: 4].
4.  **Snort IDS Configuration:**
    *   Install Snort on the Windows Server[cite: 4].
    *   Update `snort.conf` to set `ipvar HOME_NET` to `192.168.20.1/32`[cite: 4].
    *   Add custom alert and detection filter rules to `local.rules` for FTP and FIN scan detection[cite: 4].

## 📄 Project Documentation
*   [`ITVSA0-44-Formative_Assessment.pdf`](docs/ITVSA0-44-Formative_Assessment.pdf) - Comprehensive lab documentation, including Wireshark traffic captures, Metasploit exploitation logs, Nessus vulnerability reports, and Snort configuration syntax.

## 🔐 Relevance to Security Awareness Training
Imagine standing in front of a room of non-technical staff and telling them: "Hackers do not just magically bypass our front door; they rattle every single window first." In this project, I mapped exactly what that "rattling" looks like on the network level. By showing employees a live Snort alert firing fifty times a second because an automated tool is trying to guess an FTP password, the abstract idea of "use a complex password" becomes a visible, urgent reality. Understanding how rapidly tools like Metasploit compromise weak credentials allows me to confidently explain *why* we enforce account lockouts—turning a frustrating IT policy into a logical defence mechanism the staff actively supports.

## 📜 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## ⚠️ Ethical Disclaimer
**Educational Purposes Only.** All reconnaissance, exploitation, and vulnerability scanning activities documented in this repository were performed in a strictly isolated, locally hosted lab environment for educational purposes[cite: 3]. Unauthorised penetration testing or network scanning against systems you do not own or have explicit permission to test is illegal[cite: 3].
