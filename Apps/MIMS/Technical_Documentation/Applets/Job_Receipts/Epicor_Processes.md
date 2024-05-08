---
title: Epicor_Processes
description: 
published: true
date: 2024-01-17T13:34:03.105Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:17:34.166Z
---

# Serial Matching
In order for serials to be selected on the [Select Serials Screen](./Screens/Select_Serials_Screen.md), the serial numbers must be matched on the selected Job

Serials can be assigned to a Job using the "Serial Number Assignment" screen in Epicor

Serials can be matched to Job Materials using the "Serial Matching" screen in Epicor

Refer to the Epicor documentation for further information on Serial Assignment and Matching

## How MIMS Checks For Matched Serials
When a Job Demand with a serial tracked Part is selected, MIMS calls the `GHA_MIMS_JobSerialsMatched` BAQ.

See [GHA_MIMS_JobSerialsMatched](../../Epicor//BAQs/GHA_MIMS_JobSerialsMatched.md) for further information

This BAQ will return a `Matched` column for the selected Job

If the `Matched` column is `False`
- An error with the message, "Serials do not match. ", will be shown to the user

Otherwise, MIMS will then compare the count of the serials
- See [How MIMS Compares The Serial Number Count](#how-mims-compares-the-serial-number-count)

## How MIMS Compares The Serial Number Count
A list of WIP serials are retrieved for the selected Job Demand's Part
- This is done via a REST call to `~/Erp.BO.SerialNoSvc/List`
- Where `SNStatus = 'WIP'`
- Where `JobNum = '{SelectedJobNumber}'`

If this returns zero results
- An error with the message, "There are no serial numbers assigned to this job", will be shown

Otherwise, these results are saved in [Application Storage](../../Application_Storage.md), for use on the [Select Serials Screen](./Screens/Select_Serials_Screen.md)

# Perform Receipts
## Perform Receipt For Make To Stock Demands
A REST call is made to `~/Erp.BO.ReceiptsFromMfgSvc/ReceiveMfgPartToInventory`

## Perform Receipt For Make To Job Demands
A REST call is made to `~/Erp.BO.ReceiptsFromMfgSvc/ReceiveMfgPartToJob`
# Printing
## Make To Stock Receipts
A REST call is made to `~/Erp.Rpt.InventoryMovementSvc/SubmitToAgent`
- Refer to [How MIMS Creates Reports In Epicor](../../Printing.md#how-mims-creates-reports-in-epicor) for additional information about this REST call

## Make To Job Receipts
A REST call is made to `~/Erp.Rpt.InventoryMovementSvc/SubmitToAgent`
- Refer to [How MIMS Creates Reports In Epicor](../../Printing.md#how-mims-creates-reports-in-epicor) for additional information about this REST call