# Active-directory-basics

# ☁️ Active Directory Lab on Azure

This project guides you through setting up a **virtual environment for Active Directory** using **Microsoft Azure**.  
Perfect for testing, learning, and scripting with **PowerShell**, **Group Policy**, and **Active Directory Domain Services (AD DS)**.

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

1. Go to the Azure search bar → Search “Resource Groups”
2. Click Create
3. Enter a name. ex, Active-Directory-Lab ( needs to have "-" between each word)
4. Choose a region (you dont have to choose east us 2, but make sure to remember which region you chose!)
5. Your resource group should look something like this

📸:  
![Image Alt](https://raw.githubusercontent.com/OmarITx/Active-directory-basics/140f8141a65a5c7efbdddf9ea1f9f334c2e92cd6/Screenshot%202025-06-29%20142439.png)

6. Click **Review + Create → Create**

---

### 🔹 2. Create Virtual Network

1. Back to the Azure search bar → Search "Virtual Network" → Click Create
2. Choose the resource group "Active-Directory-Lab" that we created earlier
3. Name it "Active-Directory-Vnet"
4. Your Virtual Network should look like this

📸:  
![Image Alt](https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%202025-06-29%20171239.png?raw=true)

5. Click "Review and Create" at the bottom left, then press "Create"
---

### 🔹 3. Create Domain Controller (DC-1)

1. Back to the Azure search bar again and type "Virtual Machines"
2. Click "create" at the top left
3. Choose the resource group "Active-Directory-Lab", which we created earlier
4. Name it "dc-1"
5. Make sure you choose the same Region as your virtual network (East US 2 in this case)


📸:

![Image Alt](https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%201.png?raw=true)


6. For Image, choose Windows Server  2022 Datacenter

7. Size has to be at least 2 vCPUs, 4 GB RAM, so the virtual machine runs decently

📸:

![Image Alt](https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%202025-07-23%20115229.png?raw=true)


8. Username: labuser

   Password: Cyberlab123!
   
You can type whatever you like, but make sure to save it in "Notepad" on Windows or "TextEdit" on macOS for easier access.


📸:

![Image Alt](https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%202025-07-22%20232311.png?raw=true)


9. Check the Licensing box and the consent box

    
📸:

![Image Alt](https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%202025-07-22%20232338.png?raw=true)


10. Press Next until you land on the "Networking" section, then choose "Active-Directory-Vnet" as your virtual network.
    
11. Press review and create.

📸:

![Image Alt](https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%202.png?raw=true)


---

### 🔹 4. Create Client Machine (C-1)

1. Repeat VM creation
2. Name: `C-1`
3. Use same network and subnet (`AD-VNet`)
4. Enable RDP
5. Create

📸:  
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
