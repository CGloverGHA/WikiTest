---
title: MFS Epicor Installation Guide
description: 
published: true
date: 2024-02-27T17:10:15.768Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:14:33.710Z
---

# Epicor Installation of Mobile Field Service

This document outlines how to implement the BAQs and data directives and dashboards associated with the GHA Mobile Inventory Management Service application.

## System Requirements

The implementation is available for the following Epicor versions:
-	10.2.600.x
-	10.2.700.x
-	Kinetic 2021.1.x (Classic screens only)
-	Kinetic 2021.2.x (Classic screens only)

## Pre requisites

[GHA Mobile Fields for Epicor](/Apps/MobileFieldService/InstallationGuides/FieldsEpicorInstallationGuide)

[GHA Parameter Screen for Epicor](/Apps/ParameterScreen)

## Installation files

The following files are required to perform the installation
- [GHA MFS Customer Solution](/epicor_cabs/gha_mfs_customer_solution.cab)

- [GHA MFS Dashboards Customer Solution](/epicor_cabs/gha_mfs_dashboards_customer_solution.cab)

*Note that from version 15 of the Customer Cab files there is a patch file which includes only the changes, see the change log below*

## Installed Components

For a list of installed components please refer to the [TechnicalReference](/Apps/MobileFieldService/TechnicalReference)

## Installation of the main CAB file

> Note - A bug in Epicor means the BPM Data Forms need to be deleted before the install as the BPM Data Form data does not clear properly.
{.is-danger}

In Epicor open the 'BPM Data Form designer'
- Open the following forms:
	- `GHA_MFS_Covered`
	- `GHA_MFS_CovLab`
	- `GHA_MFS_CovMtl`
	- `GHA_MFS_FC`
	- `GHA_MFS_FCLab`
	- `GHA_MFS_FCMat`
	- `GHA_MFS_WHLink`
- Delete each form

In Epicor open the ‘Solutions Workbench’
-	Under the ‘Actions’ menu click ’Install Solution’.
-	Click the ‘Solution File’ button and browse to the location of the CAB file 
	**GHA MFS Customer Solution.cab**
-	Check ‘Only Target Current Company’
-	Check ‘Remove Directives with Matching Name’ and ‘Delete Previous Install’ if upgrading
-	Select “Automatically overwrite duplicate files” and “Automatically overwrite duplicate data”
-	Click Install

> Note - If the BPM Form Data was not deleted prior to the install
{.is-danger}

An error such as this occurs when you import the solution:

```
Error Summary:  
Import cancelled or failed for 'Ice.IPForm_2d5aea0f-8cdc-4d25-aed2-6c0e263817bc'.
Import cancelled or failed for 'Ice.IPForm_5065c345-f69e-4b3e-81d5-eb326d0df8c8'.
Import cancelled or failed for 'Ice.IPForm_74972639-b55d-47c5-8e1d-0b46e9670e51'.
Import cancelled or failed for 'Ice.IPForm_7b6cb660-b7d8-4d96-a371-f2fd32092e22'.
Import cancelled or failed for 'Ice.IPForm_bec471f4-f9ee-44cc-8233-1153dff309a9'.
Import cancelled or failed for 'Ice.IPForm_c0db63ff-c0ec-4803-ba3c-0d81d68d02c7'.
Import cancelled or failed for 'Ice.IPForm_e445958c-9aa1-46b8-b576-a693fa69b24f'.
Import cancelled or failed for 'DirectiveID_6dfe27b3-ffe5-4251-8d14-a7763583b5ad'.
Import cancelled or failed for 'DirectiveID_8d31d27d-0263-4182-96d6-7b3adb219710'.
Import cancelled or failed for 'DirectiveID_910ca509-f1e0-40fa-96db-9fc2311f358a'.
```

To work around it you need to do the following:

