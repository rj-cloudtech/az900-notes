# AZ-104: Azure Administrator Associate
## Learning Path 4: Deploy and manage Azure compute resources

  - **AZ-104 Started:** 11-4-2026
  - **AZ-104 Exam passed:**

---

## Inhoudsopgave

### Learning Path 4: Deploy and manage Azure compute resources

- [Module 1: Introduction to Azure virtual machines](#module-1-introduction-to-azure-virtual-machines)

---

## Learning Path 4: Deploy and manage Azure compute resources
### Module 1: Introduction to Azure virtual machines


**Compile a checklist for creating an Azure Virtual Machine**
  - Bij het aanmaken van een VM moet je rekening houden met 6 onderdelen:
    - Network: VNet, subnest, IP-ranges (niet-overlappend), NSGs voor traffic controle
    - VM naam: Max 64 tekens (Linux) of 15 tekens (Windows), gebruik een naamconvente
    - Locatie: Dichtstbijzijnde regio voor gebruikers, let op prijsverschillende en beschikbare hardware
    - VM grootte: Kies op basis van workload type
    - Disks: OS disk + data disk (aparte aanbevolen
    - Operating system
   
  - VM naamconventie elementen:
    
| Element | Voorbeeld | Beschrijving |
|---|---|---|
| Environment | dev, prod, QA | Identificeert de omgeving |
| Location | eus, jw | Identificeert de regio |
| Instance | 01, 02 | Voor meerdere instanties |
| Product/Service | service | Identificeert de applicatie |
| Role | sql, web, messaging | Identificeert de rol |

  - VM grootte opties:
    
| Optie | Gebruik |
|---|---|
| General purpose | Balanced CPU/memory — dev/test, kleine databases, web servers |
| Compute optimized | Hoge CPU/memory ratio — web servers, batch processen |
| Memory optimized | Hoge memory/CPU ratio — databases, caches, in-memory analytics |
| Storage optimized | Hoge disk throughput — databases |
| GPU | Graphics rendering, video editing, deep learning |
| High performance compute | Snelste CPU, optioneel high-throughput netwerk |

  - Kostenmodel:
    
| Resource | Kosten |
|---|---|
| Virtual network | Ja |
| NIC | Geen aparte kosten |
| IP adres | Ja |
| NSG | Geen aparte kosten |
| OS disk | Ja (standaard ~127 GiB) |
| Local disk | Geen kosten |
| OS licentie | Varieert (Linux goedkoper dan Windows) |

  - Compute kosten: Per minuut gefactureerd, gestopt + gedealloceerde VM kost geen compute
  - Storage kosten: Aparte gefactuurd van compute
  - Azure Hybrid Benefit: Bestaande licenties hergebruiken voor korting

  - Betaalopties compute:

| Optie | Beschrijving |
|---|---|
| Pay as you go | Per seconde, geen commitment, flexibel — geschikt voor korte of onvoorspelbare workloads |
| Reserved VM Instances (RI) | 1 of 3 jaar vooraf betalen — tot 72% goedkoper dan pay-as-you-go, geschikt voor continue workloads |

  - Disk types:

| | Ultra disk | Premium SSD v2 | Premium SSD | Standard SSD | Standard HDD |
|---|---|---|---|---|---|
| Type | SSD | SSD | SSD | SSD | HDD |
| Scenario | IO-intensief (SAP HANA, SQL, Oracle) | Productie, lage latency, hoge IOPS | Productie, performance-gevoelig | Web servers, dev/test | Backup, niet-kritiek |
| Max disk size | 65.536 GiB | 65.536 GiB | 32.767 GiB | 32.767 GiB | 32.767 GiB |
| Max throughput | 4.000 MB/s | 1.200 MB/s | 900 MB/s | 750 MB/s | 500 MB/s |
| Max IOPS | 160.000 | 80.000 | 20.000 | 6.000 | 2.000 |
| OS disk | Nee | Nee | Ja | Ja | Ja |


- [Exercise 15 Create a VM using the Azure portal](/03-az104/exercises/15-create-a-vm-using-the-azure portal.md)


**Describe the options available to create and manage an Azure Virtual Machine**
  - 7 manieren om VMs aan te maken en te beheren:

| Methode | Beschrijving |
|---|---|
| ARM templates | JSON-bestanden voor reproduceerbare deployments — exporteer vanuit bestaande VM via Automation > Export template |
| Azure CLI | Cross-platform command-line tool — `az vm create` |
| Azure PowerShell | PowerShell cmdlets — `New-AzVM` |
| Terraform | Infrastructure as Code via HCL syntax — Azure Terraform Provider |
| Azure REST API | HTTP-based API (GET, PUT, POST, DELETE, PATCH) voor programmatische toegang |
| Azure Client SDK | Wrapper rond REST API voor diverse talen (.NET, Java, Node.js, Python, Ruby, Go) |
| Azure VM Extensions | Kleine applicaties voor configuratie en automatisering na initiële deployment |


- Azure Automation services:
  - Process Automation: Automatiseer reacties op events via watcher tasks
  - Configuration Management: Track software updates via Microsoft Enpoint Configuration Manager
  - Update Management: Beheer updates en patches, plan installaties, controleer resultaten
 
- Auto=shutdown
  - Automatisch afsluiten van VMs op scheme (dagelijk of wekelijks)
  - Configureerbaar via VM > Operations > Auto-Shutdown
  - Bespaart kosten door VMs niet onnodig te laten draaien
    

**Manage the availability of your Azure VMs**
  - Availability: Percentage van de tijd dat een service beschikbaar is
  - Azure VMs draaien op fysieke servers: Bij een storing verplaatst Azure de VM automatisch naar een gezonde server maar dit kan enkele minuten duren

  - Availability opties:

| Optie | Beschrijving |
|---|---|
| Availability Zones | Fysiek gescheiden zones binnen een regio (3 per regio), elk met eigen power, netwerk en koeling |
| VM Scale Sets | Groep load-balanced VMs die automatisch schaalt op basis van vraag of schema. Geen kosten voor de scale set zelf |
| Azure Load Balancer | Verdeelt traffic over meerdere VMs — inbegrepen bij Standard tier VMs |
| Azure Storage redundancy | Meerdere kopieën van data voor bescherming tegen hardware-, netwerk- en stroomstoringen |
| Azure Site Recovery | Repliceert workloads van primaire naar secundaire locatie voor regionele failover — ondersteunt Azure, Hyper-V, VMware en fysieke servers |

  - Azure Site Recovery voordelen:
    - Geen secundair fysiek datacenter nodig: Azure als recovery bestemming
    - Eenvoudig failover testen zonder impact op productie
   
**Back up your virtual machines**
  - Azure Backup is een Backup-as-a-Service oplossing voor fysieke en virtuele machines. On-premises en in de cloud

  - Ondersteunde scenarios:
    - Files en folders op Windows (fysiek en virtueel)
    - Application-aware snapshots (VSS)
    - Microsoft server workloads: SQL Server, SharePoint, Exchange
    - Azure VMs (Windows en Linux)
    - Linux en Windows 10 client machines
   
  - Voordelen:
    - Automatic storage management: Pay-as-you-use, geef vooraf toegewezen storage
    - Unlimited scaling: Hoge beschikbaarheid via Azure platform
    - Multiple storage options: LRS (lokaal) of GRS (geo-redundant)
    - Unlimited data transfer: Geen kosten voor inbound/outbound data
    - Data encryption: veilige opslag en verzending
    - Application-consistent backup: Recovery point bevat alle benodigde data voor volledig herstel
    - Long-term retention: Geen tijdslimiet op bewaren van backups
   
  - Componenten:
    - Azure Backup agent
    - System Center Data Protection Manager
    - Azure Backup Server
    - Azure BAckup VM extension
   
  - Opslag: Recovery Services vault. Backed by Azure Storage blobs. Hier definieer je welke machines worden gebackupt en wanneer snapshots worden gemaakt













  
