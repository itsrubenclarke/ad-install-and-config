<p align="center">
<img src="https://github.com/user-attachments/assets/ea8315b8-28f8-4d0a-a370-917bdc1c56f3" height="200%" width="50%" alt="Microsoft Azure Logo"/>
</p>

<h1>Active Directory: Installation and Configuration</h1>

<p> 
This project is the second in a collection focused on implementing Azure and Active Directory. The goal here is to install and configure Active Directory within a virtualised network environment, providing me with hands-on learning and practical experience in managing domain services in Microsoft Azure. In this project, I will set up Active Directory Domain Services (AD DS) on a Windows Server 2022 Domain Controller, create an Active Directory forest, and configure user accounts with administrative privileges. I will also join a Windows 10 Pro Client Virtual Machine to the domain, configure DNS settings, and establish Remote Desktop access for non-administrative users. This will allow me to manage users, devices, and authentication within a structured Active Directory environment.
</p>

<h2>Prerequisites</h2>

- <a href="https://github.com/itsrubenclarke/active-directory-vm-deployment"> Active Directory: Virtual Machine Deployment </a>


<h2>Key Objectives</h2>
<p>
  <h3>Active Directory Installation</h3>
  
  -  Configure and install Active Directory services on the designated Domain Controller Virtual Machine
</p>

<p>
  <h3>Forest Creation</h3>
  
  - Establish a new Active Directory forest
</p>

<p>
  <h3>Administrator Account Creation</h3>

  - Create a user acccount with administrative priviledes for effective management of the Active Directory environment
</p>

<p>
  <h3>Domain Joining</h3>

  - Integrate the client-1 Virtual Machine into the established domain, ensuring seamless communication with the Active Directory infrastructure
</p>

<p>
  <h3>Remote Desktop Setup</h3>

  - Configure Remote Desktop access specifically tailored for non-administrative users, enhancing user accessibility while maintaining security protocols
</p>


<h3>Environments and Technologies Used</h3>

- Microsoft Azure (Virtual Machines, Networking)
- Windows App (Remote Desktop Protocol)
- Active Directory (Domain Services)


<p>
  <h3>Operating Systems Used</h3>
</p>

| **Operating System**        | **Role**               
|----------------------------|------------------------|
| <img alt= "windows logo" src="https://i.imgur.com/KcrV0u6.png" width="20"> Windows (Windows 10 Pro) | Client VM |
| <img alt= "Windows logo" src="https://i.imgur.com/KcrV0u6.png" width="20"> Windows (Server 2022) | Domain Controller (DC)             |


<h1>Setup and Configuration of Active Directory</h1></p>

<h3>Step 1: Install Active Directory on Domain Controller (dc-1)</h3>

- Log into your Domain Controller (dc-1)
- Open the Server Manager Dashboard
- Select "Add Roles and Features" then proceed with the setup wizard

<img width="1782" alt="Add Roles and Features" src="https://github.com/user-attachments/assets/ee3bb062-9458-410c-9cd5-7b02d667c097" />

- Select the "Active Directory Domain Services" Role when prompted

<img width="1781" alt="Active Directory Domain Services" src="https://github.com/user-attachments/assets/1cf68af6-2eda-49b0-966b-6030ee5a9984" />

- When confirming the Installation selections on the final window select the "Restart if required" check box
- Select "Install" then close the window once complete
  
<img width="1780" alt="Restart if required" src="https://github.com/user-attachments/assets/98b9eac9-f238-488d-bff0-2af794d3140e" />


- In the upper right corner of the Server Manager Dashboard, click the Flag icon
- Select “Promote this server to a Domain Controller”

<img width="1784" alt="Promote Server" src="https://github.com/user-attachments/assets/915b6acd-176b-4957-8f3a-efd8819ddf4e" />

  
- Select “Add a new forest” – Root domain name: "mydomain.com"

<img width="1781" alt="Add a new forest" src="https://github.com/user-attachments/assets/e4a0cd38-ff8d-4ecc-a367-7645e0e192f6" />

  
- Select “Create Password”
- Proceed with the setup wizard
- Finalise with "Install"

<img width="1781" alt="Setup" src="https://github.com/user-attachments/assets/57d12fbb-ffeb-4ba4-961f-342209f1a665" />

- Your newly promoted Domain Controller (dc-1) will automatically restart
- Log back into dc-1 as user: “mydomain.com\ruben_lab”

