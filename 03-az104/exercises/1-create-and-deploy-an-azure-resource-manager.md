# Exercise 1. Create and deploy an Azure Resource Manager template

- Learning path 1.: AZ-104: Prerequisites for Azure administrators
- Module: 1. Deploy Azure infrastructure by using JSON ARM templates

In deze oefening maak ik een ARM template aan in VSCode, deploy ik deze naar Azure, en voeg ik een storage account toe als resource. Ik heb deze oefening uitgevoerd met **Azure PowerShell** in de VSCode terminal. Een tweede uitvoering met **Azure CLI** volgt.

---

## Uitvoering 1 — Azure PowerShell (VSCode terminal, KDE Neon Linux)

### Task 1 Resource Group aanmaken

```powershell
New-AzResourceGroup -Name exercise1 -Location westeurope
```

### Task 2 Blank ARM template aanmaken en deployen

`azuredeploy.json` aangemaakt in VSCode met alle verplichte secties maar zonder resources.

```powershell
$templateFile="azuredeploy.json"
$today=Get-Date -Format "MM-dd-yyyy"
$deploymentName="blanktemplate-"+"$today"
New-AzResourceGroupDeployment -Name $deploymentName -ResourceGroupName exercise1 -TemplateFile $templateFile
```

```
DeploymentName          : blanktemplate-04-14-2026
ResourceGroupName       : exercise1
ProvisioningState       : Succeeded
Timestamp               : 4/14/2026 7:37:32 PM
Mode                    : Incremental
```

In de Azure portal gecontroleerd onder **Resource groups > exercise1 > Deployments**: 1 Succeeded.

### Task 3 Storage account toevoegen aan de ARM template

`azuredeploy.json` bijgewerkt met een `Microsoft.Storage/storageAccounts` resource met een globally unique naam.

```powershell
$templateFile="azuredeploy.json"
$today=Get-Date -Format "MM-dd-yyyy"
$deploymentName="addstorage-"+"$today"
New-AzResourceGroupDeployment -Name $deploymentName -ResourceGroupName exercise1 -TemplateFile $templateFile
```

```
DeploymentName          : addstorage-04-14-2026
ResourceGroupName       : exercise1
ProvisioningState       : Succeeded
Timestamp               : 4/14/2026 7:43:15 PM
Mode                    : Incremental
```

In de Azure portal gecontroleerd: 2 Succeeded deployments zichtbaar. Storage account succesvol aangemaakt.

### Task 4 Clean up

```powershell
Remove-AzResourceGroup -Name exercise1 -Force -AsJob
```

---

## Uitvoering 2 — Azure CLI (Konsole, KDE Neon Linux)

> Volgt

---
