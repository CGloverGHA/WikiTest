---
title: MIMS Epicor Installation Guide
description: 
published: true
date: 2024-02-26T11:48:36.603Z
tags: 
editor: markdown
dateCreated: 2023-02-28T10:14:11.957Z
---

# Epicor Installation of Mobile Inventory Management System

This document outlines how to implement the additional fields, BAQs and data directives associated with the GHA Mobile Inventory Management Service application.

## System Requirements

The implementation is available for the following Epicor versions:

- 10.2.600.x
- 10.2.700.x
- Kinetic 2021.1.x (Classic screens only)
- Kinetic 2021.2.x (Classic screens only)

## Pre requisites

[GHA Mobile Fields for Epicor](/Apps/Epicor/Installation_Guides/FieldsEpicorInstallationGuide.md)

[GHA Parameter Screen for Epicor](/Apps/ParameterScreen)

## Installation files

The following files are required to perform the installation
[GHA MIMS Customer Solution](/epicor_cabs/gha_mims_customer_solution.cab)

## Installed Components

For a list of installed components please refer to the [Technical Documentation](Technical_Documentation.md)

## Installation of the CAB file

In Epicor open the ‘Solutions Workbench’

- Under the ‘Actions’ menu click ’Install Solution’.
- Click the ‘Solution File’ button and browse to the location of the CAB file `gha_mims_customer_solution.cab`
- Check ‘Only Target Current Company’
- Check ‘Remove Directives with Matching Name’ and ‘Delete Previous Install’ if upgrading
- Select “Automatically overwrite duplicate files” and “Automatically overwrite duplicate data”
- Click Install

## Change Log

### Version 7

> Released 26/02/2024
{.is-success}

[Changes](/AppsDrafts/MobileInventoryManagementSolution/change-log/1-3-001-203)

### Version 6

> Released 20/02/2024
{.is-success}

[Changes](/AppsDrafts/MobileInventoryManagementSolution/change-log/1-3-001-200)

### Version 4

> Released 13/12/2023
{.is-success}

#### Business Activity Queries

- Added `GHA_MIMS_PartEnquiry` to improve performance, in Part Enquiry, and to support lot filtering
- Added `GHA_MIMS_PartEnquirySerial` to retrieve the Part Bin for a selected serial, in Part Enquiry
- Added `GHA_MIMS_PurchaseOrder` to improve performance, in Goods In
- Added `GHA_MIMS_PurchaseOrderLines` to improve performance, in Goods In
- Added `GHA_MIMS_PurchaseOrderReleases` to improve performance, in Goods In

### Version 3

> Released 19/09/2023
{.is-success}

#### Business Activity Queries

- Fixed updateable BAQ BPMs for Material Queue Dashboard in Epicor version 2023.1 (dotnet change in Epicor)


### Version 2

> Released 12/07/2023
{.is-success}

#### Business Activity Queries

- Set 'All Companies' field to 'true' for all BAQs

- Added BAQs for Material Queue dashboard
	- GHA_MIMS_MqEmpBasic
	- GHA_MIMS_MqEmpBasicAndTeam
	- GHA_MIMS_MqMoveRequest
	- GHA_MIMS_MqOpenSOrders
	- GHA_MIMS_MqOpenSORels
	- GHA_MIMS_MqPickedOrders
	- GHA_MIMS_MqPIP
	- GHA_MIMS_MqProcessedMoves
	- GHA_MIMS_MqQueuedMoves

#### Custom Forms

- Material Queue Dashboard
- Employee form 
	- Added MIMS User

---

### Version 1.2.016

> Released 12/1/2022
{.is-success}

#### Business Activity Queries

##### GHA_MIMS_Parameters

- Amended to read user codes for Data Wedge readers

##### GHA_MIMS_JobsMaterial 

- Added Company parameter to use as a filter for sub query

---

### Version 1.2.012

> Released 16/11/2022
{.is-success}

#### Business Activity Queries

GHA_MIMS_Employees – added BAQ to provide data for employee login drop down
