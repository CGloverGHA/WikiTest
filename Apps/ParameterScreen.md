---
title: Parameter screen
description: 
published: true
date: 2024-02-21T14:58:22.832Z
tags: 
editor: markdown
dateCreated: 2023-09-20T10:51:58.630Z
---

 # Epicor Installation of GHA Parameter Screen

This document outlines how to implement the base extensions and BAQs associated with the GHA Parameter Screen.

## System Requirements
The implementation is available for the following Epicor versions:
-	10.2.600.x
-	10.2.700.x
-	Kinetic 2021.1.x (Classic screens only)
-	Kinetic 2021.2.x (Classic screens only)

## Installation files

The following files are required to perform the installation
-	[GHA Parameters Customer Solution.cab](/epicor_cabs/gha_parameters_customer_solution.cab)

## Installed Components

The following are installed as a result of this implementation:
-	**Base Extension**
	- GHA_Parameters on the UDCodesForm

-	**BAQs**
	- GHAParamProdCal
  
- **Menu Items**
	- GHA Modifications
  		- Simple Stock Take
    		- Setup
      			- GHA Parameters
  		- Auto DMR Creation
    		- Setup
      			- GHA Parameters
		Parameters
    		- Setup
      			- Parameter Maintenance

## Installation of the CAB file

- In Epicor open the ‘Solutions Workbench’
-	Under the ‘Actions’ menu click ’Install Solution’.
-	Click the ‘Solution File’ button and browse to the location of the CAB file 
	GHA Parameters Customer Solution.cab 
-	Check ‘Remove Directives with Matching Name’ and ‘Delete Previous Install’ if upgrading
-	Select “Automatically overwrite duplicate files” and “Automatically overwrite duplicate data”
-	Click Install

## Change Log

<br/>

### Version 1.1.007

> Released 21/02/24
{.is-success}

- Added Actual Costs flag for Mobile Field Service

### Version 1.1.006

> Released 26/09/23
{.is-success}

- Removed refresh button as logic no working correctly

### Version 1.1.005

> Released 06/07/23
{.is-success}

- Fixed issues with missing parameters when first saving
- Fixed issue when some GHA custom fields are missing

### Version 1.1.004

> Last updated 06/04/2023
{.is-success}

#### Integrations\Mobile Field Service

- Maintenance job parameters
  - Default time entry method
  - Default travel time entry
  - Default travel time cap
  - Default mileage cap
  - Default minimum travel time
  - Default labour increment
  - Default min travel time
  - Default travel time increment
  
- Job display settings
  - Group jobs by...
  - Start of week

#### Integrations\MFS Back Office

New tab/sheet

- Moved 'Employee Filter By' from Mobile Field Service

#### MIMS

- Order Picking
	- Display orders to pick by

#### Misc

- Database rebuild
  - Rebuild database from time
  - Rebuild database to time
  - Rebuild database any time

<br/>

### Version 1.1.003

> Released 27/02/2023
{.is-success}


- Added OTIF report parameters to Reports tab

### Version 1.1.002

#### Business Activity Queries

GHA_MIMS_Parameters - amended to read user codes for Data Wedge readers
GHA_MIMS_JobsMaterial - Added Company parameter to use as a filter for sub query 
<br/>