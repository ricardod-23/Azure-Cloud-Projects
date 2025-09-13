# Azure-Cloud-Projects
My Azure projects for portfolio
# 📘 Azure Resource Group Lab

## 📌 Overview
This project demonstrates the design and deployment of a **secure and scalable network environment in Azure**.  

The resources were created manually in the **Azure Portal**, and the configuration was later exported as **ARM templates** for documentation and reproducibility.  

The lab simulates a real-world scenario with frontend and backend workloads behind a **Standard Load Balancer**, protected by **Network Security Groups (NSGs)**, and with outbound connectivity via **NAT Gateway**.

## 🗂 Project Structure

Azure-Cloud-Projects/
│
├── Diagram/
│   ├── RG-Lab.drawio      # Editable network diagram (Draw.io)
│   └── RG-Lab.png         # Exported diagram for documentation
│
├── RG-Lab/
│   ├── parameters.json    # Parameters file (exported from Azure Portal)
│   └── template.json      # ARM template (exported from Azure Portal)
│
└── README.md              # Project documentation
🔧 Deployment Method
All resources were deployed manually through the Azure Portal.

After deployment, the ARM template and parameters file were exported for reusability.

This workflow demonstrates both portal-based deployment and infrastructure as code documentation.

📊 Architecture Diagram

⚙️ Components Deployed
Virtual Network (VNet): Address space 10.0.0.0/16

Subnets:
--Subnet-FE (10.0.1.0/24) → frontend VM
--Subnet-BE (10.0.2.0/24) → backend VM

Network Security Groups (NSGs):
--Allow inbound HTTP (80)
--Deny all other inbound traffic

Standard Load Balancer: Distributes HTTP traffic between FE and BE VMs

Virtual Machines:
--One VM in Subnet-FE
--One VM in Subnet-BE

Installed NGINX web server on both VMs for testing

NAT Gateway: Provides outbound internet access for the VMs

🎯 Key Skills Demonstrated
Azure Portal Management: Designed and deployed a complete environment manually

Infrastructure as Code (IaC): Exported ARM templates to capture and reuse deployment configuration

Network Security: Implemented NSG rules to restrict inbound traffic and allow only HTTP

Load Balancing: Configured Standard Load Balancer for traffic distribution

Service Deployment: Installed and tested NGINX on VMs to validate end-to-end connectivity

Documentation: Produced network diagram and README for clarity and interview readiness

🚀 Next Steps / Improvements
Automate deployment using Bicep or Terraform instead of portal export

Add Azure Firewall for centralized traffic inspection

Integrate monitoring with Azure Monitor and Log Analytics

Extend with Application Gateway + WAF for Layer 7 security