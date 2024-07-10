<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Link to downloads</a>

<h2>Installation Steps</h2>

1. **Create a Virtual Machine**:
    - Go to <a href="https://portal.azure.com/">Azure Portal</a>.
    - Setup a VM with Windows 10 Pro, version 22H2.
    - Ensure the VM has at least 2 vCPUs and 16 GB of memory.

2. **Connect to the Virtual Machine**:
    - Use the public IP address of the VM.
    - Connect using the Remote Desktop Connection app.

<p align="center">
<img src="https://imgur.com/MAhXK2e.png" height="80%" width="80%" alt="Remote Desktop Connection"/>
<img src="https://imgur.com/Zf2jw07.png" height="40%" width="40%" alt="Remote Desktop Connection"/>
</p>

3. **Enable IIS**:
    - Open Control Panel -> Programs -> Turn Windows features on or off.
    - Install/enable IIS with CGI and Common HTTP Features.
    - Make sure all Common HTTP Features are checked.

<p align="center">
<img src="https://imgur.com/fGXMpx4.png" height="40%" width="40%" alt="Windows Features"/>
<img src="https://imgur.com/LBGkAw6.png" height="40%" width="40%" alt="Windows Features"/>
<img src="https://imgur.com/LQjw9le.png" height="40%" width="40%" alt="IIS Installation"/>
<img src="https://imgur.com/pbPeHb1.png" height="40%" width="40%" alt="IIS Installation"/>
</p>

4. **Verify IIS Installation**:
    - Open a browser and navigate to `127.0.0.1`.
    - The IIS welcome page should be displayed.

<p align="center">
<img src="https://imgur.com/eICujoq.png" height="40%" width="40%" alt="IIS Verification"/>
</p>

5. **Install PHP Manager for IIS**:
    - Download and install `PHPManagerForIIS_V1.5.0.msi` from the Installation Files.

6. **Install Rewrite Module**:
    - Download and install `rewrite_amd64_en-US.msi` from the Installation Files.

7. **Setup PHP**:
    - Create a folder in the C drive called `PHP`.
    - Download PHP 7.3.8 (`php-7.3.88-nts-Win32-VC15-x866.zip`) and unzip the contents into `C:\PHP`.
    - If a warning appears, choose to "Keep" the file.

<p align="center">
<img src="https://imgur.com/xZv1Yhw.png" height="40%" width="40%" alt="PHP Warning"/>
<img src="https://imgur.com/YwBhqo0.png" height="40%" width="40%" alt="PHP Warning"/>
</p>

8. **Install VC Redist**:
    - Download and install `VC_redist.x86.exe` from the Installation Files.

9. **Install MySQL**:
    - Download and install MySQL 5.5.62 (`mysql-5.5.62-win32.msi`).
    - Run the setup wizard:
        - Select Typical Setup.
        - Launch Configuration Wizard.
        - Choose Standard Configuration.
        - Set the root password to `Password1`.
    - Execute the process on the next page.

<p align="center">
<img src="https://imgur.com/KxcUy7C.png" height="40%" width="40%" alt="MySQL Setup"/>
<img src="https://imgur.com/i7sn6hT.png" height="40%" width="40%" alt="MySQL Setup"/>
</p>

10. **Configure PHP in IIS**:
    - Open IIS as an administrator.
    - Click on PHP Manager.
    - Register new PHP version by providing the path to `php-cgi.exe` in `C:\PHP`.
    - Restart the IIS server.

<p align="center">
<img src="https://imgur.com/rgdZwmM.png" height="40%" width="40%" alt="IIS"/>
<img src="https://imgur.com/vvTLNBH.png" height="40%" width="40%" alt="PHP Manager"/>
<img src="https://imgur.com/qdbn5zQ.png" height="40%" width="40%" alt="PHP Manager"/>
<img src="https://imgur.com/oJZ0gp9.png" height="40%" width="40%" alt="PHP Manager"/>
<img src="https://imgur.com/CJ3RUbG.png" height="40%" width="40%" alt="Restart IIS"/>
</p>

11. **Install osTicket**:
    - Download osTicket from the Installation Files Folder.
    - Extract and copy the "upload" folder to `C:\inetpub\wwwroot`.
    - Rename "upload" to "osTicket".
    - Reload IIS.

12. **Configure osTicket in IIS**:
    - Go to `Sites -> Default -> osTicket`.
    - Click “Browse *:80” on the right side.
    - Some extensions may not be enabled in the osTicket browser.

<p align="center">
<img src="https://imgur.com/Yw55d5b.png" height="40%" width="40%" alt="osTicket IIS"/>
<img src="https://imgur.com/eJIsGTn.png" height="40%" width="40%" alt="osTicket Extensions"/>
</p>

13. **Enable PHP Extensions**:
    - Go to IIS, `Sites -> Default -> osTicket`.
    - Double click PHP Manager.
    - Click "Enable or disable an extension".
    - Enable the following extensions:
        - `php_imap.dll`
        - `php_intl.dll`
        - `php_opcache.dll`

<p align="center">
<img src="https://imgur.com/vvTLNBH.png" height="40%" width="40%" alt="PHP Manager"/>
<img src="https://imgur.com/uigyKjb.png" height="40%" width="40%" alt="PHP Manager"/>
<img src="https://imgur.com/cOem7Nb.png" height="40%" width="40%" alt="PHP Extensions"/>
</p>

14. **Configure `ost-config.php`**:
    - Rename `ost-sampleconfig.php` to `ost-config.php` in `C:\inetpub\wwwroot\osTicket\include`.
    - Right click on the file, go to properties -> security -> advanced.
    - Disable inheritance, remove all inherited permissions.
    - Add new permissions for "Everyone" with Full Control.
    - Click Apply and OK.

<p align="center">
<img src="https://imgur.com/VPZvOdo.png" height="40%" width="40%" alt="File Permissions"/>
<img src="https://imgur.com/PoGk34d.png" height="40%" width="40%" alt="File Permissions"/>
<img src="https://imgur.com/F4H3ppM.png" height="40%" width="40%" alt="File Permissions"/>
<img src="https://imgur.com/rbbGqwB.png" height="40%" width="40%" alt="File Permissions"/>
<img src="https://imgur.com/saRO3y5.png" height="40%" width="40%" alt="File Permissions"/>
</p>

15. **Complete osTicket Setup in Browser**:
    - Continue setup in the osTicket browser page, filling out all required fields except the Database Settings.
    - Download and install HeidiSQL from the Installation Files.

<p align="center">
<img src="https://imgur.com/i7a4gWC.png" height="40%" width="40%" alt="HeidiSQL"/>
</p>

16. **Configure Database in HeidiSQL**:
    - Create a new session in HeidiSQL.
    - Ensure the username is `root` and the password is `Password1`.
    - Create a new database named `osTicket`.
    - In the osTicket browser setup, under MySQL Database, enter `osTicket` with the username `root` and password `Password1`.

<p align="center">
<img src="https://imgur.com/g5M1i61.png" height="40%" width="40%" alt="HeidiSQL"/>
<img src="https://imgur.com/LEAZNOc.png" height="40%" width="40%" alt="HeidiSQL"/>
<img src="https://imgur.com/0rG1AJm.png" height="40%" width="40%" alt="HeidiSQL
