---
title: Development Meeting
description: 
published: true
date: 2024-01-19T15:06:05.562Z
tags: 
editor: markdown
dateCreated: 2023-10-03T15:35:29.352Z
---

**25th September 2023**

## Attendees

* Peter Roden
* Josh Sweeney
* Bart Wojda
* Ashton Dunderdale
* Charlie Glover
* Harrison O'Leary

# Mobile Apps

## Mobile Field Service

#### Pipeline
`N/A`

#### In Development
- Offline functionality **Torchbearer**
	- Currently with Torchbearer to fix sync issues
  	> *Added 25/8/23*
    >- API fixes pending **PR**
      - UpdateDeviceSync - part arrays are null
      - Task Complete By GUID
      - Task Start by GUID   
    > *Completed 29/8/23*
{.is-info}

- Epicor sync error handling **PR**
	- Added Http status codes
  - Resend failures to Epicor
  - Logging errors to Epicor
 
#### In Test
- Concurrent licensing
- Upgrade to DotNet 6
- Epicor API v2

## MIMS
`No action needed`

#### Pipeline
- Requisitions

#### In Development
`N/A`

#### In Test
`N/A`

## Proof of Delivery

#### Pipeline
- Flutter rewrite
- Technical Reference Guide
- User Guides
- Epicor v2 API (service rewrite)
- Version function and BAQ to be added to CAB
  - Epicor Connection check to then check POD
  

#### In Development
- Submit Android 13 change to Google Play Review **(JS)**

#### In Test
`N/A`

## PO Approval

#### Pipeline
- Version function and BAQ to be added to CAB
  - Epicor Connection check to then check POA
- Apple/Google Store approvals **(JS)**

#### In Development
- Version 1.2.003+68 **(JS)**
- REST logging **(JS)**
- Health Checker in the API **(JS)**
- Technicial Reference Guide **(JS)**

#### In Test
`N/A`

## Installers App
`No action needed`

#### Pipeline
`N/A`

#### In Development
`N/A`

#### In Test
`N/A`

# Web Apps

## Mobile Field Service

#### Pipeline
- Technicial Reference Guide

#### In Development
- Concurrent licensing
  - To deploy to Staging

#### In Test
- Two factor authentication
- Upgrade to DotNet 6

## Alberta Quoting System

#### Pipeline
- Concurrent licensing **(JS & PR)**

#### In Development
- AQS 1.0.009
- Epicor CABs **(PR)**

> Not producing CABs until dev/test is complete
{.is-info}

#### In Test
- AQS 1.0.007 **(AW)**
- AQS 1.0.008 **(AW)**

## Licence Portal

#### Pipeline
- POD Link broken in code (move to POD section...)

#### In Development
`N/A`

#### In Test
- Wiki notifications **Done**
- Epicor v2 API
	- Cannot put live until other API work done
- Epicor user field creation **GG** see below
- Data import for MFS


# Epicor

## Printing Service
`No action needed`

#### Pipeline
- Allowing hosted customer to print using the service

#### In Development
`N/A`

#### In Test
`N/A`

## Parameters Screen

#### Pipeline
- Kinetic form

#### In Development
`N/A`

#### In Test
`N/A`

## Customer work

#### Pipeline
POTL-024 Ship Via **On hold**
POTL-038 PO Form **On hold**
POTL-039 AR Invoice errors **On hold**
Nikon BPM to be fixed

In the GHA report pack there is a sub report error on ARForm (for CBT)

#### In Development
`N/A`

#### In Test
`N/A`

## AP Automation
`No action needed`

#### Pipeline
Swapping between test and live environments **(JS & PR)**

#### In Development
`N/A`

#### In Test
`N/A`

## Testing App (Populate Epicor)

#### Pipeline
`N/A`

#### In Development
- Bug fixes

#### In Test
`N/A`

## User Field Creation

#### Pipeline

#### In Development
- Deployment to live - two app servers **(BW)**
- Bart to discuss with SW (SW to write, BW to copy to wiki) **(BW)**

#### In Test
- Whole process (license portal and rebuild service) **(GG)**

## Epicor Sync Monitoring

#### Pipeline
For this to be really useful:
- Page on the license portal displaying all issues
- Customer logs in issues displayed as a banner across the top of the page (similar to messages)
- Tie in to missed Epicor calls

#### In Development
- Review

#### In Test
`N/A`

## Epicor Error Monitoring

Push the Epicor REST errors to Epicor
  
Analyzing with Susannah and Whales as to what is going wrong
- AP Automations
- POD
- MFS

#### Pipeline
`N/A`

#### In Development
`N/A`

#### In Test
`N/A`

## Open Banking
`No action needed`

#### Pipeline
#### In Development
#### In Test

## Shopify

#### Pipeline

#### In Development
- Create Quote **(PR)**

#### In Test

# Monthly Project

## Arduino project
`No action needed`

#### Pipeline

#### In Development
- Decide on what we should aim to create
- Decide what hardware to use

#### In Test

# Utilities

## Trim logs
`No action needed`

#### Pipeline
- Trim Epicor Sync Logs

#### In Development

#### In Test

## Message Queue Check
`No action needed`
#### Pipeline

#### In Development

#### In Test

## Wiki Link
`No action needed`

#### Pipeline

#### In Development

#### In Test

## API Gateway
<span style="color:grey">
No action needed
</span>

#### Pipeline
- Use a different API Gateway solution like HAProxy **(PM)**
#### In Development
#### In Test

## Licence API

#### Pipeline
- Technical reference
- Language files will not update (ef)

#### In Development
- Sessions are read from MFS for all apps **(PR)**

#### In Test

## Language Files **(BW)**

#### Pipeline
- Language file tool

#### In Development
- Create Specification **(PR)**

#### In Test

## Copy Live DB To Test DB

#### Pipeline
- Pending

#### In Development

#### In Test

## Admin Service

#### Pipeline
- Waiting security stuff from DevOps **(PM)**

#### In Development
#### In Test

# Dev Ops

## Parameter screen CABS

#### Pipeline
#### In Development
- Link directly to CABs from wiki main page **(BW)**

#### In Test

## POD CABs

#### Pipeline
#### In Development
#### In Test

# Frameworks

## Dotnet 6.0

#### Pipeline
- AP Automation
	 - probably wait until more needs to be done

#### In Development
#### In Test
- Mobile Field Service

## Android

#### In Development
- POD to Android 13

## iOS
`No action needed`

#### Pipeline
#### In Development
#### In Test

# Sub projects

## Wiki

#### Pipeline
#### In Development
- User guides and install guides development area (Drafts)

#### In Test

## Technicial Reference Guides
#### Pipeline
- Licence API (logging in on web pages)
- MFS Web
- POD
- PO Approval

## Two Factor Authenication

#### Pipeline
#### In Development
#### In Test
- Pending

### Concurrent Licensing

#### Pipeline
#### In Development
#### In Test
- Pending

## Epicor API v2

#### Pipeline
- POD
- MIMS
- Access Scopes

#### In Development
#### In Test

## Testing procedures

#### Pipelines
#### In Development
#### In Test