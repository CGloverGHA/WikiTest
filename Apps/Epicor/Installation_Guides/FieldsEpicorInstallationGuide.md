---
title: GHA Custom Mobile Fields Epicor Installation Guide
description: 
published: true
date: 2024-01-17T13:26:29.705Z
tags: 
editor: markdown
dateCreated: 2023-03-01T16:19:48.829Z
---

[Home](/Apps.md)

# Epicor Installation of GHA Customer Mobile Fields

This document outlines how to implement the additional fields associated with the GHA Mobile applications.

## System Requirements

The implementation is available for the following Epicor versions:
-	10.2.600.x
-	10.2.700.x
-	Kinetic 2021.1.x (Classic screens only)
-	Kinetic 2021.2.x (Classic screens only)

## Installation files

The following files are required to perform the installation

- [GHA Mobile Fields Customer Solution](/epicor_cabs/gha_mobile_fields_customer_solution.cab)

## Installed Components

The following are installed as a result of this implementation:
-	UD Fields:
	Fields are added with the prefix GHA_MIMS_ and GHA_MFS_

## Installation of the additional UD fields from the CAB file

-	In Epicor open the ‘Solutions Workbench’
-	Under the ‘Actions’ menu click ’Install Solution’.
-	Click the ‘Solution File’ button and browse to the location of the CAB file 
	**GHA Mobile Fields Customer Solution.cab**
-	Check the ‘Delete Previous Install’ check box
-	Check the ‘Automatically override duplicate data’ check box
-	Click Install

## Database regeneration

- On the server which houses your Epicor installation
-	Open the Epicor Administration Console
-	Browse to your database under ‘Database Server Manager’
-	Right click and select ‘Regenerate Data Model’
-	On the next screen click ‘Generate’
-	Browse to your application server under ‘Server Management’
-	Right click and select ‘Recycle Application Pool’

## Change Log

<br/>

### Version 2

> Released 12/07/2023
{.is-info}

#### MIMS

For the MIMS Material Queue dashboard:

- Added field EmpBasic.GHA_MIMS_MIMSUser_c
- Added field Warehse.GHA_MIMS_SequenceNo_c
<br/>
