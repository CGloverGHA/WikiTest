---
title: Scanning
description: 
published: true
date: 2024-01-17T13:27:04.519Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:14:21.481Z
---

# Camera Scanning
This method of scanning uses the device's camera to scan a barcode

This method is usually triggered via a "Scan" button through the app

# Data Wedge Scanning
When the app starts up, a `MIMS` Data Wedge Profile is created
 - Keyboard input is disabled
  
Two Broadcast Receivers are registered
 - An `ActiveProfileReceiver`
 - A `ScannerReceiver`

When the app starts, a `GET_ACTIVE_PROFILE` intent is sent via the Data Wedge API
 - If the `ActiveProfileReceiver` successfully retrieves this and the active profile is MIMS, [Data Wedge Functionality](#data-wedge-functionality) will be enabled

When a barcode is scanned with the Data Wedge, the `ScannerReceiver` will pick up the result
 - The barcode will be sent to MIMS using the `MessagingCenter` and custom scanning logic will be executed depending on the current page

## Data Wedge Functionality
If a Data Wedge is detected, the following changes will be visible within the app
 
1. All scannable inputs will have the keyboard disabled
	1.1. If the [No Keyboard Parameter](./MIMS_Parameters#no-keyboard) is disabled, a button will appear in the control to allow keyboard input

# Barcode Delimiter
The barcode delimiter is stored in the [Local Database](./Local_Database.md)

The default delimiter it `~`

# Barcode Formats
Barcode formats are stored in the [Local Database](./Local_Database.md)

## Barcode Variables

| Variable              | String Format          |
| --------------------- | ---------------------- |
| Part Number           | `PARTNUM`              |
| Warehouse Code        | `WAREHOUSECODE`        |
| Bin Number            | `BINNUM`               |
| Job Number            | `JOBNUM`               |
| Assembly Part Number  | `ASSEMBLYPARTNUMBER`   |
| Operation Description | `OPERATIONDESCRIPTION` |
| Lot Number            | `LOTNUMBER`            |
| Serial Number         | `SERIALNUMBER`         |
| Pack Number           | `PACKNUMBER`           |
| Tracking Number       | `TRACKINGNUMBER`       |
| Package Code          | `PACKAGECODE`          |
| Part Revision Number  | `PARTREVISIONNUMBER`   |
| PO / RMA Number       | `PORMANUM`             |


## Available Formats
### Part Format
This format is used for scanning Parts

The default format is:
- `PARTNUM`

### Part Revision Format
This format is used for scanning Part Revisions

The default format is:
- `PARTREVISIONNUMBER`

### Part Lot Format
This format is used for scanning Part Lots

The default format is:
- `PARTNUM~LOTNUMBER`
	- *Note that the delimiter can be changed. See [Barcode Delimiter](#barcode-delimiter)*
  
### Job Number
This format is used for scanning Jobs

The default format is:
- `JOBNUMBER`

### Assembly Format
This format is used for scanning assemblies from Jobs

The default format is:
- `ASSEMBLYPARTNUMBER`

### Operation Format
This format is used for scanning operations from an Assembly from a Job

The default format is:
- `OPERATIONDESCRIPTION`

### Lot Format
This format is used for scanning lots

The default format is:
- `LOTNUMBER`

### Serial Format
This format is used for scanning Serials

The default format is:
- `SERIALNUMBER`

### Warehouse Bin Format
This format is used for scanning a Warehouse and Bin

The default format is:
- `WAREHOUSECODE~BINNUMBER`
	- *Note that the delimiter can be changed. See [Barcode Delimiter](#barcode-delimiter)*

### PO RMA Format
This format is used for scanning a Purchase Order or a RMA Order

The default format is
- `PORMANUM`

### Bin Format
This format is used for scanning a Bin

The default format is
- `BINNUM`

### Pack Format
This format is used for scanning Customer Shipments

The default format is
- `PACKNUMBER`

### Tracking Number Format
This format is used for scanning Tracking Numbers

The default format is
- `TRACKINGNUMBER`

### Package Format
This format is used for scanning Packages

The default format is
- `PACKAGECODE`

# Barcode Validation Errors
## Invalid Barcode Format
This error will be displayed if the barcode does not match the expected format

This is determined by the number of values that are returned when the barcode and format is split by the defined delimiter

If these numbers do not match, this error is shown