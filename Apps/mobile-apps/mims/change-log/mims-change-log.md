---
title: mims-change-log
description: 
published: true
date: 2024-01-17T13:33:41.401Z
tags: 
editor: markdown
dateCreated: 2023-10-16T10:40:02.643Z
---

# MIMS App Change Log
## 1.3.001+182 `(07/11/23)`
### 1. Bin Enquiry (`MIMS000058`, `MIMS000059` & `MIMS000060`)
Added the Bin Enquiry applet.
- Supports Lot Tracked Parts
- Supports Camera Scanning
- Supports DW Scanning

### 2. Show Environment Banner (`MIMS000078`)
The banner has now been moved to the top of the layout so the bar, at the bottom of iOS devices, does not overlap the banner.

The layout now adapts to the size of the screen with the banner in place so the pages are no longer cut off

### 3. Support Symbols In Part Enquiry (`MIMS000076`)
Previously, if a Part Number that contained a symbol (such as '#'), an error would be returned. Now any input in the app should be correctly encoded when sent to the REST API, fixing this problem.

### 4. Clear Autocomplete Field (`MIMS000067`)
Autocomplete fields now contain a `x` button to delete the contents of that field.

This currently only applies to the login screen.
- When the Site is cleared, so is the PIN
- When the Employee is cleared, so is the PIN & Site

The Site is now also cleared when selecting an Employee

![](assets/Pasted%20image%2020231107085201.png)

### 5. Fixed Autocomplete Suggestion Width (`MIMS000083`)
Previously, the autocomplete field suggestions would extend past the field's length, now it is equal.

![](assets/Pasted%20image%2020231107085235.png)

### 6. Show Employee On Layout (`MIMS000084`)
Now all pages, past the login screen, will display the employee name

### 7. CAB Version Warning (`MIMS000081`)
A warning message will be displayed, when the User logs in, if the installed CAB Version in Epicor does not match the CAB version expected by the app.

![](assets/Pasted%20image%2020231107090936.png)
## 1.3.001+181
### 1. Registration Barcode Changes To Staging
The QR code scanned on the barcode will now read the staging environment using `stage` rather than `staging`. e.g. `ConnectionString~CompanyCode~stage`

### 2. App Environment Banner
In test versions of the app, a banner will now appear at the bottom of the app showing the Environment and whether it is a test device

If the text overflows, the banner will become horizontally scrollable.

### 3. Login Changes
- The Format Exception that appears when logging in should be gone now
- Unregister device will clear the saved Employee and Site
- Sites won't be loaded when no saved Employee has been restored
- Fixed `Environment Not Set` message that appeared when registering sometimes

## 1.3.001+180
### 1. Apply Theme From `ThemeCubit` (`MIMS000056`)
The theme is now applied from the license portal
- The theme is retrieved when registering
- The theme is retrieved when the app launches

### 2. Login (`MIMS000049`)
#### 2.1 Enabled Fields (`MIMS000066`)
- The Site field is disabled until an Employee is selected
- The PIN field is disabled unless the Employee has a PIN defined in Epicor
- The Login button is disabled until an Employee, Site and PIN (where applicable) has been entered

#### 2.2 (BUG) Can Login Without Info (`MIMS000065`)
[2.1 Enabled Fields (`MIMS000066`)](#2.1%20Enabled%20Fields%20(`MIMS000066`)) prevents users from being able to tap login before entering the required information.

Even if they are able to bypass this, the app now validates the form when the login button is tapped.

#### 2.3 Restore Last Login (`MIMS000067`)
After logging in, the Employee and Site will be saved.

On subsequent app launches, the Employee and Site will be restored on the login page
