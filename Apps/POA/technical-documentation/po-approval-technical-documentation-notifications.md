---
title: po-approval-technical-documentation-notifications
description: 
published: true
date: 2024-01-17T13:28:36.346Z
tags: 
editor: markdown
dateCreated: 2023-12-15T09:37:18.941Z
---

Whenever a PO is sent for approval in Epicor, any relevant logged-in User should receive a notification to review the PO. See [PO Approval - Epicor](po-approval-technical-documentation-epicor.md) for more information about the notification process in Epicor.

Notifications are sent through the `GHA PO Approval API`. The `SendMessage` endpoint is called by the Epicor Data Directive. This sends a request to Firebase to send the Push Notification.

Do note that the [`Environmen` User Code](po-approval-technical-documentation-epicor-user-codes-GHA_PO_APP-Environmen.md) can override which API is used for sending notifications.
- If `Environmen` is not defined, it will use `api.ghahosted.com`
- If `Environmen` is `dev02`, it will use `dev02api.ghahosted.com`

[Firebase](https://firebase.google.com/) is an app development platform that provides tools and services for parts of app development.

PO Approval makes use of the [Firebase Cloud Messaging Solution](https://firebase.google.com/docs/cloud-messaging) to send notifications.

Once the PO Approval API has sent the message to Firebase, it should appear on the User's device.
- Note that currently notifications only appear when the app is **open** but in the **background**
