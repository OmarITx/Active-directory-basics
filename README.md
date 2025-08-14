# Active-directory-basic-setup

# ☁️ Active Directory Lab on Azure

This project guides you through setting up a **virtual environment for Active Directory** using **Microsoft Azure**.  
Perfect for testing, learning, and scripting with **PowerShell**, **Group Policy**, and **Active Directory Domain Services (AD DS)**.

---

## 🧠 Overview

We will create a **simulated corporate network** in Azure using:

- ✅ One Domain Controller (DC-1)
- ✅ One Client Machine (C-1)
- ✅ Custom Virtual Network & Resource Group

The next section of the lab will support:
- Bulk user creation with PowerShell
- Group Policy Object (GPO) management
- Domain joining and testing

---

## 📚 Table of Contents
1. [Overview](#-overview)
2. [Prerequisites](#-prerequisites)
3. [Step-by-Step Setup](#-step-by-step-setup)
   - [1. Create Resource Group](#-1-create-resource-group)
   - [2. Create Virtual Network](#-2-create-virtual-network)
   - [3. Create Domain Controller (DC-1)](#-3-create-domain-controller-dc-1)
   - [4. Create Client Machine (C-1)](#-4-create-client-machine-c-1)
   - [5. Set Static IP for DC-1](#-5-making-sure-the-ip-address-for-dc-1-stays-the-same)
   
---

## ⚙️ Prerequisites

-  Creating an account in Microsoft Azure (Use the link below and create an account)
-  Azure Subscription (Free or Pay-As-You-Go)
-  Will need to use a credit/debit card to access the $200 free credit from Azure (you won't be charged unless you exceed the free credit)
-  Azure Portal access: https://portal.azure.com/

---

## 🛠️ Step-by-Step Setup

---

### 🔹 1. Create Resource Group

1. Go to the Azure search bar → Search “Resource Groups”
2. Click Create
3. Enter a name. ex, Active-Directory-Lab (needs to have "-" between each word)
4. Choose a region (you don't have to choose East US 2, but make sure to remember which region you chose!)
5. Your resource group should look something like this

**📸:**  
<img src="https://raw.githubusercontent.com/OmarITx/Active-directory-basics/140f8141a65a5c7efbdddf9ea1f9f334c2e92cd6/Screenshot%202025-06-29%20142439.png" width="600" />

6. Click **Review + Create → Create**

---

### 🔹 2. Create Virtual Network

1. Back to the Azure search bar → Search "Virtual Network" → Click Create
2. Choose the resource group "Active-Directory-Lab" that we created earlier
3. Name it "Active-Directory-Vnet"
4. Your Virtual Network should look like this

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%202025-06-29%20171239.png?raw=true" width="600" />

5. Click "Review and Create" at the bottom left, then press "Create"

---

### 🔹 3. Create Domain Controller (DC-1)

1. Back to the Azure search bar again and type "Virtual Machines"
2. Click "Create" at the top left
3. Choose the resource group "Active-Directory-Lab", which we created earlier
4. Name it "dc-1"
5. Make sure you choose the same Region as your virtual network (East US 2 in this case)

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%201.png?raw=true" width="600" />

6. For Image, choose Windows Server 2022 Datacenter

7. Size has to be at least 2 vCPUs, 4 GB RAM, so the virtual machine runs decently

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%202025-07-23%20115229.png?raw=true" width="600" />

8. Username: labuser  
   Password: Cyberlab123!

   You can type whatever you like, but make sure to save it in "Notepad" on Windows or "TextEdit" on macOS for easier access.

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%202025-07-22%20232311.png?raw=true" width="600" />

9. Check the Licensing box and the consent box

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%202025-07-22%20232338.png?raw=true" width="600" />

10. Press Next until you land on the "Networking" section, then choose "Active-Directory-Vnet" as your virtual network.

11. Press "Review and Create"

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%202.png?raw=true" width="600" />

---

### 🔹 4. Create Client Machine (C-1)

1. Go back to Virtual Machines (using the Azure search bar at the top)
2. Click "Create" at the top left
3. Follow the same steps as when creating the domain controller, but make sure to change "Image" to "Windows 10 Pro" and name the virtual machine "client-1"
4. Use the same username and password as dc-1 (or any username and password you want, as long as you have them saved somewhere, like Notepad)

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%203.png?raw=true" width="600" />
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%204.png?raw=true" width="600" />
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%202025-07-24%20144142.png?raw=true" width="600" />
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%205.png?raw=true" width="600" />

5. Click "Review and Create"

---

### 🔹 5. Making sure the IP Address for dc-1 stays the same

1. Go back to the Virtual Machine menu (using the search bar)
2. Press on "dc-1", then click on "Networking"

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/screenshot%206.png?raw=true" width="600" />

3. A new menu should pop up with "Network settings" in it
4. Click on it, then press on the "Network interface" in the middle of the menu

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%207.png?raw=true" width="600" />

5. Click on "ipconfig1", then under "Private IP address settings" choose "Static", then press save

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%208.png?raw=true" width="600" />

6. This ensures that dc-1 maintains the same IP address through the lab, no matter how many times it's restarted.

---

### 🔹 6. Finishing touch.

1. Back to Virtual Machines, get dc-1's public IP address

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%2011.png?raw=true" width="600" />

2. Search for "Remote Desktop Connection" on your computer using the search bar if using Windows. Or download "Microsoft Remote Desktop" if running a MacBook

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%2012.png?raw=true" width="600" />

3. Copy and paste the IP address into the "Computer" section, then press continue

**📸:**  
<img src="https://github.com/OmarITx/Active-directory-basics/blob/main/Screenshot%2010.png?raw=true" width="600" />

4. Type in the username and password we made earlier, then press continue

5. Now you are connected to the domain controller!

---


## 🎯 Closing & Next Steps

Congratulations! 🎉  
You’ve successfully set up the **foundation** of your Active Directory lab in Microsoft Azure, complete with:

- ✅ A dedicated Resource Group & Virtual Network  
- ✅ A Domain Controller (DC-1) ready for configuration  
- ✅ A Client Machine (C-1) ready to join the domain  
- ✅ Static IP configuration to keep things consistent  

This is the **base environment** we’ll build upon in the next sections of the series.  

---

### 📌 In the next part of this lab, we will:

- Install and configure **Active Directory Domain Services
- Join C-1 to the new domain  
- Create **bulk user accounts** with PowerShell ISE  
- Set up and test **Group Policy Objects (GPOs)**  

---

⚠️💡 **IMPORTANT TIP – READ THIS!**

Keep this environment running for the next part **only if you’re continuing right away**.
  
💰 **Azure charges for running VMs** — even when idle!

 If you’re taking a break, **STOP both VMs** in the Azure portal to avoid burning through your credits or money.



---

<div align="center">
  <a href="PART-2-LINK-HERE" style="text-decoration:none;">
    <button style="background-color:#0078D4; color:white; padding:12px 20px; font-size:16px; border:none; border-radius:8px; cursor:pointer;">
      👉 Next: Active Directory Setup & Configuration
    </button>
  </a>
</div>

---


