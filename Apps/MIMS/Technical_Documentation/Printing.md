---
title: Printing
description: 
published: true
date: 2024-01-17T13:27:01.753Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:14:17.972Z
---

MIMS supports two methods of printing, as described below

# Standard Epicor Printing
MIMS can create reports within Epicor, that can then be handled by the Task Agent as setup within Epicor

# Cloud-Hosted Printing
This method is for Customers that use a hosted Epicor solution, where the Epicor instance is in the cloud on **not** on-premise

MIMS can create reports within Epicor, that can then be handled by the GHA Epicor Printing Service so that the report can be printed from printers that aren't defined within Epicor

The reports that MIMS creates are intentionally erroneous so that it can be handled by the GHA Epicor Printing Service instead of the Epicor Task Agent

Refer to the documentation for the GHA Epicor Printing Service for further information


# How MIMS Retrieves The Available Printers
## Epicor Printers
Printers that are defined within Epicor are retrieved via a REST call to `~/Ice.BO.SysPrinterSvc/SysPrinters`

## Non-Epicor Printers (GHA Epicor Printing Service)
Printers that aren't defined within Epicor are retrieved via a REST call to `~/Ice.BO.UserCodeSvc/UDCodes`
- Where `CodeTypeID = 'GHAPrint'`

Each User Code represents a Printer where
- The `CodeID` is the ID of the Printer
- The `CodeDesc` is the name of the Printer
- The `LongDesc` marks the printer as the default Printer
	- `LongDesc == "DEFAULT"`


# How MIMS Creates Reports In Epicor
The default Task Agent is retrieved
- This is done via a REST call to `~/Ice.BO.SysAgentSvc/GetDefaultTaskAgent`

This Task Agent is used for any reports created via MIMS

The `WorkstationID` is set to the `DeviceID`

If the Printer is defined inside Epicor
- `AutoAction` is set to `SSRSPrint`
- `PrinterName` is set to the `NetworkPath`

If the Printer is not defined inside Epicor
- `AutoAction` is set to `SSRSClientPrint`
- `PrinterName` is set to the name of the Printer
- `TaskNote` is set to `GHAPrintService`