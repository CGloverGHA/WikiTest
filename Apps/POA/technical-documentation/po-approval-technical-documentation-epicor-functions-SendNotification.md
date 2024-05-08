---
title: po-approval-technical-documentation-epicor-functions-SendNotification
description: 
published: true
date: 2024-01-17T13:28:17.501Z
tags: 
editor: markdown
dateCreated: 2023-12-15T09:36:52.311Z
---

This function is a part of the [`GHA-POA`](po-approval-technical-documentation-epicor-function-library-GHA_POA.md) Function Library

The purpose of this function is to call the `SendMessage` endpoint on the PO Approval API.

It first retrieves the license key by getting it from the `UDCodes` table where
- `Company` is the current session Company
- `CodeTypeID` is the [`GHA_PO_APP`](po-approval-technical-documentation-epicor-user-codes.md) User Codes Code Type ID

It then removes any `-` characters from the license key.

It will then retrieve the environment by reading the [`Environmen`](po-approval-technical-documentation-epicor-user-codes-GHA_PO_APP-Environmen.md) from the `UDCodes` table.

If a value has been provided, it's value will be appended to the URL. This is used to send a notification using a different server hosting the PO Approval API than the live server.

If no value has been provided, it will be sent to the live server hosting the PO Approval API.

It will then send a request to the `SendMessage` endpoint on the PO Approval API.

The license key is added as a header, named `token`, to the request.

If any exception occurs or the API call fails, this function will return a detailed error message containing:
- The API used to make the call
- The response from the API
- All the parameters used in the request

This error will also be logged to the server logs.
