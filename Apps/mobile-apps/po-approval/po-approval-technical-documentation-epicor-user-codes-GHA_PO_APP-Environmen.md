---
title: po-approval-technical-documentation-epicor-user-codes-GHA_PO_APP-Environmen
description: 
published: true
date: 2024-01-17T13:31:25.660Z
tags: 
editor: markdown
dateCreated: 2023-10-06T13:32:00.622Z
---

## `Environmen`
This value will control which server to call when attempting to call `SendMessage` of the PO Approval API.

This value is for internal use.

The value should be stored in the `CodeDesc` field.

This means the Epicor functionality can work without this value existing.

By default it will always point to `api.ghahosted.com`

But if a value is provided, it will be added as a prefix to the URL

For example:
- If `Environmen` is `dev02`, then the URL will be `dev02api.ghahosted.com`
