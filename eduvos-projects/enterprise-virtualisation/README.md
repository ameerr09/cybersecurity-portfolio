# Malware Isolation & Disaster Recovery in a Virtualised Enterprise Environment

![Status: Completed](https://img.shields.io/badge/Status-Completed-success)
![Course: Higher Certificate](https://img.shields.io/badge/Course-Higher_Certificate-blue)
![Focus: Infrastructure Security](https://img.shields.io/badge/Focus-Infrastructure_Security-orange)

## 📌 Project Overview
Designed and deployed a secure virtualised enterprise environment using Oracle VirtualBox to consolidate physical infrastructure for a simulated cybersecurity firm. Evaluated leading enterprise hypervisors to deliver a cost-benefit analysis proving a 30% reduction in energy consumption and a 40% decrease in administrative overhead. Executed disaster recovery simulations and malware isolation protocols to validate system resilience against operational disruption and lateral threat movement.

## 🏗️ Architecture & Topology
The proof-of-concept simulates a consolidated data centre featuring:
*   **Host Environment:** Oracle VirtualBox
*   **Virtual Workload 1 (Web Server):** Windows Server 2022 / Apache (via XAMPP)
*   **Virtual Workload 2 (Database Server):** Windows Server 2022 / MySQL (via XAMPP)
*   **Network Isolation:** Manual network adapter disconnection protocols to quarantine compromised instances and secure internal database queries simulating a first-responder isolation procedure equivalent to physical cable removal in a live incident.

## 💻 Technologies Used
*   **Hypervisors Evaluated:** VMware vSphere, Microsoft Hyper-V, Oracle VirtualBox
*   **Hypervisor Selected:** Oracle VirtualBox
*   **Operating Systems:** Windows Server 2022
*   **Core Concepts:** Hardware Consolidation, Resource Pooling, Live Migration, Snapshotting, Virtual Networking

## 🚀 Key Implementations
*   Allocated dynamic CPU and RAM resources to active Windows Server 2022 virtual machines and monitored performance metrics using Windows Resource Monitor to validate load balancing under stress.
*   Executed snapshot-based disaster recovery by terminating primary MySQL services and restoring the previous machine state to prove zero-data-loss recovery capabilities.
*   Simulated workload migration between Oracle VirtualBox hosts using shared folders to confirm seamless operational continuity during hardware transitions.
*   Quarantined a simulated malware infection (`malicious_script.ps1`) by disabling the host network adapter to demonstrate successful network isolation and prevent lateral movement to critical database servers.

## 🛠️ Setup & Deployment Instructions
To replicate this proof-of-concept in a lab environment:

### Prerequisites
*   A physical host machine with hardware virtualisation enabled (VT-x/AMD-V).
*   Minimum 16GB RAM and 4 Cores dedicated to the hypervisor.
*   Oracle VirtualBox 7.1.8+.

### Step-by-step Setup
1.  **Hypervisor Installation:** Install and configure Oracle VirtualBox on the host machine.
2.  **VM Provisioning:**
    *   Deploy VM1 (Web Server) using Windows Server 2022 and install Apache via XAMPP.
    *   Deploy VM2 (Database Server) using Windows Server 2022 and install MySQL via XAMPP.
3.  **Testing Procedures:**
    *   Run `malicious_script.ps1` to simulate a high-CPU malware payload.
    *   Isolate the infected machine by navigating to VirtualBox Network settings and unticking "Enable Network Adapter".
    *   Verify isolation by executing continuous ping commands from the uninfected Web Server to the Database Server IP.

## 📄 Project Documentation
Comprehensive reports and planning documents are available in the `/docs` directory:
*   [`A+-Enterprise-Virtualisation-&-Malware-Isolation-lab.pdf`](eduvos-projects/enterprise-virtualisation/docs/A+-Enterprise-Virtualisation-&-Malware-Isolation-lab.pdf) - Complete project documentation including hypervisor comparative analysis, step-by-step migration planning, ROI cost-benefit calculations, and deployment risk assessments.

## 🔐 Relevance to Security Awareness Training
Most employees have no mental model of how ransomware spreads — they assume it's an IT problem, not a behaviour problem. This project demonstrates exactly how fast a compromised machine can reach critical systems when network isolation is delayed. That simulation is the foundation of a concrete training module: showing non-technical staff the 90-second window between "something looks wrong" and "the database is encrypted" makes the case for immediate reporting better than any policy document.

## 📜 License
This project is licensed under the [MIT License](cybersecurity-portfolio/LICENSE).
