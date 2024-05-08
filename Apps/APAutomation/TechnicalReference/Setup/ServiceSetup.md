---
title: Service Setup
description: 
published: true
date: 2024-01-17T13:32:37.997Z
tags: 
editor: markdown
dateCreated: 2023-02-06T15:36:34.665Z
---

# Service Setup

The **GHA AP Automation Service** requires additional setup for it to connect the **Customer Account** on **Readsoft**

# `appsettings.json`

This file is used to configure the **GHA AP Automation Service**. The `ReadSoft` section stores the `API Key`, `Username` and `Password` needed to connect to **Readsoft.** These credentials stored are encrypted, via the `Test.API`, and are decrypted during runtime.

> This file is stored within the **AP Automation Source Code**
{.is-info}


## Configuration

> This section should not require action, unless the configuration is outdated or lost.
{.is-info}


This section describes how to setup the `appsettings.json` file, in the event that the configuration becomes outdated or lost.

## Readsoft Username

This value is set to the username of the `GHA_API_User`

> See [GHA API User](/Apps/APAutomation/TechnicalReference/GHAAPIUser)

## Readsoft Password

This value is set to the password of the `GHA_API_User`

> See [GHA API User](/Apps/APAutomation/TechnicalReference/GHAAPIUser)

## Readsoft API Key

This value is set to the `API Key` of the top-level `GHA Solutions` organization within [Readsoft](https://ghasolutions.readsoftonline.com/ "https://ghasolutions.readsoftonline.com/")

### Finding the API Key

#### 1. Login to the [Readsoft Portal](https://ghasolutions.readsoftonline.com/ "https://ghasolutions.readsoftonline.com/") using a **GHA Administrative Account**

#### 2. Navigate to `Account/Services/Target system`

![servicesetup1.png](/servicesetup1.png)

#### 3. Copy the `API Key`

![servicesetup2.png](/servicesetup2.png)
---

# Customer App Settings

>Each of the following settings are stored in the `AppSettings` table **for each customer >database** 
>- The **Username, Password and API Key** may be consistent between **each customer** 
>- **But the Organisation Id must be different**


> Currently, the only way to edit these values is using SQL Queries with a direct connection to the database
{.is-warning}


# Readsoft Organisation Id

Each **Customer Account** on Readsoft is given an **Organisation Id** which is **essential** for the **GHA AP Automation Service** to differentiate each **Customer Account**

This value is stored against the key `ReadSoftOrganizationID` as a `ValueString`

-   Refer to **Finding the Organisation** Id for retrieving the **Organisation Id**
    

## Finding the Organisation Id

### 1. Login to the [Readsoft Portal](https://ghasolutions.readsoftonline.com/ "https://ghasolutions.readsoftonline.com/") using a **GHA Administrative Account**

### 2. Navigate to `Customers/{Customer}`

> Where **{Customer}** is the name of the customer that is currently being set up
{.is-info}


![servicesetup3.png](/servicesetup3.png)

### 3. Copy the `OrganisationId` from the `Url`

-   In the URL, copy the GUID after `/org/` and before the `/{CustomerName}`
    

For example

> https://ghasolutions.readsoftonline.com/admincenter#/org/**7e73b998eab44fe4978cd2b0d465cc1c**/gha-test-customer

---

# Readsoft Support Email Address

When a **document encounters an error during extraction**, the **GHA AP Automation Service** sends an email, detailing the error, to the **Readsoft Support Email Address**

This value is stored against the key `APAutomationSupportEmailAddress` in the `Admins` table

-   Set it to the `support@ghasolutions.co.uk`