---
title: po-approval-technical-documentation-epicor-user-codes-GHA_PO_APP-GHA_PO_APP
description: 
published: true
date: 2024-01-17T13:28:24.320Z
tags: 
editor: markdown
dateCreated: 2023-12-15T09:37:02.434Z
---

## `GHA_PO_APP`
This User Code stores the Customer's license key.

It is stored without `-` delimiters.

The value should be stored in the `CodeDesc` field.

### Obtaining The Customer License Key
It can be done through SQL against the `Customers` table in the license portal

Example:

```sql
use [GHALicensePortal]

select LicenseKey, [Name] from Customers
```

Or it can be obtained by logging into the GHA License Portal as an administrator and navigating to the customer in question.
![Screenshot showing the license key field in the GHA License Portal](assets/Pasted%20image%2020230929161033.png)
