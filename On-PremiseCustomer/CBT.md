---
title: CB Technology
description: 
published: true
date: 2024-04-02T15:05:34.779Z
tags: 
editor: markdown
dateCreated: 2024-03-27T16:40:16.907Z
---

# C B Technology

## VPN Set-Up

Click [Here](https://62.6.60.12:60443/sslvpn_logon.shtml) and login with the GHA Admin details documented in 1Password.

 

Once logged in you are presented with 3 options: 

 

Option 1: Download the Watchguard Windows VPN

Option 2: Download the Watchguard Mac OS VPN

Option 3: Download the Mobile SSL VPN profile (.ovpn file)

 

The Mobile VPN with SSL client profile works with OpenVPN and the profile can be imported and used with the credentials used to login previously or Download the Windows Watchguard if not installed already and use the remote address located in 1Password and then use the same login details as before.

## Below is the server information needed to access the environments once the vpn connection has been established: 

 

### CBT Epicor App Server

**Name** - CB-EPICORAPP

**IP Address** - 192.168.0.246

## CBT SQL Server

 

**Name** - CB-EPICORSQL

**IP Address** - 192.168.0.250
 
## Certificate Installation Guide

[Certificate Install Guide](/install-cbt-app-server-cert.pdf)

## Epicor URL's

[Client Deployment](https://epiclientsdeployment.blob.core.windows.net/deployment/CBT_Client_Installer.zip)

[Live](https://cb-epicorapp/cbtlive/home)

[Pilot](https://cb-epicorapp/cbtpilot/home)

[Demo](https://cb-epicorapp/cbtdemo/home)

> Please click “Client Deployment” in the above list if you wish to download the environment locally and follow the steps below. 
{.is-warning}

To download the clients, please install the VPN. Once you have an established connection to CBT, disconnect and install the certificate (guide located within the folder). Then simply click the link below and run the .exe file within the folder. All shortcuts to each environment will appear in the “Epicor” folder on your desktop.



## Additional Information 

**Current Mods Installed:**

- PO Approval 
- Mobile Inventory Management System 

