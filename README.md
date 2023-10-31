<p align="center">
<img src="https://i.imgur.com/AeiqMDZ.png" alt="File Share Graphic"/>
</p>

<h1>File Shares and Permissions</h1>
This tutorial covers configuring file shares and permissions.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Creating sample file shares and permissions.
- Attempting to access file shares as a normal user.
- Creating, assigning permissions to, and testing access of an Accountants Security Group.


<h2>Deployment and Configuration Steps</h2>

<p>
Welcome back to the final part of my Active Directory Tutorials. I'll be assuming that you've just finished the previous tutorial. If not, go back through the previous two tutorials to catch up.
</p>
<br />

<p>
<img src="https://imgur.com/qTFwMU8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First things first, go ahead and log into DC-1 as Jane Doe. We'll be logging into Client-1 as one of the Users we created earlier with the PowerShell script. Remember, the password for all of those accounts is "Password1". Once logged in as one of those users, go back to DC-1. Create 4 folders on the C: drive, name them "read_access", "write_access", "no_access", and "accounting". From here, right click each folder and share the folder with:
<ol type="1">
   <li>Folder: “read_access”, Group: “Domain Users”, Permission: “Read”</li>
   <li>Folder: “write_access”,  Group: “Domain Users”, Permissions: “Read/Write”</li>
   <li>Folder: “no_access”,  Group: “Domain Admins”, Permissions: “Read/Write”</li>
</ol>
</p>
<br />

<p>
<img src="https://imgur.com/leZ464j.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, go to Client-1, you should be signed in as a normal user. Go to the C: Drive in Client-1 and verify the changes you made. To access the shared files, type \\dc-1 in the search bar. You should be able to make documents in write_access, not enter "no_access", and only read files in "read_access".
</p>
<br /> 

<p>
<img src="https://imgur.com/CWokdHh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, go back into DC-1 as Jane. Navigate to Active Directory and right click on _EMPLOYEES, create a new Group and name it "_ACCOUNTANTS". Now go back to the "accounting" folder you created earlier. Now share that to _ACCOUNTANTS and give them read and write permissions. Go back to Client-1 and try to access the folder, it should fail. Now log out of Client-1, and back in DC-1 make the same user a member of _ACCOUNTANTS by clicking on _ACCOUNTANTS -> Members -> Add -> type username of selected user -> Apply -> OK. Now log back into CLient-1 as the user we just put into _ACCOUNTANTS and verify that you can access the folder.
</p>
<br />

<p>
That concludes my series of tutorials in Active Directory. I hope you enjoyed!
</p>
<br />
