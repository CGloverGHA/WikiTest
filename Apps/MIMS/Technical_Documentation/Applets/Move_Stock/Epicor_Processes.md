---
title: Epicor_Processes
description: 
published: true
date: 2024-01-17T13:34:17.473Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:17:53.806Z
---

# Stock Movement
First of all, the app will set the employee of the current Epicor session to the current employee
- This is done via a REST call to `Ice.LIB.SessionModSvc/SetEmployee`

The app will then set up the parameters for the stock movement in Epicor

The `TranReference` will be set to `MIMS - {EmployeeID}`
- Where `{EmployeeID}` is the ID of the current employee using MIMS

Finally, the app will perform the stock movement in Epicor
- This is done via a REST call to `~/Erp.BO.InvTransferSvc/CommitTransfer`
