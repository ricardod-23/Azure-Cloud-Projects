# Azure-Cloud-Projects
My Azure projects for portfolio

# 📘 Azure Resource Group Lab

## 📌 Overview
This project demonstrates the design and deployment of a **secure and scalable network environment in Azure**.

The resources were created manually in the **Azure Portal**, and the configuration was later exported as **ARM templates** for documentation and reproducibility.

The lab simulates a real-world scenario with frontend and backend workloads behind a **Standard Load Balancer**, protected by **Network Security Groups (NSGs)**, and with outbound connectivity via **NAT Gateway**.


## 🗂 Project Structure
```plaintext
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
```

## 🔧 Deployment Method
- All resources were deployed manually through the **Azure Portal**.  
- After deployment, the **ARM template** and **parameters file** were exported for reusability.  
- This workflow demonstrates both **portal-based deployment** and **infrastructure as code documentation**.  

---

## 📊 Architecture Diagram
![Azure Lab Diagram](https://github.com/ricardod-23/Azure-Cloud-Projects/blob/main/1-VNet-LB/Diagram/RG-Lab.jpg)

---

---

## ⚙️ Components Deployed

- **Virtual Network (VNet):** Address space `10.0.0.0/16`  

- **Subnets:**  
  - **Subnet-FE (10.0.1.0/24):** Hosts the **frontend VM**.  
  - **Subnet-BE (10.0.2.0/24):** Hosts the **backend VM**.  

- **Network Security Groups (NSGs):**  
  - NSG-FE and NSG-BE with identical rules:  
    - Allow inbound **HTTP (80)** from Internet
    - Allow inbound **HTTP (80)** from AzureLoadBalancer (for **health probes**)
    - Deny all other inbound traffic  

- **Standard Load Balancer (LB-Public):**  
  - **Frontend IP**: PIP-LB **(Static Public IP)**.
  - **Backend pool**: Includes both **FE-VM and BE-VM**.
  - **Load balancing rule** forwards traffic on port **80(TCP)**.  
  - **Health probe**: Configured on **HTTP/80** for monitoring VM availabilit 

- **Virtual Machines (VMs):**  
  - **FE-VM:** Ubuntu 22.04, size Standard_D2s_v3, Spot instance. Runs **NGINX web server**.  
  - **BE-VM:** Ubuntu 22.04, size Standard_B1ls. Runs **NGINX backend service** (simulation).
  - Both configured with auto-shutdown schedules for cost optimization.

- **NAT Gateway(NAT-Lab):**  
  - Provides secure outbound internet access via PIP-NAT (Static Public IP)
---

## 🎯 Key Skills Demonstrated
- **Azure Portal Management**: Designed and deployed a complete environment manually.

- **Infrastructure as Code (IaC)**: Exported ARM templates for reproducibility.

- **Network Security**: Implemented NSG rules to strictly control inbound traffic.

- **Load Balancing & High Availability**: Configured a Standard Load Balancer with HTTP health probes.

- **VM Deployment & Services**: Deployed Linux VMs, installed and validated NGINX for end-to-end testing.

- **Cost Management**: Configured scheduled VM shutdowns to optimize costs.

- **Documentation**: Produced architecture diagram and structured README for interview readiness.

---

## 🚀 Next Steps / Improvements
- Automate deployment using **Bicep** or **Terraform** instead of portal export  
- Add **Azure Firewall** for centralized traffic inspection  
- Integrate monitoring with **Azure Monitor** and **Log Analytics**  
- Extend with **Application Gateway + WAF** for Layer 7 security  



