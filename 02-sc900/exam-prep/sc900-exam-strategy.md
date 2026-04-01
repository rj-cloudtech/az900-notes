# SC-900 Exam Strategy

## De rode draad voor elke vraag

Bij elke examenvraag de vraag:

| Onderwerp | Product |
|-----------|---------|
| Gebruiker / identiteit | Entra ID |
| Netwerk beschermen | Firewall / NSG / DDoS / Bastion / WAF |
| Cloud security posture | Defender for Cloud |
| Dreigingen detecteren en reageren | Microsoft Sentinel |
| Data / compliance | Microsoft Purview |

---

## De vier grote domeinen

### 1. Security, Compliance en Identity concepten
Begrijp de basisprincipes:
- **Zero Trust** — vertrouw niets, verifieer altijd
- **Defense in depth** — meerdere beveiligingslagen
- **Shared responsibility model** — wie is verantwoordelijk voor wat in de cloud?

### 2. Microsoft Identity en Access (Entra ID)
- Wie ben je? → **Authentication** (MFA, passwordless)
- Wat mag je? → **Authorization** (RBAC, Conditional Access)
- Hoe bescherm je identiteiten? → **Identity Protection, PIM**

### 3. Microsoft Security Solutions
- **Netwerk** → Firewall, NSG, DDoS Protection, Bastion, WAF
- **Cloud omgeving** → Defender for Cloud (CSPM / CWPP / DevSecOps)
- **Dreigingen detecteren** → Microsoft Sentinel (SIEM / SOAR)
- **Endpoints en workloads** → Microsoft Defender XDR, Defender plans
- **Geheimen en sleutels** → Azure Key Vault

### 4. Microsoft Compliance en Privacy (Purview)
- **Data kennen** → waar staat je data, hoe classificeer je het
- **Data beschermen** → labels, policies, DLP
- **Compliance beheren** → Compliance Manager
- **Privacy** → Service Trust Portal

---

## Veelgemaakte vergelijkingen

| | **NSG** | **Azure Firewall** |
|---|---|---|
| Type | Distributed filtering | Centralized firewall-as-a-service |
| Scope | Binnen één subscription/VNet | Meerdere subscriptions en VNets |
| Bescherming | Network layer | Network én application level |

| | **Defender for Cloud** | **Microsoft Sentinel** |
|---|---|---|
| Type | CNAPP | SIEM / SOAR |
| Focus | Cloud security posture en workload bescherming | Threat detection en response |
| Scope | Azure, multicloud en on-premises workloads | Enterprise-breed |

| | **Azure DDoS Protection** | **WAF** |
|---|---|---|
| Beschermt op | Layer 3 & 4 | Layer 7 |
| Tegen | Volumetric, protocol aanvallen | Application-layer aanvallen zoals HTTP Floods |
