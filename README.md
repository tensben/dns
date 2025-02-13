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

![Screenshot 2025-02-07 152610](https://github.com/user-attachments/assets/ee0d9f15-3f39-4c46-8d06-97f2d1bf2533)

</p>

<p>
Open the DC-1 and search for DNS.  Click dc-1, Forward Lookup Zones, and mydomain.com in the DNS manager. There, you will see the existing A- records.  Right-click, select New Host(A or AAA), type in mainframe, the dc-1 private IP address, select Create associated pointer(PTR) record, then Add Host. The new A-record mainframe is created. 
</p>
<br />

<p>
  
![Screenshot 2025-02-07 152300](https://github.com/user-attachments/assets/3d54485c-26b6-4585-b559-d19a8c02d03c)

![Screenshot 2025-02-07 152429](https://github.com/user-attachments/assets/72394efe-f191-4fbf-9bb7-5603006c686a)

![Screenshot 2025-02-07 152701](https://github.com/user-attachments/assets/55803bc7-491f-4895-bfee-95b78294236b)

![Screenshot 2025-02-07 152845](https://github.com/user-attachments/assets/f36ee019-93ef-4c0e-b2f2-935575d1bc8c)

![Screenshot 2025-02-07 152915](https://github.com/user-attachments/assets/a1f82959-0f4a-4368-952e-7b0b7d2d0f67)

</p>
<p>
  
Let’s go back to client -1 and ping the mainframe again. It will ping and match the DC -1 IP address.

</p>
<br />

<p>
  
![Screenshot 2025-02-07 153058](https://github.com/user-attachments/assets/a6b980f7-36e1-4265-a19d-124b9bc2275b)

</p>
<p>
Return to DC -1 and change the mainframe’s record address to 8.8.8.8. Double-click the mainframe in the DNS Manager, then change its IP address to 8.8.8.8.
</p>
<br />

<p>
  
![Screenshot 2025-02-07 153319](https://github.com/user-attachments/assets/8e29e165-b398-469d-a79c-8d43c367285d)

![Screenshot 2025-02-07 153403](https://github.com/user-attachments/assets/75553b38-9739-467e-816a-628248f479e5)

</p>

<p>
Go back to client -1 and ping the mainframe again. The old IP address will still be in the Local DNS cache. Type it in ipconfig/ displaydns > dns.text, enter, and then type notepad dns.txt to examine the local DNS cache. We must flush the cache so the new IP address will appear.
</p>
<br />

<p>
  
![Screenshot 2025-02-07 153527](https://github.com/user-attachments/assets/1729c5b9-11cd-40ad-9af3-11418d4d4edc)

![Screenshot 2025-02-07 153842](https://github.com/user-attachments/assets/3da4299d-d894-40ac-ad33-863c5c7a4492)

![Screenshot 2025-02-07 153910](https://github.com/user-attachments/assets/ab503ac8-de5c-48e4-9c4e-7f6ef0ee43a1)

![Screenshot 2025-02-07 153950](https://github.com/user-attachments/assets/c186446a-e2d7-48b0-ab55-b121ce30e6b0)

</p>
<p>
To do this, open Powershell, run it as administrator and type in ipconfig/flushdns. It will flush the DNS cache. Type ipconfig/displaydns and ensure the old IP address is not in the cache. 
</p>
<br />

<p>
  
![Screenshot 2025-02-07 154110](https://github.com/user-attachments/assets/c385c12b-169b-4e62-8506-b0027369f370)

![Screenshot 2025-02-07 154219](https://github.com/user-attachments/assets/62ad44b9-a8b0-4b30-8d95-20cf385004f1)

![Screenshot 2025-02-07 154241](https://github.com/user-attachments/assets/7e727492-05e5-4f05-bc32-b7d84ff84257)

![Screenshot 2025-02-07 154336](https://github.com/user-attachments/assets/0b83c38a-a3c6-42c6-a162-44ccb6ec5d21)

</p>
<p>

Ping the mainframe again, and the new IP address will appear. 

</p>
<br />

<p>
  
![Screenshot 2025-02-07 154438](https://github.com/user-attachments/assets/cb4c518e-edff-4c6b-8998-7c78eae588e6)

</p>

<p>
Return to DC-1 and create a CNAME record that points the host “search” to map to “www.google.com” in the DNS Manager. Right-click and select New Alias (CNAME), name it, search and map the target host to www.google.com, and then hit okay.
</p>
<br />

<p>
  
![Screenshot 2025-02-07 154543](https://github.com/user-attachments/assets/859071f6-77b9-4bee-a792-a52fd9288e71)

![Screenshot 2025-02-07 154628](https://github.com/user-attachments/assets/47254e99-c163-45b2-a455-b0a743cc4a90)

![Screenshot 2025-02-07 154747](https://github.com/user-attachments/assets/9918e3ec-a6f0-4f55-a12b-e050b8b15bb4)

![Screenshot 2025-02-07 154830](https://github.com/user-attachments/assets/0f5296d9-a535-4f7c-aa2e-16808750d99e)

</p>
<p>
Back in client -1, ping search and examine the CNAME record. It pings “www.google.com”. Type in nslookup search and explore the results of the CNAME record.
</p>
<br />

<p>
  
![Screenshot 2025-02-07 155045](https://github.com/user-attachments/assets/a4629cd6-6c9a-49e5-b107-1686687c5a41)

</p>



