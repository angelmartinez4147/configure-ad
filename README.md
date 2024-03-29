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
As of now, only administrative accounts are able to log into client-1 I will need to change this in order for any Domain User "employee" can log in and conduct work. To make this change log into client-1 with the admin account (in my case, mydomain.com\angel_admin). Once again right-click the start menu and go to settings and click on Remote Desktop under "Users accounts" go to "Select users that can remotely access this PC". From there type in "domain users" and check names then apply. Now any account created under the organization group "Domain User" can log into client-1. A Group Policy can be used and it allows changes to many systems at once. For the purposes of this lab, a Group Policy won't be used to make this change.
</p>
<br />

<img width="700" alt="Screen Shot 2023-08-03 at 2 17 57 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/48ddf994-1138-41e1-acd6-f8ababdc8374">

<img width="700" alt="Screen Shot 2023-08-03 at 2 19 23 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/d1c9ffa2-5db8-486a-ad0a-8e88f249f3aa">

<img width="700" alt="Screen Shot 2023-08-03 at 2 20 05 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/a73aee49-92a4-407c-b109-c698efc3bb8c">
</p>
<p>
To fully exercise this lab I will create some Domain Users accounts to try and log into client-1 with them. Creating accounts is usually done manually but for the sake of time, I will be using a PowerShell script to automate the creation of these accounts. The PowerShell script can be found <a href="https://github.com/AsiaPonder001/BunchofUsers/blob/main/README.md?plain=1)">here. </a> Within the domain controller(dc1) using an admin account open PowerShell ISE as an administrator create a new file and paste the script into ISE console. Run the script and observe the accounts being created.
</p>
<br />

<img width="700" alt="Screen Shot 2023-08-03 at 2 22 05 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/46a20c46-5cb1-41d1-86da-0eb1d80b36ca">

<img width="700" alt="Screen Shot 2023-08-03 at 2 22 58 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/75e39c24-e4a2-458f-b769-d1a34fec61b1">
</p>
<p>
After all the users are created I can now pick any one and use it to log into client-1. By picking a user and signing in with the context of the domain mine being mydomain.com\xun.kise. While logged in I can open up Command Prompt and use the prompt "whoami" to see which user is being used. With xun.kise showing up letting me know that everything done in this lab was succeded. 
</p>
<br />

<h2>Lessons Learned</h2>

By completing this lab I was able to learn how to configure Active Directory and join different VMs to a domain. Also being able to create and automate users if need and assign the right necessary permissions. Active Directory is not difficult to learn and with more practice, I will become more comfortable with all the menu navigation that is needed to configure Active Directory correctly.  
