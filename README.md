# Lab 1: Initial Infrastructure
This repository contains an Azure Resource Manager (ARM) template exported from the RG-LAB1 resource group. This template captures the environment as Infrastructure as Code (IaC), serving as a reusable blueprint for automated, repeatable deployments.

The template deploys the following cloud infrastructure:  
• Resource Group: RG-LAB1.  
• Virtual Network: VNET-LAB1 (Address Space: 10.0.0.0/16) with a dedicated subnet SUBNET-WEB (10.0.1.0/24).  
• Virtual Machine: An Ubuntu 22.04 LTS VM named WEB1 (Size: Standard_D2s_v3).  
• Networking: A Public IP for remote access and a Network Security Group (NSG-WEB) configured to allow SSH (Port 22) and HTTP (Port 80) traffic.  
• Storage: A managed OS disk and an additional 16 GiB managed data disk (WEB1-DATA1) formatted with an ext4 filesystem and mounted to /data.  
• Web Services: The environment is prepared to host an Apache web server.  

Export Date: January 27, 2026.

# Lab 2: Updated Template 
Several properties included by the Azure portal export were removed because they are not valid for repeatable deployments. References to existing managed disk IDs were eliminated and disk creation options were adjusted so that disks are created during deployment. The requireGuestProvisionSignal property was also removed because it depends on a subscription feature that is not enabled. These changes ensure the template is valid, reusable, and able to deploy successfully without dependency or configuration errors.

# Lab 2: Activity 2 
The template was updated further to provide the following:  
• Two web servers deployed from a single ARM template  
• Identical configuration across instances  
• Independent access paths to each server  

Note: This template does not  provide automatic traffic distribution or failover

# Lab 2: Activity 5
The ARM template was extended to introduce a Standard Azure Load Balancer for the replicated web tier. A static public IP was added to serve as the frontend of the load balancer. The load balancer itself was configured with a frontend IP configuration, a backend address pool, an HTTP health probe on port 80, and a load balancing rule mapping frontend port 80 to backend port 80. Both WEB1 and WEB2 network interfaces were updated to join the backend pool, enabling the load balancer to automatically distribute traffic and provide a single, resilient entry point for the application.
