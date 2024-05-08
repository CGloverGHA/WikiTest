---
title: Parameters Epicor Installation Guide
description: 
published: true
date: 2024-01-17T13:26:32.472Z
tags: 
editor: markdown
dateCreated: 2023-03-01T16:19:52.250Z
---

[Home](/Apps.md)
 
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

### Version 1.1.005

> Released 12/07/2023
{.is-info}

#### MIMS

- UD Table for material queue fix

<br/>

### Version 1.1.004

> Released 20/06/2023
{.is-info}

#### MIMS

- Default Report Style for Transfer Orders added
- UD Table for material queue added

<br/>

### Version 1.1.003

> Released 08/06/2023
{.is-info}

#### Integrations\Mobile Field Service

- Maintenance job parameters
  - Default time entry method
  - Default labour increment
  - Default min job time
  
- Job display settings
  - Group jobs by...
  - Start of week

#### Integrations\MFS Back Office

New tab/sheet

- Moved 'Employee Filter By' from Mobile Field Service

#### MIMS

- Order Picking
	- Display orders to pick by
- Default Report Style (PO)
	- Changed to Print tags report (from print labels)
- Default Repost Style for Transfer Orders added

#### Misc

- Database rebuild
  - Rebuild database from time
  - Rebuild database to time
  - Rebuild database any time
  
<br/>

### Version 1.1.002

> Released 27/02/2023
{.is-success}


- Added OTIF report parameters to Reports tab

### Version 1.1.001

#### Business Activity Queries

GHA_MIMS_Parameters - amended to read user codes for Data Wedge readers
GHA_MIMS_JobsMaterial - Added Company parameter to use as a filter for sub query 
<br/>