# Active-directory-basics

# ☁️ Active Directory Lab on Azure

This project guides you through setting up a **virtual environment for Active Directory** using **Microsoft Azure**.  
Perfect for testing, learning, and scripting with **PowerShell**, **Group Policy**, and **Active Directory Domain Services (AD DS)**.

---

## 📁 Table of Contents

1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Step-by-Step Setup](#step-by-step-setup)
    - [Create Resource Group](#1-create-resource-group)
    - [Create Virtual Network](#2-create-virtual-network)
    - [Create Domain Controller (DC-1)](#3-create-domain-controller-dc-1)
    - [Create Client Machine (C-1)](#4-create-client-machine-c-1)
4. [Next Steps](#next-steps)
5. [Screenshots](#screenshots)
6. [Credits](#credits)

---

## 🧠 Overview

We will create a **simulated corporate network** in Azure using:

- ✅ One Domain Controller (DC-1)
- ✅ One Client Machine (C-1)
- ✅ Custom Virtual Network & Resource Group

This lab will later support:
- Bulk user creation with PowerShell
- Group Policy Object (GPO) management
- Domain joining and testing

---

## ⚙️ Prerequisites

- Azure Subscription (Free or Pay-As-You-Go)
- Basic knowledge of virtual networks, VMs, and PowerShell
- Azure Portal access: https://portal.azure.com/

---

## 🛠️ Step-by-Step Setup

---

### 🔹 1. Create Resource Group

1. Go to the Azure Portal → Search “Resource Groups”
2. Click **+ Create**
3. Enter a name (e.g., `AD-Lab-RG`)
4. Choose a region (e.g., East US)
5. Click **Review + Create → Create**

📸 Screenshot:  
![Resource Group](images/01_resource_group.png)

---

### 🔹 2. Create Virtual Network

1. Go to **Virtual Networks** → Click **+ Create**
2. Resource Group: `AD-Lab-RG`
3. Name: `AD-VNet`
4. Address space: `10.0.0.0/16`
5. Add a subnet: `10.0.1.0/24`
6. Review and Create

📸 Screenshot:  
![Virtual Network](images/02_virtual_network.png)

---

### 🔹 3. Create Domain Controller (DC-1)

1. Go to **Virtual Machines** → Click **+ Create**
2. Resource Group: `AD-Lab-RG`
3. Name: `DC-1`
4. Image: Windows Server 2019/2022
5. Size: At least 2 vCPUs, 4 GB RAM
6. Network: Attach to `AD-VNet` > `default` subnet
7. Enable RDP
8. Create

📸 Screenshot:  
![DC-1 Creation](images/03_dc1_create.png)

---

### 🔹 4. Create Client Machine (C-1)

1. Repeat VM creation
2. Name: `C-1`
3. Use same network and subnet (`AD-VNet`)
4. Enable RDP
5. Create

📸 Screenshot:  
![Client Creation](images/04_client_create.png)

---

## 🚀 Next Steps

After creating the VMs:

- Connect to **DC-1** via RDP
- Install **Active Directory Domain Services**
- Promote it to a domain controller
- Connect **C-1** and join it to the domain
- Start scripting with PowerShell and managing with GPO

📘 Follow-up guide: [PowerShell Bulk User Script](link-to-your-next-page)

---

## 🖼️ Screenshots

Add all your actual screenshots into an `/images/` folder in your repo.

| Step | Description | Image |
|------|-------------|----
