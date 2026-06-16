# Project 01 - Create and Deploy an Azure Resource Manager (ARM) Template

## Description
**Create and deploy an Azure Resource Manager template** including parameters and outputs.

## Objectives Completed
- Created basic ARM template
- Added Storage Account resource
- Made template flexible using **parameters** (`storageName`, `storageSKU`)
- Added **outputs** to return storage endpoints
- Demonstrated idempotency (update existing resource)
- Tested input validation (`allowedValues`)

## Resource Group
- Name: `rg-chiji-arm-demo`
- Location: `southafricanorth`

## Technologies Used
- Azure Resource Manager (ARM) Templates
- Azure PowerShell
- Visual Studio Code
- Azure Portal

## Final Template Features
- Parameterized Storage Account name
- SKU selection with allowed values
- Dynamic location using `resourceGroup().location`
- Output of storage endpoints

## Deployment Examples

```powershell
New-AzResourceGroupDeployment `
  -Name $deploymentName `
  -TemplateFile "azuredeploy.json" `
  -storageName "chijistorage2026" `
  -storageSKU "Standard_LRS"
