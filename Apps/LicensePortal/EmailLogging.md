---
title: Email Logging
description: 
published: true
date: 2024-01-19T15:01:11.109Z
tags: 
editor: markdown
dateCreated: 2023-06-13T14:25:10.994Z
---

# Email Logging	
Customers have complained about not recieving an email and therefore a log to all emails has been added. This logs to a new table in the GHALicensePortal called EmailLogs:

| Name |Type|
|-|-|
|EmailId|UniqueIdentifier|
|DateStamp|DateTime|
|SendingTo|NVARCHAR(100)|
|Subject|NVARCHAR(200)|
|Body|NVARCHAR(max)|

A new DbSet was added to the LicenseServerContent inside the LicenseServer. This contains a Write Function.

This allows for easy writing to these logs. The write function is:

EmailLogs.Write(string SendingTo, string Subject, string Body)

The logs also automatically assign a DateStamp and a unique identifier.