# Azureproject
Overview
In this project, we will create a secure and scalable network architecture using Azure. We will deploy a Virtual Machine (VM) with a NGINX web server in a secure environment, allowing external access through a firewall while maintaining internal security using Bastion for SSH access.

Objectives
Create a Virtual Network (VNet).
Set up a web subnet and firewall.
Deploy a VM in the subnet and install NGINX with a static HTML site.
Configure firewall rules to allow external access to the NGINX site.
Use Azure Bastion for secure SSH access to the VM.
Learning Outcomes
Understanding of Azure VNet and subnet configuration.
Implementation of Azure Firewall for network security.
Deployment and configuration of a VM in Azure.
Installation and configuration of a web server (NGINX).
Secure VM access using Azure Bastion.
Firewall rules configuration for secure web access.
Steps
1. Create Resource Group
Navigate to the Azure portal.
Click on "Resource groups" in the left menu.
Click "Add" to create a new resource group.
Provide a name and select a region, then click "Review + create" and "Create".
2. Create Virtual Network (VNet) and Enable Bastion
In the Azure portal, search for "Virtual networks" and click "Create".
Enter the required details and enable Bastion.
Create three subnets: one for the firewall, one for Bastion, and one for the web.
3. Enable Firewall
In the Azure portal, search for "Firewalls" and click "Create".
Fill in the required details and ensure the firewall is in the same VNet.
Create subnet configurations as shown in the images.
4. Deploy Virtual Machine (VM)
In the Azure portal, search for "Virtual machines" and click "Create".
Select your resource group and provide VM details.
Ensure the VM is deployed in the web subnet and does not have a public IP.
5. Connect to VM Using Bastion
Navigate to the VM in the Azure portal.
Click on "Connect" and select "Bastion".
Provide the username and password to connect.
6. Install NGINX on VM
Connect to the VM using Bastion.

Switch to the root user:

bash
Copy code
sudo su
Update the package list:

bash
Copy code
apt-get update
Install NGINX:

bash
Copy code
apt-get install nginx -y
Navigate to the HTML directory and create an index file:

bash
Copy code
cd /var/www/html
vim index.html
Insert your HTML content, then save and exit:

Press i to insert text.
After writing, press Esc and type :wq! to save and exit.
Restart NGINX:

bash
Copy code
systemctl restart nginx
7. Configure Firewall for External Access
Navigate to your firewall in the Azure portal.
Click on "Firewall policies" and then "DNAT rules".
Add a rule collection:
Source IP: Your PC's IP.
Destination IP: Firewall's public IP.
Translated Address: VM's private IP.
Translated Port: 80.
Testing
Open a browser and access the firewall IP with the specified port (e.g., http://172.179.152.219:4000). You should see the NGINX web page.
Conclusion
This project demonstrates creating a secure network architecture in Azure, deploying a web server, and configuring firewall rules for external access. By using Bastion, we ensured secure SSH access to the VM, highlighting the importance of security and best practices in cloud environments.
