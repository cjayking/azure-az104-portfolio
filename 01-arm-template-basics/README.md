# Project 01 - Create and Deploy an Azure Resource Manager (ARM) Template

## Project Description
**Create and deploy an Azure Resource Manager template** including parameters and outputs.

This project demonstrates creating an ARM template from scratch, making it flexible with parameters, adding validation, and returning outputs.

## Objectives Completed
- Created a basic ARM template skeleton
- Added a Storage Account resource
- Made the template reusable using **Parameters** (`storageName`, `storageSKU`)
- Implemented input validation with `allowedValues`
- Added **Outputs** to return storage endpoints
- Demonstrated **idempotency** (updating existing resources)
- Tested both valid and invalid parameter values

## Resource Group
- **Name**: `rg-chiji-arm-demo`
- **Location**: `southafricanorth`

## Technologies Used
- Azure Resource Manager (ARM) Templates (JSON)
- Azure PowerShell (`New-AzResourceGroupDeployment`)
- Visual Studio Code
- Azure Portal

## Step-by-Step Journey

| Step | Description | Deployment Name Pattern |
|------|-------------|-------------------------|
| 1 | Basic empty template deployment | `blanktemplate-...` |
| 2 | Added Storage Account (hardcoded) | — |
| 3 | Added `storageName` parameter | `addnameparameter-...` |
| 4 | Added `storageSKU` parameter + allowed values | `addSkuParameter-...` |
| 5 | Tested invalid SKU (`Basic`) | `addSkuParameter-...` (Failed) |
| 6 | Added Outputs (`storageEndpoint`) | `addOutputs-...` |

## Final ARM Template (`azuredeploy.json`)

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "storageName": {
      "type": "string",
      "minLength": 3,
      "maxLength": 24,
      "metadata": {
        "description": "The name of the Azure storage resource"
      }
    },
    "storageSKU": {
      "type": "string",
      "defaultValue": "Standard_LRS",
      "allowedValues": [
        "Standard_LRS", "Standard_GRS", "Standard_RAGRS", "Standard_ZRS",
        "Premium_LRS", "Premium_ZRS", "Standard_GZRS", "Standard_RAGZRS"
      ]
    }
  },
  "resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "apiVersion": "2025-01-01",
      "name": "[parameters('storageName')]",
      "tags": {
        "displayName": "[parameters('storageName')]"
      },
      "location": "[resourceGroup().location]",
      "kind": "StorageV2",
      "sku": {
        "name": "[parameters('storageSKU')]"
      }
    }
  ],
  "outputs": {
    "storageEndpoint": {
      "type": "object",
      "value": "[reference(parameters('storageName')).primaryEndpoints]"
    }
  }
}
```

## Screenshots
![1. Starting Point](./screenshots/01-starting-point.png)  
**Starting Point** – Empty ARM template, Resource Group creation, and first blank deployment

![2. Adding Storage Account](./screenshots/02-hardcoded-storage.png)  
**Adding Storage Account Resource** – Hardcoded version

![3. Parameters & Outputs](./screenshots/03-parameters-and-outputs.png)  
**Adding Flexibility** – Parameters (`storageName`, `storageSKU` with validation) and Outputs

![4. Successful Deployment](./screenshots/04-deployment-success.png)  
**Successful Deployment** – Showing parameters passed and outputs returned

![5. Multiple Deployments](./screenshots/05-deployments-list.png)  
**Multiple Successful Deployments** – Demonstrating idempotency in Azure Portal
