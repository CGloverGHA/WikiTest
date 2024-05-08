---
title: po-approval-technical-documentation-logging-in
description: 
published: true
date: 2024-01-17T13:28:33.762Z
tags: 
editor: markdown
dateCreated: 2023-12-15T09:37:15.684Z
---

When the login screen is loaded, the app will try to retrieve an existing login from secure storage. If one is found, the following process will be automatically triggered. Otherwise the user will need to enter a `username` and `password` and tap the login button to trigger this process.

A REST call to `Ice.BO.UserFileSvc/ValidatePassword` is made with the entered `username` and `password`.

If this is successful, a firebase token is generated. See [Notifications](po-approval-technical-documentation-notifications.md) for more information about firebase.

The firebase token is used to make an API call to `POApprovalSvc/Login` on the GHA PO Approval API. This will register the User with GHA PO Approval so that they may receive notifications when a PO is sent for approval.

If this is successful, the `username`, `password` and `firebaseToken` are saved to secure storage and the user will be logged in.
