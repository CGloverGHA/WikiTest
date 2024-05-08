---
title: Development Meeting
description: 
published: true
date: 2024-02-26T15:11:53.032Z
tags: 
editor: markdown
dateCreated: 2023-06-30T15:22:09.056Z
---

**26th February 2024**

## Attendees

* Peter Roden
* Josh Sweeney
* Bart Wojda
* Charlie Glover
* Harrison O'Leary
* Ashton Dunderdale

## Agenda

### Wiki

Bart has looked into alternative software and settled on MediaWiki. It does everything we require wiki.js to do, however it does have the following disadvantages:

- Assets can be downloaded from a direct link when not logged in (is this really an issue?)
- It uses either git or a database. 
- Image addition works the same as wiki.js, there is no cut an paste only upload

Git is not working at all anymore. It hasn't synced for a month.

<br/>

### Dev/Requirements pipeline

This is known about in thew wider business. The next time PR goes to Shirebrook it wil be on the Agenda to discuss between PR/AJW/GG

## Mobile Apps

### MFS App
- Offline Sync Deletions?
- Elimate Epicor BAQ Calls
- Copy Live to Test Requirements

### POD
- Technical Reference

### POA
- Staggered Notifications

### MIMS
- Unregister Button & Scan Button Text Overflow
- Center Welcome Text
- Move Stock Not Setting Employee In Epicor
- Move Stock Moving Between Sites
  - Andy suggested displaying a message if there is no `PartWarehouse` record
  - Is not supporting movement between sites sufficient?

## Web Apps

### MFS Web
N/A

### Alberta Quoting System
N/A

### License Portal
N/A

### Language Maintenance
- Password Reset Frontend Changes

### Kanban Project
- Adding Phases

### Support Desk
N/A

### MFS Testing
N/A

## APIs

### Epicor Incoming API
N/A

### License API
- API Call to Request Password Reset
- Concurrent Licensing Controller
- API Call to Reset Password

## Services

### AP Automation
- Import Additional Supplier Information
- Synchronise Suppliers on Different Thread (Daily)
- Live / Test Switch Requirements
- Service Loop Interval Configuration

### Log Trim
N/A

### Field Service Sync
N/A

### Field Service Data Sync
N/A

## Epicor
- Measure Test Cycles
- Hosting MFS + MIMS Dashboards

### Soltech
- Epicor Data Definition
- Report Data Definition
- Quote Line Sub Report
- Link Data to Report Layout

## Miscellaneous.
- Enable encryption on the Dev SQL Server
- Deployment Release Procedures