<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
For this lab, I share how to get started with using and installing osTicket with files that are referenced <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">here</a>. I completed this lab using a Windows 10 Pro Virtual Machine created through Microsoft Azure.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- MySQL
<h2>Operating Systems Used</h2>

- Windows 10 (21H2)

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/m6Bek7Y.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Prior to getting started, the Internet Information Services must be enabled. To use osTicket locally, it requires IIS to properly function.
  That can be done by: 
 <p> Opening the Control Panel > Open Programs > Turn Windows Features On or Off</p>
 <p>From this menu, you select Internet Information Services > Web Management Tools > enable IIS Management Console you can then click through World Wide Web Services > Application Development Features > enable CGI and click ok to confirm.</p>
</p>
<br />

<p>
<img src="https://i.imgur.com/RB5YByC.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
After enabling IIS, you can download and install PHP Manager for IIS (PHPManagerforIIS_V1.5.0.msi) from the provided installation files folder. Download and install the Rewrite Module (rewrite_amd64_en-US.msi) after installing PHP Manager for IIS.
</p>
<br />

<p>
<img src="https://i.imgur.com/neliVrg.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
After installing the Rewrite Module, create a new folder/directory called C:\PHP on the Windows (C:) drive. This new folder will be used to unzip the contents from the PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) zip folder downloaded from the installation files. Extract all contents from the zip folder into the C:\PHP folder.
</p>
<br />

<p>
<img src="https://i.imgur.com/mYKZExi.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Following the previous step, download and install VC_redist.x86.exe from the installation files folder.
</p>
<br />

<p>
<img src="https://i.imgur.com/UW2eIpW.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Then, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files. Inside the MySQL setup wizard, select "I agree" > Typical install > Install > Launch the Configuration Wizard after the installation. Select Standard Configuration > Install As Windows Service > ensure the "Launch the MySQL Server automatically" is checked. 

<p>For credentials, the username will be root and the password is Password1. In a practical setting, the credentials will be basic to where they can be easily guessed. For the purposes of this lab, the standard credentials root and Password1 will do.</p>
<br />

<p>
<img src="https://i.imgur.com/UW2eIpW.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Before installing osTicket, configurations need to be made within IIS. </p>
<p>So Open IIS as an admin > select PHP Manager. Within PHP Manager > Register new PHP version > Browse and select the PHP CGI executable file (php-cgi.exe) within the PHP folder created earlier in the lab. After registering the PHP version, reload the IIS server within the management console.</p>
</p>
<br />

<p>
<img src="https://i.imgur.com/9ylqXGk.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/KoK1Lug.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
From the installation files, download osTicket v1.15.8. Extract and copy the "upload" folder to the following path: c:\inetpub\wwwroot. Within the c:\inetpub\wwwroot folder, rename "upload" to "osTicket." Reload the IIS server afterward.
</p>
<br />

<p>
<img src="https://i.imgur.com/ivQmua0.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/s856Cpz.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/pNkLVo6.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/Mpq7ybU.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Within the IIS console, select Sites > Default > osTicket. Click "Browse *:80" and the installation page for osTicket will now show up. Some extensions are not enabled and they will be enabled with the IIS console before installing osTicket. To do so, click on PHP Manager while in the osTicket menu in IIS. Click on "Enable or disable an extension." Enable the following extensions: php_imap.dll, php_intl.dll, php_opcache.dll.
<img src="https://i.imgur.com/CdkPTsv.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/5ggnkk9.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<br />

<p>
Before continuing to install osTicket, a file needs to be renamed and its permissions need to be changed. From C:\inetpub\wwwroot\osTicket\include, rename ost-sampleconfig.php to ost-config.php. The newly named ost-config.php will have its permissions changed. Open its Properties and change the following permissions: Disable inheritance > Remove All and New Permissions > Everyone > All.</p>
<p><img src="https://i.imgur.com/zExrqYG.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/PiJMYZ6.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<br />

<p>
From the installation files, download and install HeidiSQL. Create a new session with HeidiSQL and enter the password used in the installation of MySQL earlier. Within the new session, right-click on Unnamed and create a new database named osTicket.
<img src="https://i.imgur.com/gOqjR1k.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<br />

<p>Within osTicket browser window, enter the necessary details to set up osTicket. For the MySQL database, use the credentials used for MySQL and HeidiSQL.</p>
<img src="https://i.imgur.com/3nczMAD.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/7V2YmH6.png" height="80%" width="80%" alt="Installation Steps"/>

<p>After everything is done, osTicket should now be installed! Before continuing to use osTicket, some clean up has to be done. First, delete the setup folder found in C:\inetpub\wwwroot\osTicket. Next, return to C:\inetpub\wwwroot\osTicket\include and change the permissions of the ost-config.php file. The file should no longer have full access to Everyone. Revert the permissions to "Read" only.</p>

<h2>osTicket Installed!</h2>

Now, osTicket is now installed and ready to be used. I used osTicket to understand how ticketing systems work and how to resolve tickets. I understand that working in a help desk or desktop support position I will be working to clear tickets while in a variety of situations. Running simulations of a ticketing system and implementing the system itself in a lab environment gave me experience on multiple sides of the program as the administrator and a user of the system.
