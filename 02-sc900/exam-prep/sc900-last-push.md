# SC-900 — Last Push Study Notes

This document summarizes the topics I got wrong most often across all practice exams.
Read this the morning before the real exam. Focus on the exam-style traps section —
those cost the most points not because of missing knowledge but because of subtle wording.

---

## 1. Sentinel — three components, three roles

| Component | Role | Key word |
|---|---|---|
| Analytics rules | Detects threats and creates incidents | detect |
| Automation rules | Determines WHEN playbooks are triggered | orchestrate / trigger |
| Playbooks | EXECUTES response actions via Azure Logic Apps | execute / perform |

**Exam trap:** "execute the actual response actions" → always Playbooks, never Automation rules.

---

## 2. eDiscovery Standard vs Premium

| Feature | Standard | Premium |
|---|---|---|
| Search | ✓ | ✓ |
| Holds | ✓ | ✓ |
| Export | ✓ | ✓ |
| Review sets | ✗ | ✓ |
| Conversation threading | ✗ | ✓ |
| Near-duplicate detection | ✗ | ✓ |
| OCR | ✗ | ✓ |

**Remember:** If the question mentions review sets, threading, or analytics → always Premium.

---

## 3. Audit Standard vs Premium

| Feature | Standard | Premium |
|---|---|---|
| Retention | 180 days | 1 year (10 years with add-on) |
| MailItemsAccessed | ✗ | ✓ |
| SharePoint search query logging | ✗ | ✓ |
| Higher API bandwidth | ✗ | ✓ |

**Remember:** Forensic investigation into mailbox access or search queries → always Audit Premium.

---

## 4. License tiers P1 vs P2

| Feature | License |
|---|---|
| Conditional Access | P1 |
| SSPR | P1 |
| Custom banned password list | P1 |
| Custom roles | P1 |
| PIM | **P2** |
| Identity Protection | **P2** |
| Entitlement Management / Access packages | **P2** |
| Access Reviews | **P2** |

**Rule of thumb:** Everything involving just-in-time access, risk detection, or governance = P2.

---

## 5. Purview solutions — choosing the right product

| Situation | Solution |
|---|---|
| Block data from leaving the organization | DLP |
| Route flagged messages to a human reviewer | Communication Compliance |
| Detect risky employee behavior | Insider Risk Management |
| Collect documents for a legal case or audit | eDiscovery |
| Improve compliance score | Compliance Manager |
| Classify and encrypt sensitive data | Sensitivity Labels |
| See where sensitive data is stored | Content Explorer |

---

## 6. Defender products — what they protect

| Product | Scope | Key words |
|---|---|---|
| Defender for Identity | On-premises Active Directory | lateral movement, credential theft |
| Defender for Endpoint | Laptops, phones, servers | EDR, ASR |
| Defender Vulnerability Management | CVEs and misconfigurations | CVE, misconfiguration |
| Defender for Cloud | Azure workloads | CSPM, CWPP, Secure Score |
| Defender for Cloud Apps | SaaS applications | CASB, shadow IT |
| Defender for Office 365 | Email and Teams | phishing, Safe Links, ZAP |

**Remember:** Misconfigurations are vulnerabilities → Vulnerability Management, not Endpoint.

---

## 7. Azure network — key words

- **SNAT** → Azure Firewall
- **SSL termination** → WAF
- **Distributed filtering within VNet** → NSG
- **Network segmentation per department** → VNet (not VPN)
- **VPN** = connects two networks together, not segmentation within Azure

---

## 8. Sentinel vs Defender for Cloud vs Defender XDR

- **Microsoft Sentinel** = SIEM + SOAR, collects from everywhere, cloud-native
- **Defender for Cloud** = CSPM (posture + Secure Score) + CWPP (runtime workload protection), focused on Azure and cloud
- **Defender XDR** = unified portal combining all Defender products

---

## 9. Edge knowledge Microsoft tests

- **Verified ID** → cryptographically signed credentials stored in a digital wallet (did:web trust system)
- **SCIM** → standard protocol for automated identity provisioning and deprovisioning
- **Honeytoken** → fake accounts used as bait in Defender for Identity to detect reconnaissance
- **Microsoft privacy principles** → control, transparency, security, strong legal protections, no content-based targeting, benefits to you
- **Security baselines** → apply Azure Security Benchmark guidance to specific services like Microsoft Entra

---

## 10. Exam-style traps — wording matters

| If you see this | Answer |
|---|---|
| "execute the actual response actions" | Playbooks — not automation rules |
| "guarantees legal compliance" | FALSE — a score is not a legal certification |
| "always", "never", "only", "guarantees" | Almost always signals a FALSE statement |
| "network segmentation per department" | VNet — not VPN |
| "container label protects all files inside" | FALSE — container labels do not propagate to files |
| "Security Reader can access Purview portal" | FALSE — Security Reader is a Defender portal role |
| "PIM is included in P1" | FALSE — PIM requires P2 |
| "SMS is the most secure MFA method" | FALSE — SMS is the least secure MFA method |
