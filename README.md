<p align="center">

</p>

<h1>Analyze DNS with Azure Virtual Machines </h1>
This tutorial explores DNS using Azure Virtual Machines. .<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Deployment and Configuration Steps</h2>

<p>
This lab will explore A-Record, Local DNS Cache, and CName Record using the Dc-1 and Client -1 Virtual Machines(VMs) created in the previous exercise. Log into Client -1 as an admin (mydomainjane_admin). 

Once we log in to client -1, we go to Windows Powershell and ping the mainframe. It will say the ping request could not find the host mainframe. The computer will then look in the local DNS cache (fastest), local host file (faster), and DNS server (slowest) to find the mainframe. 

</p>
<br />

<p>
  
![Screenshot 2025-02-07 150345](https://github.com/user-attachments/assets/72bf4301-29ea-4815-95fd-d44e5ee9051c)

</p>
<p>
When we type ipconfig/ displaydns, we can see the computer's local DNS cache. However, if we look through the DNS cache, we won’t find anything about the mainframe.
</p>
<br />

<p>
  
![Screenshot 2025-02-07 150802](https://github.com/user-attachments/assets/c2875ed4-a0d9-4d93-bb8d-b7e3c088a947)
![Screenshot 2025-02-07 151042](https://github.com/user-attachments/assets/ae9dc235-4c85-4133-882a-72e772f85406)

![Screenshot 2025-02-07 151020](https://github.com/user-attachments/assets/9386f4ed-6ce5-43cd-a00a-e1ee07df1c9d)

</p>
<p>
We will look at the local host file by opening Notepad and running it as administrator. Select Open, and change the file type to all files. 
</p>
<br />

<p>
  
![Screenshot 2025-02-07 151208](https://github.com/user-attachments/assets/18473944-9a73-48ab-9957-43b5d48e4439)

![Screenshot 2025-02-07 151240](https://github.com/user-attachments/assets/9573113d-d6d0-4046-973a-873ff5aa14bc)

</p>

<p>
Make sure you are in systems32 > drivers > etc>. Select host, and you will see the local host file.
</p>
<br />

<p>
  
![Screenshot 2025-02-07 151343](https://github.com/user-attachments/assets/53327d70-d40d-47c4-a6ae-7948ae37bb38)
![Screenshot 2025-02-07 151417](https://github.com/user-attachments/assets/f7f7bb30-7407-46e0-bdc5-cc8905e45ce6)
![Screenshot 2025-02-07 151438](https://github.com/user-attachments/assets/feeed4d0-4476-4565-b5fb-7f7d3172315b)
![Screenshot 2025-02-07 151505](https://github.com/user-attachments/assets/a5a09925-7066-4be2-a95c-e2513722f0b9)

</p>
<p>
You can map the IP address to the hostname. For example, on the Powershell, type in ping zebra. It will not be found. In the host Notepad, type in the local IP address, then zebra, and save the file. Enter ping zebra again, and it will ping because we saved it on the local host file. Let’s use the nslookup mainframe in Powershell. It still fails again. 
</p>
<br />

<p>
  
![Screenshot 2025-02-07 151604](https://github.com/user-attachments/assets/3004af09-bdb8-4a86-863b-8666e61b133c)

![Screenshot 2025-02-07 151709](https://github.com/user-attachments/assets/3c8f6b68-6efc-4cf8-89af-202caf736e88)

![Screenshot 2025-02-07 151841](https://github.com/user-attachments/assets/901aafc9-7833-4a9b-a5fb-adde07d3f144)

![Screenshot 2025-02-07 151925](https://github.com/user-attachments/assets/2fa3ead0-5287-40ac-8e9d-21328df26b61)

![Screenshot 2025-02-07 152033](https://github.com/user-attachments/assets/1f699aab-e6c4-49ff-a7ec-19bfe12c384a)

</p>
<p>
We will create a DNS A-record on the DC-1 virtual machine for the mainframe and point it to DC-1’s private IP address. If you don’t remember the IP address, open Powershell and type ipconfig, and it will see the IP address. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
