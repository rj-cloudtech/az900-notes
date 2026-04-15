# Exercise 2. Add parameters and outputs to your Azure Resource Manager template

- Learning path 1.: AZ-104: Prerequisites for Azure administrators
- Module: 1. Deploy Azure infrastructure by using JSON ARM templates

In deze oefening voeg ik parameters en outputs toe aan de ARM template uit Exercise 1. Ik maak de template herbruikbaar door de storage account naam en SKU als parameters te definiëren, valideer de allowedValues door een ongeldige SKU te proberen, en voeg een output toe die de storage endpoints teruggeeft na deployment.

---

## Uitvoering — Azure PowerShell (VSCode terminal)

### Task 1 Resource Group aanmaken

```powershell
New-AzResourceGroup -Name exercise1 -Location westeurope
```

```
ResourceGroupName : exercise1
Location          : westeurope
ProvisioningState : Succeeded
ResourceId        : /subscriptions/69799361-14fa-4e9b-8b7f-e48e93f9e422/resourceGroups/exercise1
```

### Task 2 storageName parameter toevoegen en deployen

`azuredeploy.json` bijgewerkt: `parameters` sectie uitgebreid met `storageName` (type string, minLength 3, maxLength 24). De `name` en `displayName` in de resources sectie vervangen door `[parameters('storageName')]`.

Eerste poging mislukt: `{your-unique-name}` letterlijk ingevoerd — PowerShell interpreteert `{}` als script block. Oplossing: naam direct zonder accolades meegeven.

```powershell
$templateFile="azuredeploy.json"
$today=Get-Date -Format "MM-dd-yyyy"
$deploymentName="addnameparameter-"+"$today"
New-AzResourceGroupDeployment -Name $deploymentName -TemplateFile $templateFile -storageName rjstorageaccount1
```

```
DeploymentName          : addnameparameter-04-15-2026
ResourceGroupName       : exercise1
ProvisioningState       : Succeeded
Timestamp               : 4/15/2026 6:51:22 PM
Mode                    : Incremental
Parameters              :
                          storageName      String    "rjstorageaccount1"
```

### Task 3 storageSKU parameter toevoegen met allowedValues

`azuredeploy.json` bijgewerkt: `storageSKU` parameter toegevoegd aan de `parameters` sectie met `defaultValue: Standard_LRS` en een lijst van `allowedValues`. De `sku.name` in resources vervangen door `[parameters('storageSKU')]`.

**Deployment met geldige SKU (Standard_GRS):**

```powershell
$today=Get-Date -Format "MM-dd-yyyy"
$deploymentName="addSkuParameter-"+"$today"
New-AzResourceGroupDeployment -Name $deploymentName -TemplateFile $templateFile -storageName rjexercise1 -storageSKU Standard_GRS
```

```
DeploymentName          : addSkuParameter-04-15-2026
ResourceGroupName       : exercise1
ProvisioningState       : Succeeded
Timestamp               : 4/15/2026 6:56:55 PM
Mode                    : Incremental
Parameters              :
                          storageName      String    "rjexercise1"
                          storageSKU       String    "Standard_GRS"
```

**Deployment met ongeldige SKU (Basic) — verwachte fout:**

```powershell
New-AzResourceGroupDeployment -Name $deploymentName -TemplateFile $templateFile -storageName rjexercise1 -storageSKU Basic
```

```
New-AzResourceGroupDeployment: Error: Code=InvalidTemplate;
Message=Deployment template validation failed: 'The provided value for the template
parameter 'storageSKU' is not valid. The value 'Basic' is not part of the allowed
value(s): Standard_LRS,Standard_GRS,Standard_RAGRS,Standard_ZRS,Premium_LRS,
Premium_ZRS,Standard_GZRS,Standard_RAGZRS'.
```

Deployment mislukt zoals verwacht — de `allowedValues` validatie werkt correct.

### Task 4 Output toevoegen aan de ARM template

`azuredeploy.json` bijgewerkt: `outputs` sectie uitgebreid met `storageEndpoint` die de `primaryEndpoints` van het storage account teruggeeft via de `reference()` functie.

```powershell
$today=Get-Date -Format "MM-dd-yyyy"
$deploymentName="addOutputs-"+"$today"
New-AzResourceGroupDeployment -Name $deploymentName -TemplateFile $templateFile -storageName rjexercise1 -storageSKU Standard_LRS
```

```
DeploymentName          : addOutputs-04-15-2026
ResourceGroupName       : exercise1
ProvisioningState       : Succeeded
Timestamp               : 4/15/2026 6:59:29 PM
Mode                    : Incremental
Parameters              :
                          storageName      String    "rjexercise1"
                          storageSKU       String    "Standard_LRS"
Outputs                 :
                          storageEndpoint  Object    {
                            "dfs":   "https://rjexercise1.dfs.core.windows.net/",
                            "web":   "https://rjexercise1.z6.web.core.windows.net/",
                            "blob":  "https://rjexercise1.blob.core.windows.net/",
                            "queue": "https://rjexercise1.queue.core.windows.net/",
                            "table": "https://rjexercise1.table.core.windows.net/",
                            "file":  "https://rjexercise1.file.core.windows.net/"
                          }
```

In de Azure portal gecontroleerd onder **Resource groups > exercise1 > Deployments > addOutputs**: output zichtbaar.

### Task 5 Clean up

```powershell
Remove-AzResourceGroup -Name exercise1 -Force -AsJob
```

---
