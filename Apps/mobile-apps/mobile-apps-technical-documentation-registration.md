---
title: mobile-apps-technical-documentation-registration
description: 
published: true
date: 2024-01-19T15:02:51.352Z
tags: 
editor: markdown
dateCreated: 2023-10-06T13:31:20.338Z
---

To register a device with a mobile app, the customer
- Must be on the License Portal
- Must be licensed for the Application
- Must have at least one device license available

The QR Code used for registration can be found on the License Portal in by clicking on the `Licenses` icon next to the relevant application on the Customer's `Applications` page

This QR Code can be scanned via the device's Camera or the via the Data Wedge scanner

This QR Code contains a `Connection String` and `Company Code`
- `Connection String` is the Customer's Application License Key
- `Company Code` is the Customer's License Key

An optional `Device Name` can be provided though a default value will be generated

When the device registration begins, it calls the `Register` endpoint of the License API

By default, the app will call the License API on the Live Server. To override this, provide a QR Code in the format `{Connection String}~{Company Code}~{Environment}` where
- `{Connection String}` is the Connection String on QR Code on the License Portal
- `{Company Code}` is the Company Code on the QR Code on the License Portal
- `{Environment}` is either `dev`, `test`, `staging` or `prod`

Once successful, the following information will be saved to the device
- The `Device ID`
- The `Connection String`
- The `Company Code`
- The `Application License Key`
- The `Device Name`
- The `Device's OS`
- The `Enviroment`

On subsequent app launches, the app will check if the device is registered using this saved information. This is done by calling the `CheckDevice` endpoints on the License API. The given `CheckDevice` endpoint is determined by which app is calling the endpoint. For example, Proof Of Approval will call `CheckDevicePOA`