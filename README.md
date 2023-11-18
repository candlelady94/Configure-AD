# configure-AD<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud (Azure)</h1>
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

- Setup Resources in Azure
- Setup domain and Install Active Directory
- Join Server and User Computer
- Setup Remote Desktop for non-Admin users
- create random users and sign a non admin into user computer



<h2>Deployment and Configuration Steps</h2>

I created DC-1 and Client-1 in Azure.  
I set DC-1's private IP to be static.  
I enabled ICMPv4 on the DC-1's firewall (inbound rules) so the computers will communicate with each other.
Ping succeeded from Client 1 to DC-1


![picture 1 github](https://github.com/candlelady94/Configure-AD/assets/146590015/2f0100ed-ee53-4b90-ab86-e84ce99e3115)





<p>


  
</p>
<p>
</p>
<br />

<p>
From DC-1 in Azure I installed AD from roles and features.
Configured a new forest for the server DC-1 as mydomain.com. 
I created a new user and gave Jane Doe access as a Domain Admin.
I restarted DC-1 and logged in mydomain.com\jane_doe.
  

![Picture 2 github](https://github.com/candlelady94/Configure-AD/assets/146590015/b347d4f6-2297-4285-b046-7da9f3c2f53a)
 



Joining Client 1 to mydomain.com (DC-1)
In Azure portal using networking, NIC, DNS servers,custom, and entering DC-1's Private IP address, Save 
Logged into Client 1 (labuser) and joined it to the domain. Opened Advanced settings, rename this PC, member of mydomain.com  

 
 <p> 
 Setup remote desktop for non-administrative users.
 <p>
 Logged into Client-1 with as mydomain.com\jane_admin and open system properties
   
![Picture 3 github](https://github.com/candlelady94/Configure-AD/assets/146590015/54b031eb-394d-4f60-8105-ee61151b247a)



![System properties remote access](https://github.com/candlelady94/Configure-AD/assets/146590015/a99d152e-310a-4ed4-97d2-7674e01f6953)


   
 </p>
 Click remote desktop , user accounts add, allow domain users access to remote desktop
 
![Allowed all domain users to access client 1](https://github.com/candlelady94/Configure-AD/assets/146590015/57f3877f-a1b5-4166-b4cc-45ad7188990e)

 
 Client-1 can now be logged as normal, non admin users now

 
![labuser logged on client 1 as normal user](https://github.com/candlelady94/Configure-AD/assets/146590015/3ac6ac3f-61a5-4e1e-9c6c-9951bf63df13)





Opened powershell_ise as an admin

![open power shell as admin](https://github.com/candlelady94/Configure-AD/assets/146590015/b6800037-dcdc-46f8-bd6f-b7d895a9920f)


Copied and pasted script from my instructor Josh from course careers github page

![running script](https://github.com/candlelady94/Configure-AD/assets/146590015/3005b9fe-c492-4f6d-ae01-8bf2181c99c7)

I manipulated the script to create 100 users instead of 10,000 users

![manipulating script](https://github.com/candlelady94/Configure-AD/assets/146590015/34776e49-9e79-4fe4-8e34-8bf5718815ba)

Showing the users were added to the _EMPLOYEES file in AD

![users in AD](https://github.com/candlelady94/Configure-AD/assets/146590015/e87da25a-0de8-4e46-8350-240722a787fe)

Logged in the client 1 with one of the users cat.nuk as a normal user

![cat nuk](https://github.com/candlelady94/Configure-AD/assets/146590015/7e145f52-ab6c-4f16-ba64-79891f8edec7)

</p>










