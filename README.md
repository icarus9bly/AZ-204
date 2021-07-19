# AZ-204
    - https://icarus9bly.azurewebsites.net/# (Pathfinding Visualizer)
    - https://app.pluralsight.com/paths/skills/developing-solutions-for-microsoft-azure-az-204?aid=7010a000002BWq6AAG 
    - The AZ-204 exam covers the following domains:
      - Develop Azure compute solutions (25-30%)
      - Develop for Azure storage (10-15%)
      - Implement Azure security (15-20%)
      - Monitor, troubleshoot, and optimize Azure solutions (10-15%)
      - Connect to and consume Azure services and third-party services (25-30%)
# Azure CLI pattern
    - az objectname verb parameters   
    - az group create --location --name
    - Useful Commands:
        - az group list --output=table # List resource groups (in tabular format)
        - az group delete --name "vimeo-rg" # Delete RG (also deletes any resources in them)
        - az account set --subscription "Azure subscription 1"
# ARM Templates (Azure resource management)
    - Is a JSON file that defines your resources building block for automation.
    - Basic syntax of ARM Templates (https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/syntax):
      {
          "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
          "contentVersion": "",
          "apiProfile": "",
          "parameters": {  },
          "variables": {  },
          "functions": [  ],
          "resources": [  ],
          "outputs": {  }
      }
    - parameters are like values file from helm
    - variables are like configmap
    - functions are like in-built functions from helm.
    - Deploying ARM from Azure CLI:
        - az deployment group create --resource-group Web-App --template-file ./template.json --parameters '@parameters.json'
    
# Virtual Machines in Azure
    - Default Size: Standard D2S
    - create VMs with azure cli
        - az group create --name "vimeo-rg" --location "centralus" # Create Resource group
        - az vm create --resource-group "vimeo-rg" --name "vimeo" --image "UbuntuLTS" --admin-username "demo-admin" --authentication-type "ssh" --ssh-key-value ~/.ssh/id_rsa.pub # Creating vm with ssh pub from host machine
        - az vm open-port --resource-group "vimeo-rg" --name "vimeo" --port "22" # Enable remote port access
        - az vm list-ip-addresses # List public ip addr of VMs
# Containers in Azure:
    - Azure container registry (ACR) hosted in azure based on docker registry
    - Azure container instances (ACI)
    - Commands:
        - az group create --resource-group "acr_test-rg" --location westus
        - az acr create --resource-group "acr_test-rg" --name "icarus9bly" --sku Standard # Create ACR, name should be unique as it will the part of azure domain name
        - az acr login --name icarus9bly # Login to acr in docker or you can user docker login aswell
        - az acr show -n icarus9bly --query loginServer # To get the registry server url for e.g. icarus9bly.azurecr.io
        - docker tag tryreact:latest icarus9bly.azurecr.io/tryreact:latest # Tag image to push it to ACR
        - docker push icarus9bly.azurecr.io/tryreact:latest # Push to ACR
        - az acr repository list --name icarus9bly -o table # Show images in ACR
        - az acr repository show-tags --name icarus9bly --repository tryreact -o table # Show images tag
        - We Don't have to build locally then push, we can build in ACR with Tasks.
            - az acr build --image "tryreact:v1-acr-task" --registry "icarus9bly" . # build, tag and push the image from dockerfile in pwd to ACR
    
# Web App
   - App Service Web Apps lets you quickly build, deploy, and scale enterprise-grade web, mobile, and API apps running on any platform. Meet rigorous performance, scalability, security and compliance requirements while using a fully managed platform to perform infrastructure maintenance.

