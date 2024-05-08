---
title: POD Technical Documentation
description: 
published: true
date: 2024-01-19T15:02:28.144Z
tags: 
editor: markdown
dateCreated: 2023-09-04T08:56:34.401Z
---

# POD Technicial Documentation

# Epicor Link

## Pre-requisites

## Epicor

In order for GHA Proof of Delivery to integrate with Epicor the following customisations are made

### Fields

The following fields are created in the tables

ShipHead
MscShpHd
SubShipH

| Field Name | Description |
|---|---|
|GHA_LocationLeft_c	|Location left if the package was not signed for. Should be backed up with a photograph.|
GHA_SignedBy_c|The person who signed for the delivery
GHA_CustomerIn_c|Whether or not the customer was in when delivery was attempted
GHA_LeaveDelivery_c|Whether the 'leave delivery' option was selected on the POD app
GHA_TakePhoto_c|Whether the 'Take Photo' option was selected on the POD app
GHA_Delivered_c|Whether the pack was delivered or returned
GHA_DateStamp_c|The time the delivery was created on he POD app
GHA_Latitude_c|The latitude recorded when the delivery was made
GHA_Longitude_c|The longitude recorded when the delivery was made
GHA_DeviceID_c|The ID of the device used to record the delivery
GHA_DeviceName_c|The name of the device used to record the delivery
GHA_DeliveryAttempted_c|


### BAQs

The following BAQs are used by dashboards within Epicor

| BAQ Name                    | Dashboard            |
|-----------------------------|----------------------|
| GHAProofOfDeliveryImages    | GHA_ProofOfDelivery  |
| GHAProofOfDeliveryImages    | GHA_ProofOfDelivery  |


### Dashboards

The following dashboards are installed

|Name	|Description|
|---|---|
|GHA_ProofOfDelivery	|Main dashboard showing delivery information from the app|
