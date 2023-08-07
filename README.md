<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="700" alt="Screen Shot 2023-08-03 at 1 47 28 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/b96fc2da-4c78-4e8c-bd1a-593a2faeeab0">

<img width="700" alt="Screen Shot 2023-08-03 at 1 49 36 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/2931f242-3b6f-49b5-8976-93b779cea20e">

<img width="700" alt="Screen Shot 2023-08-03 at 1 49 59 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/2951f537-3ab3-47c5-95cf-423c08701bc4">

<img width="700" alt="Screen Shot 2023-08-03 at 1 55 03 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/234be968-99d4-476d-af91-b2be5ea31da5">
</p>
<p>
For this lab, I used two VMs (virtual machines) first named dc1 with Active Directory freshly installed and the second VM being client-1 the second VM being used to connect to the active directory so all the users we create later on in the lab can log into client-1. To start log into dc1 and open up Active Directory Users and Computers(ADUC) within ADUC right click on the domain you created (in my case, mydomain.com) and create two Organization Units(OU) one being _EMPLOYEES and the other named _ADMINS. Next, click on the new _ADMINS Organization Unit and make a new user. I created the user "angel doe" with the username angel_admin this will be the account ill use on the dc1(VM) from now on. But before it becomes a true admin account right click on the user then on "properties" next to "member of" and type in domain admin to check for the security group and apply. I will now log off of dc1 so I can relog into it with the new admin account mydomain.com\angel_admin.
</p>
<br />

<p>
<img width="700" alt="Screen Shot 2023-08-03 at 2 01 31 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/adf86ffe-8b88-4c2d-84b4-85fb9737e2ec">
</p>
<p>
With Active Directory and the new admin account all set up, I will try to join client-1 to my domain. But for that to be possible I need to set client-1 DNS to that of dc1 private IP address. So from Azure Portal, I will retrieve dc1 private IP address and then go to client-1s networking within Azure and set its DNS to that of the dc1s private IP. Now by resetting client-1, it will apply the Changed DNS making it possible to connect client-1 to the domain.
</p>
<br />

<img width="700" alt="Screen Shot 2023-08-03 at 2 06 58 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/e80e531a-6a3e-4149-b719-e11f7c4575c6">

<img width="700" alt="Screen Shot 2023-08-03 at 2 08 48 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/ce5a79b7-edde-4abe-b7e6-63e3756d47fb">
</p>
<p>
Logging on to Client-1 we can now connect it to the domain, to do so right-click the start menu go to settings go to rename this pc(advance). A new tab will open up and click on change A section will be named "member of" Click on the domain circle and enter the name of the domain "mydomain.com". A new tab will appear prompting you to enter an account with permission to join the domain I will enter the admin account I created "mydomain.com\angel_admin". This will cause the VM(client-1) to restart. Now I can log into client-1 using my admin account (mydomain.com\angel_admin). Checking back with dc1 I can see in ADUC under "mydomain.com" and in the "computer" file the VM(client-1) is shown verifying that client-1 was successful in joining the domain. 
</p>
<br />

<img width="700" alt="Screen Shot 2023-08-03 at 2 11 07 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/62fd4c26-fa09-4fbf-aa06-3d2e9c45d6f7">
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<img width="700" alt="Screen Shot 2023-08-03 at 2 17 57 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/48ddf994-1138-41e1-acd6-f8ababdc8374">

<img width="700" alt="Screen Shot 2023-08-03 at 2 19 23 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/d1c9ffa2-5db8-486a-ad0a-8e88f249f3aa">

<img width="700" alt="Screen Shot 2023-08-03 at 2 20 05 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/a73aee49-92a4-407c-b109-c698efc3bb8c">
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<img width="700" alt="Screen Shot 2023-08-03 at 2 22 05 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/46a20c46-5cb1-41d1-86da-0eb1d80b36ca">

<img width="700" alt="Screen Shot 2023-08-03 at 2 22 58 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/75e39c24-e4a2-458f-b769-d1a34fec61b1">
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
