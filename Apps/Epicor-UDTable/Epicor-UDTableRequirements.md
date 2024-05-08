---
title: Epicor - UD Table Requirements
description: 
published: true
date: 2024-01-19T15:00:51.076Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:00:42.453Z
---

# Requirements


## Business Requirements 

GHA host Epicor for several of its customers. If a customer wants to add a UD field they contact GHA support and the field is added manually out of hours. This process should be automated.

Curently when a customer wants to make a change to a UD table, the have to get in contact with us and the table has to be amended and then manually restarted. This is time consuming and can become a problem with higher amounts of customers. This process should be automated. Customers would make a request to change a table through the licence portal (TBC). This request will be stored in a database and actioned.
 

## Functional Requirements 

The customer will request a change (new field, delete existing field) via the Licence Portal.

A service will run which will action the changes at a set time each evening. This will
- add the field to UD Column Maintenance
- rebuild the Epicor database
- recycle the application pool for each application
> The application pool cannot be recycled if a process is running{.is-warning}

## Technical Requirements

### Database changes

A new table added to the GHALicensePortal database, `erp.columns` with the following structure:

Column|Type|Notes
---|---|---
CustomerId|Guid| |
UserId|Guid| |
DateRequested|DateTime| |
TableName|String| |
FieldName|String| |
DataType|String| |
FieldFormat|String| |
Required|Bool| |
Description|String| |
DateActioned|DateTime| |
Actioned|Bool|Attempted to be done|
Success| Bool|Marks a successful regen|


### Licence Portal

The customer needs to be able to submit a request. Do we do this via Epicor  (with a rest call and a message queue to add to the erp.columns table) or via the license portal?

### Worker Service

The worker will run on a schedule. For each customer it needs to find the optimum time to add the field
- out of office hours (using the time zone?)
- when no users are logged in (Session Manager)
- when no planned tasks are running (user specific databases)
<br/>

#### Add a record to the ZDataField table in Epicor

- Read the erp.columns table where Success = false
- Get the Epicor REST detais for each customer
- Add the fields to ZDataField using the ... Service

#### Regenerate the database

This can be achieved by calling the following on the Application server

`"C:\Program Files (x86)\Common Files\Epicor Software\Database Manager Extensions\3.2.500\DataModelGenerator\Ice.Tool.DataModelGenerator.CL.exe" /ConfigFile = "C:\epicor\scripts\ConfigDM.xml" /logfile="C:\temp\DataModel.log"`

The regenerate funcation can take a few minutes to happen. This means the server should be dissabled for a little while to stop users from logging in.

#### Recycle the application pool

This can be achieved by calling the following on the Application server

`net stop  EpicorICETaskAgent`
`net start  EpicorICETaskAgent`

The task agent may well need to be saved in the company settings somewhere - how can we future proof this?

This also needs to be repeated for many different applications that need to also be recycled.

After the regeneration, the files:
 - Erp.Data{company}.dll
 - Ice.Data.Model.dll 
 should be new. 
 
 Also need to find a way to make sure that the tables are synced up.

#### Error reporting

What do we do about unsuccessful attempts?

> Note this service may be extended to other facilities within Epicor
{.is-info}
