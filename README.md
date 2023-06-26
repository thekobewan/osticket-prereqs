
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket. <br> A ticketing system 
is an invaluable resource for any company using a help desk, so I took it upon myself to learn, <br> implement, and write a tutorial of the installation and configuration of one.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Prerequisite osTicket Files Used</h2>

- Internet Information Services in Windows WITH CGI
- PHP Manager for IIS
- The Rewrite Module
- PHP 7.3.8
- VC_redist.x86.exe
- MySQL 5.5.62
- osTicket 1.15.8.
- All installation files used can be found [here](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

<h2>Overview</h2>

1. Create a Resource Group and Windows Virtual Machine within Azure
2. Install Prerequisites
3. Install osTicket

<h2>Installation Steps</h2>
<h3>Create a Resource Group and Windows Virtual Machine within Azure:</h3><p>

<p>In order to download osTicket, we first need to create a Virtual Machine for osTicket to run off of. We'll be using Microsoft's Azure platform to create the VM in order to test various software and services without tampering with our physical computer.</p>

<h4>Creating the Resource Group and Microsoft VM:</h4>

1. Navigate to Microsoft Azure > Navigate to 'Resource Groups' via the quick access icon or search bar > select 'Create Resource Group'
2. We'll name our Resource Group: "RG-osTicket". There is nothing left for us to alter so select 'Review + Create'

<br>
<img src="https://i.imgur.com/a5aZTph.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br>

3. Navigate to 'Virtual Machines' within Azure via quick access icon or search bar > select 'Create Virtual Machine'
4. Within the Virtual Machine portal, we will make the following changes:

- Pick the resource group we just created: 'RG-osTicket'
- Name of Virtual Machine: 'VM-osTicket'
- Image: 'Windows 10 Pro, version 22H2 - x64 Gen2'
- Size: 2-4 vcpus (4vcpu is okay since we’re only using 1 virtual machine and thus is free to utilize all power)
- Username/password of choice: Example username: darinstathos (Remember this username/password for later when logging into VM)
- Check Licensing Box: [X] ‘I confirm I have an eligible Windows 10/11 license with multi-tenant hosting rights.’
- Select 'Next: Disks >', 'Next: Networking >': Beside Virtual Network: We don't have a virtual network yet so Azure automatically created on for us: '(new)VM-osTicket-vnet'
- Select 'Review + Create'

<img src="https://user-images.githubusercontent.com/129685324/234038547-1f11debd-934d-4ae2-b58b-74d10281c132.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Here is where I enabled Internet Information Services within the Windows settings. I navigated to Control Panel -> Programs -> World Wide Web Services -> Application Development Features -> and selected CGI.
</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409324-4571afe5-9fc6-4d4f-b01f-17ca7c15b22a.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<p>
Next up I downloaded and installed PHP Manager for IIS.
</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409327-538bfa0a-28b5-4fc9-958b-7c29e319f623.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>

<p>
I then downloaded and installed the Rewrite Module. Nothing special. 
</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409330-b9844eba-d90b-4492-9a53-6b50bc9c82e6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After that I made a new directory in the C: Drive for PHP. We'll notice why in an upcoming step.
</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409333-f4499dcd-50ab-45b4-aa93-fe7daef620dc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After creating the directory I downloaded installed PHP 7.3.8. I then unzipped the contents into C:\PHP (that handy directory we made).
</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409336-6bac222a-d46f-4e94-b758-9405e1615bb0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I then downloaded and installed VC_redist.x86.exe. We're almost done with the installs.

</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409339-ae9eb487-3935-4e87-aa94-f83c5e85722e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://user-images.githubusercontent.com/129685324/234409346-9d3cc8d6-e665-4320-90e1-e86a4ad3742f.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I proceeded to download and install MySQL 5.5.62, this will act as the database to hold our ticketing system's information. MySQL's installation has a couple of more steps but it was still simple.
- I selected Typical Setup on the first install
- Then Launch Configuration Wizard after that finished.
- On the next install window, I hit Standard Configuration
- Here we needed to make a password for the root user. I chose Password1 (don't tell anyone!)

</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409350-7c2796de-0efc-4cb1-9563-65f86dc738e6.png"/>
</p>
<p>
From here we need to open IIS as an Admin. This is so we can register PHP from within IIS. Be sure to reload the server so the changes follow. 
</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409357-74ac9d4e-2c1e-4eec-a6fe-d09aa729c41d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, it's time to install osTicket! It's still not our last install however. Be sure to refresh the server again!
</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409361-a93880bf-22d7-409b-ab74-89ba50301957.PNG" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Here we navigate to sites -> Default -> osTicket within IIS.
On the right, click “Browse *:80”
Note that some extensions are not enabled. We'll need to fix that before we can use the service
- Go back to IIS, sites -> Default -> osTicket
- Double-click PHP Manager
- Click “Enable or disable an extension”
- Enable: php_imap.dll
- Enable: php_intl.dll
- Enable: php_opcache.dll
Refresh the osTicket site in your browser, and observe the changes. Looking good!

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From here we need to rename ost-config.php. Change it from:
- C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
- To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

We'll also need to assign permissions. To do that navigate to...
- ost-config.php
- Disable inheritance -> Remove All
- New Permissions -> Everyone -> All

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We're going to continue Setting up osTicket in the browser (click Continue)
- Edit the Name (I chose Helpdesk)
- Add in the Default email that receives email from customers. 

</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409350-7c2796de-0efc-4cb1-9563-65f86dc738e6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now it's time to download and install HeidiSQL.
- Open Heidi SQL
- Create a new session, root/Password1
- Connect to the session
- Create a database called “osTicket”

</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409350-7c2796de-0efc-4cb1-9563-65f86dc738e6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, we can finish setting up osTicket in our browser! Our settings so far are:
- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: Password1
- And Click “Install Now!”

</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409350-7c2796de-0efc-4cb1-9563-65f86dc738e6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Congratulations! We should see an install page without errors. To continue in our next tutorial, we can browse to your help desk login page at: http://localhost/osTicket/scp/login.php
</p>
<br />

<p>
<img src="https://user-images.githubusercontent.com/129685324/234409350-7c2796de-0efc-4cb1-9563-65f86dc738e6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
There are also a few clean-up steps we need to do.
- Delete: C:\inetpub\wwwroot\osTicket\setup
- Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<br />
