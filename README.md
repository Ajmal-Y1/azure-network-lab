

Readme · MD
Azure Network Lab
A virtual network with two subnets and a network security group (NSG), defined as code with Bicep and deployed with the Azure CLI.

What I Built
Virtual network lab-vnet with address space 10.0.0.0/16
web-subnet (10.0.1.0/24) with the NSG attached
app-subnet (10.0.2.0/24)
Network security group lab-web-nsg allowing inbound HTTP (80) and HTTPS (443) from the internet
Everything is defined in main.bicep, so the environment can be rebuilt or deleted with a single command.

Architecture
Show Image

Deployment
Deployed from Azure Cloud Shell:

az group create -n lab-rg -l eastus
az deployment group create -g lab-rg -f main.bicep
Show Image

Results
Resource group containing the VNet and NSG:

Show Image

Subnets with the NSG attached to web-subnet:

Show Image

NSG inbound rules for HTTP and HTTPS:

Show Image

Clean Up
az group delete -n lab-rg --yes
What I Learned
How to define Azure networking resources as code with Bicep
How address spaces, subnets, and NSGs relate to each other
How to deploy and verify infrastructure from the Azure CLI
Next Steps
Add a second NSG for app-subnet that only accepts traffic from the web subnet
Automate deployment with a GitHub Actions workflow
Add a VM or App Service inside the subnets, plus monitoring with Log Analytics


