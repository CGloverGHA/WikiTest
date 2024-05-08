---
title: POD Installation Guide
description: 
published: true
date: 2024-01-19T15:02:25.869Z
tags: 
editor: markdown
dateCreated: 2023-09-04T08:34:48.910Z
---

# Epicor Installation of Proof of Delivery Solution

This document outlines how to implement the additional fields, BAQs and dashboards associated with the GHA Prrod of Delivery application.

## System Requirements

The implementation is available for the following Epicor versions:

- 10.2.600.x
- 10.2.700.x
- Kinetic 2021.1.x (Classic screens only)
- Kinetic 2021.2.x (Classic screens only)

## Pre requisites

[GHA Mobile Fields for Epicor](/Apps/Epicor/Installation_Guides/FieldsEpicorInstallationGuide.md)

[GHA Parameter Screen for Epicor](/Apps/Epicor/Installation_Guides/ParametersEpicorInstallationGuide.md)

## Installation files

The following files are required to perform the installation
[GHA POD Customer Solution](/epicor_cabs/gha_pod_customer_solution.cab)

## Installed Components

For a list of installed components please refer to the [Technical Documentation](Technical_Documentation.md)

## Installation of the CAB file

In Epicor open the ‘Solutions Workbench’

- Under the ‘Actions’ menu click ’Install Solution’.
- Click the ‘Solution File’ button and browse to the location of the CAB file `gha_pod_customer_solution.cab`
- Check ‘Only Target Current Company’
- Check ‘Remove Directives with Matching Name’ and ‘Delete Previous Install’ if upgrading
- Select “Automatically overwrite duplicate files” and “Automatically overwrite duplicate data”
- Click Install