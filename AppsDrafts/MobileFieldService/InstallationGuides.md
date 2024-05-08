---
title: Installation Guides
description: 
published: true
date: 2024-01-19T15:03:11.924Z
tags: 
editor: markdown
dateCreated: 2023-09-08T13:34:11.305Z
---

# <div style="color:red"> Epicor Installation of Mobile Field Service </div>

This document outlines how to implement the BAQs and data directives and dashboards associated with the GHA Mobile Inventory Management Service application.

## System Requirements

The implementation is available for the following Epicor versions:
-	10.2.600.x
-	10.2.700.x
-	Kinetic 2021.1.x (Classic screens only)
-	Kinetic 2021.2.x (Classic screens only)

## Pre requisites

[GHA Mobile Fields for Epicor](/Apps/MobileFieldService/InstallationGuides/FieldsEpicorInstallationGuide)

[GHA Parameter Screen for Epicor](/Apps/MobileFieldService/InstallationGuides/ParametersEpicorInstallationGuide)

## Installation files

The following files are required to perform the installation
- [GHA MFS Customer Solution](/epicor_cabs/gha_mfs_customer_solution.cab)

- [GHA MFS Dashboards Customer Solution](/epicor_cabs/gha_mfs_dashboards_customer_solution.cab)

## Installed Components

For a list of installed components please refer to the [TechnicalReference](/Apps/MobileFieldService/TechnicalReference)

## Installation of the main CAB file

In Epicor open the ‘Solutions Workbench’
-	Under the ‘Actions’ menu click ’Install Solution’.
-	Click the ‘Solution File’ button and browse to the location of the CAB file 
	**GHA MFS Customer Solution.cab**
-	Check ‘Only Target Current Company’
-	Check ‘Remove Directives with Matching Name’ and ‘Delete Previous Install’ if upgrading
-	Select “Automatically overwrite duplicate files” and “Automatically overwrite duplicate data”
-	Click Install

## Installation of the Dashboard CAB file

In Epicor open the ‘Solutions Workbench’
-	Under the ‘Actions’ menu click ’Install Solution’.
-	Click the ‘Solution File’ button and browse to the location of the CAB file 
	**GHA MFS Dashboards Customer Solution.cab**
-	Check ‘Only Target Current Company’
-	Check ‘Remove Directives with Matching Name’ and ‘Delete Previous Install’ if upgrading
-	Select “Automatically overwrite duplicate files” and “Automatically overwrite duplicate data”
-	Click Install
<br/>
In Epicor go to Dashboard Maintenance
-	Click Dashboard ID
-	Search for the following Dashboards 
	-	GHA_MFS
	-	GHA_MFS_Errors
	-	GHA_MFS-Status
-	Select these dashboards and click OK
-	Click “Actions” and “Deploy All UI Applications” to deploy all Dashboards

## Change Log

<br/>

### Version 12

> Released 10/8/2023
{.is-info}

#### Data Directives

- JobOpDtl (Operation Scheduled Resources ***GHA_MFS_OpDtlService_Link***, ***GHA_MFS_OpDtl_Link*** Fix for operations being sent multiple time causing occasional sync issues, manifesting in labour records not being added
- PartWhse (***GHA_MFS_PartWhseLink***) caused speed issues - improved

### Version 11

> Released 14/7/2023
{.is-info}

#### Data Directives

- *UDCodes **GHA_MFS_EmployeeFilter_Link*** added for employee filters based on the parameter screen settings
- *Employee **GHA_MFS_EmpBasic_Link*** link amended for employee filters
- *PartBin **GHA_MFS_PartBin_Link*** Fixed issue where both transaction (before and after) were sent, now only the after number is
<br/>

### Version 10

> Released 30/6/2023
{.is-info}

#### Business Activity Queries

- GHA_MFS_PartSerials amended to include status of SHIPPED for the job history to work
- 

#### Data Directives

- *SerialNo **GHA_MFS_SerialNo_Link*** link amended for status 'SHIPPED'
- *UDCodes **GHA_MFS_EmployeeFilter_Link*** added for employee filters based on the parameter screen settings
- *Employee **GHA_MFS_EmpBasic_Link*** link amended for employee filters

<br/>

### Version 9

> Released 7/6/2023
{.is-info}

#### Business Activity Queries

- GHA_MFS_Equipment added to include equipment for maintenance jobs
- GHA_MFS_Customers amended to include plant/site details for maintenance jobs
- GHA_MFS_JobHead amended to include maintenance jobs
- GHA_MFS_JobMtl amended to include maintenance jobs
- GHA_MFS_JobOper amended to include maintenance jobs
- GHA_MFS_JobPlants amended to include maintenance jobs

#### Data Directives

- *Plant **GHA_MFS_Plant_Link*** added for maintenance jobs
- *Equip **GHA_MFS_Equip_Link*** added for maintenance jobs
- *JobHead **GHA_MFS_JobHead_Maintenance_Link*** added for maintenance jobs
- *JobMtl **GHA_MFS_JobMtl_Link*** link amended for maintenance jobs
- *JobOper **GHA_MFS_JobOper_Link*** link amended for maintenance jobs


<br/>

### Version 8

> Released 22/3/2023
{.is-success}

* Bug fix - Reason codes stored in the app settings were not exporting with the correct code type

* Bug fix - Firming a job caused an error with job material link
<br/>
### Version 7

> Released 24/02/2023
{.is-success}

#### Data Directives

Bug fix - JobOpDtl data directive was not returning cash payments flag to field service

### Version 6

> Released 02/02/23
{.is-success}

### Business Activity Queries

GHA_MFS_Jobs filtered out historical (completed) jobs with no date from the initial import

### Version 5

> Staged 24/11/2022
> Awaiting release
{.is-success}

#### Dashboards

The Field Service dashboard now displays notes stored against photos taken on the app

#### Data Directives

JobHead Link now sends the serial number defined against the service call to Epicor
AppSettings Link
EmpBasicLink
ResourceGroup Link
JCSshift Link
JCDept Link
LabExpCd Link
These tables now send data to MFS to classify/filter the employees on the scheduling dashboard

#### Business Activity Queries

GHA_MFS_EmpBasic – added column for employee filter, EmpFilter
GHA_MFS_EmpFilter – table which displays the category used for classifying/filtering employees in MFS

#### User codes

New user code ‘EmpFilter’ which defines the employee category used for classifying/filtering employees in MFS, one of
•	SHIFT
•	EXPENSECODE
•	JCDEPT
•	RESOURCEGRPID

<br/>

### Version 4
> Released 15/11/2022
{.is-success}

#### Data Directives	
JobHead Service Link 
JobHead Link – Deleting a job will make the job void in Field Service
#### Method Directives
JobEntry.Update GHA_MFS_PreventDeleteIfStarted – amended to prevent material lines being deleted if the job is started

<br/>

### Version 3
> Released 13/10/2022
{.is-success}
#### Data Directives	
Part Bin Link – issue with stock updates from Transfer orders not uploading to field service
JobHead Link – if a released job is deleted mark as void in Field Service
FsTech Link – one time ship to not sent up to MFS
#### Method Directives
Warehouse Link – updates parts, part bins and serial numbers associated with the warehouse if the mobile flag is checked. A warning message is shown before updating.
JobHead – prevent deletion if a job has been started in field service
#### Functions
Changes from Epicor are added to the usual queue, changes from outside (eg rest, DMT) are added to the sync queue
Added UD100 table to the sync function
<br/>

