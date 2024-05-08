---
title: mobile-apps-technical-documentation-theme
description: 
published: true
date: 2024-01-19T15:02:55.893Z
tags: 
editor: markdown
dateCreated: 2023-10-06T13:31:29.359Z
---

## Setting The Theme
The theme is controlled by the following fields against the `GHALicensePortal.Customer` table

`BackgroundColor`
A string representing the Hex Colour of the background without the `#` prefix

`ForegroundColor`
A string representing the Hex Colour of the foreground without the `#` prefix

`CompanyLogo`
A Base64-encoded string representing the image file contents of the company's logo

These values can be set on the License Portal in the `Appearance` page

## How The App Creates The Theme
The apps make use of the [Material Colour Scheme](https://m2.material.io/design/color/the-color-system.html) though a wrapper object is used to control certain settings

`themeBrightness`
This setting controls whether the app should run in `light` or `dark` mode. It is always set to `dark` mode.

`usePalette`
This setting will determine if intermediate colours should be generated. 

If this value is true, the colour scheme will be generated via the `ColorScheme.fromSeed()` method
> NOTE: The final colour scheme will not be representative of colours close to black or white. This is done automatically by `ColorScheme.fromSeed()` to ensure that the colour scheme is always readable

If this value is false, it will generate the following colour scheme 
- `background` is set to the `BackgroundColor`
- `error` is set to `red`
- `onBackground` is set to `ForegroundColor`
- `onError` is set to `BackgroundColor`
- `onPrimary` is set to `BackgroundColor`
- `onSecondary` is set to `ForegroundColor`
- `onSurface` is set to `ForegroundColor`
- `primary` is set to `ForegroundColor`
- `secondary` is set to `BackgroundColor`
- `surface` is set to `BackgroundColor`

## When The App Gets The Theme
When the app is launched, the theme will be retrieved via a call to the `CheckDevice` endpoint on the License Portal. *The `CheckDevice` endpoint depends on the app*.

If the call is successful, the current theme is updated with the `BackgroundColor`, `ForegroundColor` and `CompanyLogo`. This theme will be used for the duration of the app's runtime, it is not saved to the device.

By default, or in the case of an error, a default theme will be used which consists of the following
- `primaryColor` is white (`FFFFFFFF`)
- `secondaryColor` is black (`FF000000`)
- `tertiaryColor` is grey (`FF808080`)
- `themeBrightness` is `dark`
- `usePalette` is `false`
- `companyLogo` is the GHA's Logo