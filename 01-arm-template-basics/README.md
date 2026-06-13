# Project - Basic ARM Template Deployment

## Description
This project demonstrates creating and deploying Azure resources using an **Azure Resource Manager (ARM)** JSON template as part of the AZ-104 training.

## Resources Deployed
- Storage Account (or Virtual Network / other resource from the exercise)

## Technologies Used
- Azure Resource Manager (ARM Templates)
- JSON
- Azure PowerShell (`New-AzResourceGroupDeployment`)
- VS Code with Azure Resource Manager Tools extension
- Azure Portal (Export Template feature)

## Deployment Steps
1. Created a resource manually in the Azure Portal
2. Exported the resource as an ARM template (`azuredeploy.json`)
3. Opened and reviewed the template in VS Code
4. Deployed the template using PowerShell
5. Verified the deployment in the Azure Portal
6. Deleted the resources to stay in the free tier

## Commands Used
```powershell
# Connect to Azure
Connect-AzAccount

# Deploy the ARM template
New-AzResourceGroupDeployment `
  -ResourceGroupName "rg-arm-demo" `
  -TemplateFile "azuredeploy.json"
