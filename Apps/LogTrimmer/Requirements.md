---
title: Log Trimmer Requirements
description: 
published: true
date: 2024-01-19T15:01:36.112Z
tags: 
editor: markdown
dateCreated: 2023-02-02T13:12:42.036Z
---

# Log Trimmer Requirements

**Requirement Specification**
**MFS 00001**
**04/10/22**

**Peter Roden**

## Revision History


|Date|Description|Author|Comments|
|-|-|-|-|
|04/10/22|First Release|PR|Rev 1|


## Document Approval

The following Software Requirements Specification has been accepeted and approved.

## Target Version
TBD

## 1. Business Requirements

- Various logs are written to in our mobile applications database, but there is no truncation and so the logs will grow forever. The logs need to be trimmed periodically.
 
## 2. Funcational Requirements

The log tables in each customer database need to be truncated.

The tables (to date) are:

	mfs.MessageLogs
	mfs.ErrorLogs
	mfs.KeyLogs
	mfs.ChangeLogs
  
Logs more than 60 days old should be cleared out.
 
Phase 2 - we will need to specify a list of tables to be truncated and loop through this

	aqs.MessageLogs
	aqs.ErrorLogs
  
## 3. Technical Requirements

Create a worker process that can run in a docker container.
The process should loop every day.
A configuration file should define the loop period and the clear period.
The process should firstly loop through each customer.
The customers are defined in GHALicensePortal.dbo.Customers.
Loop through each of the tables above for each customer.
`db = new FieldServiceRepository(_licrepository, _token).Context; `

**Deleting the data**
Use :  `db.MessageLogs.RemoveRange(<dataset>)`