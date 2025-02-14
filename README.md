<p align="center">
<img src="https://github.com/user-attachments/assets/ea8315b8-28f8-4d0a-a370-917bdc1c56f3" height="30%" width="50%" alt="Microsoft Azure Logo"/>
</p>

<h1>Active Directory: Virtual Machine Deployment</h1>

<p> 
This project is the second amongst a collection focused on implementing Azure and Active Directory.
The goal here is to create a basic lab that mirrors a real working network environment, providing me with hands-on-learning and practical experience with Microsoft Azure, PowerShell and WireShark.
In this project, I will set up and establish a connection between two virtual machines using Windows and Linux in Microsoft Azure's Cloud environment. 
This will allow me to perform a basic network traffic inspection using WireShark and implement some Network Security Group rules to block, re-enable and observe different traffic types.
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

  - Integrate the client-01 Virtual Machine into the established domain, ensuring seamless communication with the Active Directory infrastructure
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

- In the Server Manager Dashboard, click "Add Roles and Features" then proceed with the setup wizard
- 










