# Project 01 - Create and Deploy an Azure Resource Manager (ARM) Template

## Project Description
**Create and deploy an Azure Resource Manager template**, including parameters and outputs.

This project demonstrates building an ARM template from scratch, adding a real resource, making it reusable with parameters, implementing validation, and returning outputs.

## Resource Group
- **Name**: `rg-chiji-arm-demo`
- **Location**: `southafricanorth`

## Technologies Used
- Azure Resource Manager (ARM) Templates (JSON)
- Azure PowerShell
- Visual Studio Code
- Azure Portal

## Journey & Screenshots

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

## Key Learnings
- ARM template structure and syntax
- Using **Parameters** for reusability and environment flexibility
- Input validation with `allowedValues`, `minLength`, and `maxLength`
- Using the `reference()` function in **Outputs**
- Idempotent deployments (safe to run multiple times)
- Importance of Infrastructure as Code (IaC)

## Status
**✅ Completed**