![Log in](https://github.com/user-attachments/assets/28b9e21b-1484-4f72-8a78-553077fd5920)


<h3>Step 2: Create a Domain Admin and Normal User Account in Active Directory </h3>

- Whilst logged into your Domain Controller (dc-1)
- Open the Start Menu
- Select "Windows Administrative Tools"
- Select "Active Directory Users and Computers"

<img width="1791" alt="Active Directory Users and Computers" src="https://github.com/user-attachments/assets/b4ddd662-2fd5-4fa7-9656-caed77e03481" />


- Within the A"Active Directory Users and Computers" window click “Mydomain.com” 
- Right click and select “New” 
- Select “Organisational Unit” this is where we will be creating two folders:
  - "_EMPLOYEES"
  - "_ADMINS"

<img width="1791" alt="New Organisational Unit" src="https://github.com/user-attachments/assets/191c9570-576d-48d0-8a08-7b603a24756a" />
<img width="1788" alt="_EMPLOYEES" src="https://github.com/user-attachments/assets/5b460a4d-0d3b-4bf5-a637-a7b2e62db06c" />
<img width="1789" alt="_ADMINS" src="https://github.com/user-attachments/assets/6b541cc6-854c-4ea3-a899-83f3ce877f27" />



- Right click "mydomain.com" and click Refresh to sort the new organisational units to the top.
- Select the "_ADMINS" organisational unit
- Right click and select "New"
- Select "User" and create a user with the following details
    - First/Last name: Jane Doe
    - User login nam: jane_admin
- Select "next" and create a password
- Uncheck all boxes
- Select "next" and them select "finish"

<img width="1791" alt="New User" src="https://github.com/user-attachments/assets/8a26bfe1-cf1c-4ab5-900b-29014a203489" />
<img width="1786" alt="Jane Doe" src="https://github.com/user-attachments/assets/9b69afa3-e447-47ad-803f-1e8460363e06" />
<img width="1789" alt="Password" src="https://github.com/user-attachments/assets/976adf6e-d600-4f5b-bf77-2dbf3fa77e98" />

- Open the "_ADMINS" organisational unit
- Right-click on "Jane Doe"
- Select "Properties"
- Open the "Member of" tab
- Select "Add"
- Type in "domain admins"
- Check Names
- Select "Ok" and then "Apply"
- Log out of Domain Controller (dc-1) as "ruben_lab"
- Log back in as "mydomain.com\jane_admin"

 
<img width="1788" alt="Select Properties" src="https://github.com/user-attachments/assets/ac7fbb46-e877-496b-8958-d5dbc767a3cd" />
<img width="1789" alt="Member of" src="https://github.com/user-attachments/assets/700f4b88-3da4-4d18-8250-fc3afef4dfcf" />
<img width="1788" alt="Apply" src="https://github.com/user-attachments/assets/cb2f13ab-1a8d-4ced-a30b-5470c5b591de" />
<img width="1788" alt="Login" src="https://github.com/user-attachments/assets/569b3f89-0742-4a42-8f0a-f186d524a405" />


<h3>Step 3: Setup Remote Desktop for non-administrative users on Client-1</h3>

- Connect to Client-1 Virtual Machine
- Use mydomain.com\jane_admin
- Right click the start menu and select "System"
- Select "Rename this PC (advanced)"
- Select "Change"
- Under the "Member of" (Domain) section Enter "mydomain.com"
- When prompted enter the credentials for your admin user "mydomain.com\jane_admin"'
- Restart Virtual Machine

<img width="1788" alt="Client 1" src="https://github.com/user-attachments/assets/c9cfedb3-b202-458b-aeb5-5f2115115228" />

<img width="1181" alt="Rename PC Advanced" src="https://github.com/user-attachments/assets/485a43de-09e9-4124-aa8e-3a430e134c27" />


- Connect to dc-1 Virtual Machine
- Whilst logged into your Domain Controller (dc-1)
- Open the Start Menu
- Select "Windows Administrative Tools"
- Select "Active Directory Users and Computers"
- Expand "My Domain"
- Open up "My Computers"
- Confirm "Client-1" is present

![Log in](https://github.com/user-attachments/assets/28b9e21b-1484-4f72-8a78-553077fd5920)

<img width="1791" alt="Active Directory Users and Computers" src="https://github.com/user-attachments/assets/b4ddd662-2fd5-4fa7-9656-caed77e03481" />

<img width="1788" alt="Computers" src="https://github.com/user-attachments/assets/190b2798-677b-4b72-b579-1b5d6f14c4d1" />



<h1>Project Summary</h1>

🎉Congratulations! You have successfully installed and configured Active Directory in Azure!🎉  

In this project, we deployed Active Directory Domain Services (AD DS) on a Windows Server 2022 Virtual Machine, creating a new Active Directory forest and setting up user accounts with administrative privileges. We joined a Windows 10 Pro Client Virtual Machine to the domain, configured DNS settings, and verified connectivity. Additionally, we enabled Remote Desktop access for non-administrative users, ensuring proper authentication and domain management within the Active Directory environment.












