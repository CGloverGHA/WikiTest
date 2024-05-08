---
title: mobile-apps-technical-documentation-scanning
description: 
published: true
date: 2024-01-19T15:02:53.639Z
tags: 
editor: markdown
dateCreated: 2023-10-06T13:31:25.629Z
---

The mobile apps generally support the following kinds of barcode scanning

## Camera Scanning
Typically a button with the prefix `Scan` will trigger Camera Scanning. In this kind of scanning, the device's camera will be used to scan a barcode. The user will be presented with a live preview of the camera's feed with instructions on what to do.

## Data Wedge Scanning
> Note: This type of scanning is only supported on **Zebra Android Data Wedge Devices**

If the device is a Data Wedge, the laser scanner can be used to scan a barcode. Unlike camera scanning, the app doesn't trigger the scanning but rather the Data Wedge will send the barcode to the app.

The behaviour of is determined by the page of the app that the user is currently on. In most cases, it will fill in the information, as provided by the barcode, and navigate to the next screen.

### Data Wedge Setup
When the app launches, the following occurs
1. The Data Wedge is enabled
2. A Data Wedge Profile is created, using the App's abbreviated name
3. The Data Wedge Profile is updated with the [Data Wedge Settings](#Data%20Wedge%20Settings)
4. It switches to the Data Wedge Profile

#### Data Wedge Settings
`scanner_input_enabled` is set to `true`
- This enables input via the scanner.

`scanner_selection` is set to `auto`
- This defines the scanner to use. `auto` will pick the first available scanner.

`decoder_ean8` is set to `true`
- This enables `ean8` barcode support

`decoder_ean13` is set to `true`
- This enables `ean13` barcode support

`decoder_code39` is set to `true`
- This enables `code39` barcode support

`decoder_code128` is set to `true`
- This enables `code128` barcode support

`decoder_upca` is set to `true`
- This enables `upca` barcode support

`decoder_upce0` is set to `true`
- This enables `upce0` barcode support

`decoder_upce1` is set to `true`
- This enables `upce1` barcode support

`decoder_d2of5` is set to `true`
- This enables `d2of5` barcode support

`decoder_i2of5` is set to `true`
- This enables `i2of5` barcode support

`decoder_aztec` is set to `true`
- This enables `aztec` barcode support

`decoder_pdf417` is set to `true`
- This enables `pdf417` barcode support

`decoder_qrcode` is set to `true`
- This enables `qrcode` barcode support

`PLUGIN_NAME` is set to the app's package name
- This will associate the profile with the relevant app

`ACTIVITY_LIST` is set to `*`
- This associates the profile with any activity created by the app

`intent_output_enabled` is set to `true`
- This enables output via an intent so the app can read the barcode

`intent_action` is set to a unique action for the app
- This sets the action that the app will listen to

`intent_delivery` is set to `2`
- `2` is Broadcast intent. This allows the app to receive the intent via a Broadcast Receiver

`keystore_output_enabled` is set to `false`
- This disables typing out the barcode automatically
