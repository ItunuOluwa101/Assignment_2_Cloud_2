Deployment Guide for ARM Template
Prerequisites
Install Azure CLI (learn.microsoft.com in Bing).
Log in to Azure:
az login
Ensure you have a resource group created:
az group create --name MyResourceGroup --location southafricanorth

Deployment Steps

1. Validate the Template

Before deploying, validate the ARM template and parameter file:

az deployment group validate \
  --resource-group MyResourceGroup \
  --template-file azuredeploy.json \
  --parameters @parameters.json

2. Deploy the Template

Run the deployment command:

az deployment group create \
  --resource-group MyResourceGroup \
  --template-file azuredeploy.json \
  --parameters @parameters.json

3. Check Deployment Status

View deployment details:

az deployment group show \
  --resource-group MyResourceGroup \
  --name <deploymentName>

🔍 Post-Deployment Validation

Get Public IP of VM

az vm show -d -g MyResourceGroup -n myVM --query publicIps -o tsv

Connect to VM via SSH

ssh azureuser@<publicIP>

🛠 Troubleshooting

Use az deployment group validate to catch syntax errors.

Check logs with:

az deployment group operation list \
  --resource-group MyResourceGroup \
  --name <deploymentName>
