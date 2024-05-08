---
title: MIMS Epicor Installation Guide
description: 
published: true
date: 2024-01-19T15:07:53.731Z
tags: 
editor: markdown
dateCreated: 2023-09-08T14:40:10.948Z
---

# <div style= "color:red"> Epicor Installation of Mobile Inventory Management System - Draft</div>

This document outlines how to implement the additional fields, BAQs and data directives associated with the GHA Mobile Inventory Management Service application.

## System Requirements

The implementation is available for the following Epicor versions:

- 10.2.600.x
- 10.2.700.x
- Kinetic 2021.1.x (Classic screens only)
- Kinetic 2021.2.x (Classic screens only)

## Pre requisites

[GHA Mobile Fields for Epicor](./FieldsEpicorInstallationGuide.md)

[GHA Parameter Screen for Epicor](./ParametersEpicorInstallationGuide.md)

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
