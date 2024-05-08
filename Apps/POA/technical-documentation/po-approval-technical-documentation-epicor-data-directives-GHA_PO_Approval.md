---
title: po-approval-technical-documentation-epicor-data-directives-GHA_PO_Approval
description: 
published: true
date: 2024-01-17T13:28:10.719Z
tags: 
editor: markdown
dateCreated: 2023-12-15T09:36:42.587Z
---

## `GHA_PO_Approval`
This standard data directive is triggered when a row is added to the `POApvMsg` table

It loops over the `POApvMsg` table where
- `RowMod = U`
- `MsgType = 1` (Request For Approval)

Then it loops over the `PurAuth` table where
- `Company` is the current Company
- `BuyerID` is `MsgTo` from the current row in the `POApvMsg` table

It then gets the PO from the `POHeader` table using the current Company and the current `POApvMsg.BuyerID` value

It then gets the PO vendor from the `Vendor` table using the current Company and the PO's `VendorNum`

It then gets the buyer from the `PurAgent` table using the current Company and the current `POApvMsg.MsgFrom` value

It then invokes the [`SendNotification`](po-approval-technical-documentation-epicor-functions-SendNotification.md) Epicor Function

If this function returns an error message, it will be displayed to the user.

If it is successful, the notification should be sent to the device of each authorised user of the Buyer defined on the Purchase Order.
