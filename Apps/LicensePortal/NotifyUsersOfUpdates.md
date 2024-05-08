---
title: UpdateEmailTechRef
description: 
published: true
date: 2024-01-19T15:01:23.268Z
tags: 
editor: markdown
dateCreated: 2023-04-11T09:41:46.321Z
---

# Technical Reference


The Update Emails project adds 3 extra options to Applications on the License Portal

![image_2023-04-11_102839541.png](/image_2023-04-11_102839541.png)

The three options only show up if the "WikiLinks" column (bit) in the Application table is set to true. 

The three options are: 
- Send Cab Emails
- Send Update Emails
- Send User Guide Emails


### Requirements for emails to be sent

If the user's **Customer ID** is **"99999999-9999-9999-9999-999999999999"** then the email will be sent to all the users with the **"Comm"** role.

However, if the customer id is not the testing one then certain requirements have to be met.

Requirements:
- Customer must have the application
- Application must not be suspended
- Customer must not be suspended
- User but have the "Comm" role
- User must have a GHA Wiki account which is active


The Cab email also requires for the "HostingType" column (varchar) must be either set to "OnPremise" or "EpicorSaaS" 

Email which the user will recieve differs from each option. All can be seen below.


#### Cab Email
![image_2023-04-11_104017160.png](/image_2023-04-11_104017160.png)

#### Update Email
![image_2023-04-11_104059308.png](/image_2023-04-11_104059308.png)

#### User Guide Update
![image_2023-04-11_104135149.png](/image_2023-04-11_104135149.png)