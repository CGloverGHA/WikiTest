---
title: Development Meeting 2023-08-24
description: 
published: true
date: 2024-01-19T15:05:55.346Z
tags: 
editor: markdown
dateCreated: 2023-08-29T07:18:59.535Z
---

**24th August 2023**

## Attendees

* Peter Roden
* Josh Sweeney
* Bart Wojda

# Mobile Apps

## Mobile Field Service
<!--
#### Pipeline
<br/>
-->
#### In Development
- Offline functionality **Torchbearer**
	- Currently with Torchbearer to fix sync issues
- Epicor sync error handling **PR**
	- Added Http status codes
  - Resend failures to Epicor
  - Logging errors to Epicor
 <br/>
 
#### In Test
- Concurrent licensing
- Upgrade to DotNet 6
- Epicor API v2
<br/>


## MIMS
<span style="color:grey">
No action needed
</span>

<!--
#### Pipeline
<br/>

#### In Development
<br/>

#### In Test
-->
<br/>

## Proof of Delivery
#### Pipeline
- Technical Reference Guide
- Epicor v2 API (service rewrite)
#### In Development
- Upgrade to Android 13 **JS**
<!--
#### In Test
<br/>
-->
## PO Approval
<!--
#### Pipeline
<br/>
-->
#### In Development
- Deployment scripts **JS**
- Epicor v2 API **JS**
- REST logging **JS**
- Health Checker **JS**
- Technicial Reference Guide **JS**
- Apple/Google Store approvals **JS**
<br/>

#### In Test
Imminent
<br/>

## Installers App
<span style="color:grey">
No action needed
</span>

<!--
#### Pipeline
<br/>

#### In Development
<br/>

#### In Test
-->
<br/>

# Web Apps

## Mobile Field Service
#### Pipeline
- Technicial Reference Guide
<br/>
<!--
#### In Development
<br/>
-->
#### In Test
(these may be live)
- Two factor authentication
- Concurrent licensing
- Upgrade to DotNet 6
<br/>

## Alberta Quoting System
#### Pipeline
- Front end changes 
	- Pending API changes in development
<br/>

#### In Development
- API Changes **JS**
- Epicor CABs **PR**
<br/>
<!--
#### In Test
<br/>
-->
## Licence Portal
<!--
#### Pipeline
<br/>

#### In Development
<br/>
-->
#### In Test
- Wiki notifications **Done**
- Epicor v2 API
	- Cannot put live until other API work done
- Epicor user field creation **GG** see below
<br/>


# Epicor

## Printing Service
<span style="color:grey">
No action needed
</span>

<!--
#### Pipeline
<br/>

#### In Development
<br/>

#### In Test
-->
<br/>

## Parameters Screen
#### Pipeline
- Kinetic form
<br/>

#### In Development
- Refresh button **PR**
<br/>
<!--
#### In Test
<br/>
-->
## Customer work
#### Pipeline
CBT-069 SSRS Report **PR**
POTL-024 Ship Via **On hold**
POTL-038 PO Form **On hold**
POTL-039 AR Invoice errors **On hold**
<br/>
<!--
#### In Development
<br/>
-->
#### In Test
<br/>

## AP Automation
<span style="color:grey">
No action needed
</span>

<!--
#### Pipeline
<br/>

#### In Development
<br/>

#### In Test
-->
<br/>


## Test app (populate Epicor)
<!--
#### Pipeline
<br/>
-->
#### In Development
- New flutter app **BW**
<br/>
<!--
#### In Test
<br/>
-->
## User Field Creation
<!--
#### Pipeline
<br/>
-->

#### In Development
- Deployment to live - two app servers **BW**
<br/>

#### In Test
- Whole process (license portal and rebuild service) **GG**
<br/>

## Epicor Sync Monitoring
<!--
#### Pipeline
<br/>

#### In Development
<br/>
-->
#### In Test
- awaiting test **PR**
<br/>

## Epicor error monitoring

Push the Epicor REST errors to Epicor
  
At requirements stage
  
&nbsp;&nbsp;&nbsp;&nbsp;AP Automations
&nbsp;&nbsp;&nbsp;&nbsp;POD
&nbsp;&nbsp;&nbsp;&nbsp;MFS
<span style="color:grey">
No action needed
</span>

<!--
#### Pipeline
<br/>

#### In Development
<br/>

#### In Test
-->
<br/>


## Shopify
<span style="color:grey">
No action needed
</span>

<!--
#### Pipeline
<br/>

#### In Development
<br/>

#### In Test
-->
<br/>


# Utilities

## Trim logs
<span style="color:grey">
No action needed
</span>

<!--
#### Pipeline
<br/>

#### In Development
<br/>

#### In Test
-->
<br/>

## Message Queue Check
<span style="color:grey">
No action needed
</span>

<!--
#### Pipeline
<br/>

#### In Development
<br/>

#### In Test
-->
<br/>


## Wiki Link
<span style="color:grey">
No action needed
</span>

<!--
#### Pipeline
<br/>

#### In Development
<br/>

#### In Test
-->
<br/>


## API Gateway
<span style="color:grey">
No action needed
</span>

<!--
#### Pipeline
<br/>

#### In Development
<br/>

#### In Test
-->
<br/>


## Licence API
#### Pipeline
- Technical reference
<br/>
<!--
#### In Development
<br/>

#### In Test
-->
<br/>


## Language Files
#### Pipeline
- Language file tool
<br/>
<!--
#### In Development
<br/>

#### In Test
<br/>
-->
## Copy live to test
#### Pipeline
- Pending
<br/>
<!--
#### In Development
<br/>

#### In Test
<br/>
-->
## Admin Service

#### Pipeline
- Waiting security stuff from DevOps **PM**
<br/>
#### In Development
- Single script for Devops to run **PR**
<br/>

# Dev Ops

## Parameter screen CABS

#### In Development
- Link directly to CABs from wiki main page **BW**
<br/>

## POD CABs
#### In Development
- Move to wiki **PR/BW**
<br/>

# Frameworks

## Dotnet
#### Pipeline
- AP Automation
	 - probably wait until more needs to be done
<br/>
<!--
#### In Development
<br/>
-->
#### In Test
- Mobile Field Service
<br/>

## Android

#### In Development
- POD to Android 13
<br/>

## iOS
<span style="color:grey">
No action needed
</span>

<!--
#### Pipeline
<br/>

#### In Development
<br/>

#### In Test
-->
<br/>



# Sub projects

## Technicial Reference Guides
#### Pipeline
- Licence API (logging in on web pages)
- MFS Web
- POD
- PO Approval
<br/>

## Two Factor Authenication
<!--
#### Pipeline
<br/>

#### In Development
<br/>
->
#### In Test
- Pending
<br/>

### Concurrent Licensing
<!--
#### Pipeline
<br/>

#### In Development
<br/>
-->
#### In Test
- Pending
<br/>


## Epicor API v2
#### Pipeline
- POD
- MIMS
- Access Scopes
<br/>
<!--
#### In Development
<br/>

#### In Test
<br/>
-->

