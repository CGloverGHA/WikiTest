---
title: App Version Checks
description: 
published: true
date: 2024-01-19T15:01:03.946Z
tags: 
editor: markdown
dateCreated: 2023-04-26T09:51:55.176Z
---

# 1-2-3 App Version Checks


In the License Portal on the device screen the device ID has been made shorter. Prior to this it just looked unkempt. A tooltip has been added over the id to be able to view the whole id incase it is needed.


![image.png](/image.png)
<br>

Also a check has been added for the device app version. This uses a new column in GHALicensePortal.dbo.Devices called AppVersion. This AppVersion on the device is checked against the current application AppVersion. If these are different then the device app version turns red and a red icon appears at the end of the row. This icon contains a tooltip to let the user know that there is a error in the row.

![image_2023-04-26_105142298.png](/image_2023-04-26_105142298.png)
