---
title: PO Approval Epicor Installation
description: 
published: true
date: 2024-01-30T09:47:25.522Z
tags: 
editor: markdown
dateCreated: 2024-01-30T09:47:22.910Z
---

# Epicor Installation of PO Approval

This document outlines how to implement the data directives and functions associated with the PO Approval application.

## System Requirements

The implementation is available for the following Epicor versions:

- 10.2.600.x
- 10.2.700.x
- Kinetic 2021.x
- Kinetic 2022.x
- Kinetic 2023.x

## Installation files

The following files are required to perform the installation
[GHA POA Customer Solution](/epicor_cabs/gha_poa_customer_solution.cab)

## Installation of the CAB file

In Epicor open the ‘Solutions Workbench’

- Under the ‘Actions’ menu click ’Install Solution’.
- Click the ‘Solution File’ button and browse to the location of the CAB file `gha_mims_customer_solution.cab`
- Check ‘Only Target Current Company’
- Check ‘Remove Directives with Matching Name’ and ‘Delete Previous Install’ if upgrading
- Select “Automatically overwrite duplicate files” and “Automatically overwrite duplicate data”
- Click Install

## Change Log

### Version 3

> Not yet released
{.is-warning}

Fixed notifications

