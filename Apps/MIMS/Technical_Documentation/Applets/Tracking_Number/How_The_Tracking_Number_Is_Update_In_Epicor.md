---
title: How_The_Tracking_Number_Is_Update_In_Epicor
description: 
published: true
date: 2024-01-17T13:34:43.962Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:18:46.360Z
---

The Tracking Number is updated in Epicor using the following REST calls
- `~/Erp.BO.CustShipSvc/CustShips`

# `Erp.BO.CustShipsSvc/CustShips`
This method is called to update the Customer Shipment entry in Epicor

## Parameters
- `Company = Current Company`
- `PackNum = Selected Pack Number`
- `TrackingNumber = Entered Tracking Number`
- `RowMod = "U"`
