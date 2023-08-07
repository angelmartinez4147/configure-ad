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
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<img width="700" alt="Screen Shot 2023-08-03 at 1 55 03 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/234be968-99d4-476d-af91-b2be5ea31da5">
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<img width="700" alt="Screen Shot 2023-08-03 at 2 01 31 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/adf86ffe-8b88-4c2d-84b4-85fb9737e2ec">
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<img width="700" alt="Screen Shot 2023-08-03 at 2 06 58 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/e80e531a-6a3e-4149-b719-e11f7c4575c6">

<img width="700" alt="Screen Shot 2023-08-03 at 2 08 48 PM" src="https://github.com/angelmartinez4147/configure-ad/assets/131706484/ce5a79b7-edde-4abe-b7e6-63e3756d47fb">
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
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