- Open the BPM Data Form Designer in Epicor
- Add the following forms one at a time
	- `GHA_MFS_Covered`
	- `GHA_MFS_CovLab`
	- `GHA_MFS_CovMtl`
	- `GHA_MFS_FC`
	- `GHA_MFS_FCLab`
	- `GHA_MFS_FCMat`
	- `GHA_MFS_WHLink`
- Clear the BPM Data Form Designer screen
- Open the forms entered above (make sure it is only these forms and not one of your own)
- Delete each of the forms
- Install the BPM Data Forms affected by installing the CAB file found [here](/epicor_cabs/gha_mfs_data_forms_customer_solution.cab)


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

## Installation of a patch file

In Epicor open the ‘Solutions Workbench’
-	Under the ‘Actions’ menu click ’Install Solution’.
-	Click the ‘Solution File’ button and browse to the location of the CAB file 
	**GHA MFS Dashboards Customer Solution.cab**
-	Check ‘Only Target Current Company’
-	Check ‘Remove Directives with Matching Name’
-	Select “Automatically overwrite duplicate files” and “Automatically overwrite duplicate data”
-	Click Install
<br/>

## Change Log

<br/>


### Version 16

> Not yet released
{.is-warning}

#### Custom Fields

- **FsCallHd.GHA_MFS_CallNum_c** - link to call added in Field service application
- **JobHead.GHA_MFS_JobNum_c** - link to job added in Field service application
- **Part.GHA_MFS_ServicePart_c** - The part is servicable and therefore able to be selected when creating a service job
- **HDTopic.GHA_MFS_Topic_c** - MFS Topic/Issue
- **FsCallCd.GHA_MFS_CallType_c** - MFS call type

The fields need to be updated first before applying the patch file below

[GHA Mobile Fields for Epicor](/Apps/MobileFieldService/InstallationGuides/FieldsEpicorInstallationGuide)

> **Note**
> 
> A new field has been added to the part table and the GHA Part form for servicable part. Servicable parts are used to create a job in MFS and will ultimately be the part number against the service call line in Epicor. 
>
>This defaults to false in Epicor, though they have all been set to true in GHA Field Service. 
>
>If you make an amendment in or import parts from Epicor you will overwrite this value in Field Service. 
>
>We suggest you populate this field accordingly in Epicor which will then update Field Service.
>
>To remove the flag in Field service you will either have to check it, save and uncheck in Epicor, or perform a data import using the GHA License Portal.
>
>***Please contact GHA support if you are unsure***
{.is-danger}

> **Note**
> 
> New fields have been added to the task/operation table for labour rates, task times and task types.
>
>We suggest you reimport the operations from Epicor into field service using the import facility of the GHA Portal
>
>***Please contact GHA support if you are unsure***
{.is-danger}

<br/>

#### Customisations

- **Part Entry Form** Added fields as above
- **Help Desk Topic Entry Form** Added fields as above
- **Field Service Call Code Form** Added fields as above

<br/>

#### Data Directives

- JobHead (**GHA_MFS_JobHead_Service_Link**) - added field for job released, link if call addded in field service
- JobHead (**GHA_MFS_JobHead_Link**) - added field for job released
- JobHead (**GHA_MFS_JobHead_Maintenance_Link**) - added field for job released
- JobOper (**GHA_MFS_JobOper_Service_Link**) - sync tasks for calls created in MFS
- JobMtl (**GHA_MFS_JobMtl_Service_Link**) - sync materials for calls created in MFS
- JobFsTech (**GHA_MFS_FsTech_Link**) - added field for job released, link if call addded in field service
- JobFsCallHd (**GHA_MFS_FsCallHd_Link**) - added field for job released, link if call addded in field service
- JobFsCallDt (**GHA_MFS_FsCallDt_Link**) - added field for job released, link if call addded in field service
- JobOpDtl (**GHA_MFS_JobOpDtl_Service_Link**) - added field for job released, link if call addded in field service
- JobOpDtl (**GHA_MFS_JobOpDtl_Link**) - added field for job released
- HDTopic (**GHA_MFS_HDTopic_Link**) - topics for field service back office Call page
- FSCallType (**GHA_MFS_CallTypes_Link**) - service call types for field service back office Call page
- FSCallHd (**GHA_MFS_FsCallHd_Handshake**) - handshake the call number assigned in Epicor back to MFS
- Part (**GHA_MFS_Part_Link**) - filter by servicable parts
- OpMaster (**GHA_MFS_OpMaster_Link**) - add Labour Rates, Estimated Hours and Operation Type fields
- UDCodes (**GHA_MFS_AppSettings_Link**) - Add parameter for actual costs

