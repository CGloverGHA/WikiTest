---
title: Hobsons
description: 
published: true
date: 2024-04-02T15:07:03.568Z
tags: 
editor: markdown
dateCreated: 2024-04-02T12:27:02.367Z
---

# Hobsons

## OpenVPN Connect Client Required to connect

1.) [Download](https://openvpn.net/client-connect-vpn-for-windows/)

2.) Copy the extracted folder which contains the .ovpn file to             C:\Users<username>\OpenVPN\Config folder

3.) Import the certificate 1st from the settings of the OpenVPN client and use the password located via the link below in 1Password.

4.) Import the .ovpn file in the OpenVPN client from the profiles screen (click "+")

5.) Use the VPN user details from the link below
  
  
---


## Below is the server information needed to access the environments once the VPN connection has been established: 

### Hobsons Epicor Application Server

 **Name** - HOBAPP01 

**IP Address** - 10.0.140.214

**Server hosting:**

- Epicor ERP App Servers
- TIMS ERP (old system)
- Sage 50 Accounts data
 

---

### Hobsons SQL Server

**Name** - HOBSQL01

**IP Address** - 10.0.140.215

**Databases held:**

- Epicor ERP
- TIMS
- Hobsons File Server

---

### Hobsons File Server

**Name** - HOBFS01

**IP Address** - 10.0.140.213

## Epicor URL's

> [Live](https://hobapp01/hobsonslive/home)
{.is-info}


> [Pilot](https://hobapp01/hobsonspilot/home)
{.is-info}


> [Demo](https://hobapp01/hobsonsdemo/home)
{.is-info}


 