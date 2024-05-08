---
title: po-approval-technical-documentation-po-list
description: 
published: true
date: 2024-01-17T13:28:41.558Z
tags: 
editor: markdown
dateCreated: 2023-12-15T09:37:25.522Z
---

The PO list, as seen in the app, is retrieved via a REST call to `/ERP.BO.POApvMsgSvc/GetRows` with the following request body:

```json
{
    // MsgType = 1 means 'Request for approval'
    // It is ordered by MsgDate then MsgTime, both in descending order
    // to show the most recently sent PO's first
    "whereClausePOApvMsg": "MsgType = '1' BY MsgDate, MsgTime",
    "pageSize": 0,
    "absolutePage": 0,
}
```

Then for each PO in the response, a REST call is made to `/ERP.BO.POSvc/POes` with the following  parameters:

```json
{
    // {PONum} is the current PO Number in the loop
    "$filter": "PONum eq {PONum}",
    "$select": "..." // hidden due to size
}
```

This process retrieves the following fields from Epicor for each PO

| Epicor Field Name                 | Description          |
| --------------------------------- | -------------------- |
| `POHeader.PONum`                  | PO Num               |
| `Vendor.Name`                     | Supplier Name        |
| `PurAgent.BuyerID`                | Buyer Id             |
| `PurAgent.Name`                   | Buyer Name           |
| `POHeader.DocTotalOrder`          | PO Value             |
| `POHeader.CommentText`            | PO Approval Comments |
| `POHeader.CurrencyCodeCurrSymbol` | e.g. $, £, €         |
| `POHeader.POType`                 | PO Type              |
