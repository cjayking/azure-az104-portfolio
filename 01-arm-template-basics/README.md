# Project 01 - Create and Deploy a Basic ARM Template

## Description
**Create and deploy an Azure Resource Manager template**.  
This project demonstrates creating a basic ARM template from scratch, deploying it using Azure PowerShell, and understanding the template structure.

## Exercise Objectives Completed
- Created `azuredeploy.json` with the full ARM template skeleton
- Deployed the template using `New-AzResourceGroupDeployment`
- Verified the deployment in Azure Portal
- Understood all main sections of an ARM template (`parameters`, `variables`, `resources`, `outputs`, etc.)

## Technologies Used
- Azure Resource Manager (ARM) Templates
- JSON
- Visual Studio Code
- Azure PowerShell (`Connect-AzAccount`, `New-AzResourceGroupDeployment`)
- Azure Portal

## Steps Followed (from Microsoft Learn)

1. Created a new file `azuredeploy.json` in VS Code
2. Added the basic ARM template skeleton
3. Opened PowerShell terminal in VS Code
4. Connected to Azure using `Connect-AzAccount`
5. Created a Resource Group (`rg-arm-exercise`)
6. Deployed the template using `New-AzResourceGroupDeployment`
7. Verified the successful deployment in the Azure Portal

## Files
- [`azuredeploy.json`](./azuredeploy.json) — Basic ARM template

## Deployment Commands Used

```powershell
Connect-AzAccount

New-AzResourceGroup -Name "rg-chiji-arm-demo" -Location "southafricanorth"
Set-AzDefault -ResourceGroupName "rg-chiji-arm-demo"

$templateFile = "azuredeploy.json"
$today = Get-Date -Format "MM-dd-yyyy"
$deploymentName = "blanktemplate-" + $today

New-AzResourceGroupDeployment `
  -Name $deploymentName `
  -TemplateFile $templateFile