#### Method Directives

- ServiceCallCenter.CreateServiceCallJob (**GHA_MFS_Create_Job_From_Template**) - fixed issue where billable flag was not copying for tasks from template jobs

#### BAQs

- **GHA_MFS_Jobs** - added Released flag
- **GHA_MFS_Topics** - topics for field service back office Call page
- **GHA_MFS_CallTypes** - service call types for field service back office Call page
- **GHA_MFS_Parts** - Added fields for Servicable parts to filter when creating a job in MFS
- **GHA_MFS_Operations** - Added fields for Labour Rates, Estimated Hours and Operation Types
- **GHA_MFS_Dashboard** - Fixed format issue for calls
- **GHA_MFS_Contacts** - Added email address and distinguished office and mobile phone numbers
- **GHA_MFS_JobLabor** - Added link to FS Call

<br/>

Patch file can be downloaded from [here](/epicor_cabs/gha_mfs_customer_solution_16.cab)

<br/>

### Version 15.1

> Released 27/02/2024
{.is-success}

#### Data Directives
- JobOpDtl (**GHA_MFS_JobOpDtl_Link**) - fixed OTS not transferring correctly to MFS

<br/>

Patch file can be downloaded from [here](/epicor_cabs/gha_mfs_customer_solution_15.1.cab)

<br/>

### Version 15

> Released 15/11/2023
{.is-success}

#### Data Directives

- JobHead (***GHA_MFS_ScheduleStartDate***) Updates the scheduled date on the service call when the job is scheduled. Neccessary for the scheduling page on the Field Service web app.

Patch file can be downloaded from [here](/epicor_cabs/gha_mfs_customer_solution_15.cab)

**The patch release only includes the fixes pertaining to this version**
<br/>
### Version 14

> Released 26/10/2023
{.is-success}

#### Data Directives

- JobOpDtl (***GHA_MFS_JobOpDtlService_Link***) Service jobs not syncing correctly due to a missing Serial Number field
- JobOpDtl (***GHA_MFS_JobOpDtl_Link***) Installation jobs not syncing correctly due to a missing Serial Number field
<br/>


### Version 13

> Released 13/10/2023
{.is-success}

#### Data Directives

- JobHead (***GHA_MFS_JobHead_Link***) Installation jobs not syncing correctly due to a missing Serial Number field
- FSCallDt (***GHA_MFS_FsCallDt_Link***) Deleting calls was not removing the job on Field Service

### Version 12

> Released 10/8/2023
{.is-success}

#### Data Directives

- JobOpDtl (Operation Scheduled Resources ***GHA_MFS_OpDtlService_Link***, ***GHA_MFS_OpDtl_Link*** Fix for operations being sent multiple time causing occasional sync issues, manifesting in labour records not being added
- PartWhse (***GHA_MFS_PartWhseLink***) caused speed issues - improved

### Version 11

> Released 14/7/2023
{.is-success}

#### Data Directives

- *UDCodes **GHA_MFS_EmployeeFilter_Link*** added for employee filters based on the parameter screen settings
- *Employee **GHA_MFS_EmpBasic_Link*** link amended for employee filters
- *PartBin **GHA_MFS_PartBin_Link*** Fixed issue where both transaction (before and after) were sent, now only the after number is
<br/>

### Version 10

> Released 30/6/2023
{.is-success}

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
{.is-success}

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

