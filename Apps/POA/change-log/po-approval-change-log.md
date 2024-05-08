---
title: po-approval-change-log
description: 
published: true
date: 2024-01-17T13:28:05.965Z
tags: 
editor: markdown
dateCreated: 2023-12-15T09:36:35.683Z
---

## PO Approval App Change Log

---
## 1.2.004+74
### 1. Use User Login For REST (POA000046)
Previously, the app was only using the Epicor user defined in the License Portal for REST Calls. This meant that:
- Either the same or no PO's would be shown for all users
- Approved or Rejected PO's would be against the connection user, not the logged-in user

It will now override the default connection when the user logs in

---
## 1.2.004+73
### 1. Lock To Portrait (POA000045)
App is now locked as portrait, single-top, only

---
## 1.2.004+72
### 1. Closed App Notifications (POA000038)
- Changed notification icon to GHA Solutions logo
![Screenshot showing that the notification icon has been changed to the GHA logo](assets/Pasted%20image%2020231016111357.png)
