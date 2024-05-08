---
title: po-approval-technical-documentation-po-details
description: 
published: true
date: 2024-01-17T13:28:38.994Z
tags: 
editor: markdown
dateCreated: 2023-12-15T09:37:22.233Z
---

When a the PO Details page is loaded, a REST call is made to `Erp.BO.POSvc/GetByID` with the following body

```json
{
    "poNum": "{PONum}" // {PONum} is the number of the selected PO
}
```

This is done to get the header charges, lines and line charges

The following table dictates the notable fields are retrieved from this call:

| Description      | `POHeadMisc` Field       | `PODetail` Field        | `POMisc` Field       |
| ---------------- | ------------------------ | ----------------------- | -------------------- |
| PO Number        | `POHeadMisc.PONum`       | `PODetail.PONum`        | `POMisc.PONum`       |
| Line Number      | `POHeadMisc.POLine`      | `PODetail.POLine`       | `POMisc.POLine`      |
| Part Number      | `POHeadMisc.MiscCode`    | `PODetail.PartNum`      | `POMisc.MiscCode`    |
| Part Description | `POHeadMisc.Description` | `PODetail.LineDesc`     | `POMisc.Description` |
| Quantity         | 1                        | `PODetail.OrderQty`     | 1                    |
| Cost             | `POHeadMisc.MiscAmt`     | `PODetail.ExtCost`      | `POMisc.MiscAmt`     |
| UOM              | *nothing*                | `PODetail.PUM`          | *nothing*            |
| Buy For Type     | none                     | `PODetail.CalcTranType` | none                 |
