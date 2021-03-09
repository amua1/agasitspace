---
author: "Aga's IT Space"
date: "2021-03-09" 
linktitle: "Tutorial 2: Install and Configure OpenSSH Server in Windows"
title: "Tutorial 2: Install and Configure OpenSSH Server in Windows"
weight: 10
---


* The following article provides instructions on how to install and configure OpenSSH Server under Windows 10 and Server 2016/2019

# Fast set-up (when in hurry - just copy and paste without asking):
```powershell
Get-WindowsCapability -Online | ? Name -like 'OpenSSH*'

Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0

Start-Service sshd

Set-Service -Name sshd -StartupType 'Automatic'

# Confirm the Firewall rule is configured. It should be created automatically by setup.
Get-NetFirewallRule -Name *ssh*

New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force

ssh user@domain@IP-HOST
```
 &nbsp;

# Main Points:

1. Check whether OpenSSH Server is already installed
2. Install OpenSSH using PowerShell
3. Initial Configuration
4. Configure PowerShell as the default SSH shell.
5. Connect to the remote Windows Server machine using SSH

&nbsp;

# 1. Check whether OpenSSH Server is already installed:
* First of all we check whether we have OpenSSH Server already installed on our system by using the following PowerShell command:
```powershell
Get-WindowsCapability -Online | ? Name -like 'OpenSSH*
```
&nbsp;
# 2. Install OpenSSH using PowerShell:
* If OpenSSH Server is not installed , proceed by entering the following PowerShell command to install it:
```powershell
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
```
&nbsp;
# 3. Initial Configuration:
* After the installation finishes , we need to make some initial configuration in order for OpenSSH to be setup properly: 
* We will continue by configuring the following settings

1. Start the sshd service:
```powershell
Start-Service sshd
```
2. Set the startup type to Automatic:
```powershell
Set-Service -Name sshd -StartupType 'Automatic'
```
3. Check whether the Firewall rule for SSH is created (in most cases the rule is automatically created) , if not proceed to add the rule
```powershell
Get-NetFirewallRule -Name *ssh*
New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
```

&nbsp;

# 4. Configure PowerShell as the default SSH shell (optional):
* If you want to use PowerShell as the default shell instead of CMD when you connect to the server , use the following command:
```powershell
New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force
```
&nbsp;

# 5. Connect using SSH:
* It is time to test your work, if the computer you are connecting to is part of an Active Directory Domain then use the following command to SSH into it:
```powershell
ssh user@domain@ipaddress
```
* If the computer is not part of an Active Directory Domain , use the classic command to SSH into it:
```powershell
ssh user@ipaddress
```

&nbsp;

#### More in-depth explanation can be found at the Microsoft website:
```
https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse
https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_server_configuration
```

