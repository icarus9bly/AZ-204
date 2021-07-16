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
# Virtual Machines in Azure
    - Default Size: Standard D2S
    - create VMs with azure cli
        - az group create --name "vimeo-rg" --location "centralus" # Create Resource group
        - az vm create --resource-group "vimeo-rg" --name "vimeo" --image "UbuntuLTS" --admin-username "demo-admin" --authentication-type "ssh" --ssh-key-value ~/.ssh/id_rsa.pub # Creating vm with ssh pub from host machine
        - az vm open-port --resource-group "vimeo-rg" --name "vimeo" --port "22" # Enable remote port access
        - az vm list-ip-addresses # List public ip addr of VMs

# Web App
   - App Service Web Apps lets you quickly build, deploy, and scale enterprise-grade web, mobile, and API apps running on any platform. Meet rigorous performance, scalability, security and compliance requirements while using a fully managed platform to perform infrastructure maintenance.

