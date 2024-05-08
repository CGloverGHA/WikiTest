---
title: po-approval-technical-documentation-approving-and-rejecting-po
description: 
published: true
date: 2024-01-17T13:28:08.406Z
tags: 
editor: markdown
dateCreated: 2023-12-15T09:36:39.160Z
---

When a PO is approved or reject, a REST call to `Erp.BO.POApvMsgSvc/GetByID` with the following request body:

```json
{
    "poNum": "{PONum}" // {PONum} is the number of the selected PO
}
```

Then the following fields are set based on whether the PO is being approved or rejected:
- `{comments}` refers to the comments set on the PO Details page

| Field Name                  | Approved Value   | Rejected Value   |
| --------------------------- | ---------------- | ---------------- |
| `POApvMsg.ApproverResponse` | APPROVED         | REJECTED         |
| `POApvMsg.ApvAmt`           | `POApvMsg.POAmt` | `POApvMsg.POAmt` |
| `POApvMsg.MsgText`          | `{comments}`     | `{comments}`     |

Then a REST call to `Erp.BO.POApvMsgSvc/Update` is made to commit the changes to Epicor
