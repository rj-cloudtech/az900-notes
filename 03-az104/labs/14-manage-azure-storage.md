# Exercise 14 Manage Azure Storage
- Learning path 3.: AZ-104: Implement and manage storage in Azure
- Module: 3. Configure Azure Storage security

---

## Task 1 Storage account aanmaken en configureren

Uitgevoerd via **Azure portal > Storage accounts > + Create**

| Setting | Value |
|---|---|
| Resource group | exercise14 |
| Storage account name | storage14ioio |
| Region | West Europe |
| Redundancy | Geo-redundant storage (GRS) + read access enabled |
| Public network access | Disabled |

Redundancy gecontroleerd:

| Location | Type | Status |
|---|---|---|
| West Europe | Primary | Available |
| North Europe | Secondary | Available |

Lifecycle management rule aangemaakt: blobs die meer dan 30 dagen niet gewijzigd zijn worden verplaatst naar Cool storage.

---

## Task 2 Secure blob storage aanmaken en configureren

Container aangemaakt:

| Setting | Value |
|---|---|
| Name | data |
| Public access level | Private |

Immutable blob storage policy ingesteld:

| Setting | Value |
|---|---|
| Policy type | Time-based retention |
| Retention period | 180 days |

Bestand geüpload:

| Setting | Value |
|---|---|
| Bestand | cloud.jpg |
| Blob type | Block blob |
| Block size | 4 MiB |
| Access tier | Hot |
| Upload folder | securitytest |

URL getest in InPrivate browser:

```
https://storage14ioio.blob.core.windows.net/data/securitytest/cloud.jpg
```

Resultaat:

```xml
<Error>
  <Code>PublicAccessNotPermitted</Code>
  <Message>Public access is not permitted on this storage account.</Message>
</Error>
```

SAS token gegenereerd met Read permissie, start gisteren, vervalt morgen. Blob toegankelijk via SAS URL in InPrivate browser.

---

## Task 3 Secure Azure File storage aanmaken en configureren

File share aangemaakt:

| Setting | Value |
|---|---|
| Name | share1 |
| Access tier | Transaction optimized |
| Backup | Disabled |

Bestand geüpload via Storage Browser.

VNet aangemaakt (`vnet1`) met service endpoint voor `Microsoft.Storage` op het Default subnet. Storage account netwerktoegang beperkt tot `vnet1` — eigen client IP verwijderd.

Storage Browser na netwerkrestrictie:

```
Error 403 — This request is not authorized to perform this operation.
This storage account's 'Firewalls and virtual networks' settings may be blocking access.
```

Verwacht gedrag — toegang is correct geblokkeerd omdat verbinding niet via `vnet1` loopt.

---

## Copilot prompts uitgevoerd

- PowerShell script gegenereerd voor aanmaken storage account + blob container
- Security checklist gegenereerd voor Azure Storage
- Vergelijkingstabel gegenereerd voor Azure Storage redundancy modellen

---

## Task 4 Clean up

Resource group `exercise14` verwijderd.

---
