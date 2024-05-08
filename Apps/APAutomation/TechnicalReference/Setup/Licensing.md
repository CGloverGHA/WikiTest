---
title: Licensing Setup
description: 
published: true
date: 2024-01-17T13:32:32.926Z
tags: 
editor: markdown
dateCreated: 2023-02-02T14:34:05.731Z
---

# Licensing Setup (AP Automation)


Before the customer can use the service, the customer must have a license key. This can be created by a GHA administrator on the [License Portal](https://mobileapps.ghahosted.com/licenseportal).

Please note that the **GHA License Portal** is undergoing a re-write and the following documentation may be **irrelevant** or **misleading** once the re-write is complete and deployed

## Creating the Customer

These steps are only required if the customer does not already exist on the [License Portal](https://mobileapps.ghahosted.com/licenseportal). If the customer already exists, these steps can be skipped

### 1. Login to the [License Portal](https://mobileapps.ghahosted.com/licenseportal) as a **GHA Administrator**

### 2. Navigate to Customers on the sidebar

![083695d1-5767-4a5b-ad95-f9ab09d79849.png](/083695d1-5767-4a5b-ad95-f9ab09d79849.png)

### 3. Click on **Add new customer**

![4840d5c3-70ac-4bb6-9d9b-242298e3088a.png](/4840d5c3-70ac-4bb6-9d9b-242298e3088a.png)

### 4. Specify a **Name** and **Domain Name**

![af6644eb-eb84-4988-970f-db007596fcab.png](/af6644eb-eb84-4988-970f-db007596fcab.png)

## Activating the Customer

Before further action can be taken, the customer must be activated using the **database upgrade tool**

This tool is only available at **localhost:3000/DBUpdate** on the **Dev01 server**

-   In order to access it, you will need remote desktop access to **Dev01**
    

Please note that this documentation may become **irrelevant or misleading** as a result of the GHA License Portal re-write

### 1. Select the **newly created customer**

![a6081e7a-48e5-4629-914c-017dae133dd5.png](/a6081e7a-48e5-4629-914c-017dae133dd5.png)

### 2. Click on **Create**

![e16305c8-cdcf-4bba-8fa2-592c03a93d2d.png](/e16305c8-cdcf-4bba-8fa2-592c03a93d2d.png)

This will create the **required databases** for the **new customer**, thus activating the customer

## Add AP Automation to the Customer’s Applications

The **AP Automation** application must be added to the customer to license the customer to use it

### 1. Login to the [License Portal](https://mobileapps.ghahosted.com/licenseportal) as a **GHA Administrator**

### 2. Navigate to **Customers**

![3d5b4746-6341-4c67-a2ff-2f654e126d7c.png](/3d5b4746-6341-4c67-a2ff-2f654e126d7c.png)

### 3. Click the **Edit icon** of the **required customer**

![b6229455-f44f-426d-b1b1-7459c2c39a7a.png](/b6229455-f44f-426d-b1b1-7459c2c39a7a.png)

### 4. **Scroll down** to **Applications** and click **Edit Applications**

![8b817a24-100e-4600-8d6a-c5d580dd1442.png](/8b817a24-100e-4600-8d6a-c5d580dd1442.png)

### 5. Click the **Plus icon** on the **AP Automation** row

![677cde4f-cf03-4f44-aef6-249319c18925.png](/677cde4f-cf03-4f44-aef6-249319c18925.png)

### 6. Enter **one** for **Devices Licensed** and click **Save**

![9244755d-6b21-488c-8e5c-36186b8a1027.png](/9244755d-6b21-488c-8e5c-36186b8a1027.png)