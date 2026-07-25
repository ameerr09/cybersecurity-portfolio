# SecurityX Lab: Architecting Defences — Enterprise Risk, Cloud Security & Insider Threat Management

![Status: Completed](https://img.shields.io/badge/Status-Completed-success)
![Course: Higher Certificate](https://img.shields.io/badge/Course-Higher_Certificate-blue)
![Focus: Security_Governance](https://img.shields.io/badge/Focus-Security_Governance_&_Architecture-purple)

## 📌 Project Overview
Applied SecurityX-level enterprise security architecture principles to two simulated corporate scenarios — ABCTech and Delware Inc. — each presenting distinct strategic challenges. For ABCTech, evaluated cloud-based security offloading and designed a blockchain-backed financial reporting structure to provide cryptographically verifiable audit trails for global regulatory compliance. For Delware Inc., assessed the insider threat and access control risks introduced during a corporate acquisition, and diagnosed the SIEM interoperability failures caused by aggregating telemetry from legacy multi-vendor intrusion detection systems — identifying alert fatigue as the critical barrier to automated threat response.

## 🌐 Key Domains Explored
*   **Cloud Security Architecture:** Evaluating cloud-based hash matching (anti-malware/spam), cloud sandboxing for internal application testing, and cloud content filtering.
*   **Blockchain for Compliance:** Leveraging decentralised ledgers and cryptographic hashing to guarantee the immutable integrity of historical financial records for global auditing.
*   **Enterprise Risk Management (ERM):** Aligning security standards with business objectives and assessing human/personnel risks during corporate acquisitions.
*   **Security Operations (SecOps) Interoperability:** Addressing the challenges of aggregating data from legacy, multi-vendor Host-based Intrusion Prevention Systems (HIPS) and Network Intrusion Detection Systems (NIDS) into a modern SIEM appliance.

## 🚀 Key Implementations
*   Evaluated cloud hash matching and cloud sandboxing capabilities to offload endpoint processing while proactively filtering known malware and spam from the network.
*   Designed a blockchain integration strategy to secure financial data, using cryptographic hashes and decentralised consensus mechanisms to provide immutable, audit-ready records.
*   Analysed Enterprise Risk Management (ERM) frameworks (NIST CSF, ISO 27001) to map security controls against industry mandates like POPIA and PCI DSS.
*   Assessed insider threat vectors introduced during corporate acquisitions, highlighting the risks of disgruntled employees, orphaned legacy systems, and access control over-privileging.
*   Diagnosed multi-vendor SIEM integration roadblocks, identifying proprietary data formats and alert fatigue as critical barriers to automated threat response.

## 📊 Strategic Scenarios Addressed
The theoretical analysis covers the following business cases:
*   **ABCTech (Cloud & Blockchain):** Designing a cost-efficient cloud security offloading strategy and engineering a blockchain-backed financial reporting structure for global regulatory compliance.
*   **Delware Inc. (ERM & M&A):** Navigating the security and personnel risks of acquiring a smaller competitor while attempting to unify a fragmented, multi-vendor intrusion detection infrastructure into a cohesive SIEM environment.

## 📄 Project Documentation
*   [securityx-enterprise-risk.pdf](docs/securityx-enterprise-risk.pdf) - Comprehensive strategic analysis covering SECaaS adoption, decentralised financial ledgers, acquisition insider threats, and SIEM interoperability challenges.

## 🔐 Relevance to Security Awareness Training
When explaining insider threats and access control to HR or 
management during a merger, I use the Delware Inc. 
acquisition scenario from this project. I ask them: "When 
we buy a company, what happens to the IT admin who thinks 
he is getting fired next week but still holds the keys to 
the legacy database?" This shifts the conversation from 
abstract "M&A risk" to a very real, human problem. It helps 
non-technical leaders understand why we must immediately 
audit access privileges and unify SIEM logs — not just to 
tick a compliance box, but to ensure a disgruntled employee 
cannot silently exfiltrate our customer list before their 
exit interview. That view has 
reframed M&A security conversations from a compliance 
checkbox into an urgent operational priority — which is 
exactly what awareness training is designed to do.
## 📜 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
