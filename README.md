# Description
This repository contains an Azure Resource Manager (ARM) template exported from the RG-LAB1 resource group. This template captures the environment as Infrastructure as Code (IaC), serving as a reusable blueprint for automated, repeatable deployments.

The template deploys the following cloud infrastructure:  
• Resource Group: RG-LAB1.  
• Virtual Network: VNET-LAB1 (Address Space: 10.0.0.0/16) with a dedicated subnet SUBNET-WEB (10.0.1.0/24).  
• Virtual Machine: An Ubuntu 22.04 LTS VM named WEB1 (Size: Standard_D2s_v3).  
• Networking: A Public IP for remote access and a Network Security Group (NSG-WEB) configured to allow SSH (Port 22) and HTTP (Port 80) traffic.  
• Storage: A managed OS disk and an additional 16 GiB managed data disk (WEB1-DATA1) formatted with an ext4 filesystem and mounted to /data.  
• Web Services: The environment is prepared to host an Apache web server.  

Export Date: January 27, 2026.

# Updated Template 
Several properties included by the Azure portal export were removed because they are not valid for repeatable deployments. References to existing managed disk IDs were eliminated and disk creation options were adjusted so that disks are created during deployment. The requireGuestProvisionSignal property was also removed because it depends on a subscription feature that is not enabled. These changes ensure the template is valid, reusable, and able to deploy successfully without dependency or configuration errors.
