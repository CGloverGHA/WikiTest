---
title: Add_&_Issue_Material_Epicor_Flow
description: 
published: true
date: 2024-01-17T13:33:46.186Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:17:11.588Z
---

The following page describes the process of both adding and issuing the Parts in Epicor

# Adding the material
The following REST calls are made, to the `~/Erp.BO.JobEntrySvc`, to add a new material to the selected Job
```mermaid
flowchart LR

A[[ChangeJobMtlPartNum]]
B[[JobMtls]]

A --> B
```

## `ChangeJobMtlPartNum`
A call to this REST method is made to generate a new `JobEntry` dataset with a `JobMtl` entry for the selected Part

This call will also bring over default information about the Part, such as
- Revision Number
- Unit Cost
- Purchase Direct

## `JobMtls`
A call to this REST method is made to create the `JobMtl` entry in Epicor

The request object is a modified version of the resulting `JobMtl` from the call to `ChangeJobMtlPartNum`

# Issuing The Material
The following REST calls are made to issue the selected Part to the selected Job's material
```mermaid
flowchart LR

A[["Ice.LIB.SessionModSvc/SetEmployee"]]
B[["Erp.BO.IssueReturnSvc/PerformMaterialMovement"]]

A --> B
B --> B
```

## `Ice.LIB.SessionModSvc/SetEmployee`
A call to this REST method is made to set the associate the current session with the current Employee

This is done so that the subsequent call to `Erp.BO.IssueReturnSvc/PerformMaterialMovement` is tracked / logged against the current Employee using the app

## `Erp.BO.IssueReturnSvc/PerformMaterialMovement`
*NOTE: This REST call is called each time for the selected Part Bins*

A call to this REST method is made to issue the material from the current Part Bin to the selected Job's material

### Advanced Material Management
If [Advanced Material Management](../../AMM_Handling.md) is **not licensed**
- The `ToWarehouseCode` and `ToBinNum` parameters will not be set

