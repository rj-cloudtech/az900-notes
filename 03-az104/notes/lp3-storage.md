# AZ-104: Azure Administrator Associate
## Learning Path 3: Implement and manage storage in Azure

  - **AZ-104 Started:** 11-4-2026
  - **AZ-104 Exam passed:** 

  ---
  
## Inhoudsopgave

### Learning Path 3: Implement and manage storage in Azure

- [Module 1: Configure storage accounts ](#module-1-Configure-storage-accounts)

   ---

## Learning Path 3: Implement and manage storage in Azure
### Module 1: Configure storage accounts 

**Implement Azure Storage**
  - Blob (Binary Large Object) Storage: Object storage voor ongestructeerde data (tekst, Binair). Ideaal voor: Afbeeldingen/documenten naar browsers serveren, streaming video/aduio, backup en archivering. Toegankeljk via HTTP/HTTPS, REST API, PowerShell, CLI of client libraries
  - Azure Files: Highly available network file shares via SMB of NFS protocol. Meerdere VMs kunnen dezelfde bestanden lezen en schrijven. Geschikt voor migratie van on-premises apps die file shares gebruiken.
  - Queue Storage: Berichten opslaan voor asynchrone verwerking. Max 64 KB per bericht, een queue kan miljoenen berichten bevatten.
  - Table Storage: Schemaless NoSQL key/attribute store voor gestructureerde, niet-relationele data. Goedkoper dan traditionele SQL voor vergelijkbare datavolumes. Maakt deel uit van Azure Cosmos DB





**Explore Azure Storage services**
  - Standard: Backed by HDD, laagste kosten per GB, geschikt voor bulk storage of infrequent access
  - Premium: Backed by SSD, consistent lage latency, geschikt voor I/O intensieve workloads zoals databases

  - Conversie tussen Standard en Premium is niet mogelijk. Je moet een nieuw account aanmaken en data kopieren. Alle storage accounts zijn versleuteld via Storage Service Engryption (SSE)


| Account type | Ondersteunde services | Redundancy | Gebruik |
|---|---|---|---|
| Standard general-purpose v2 | Blob, Queue, Table, Azure Files | LRS, GRS, RA-GRS, ZRS, GZRS, RA-GZRS | Standaard voor de meeste scenario's |
| Premium block blobs | Blob (incl. Data Lake Storage) | LRS, ZRS | Hoge transactiesnelheid, kleine objecten, lage latency |
| Premium file shares | Azure Files | LRS, ZRS | Enterprise file shares, SMB én NFS ondersteuning |
| Premium page blobs | Page blobs only | LRS only | OS disks, VM data disks, databases |


  - Legacy account types GPv1, BlobStorage) worden niet meer aanbevolen. Upgrade naar General-purpose v2 via portal, CLI of PowerShell
  - 
  - 
  - 
  - 
  - 
  - 
  - 
  - 



  

**Determine storage account types**
  - 
  - 
  - 
  - 
  - 
  - 



  
**Determine replication strategies**
  - 
  - 
  - 
  - 
  - 
  - 


  
**Access storage**
  - 
  - 
  - 
  - 
  - 
  - 
  - 

 

**Secure storage endpoints**
  - 
  - 
  - 
  - 
  - 
  - 
  - 


---

## Learning Path 3: Implement and manage storage in Azure
### Module 2: Configure Azure Blob Storage

  - 
  -  
  -  
  -  
  -  
  -  
  -  
  -  
  -  
  -  
  -  


  ---


## Learning Path 3: Implement and manage storage in Azure
### Module 3: Configure Azure Storage security

  - 
  -  
  -  
  -  
  -  
  -  
  -  
  -  
  -  
  -  
  -  



  ---



## Learning Path 3: Implement and manage storage in Azure
### Module 4: Configure Azure Files 


  - 
  -  
  -  
  -  
  -  
  -  
  -  
  -  
  -  
  -  
  -  

