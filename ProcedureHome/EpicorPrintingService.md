---
title: EpicorPrintingService
description: 
published: true
date: 2024-01-19T15:08:28.826Z
tags: 
editor: markdown
dateCreated: 2023-02-06T14:49:10.624Z
---

# GHA Epicor Printing Service

# Description

The GHA Epicor Printing Service provides a printing solution to a hosted Epicor instance which allows employees to print to printers on the Epicor server from GHA Applications, such as MIMS.

# Service Flow

![serviceflow.png](/serviceflow.png)

# Installation

## Prerequisites

### Session Impersonation

Ensure that `Allow Session Impersonation` is **checked** for the user you intend to login with on the service. This option is located in the `User Account Maintenance` form, under the `Options Tab` under `Background Task Permission`

![sessionimpersonation.png](/sessionimpersonation.png)

### `GHAPrint` User Code

Ensure that the following User Code Type has been created in `User Codes`

![GHA Print User Code](assets/Screenshot%202023-06-14%20142255.png)

### Dotnet 5.0

`DotNet 5.0` is required for `GHA Epicor Printing Service Configuration` to run.

1.      [Download the installer](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-desktop-5.0.16-windows-x86-installer)

2.      Run the installer to install `DotNet 5.0`

### Installation Files

Installation files are stored on SharePoint under `General\Development Work\_Installation\GHA Epicor Printing Service` on SharePoint. Copy both the `Configuration Installation` and `Service Installation` folder to the server.

## GHA Epicor Printing Service Installation

1.      Run `Service Installation\GHA Epicor Printing Service Installer.exe`

2.      Follow the installation wizard

### Installation Verification

1.      Open the start menu and search for and open `services.msc`

2.      Ensure that the `GHA Epicor Printing Service` is running and present within the list

The service will show warnings if the service is not properly configured. Follow the steps under [GHA Epicor Printing Service Configuration](#GHA-Epicor-Printing-Service-Configurati) to install the configuration program.

## GHA Epicor Printing Service Configuration Installation

1.      Run `Configuration Installation\GHA Epicor Printing Service Configuration.exe`

2.      Follow the installation wizard

It is advised to check `Create a desktop shortcut` so that the application can be accessed via a shortcut

### Installation Verification

Once the program has been installed, it should be available as `GHA Epicor Printing Service Configuration` within the start menu.

## Configuration

Within the start menu, search for and open `GHA Epicor Printing Service Configuration`

![configuration.png](/configuration.png)

|**Parameter**|**Description**|**Example Value**|
| :-: | :-: | :-: |
|App Pool Host|Where the Epicor instance is installed, as a URL|erp.company.com|
|App Pool Instance|The desired Epicor instance to use|EpicorDemo|
|Company|The company to run the service on|EPIC06|
|Username|The username of the user to login to the Epicor instance as| |
|Password|The password of the user to login to the Epicor instance as| |

## Logging

Logs for the service are available in `Event Viewer` under `Windows Logs\Application`

## Uninstall

Both the service and the configuration program can be uninstalled within the `Programs and Features` screen in `Control Panel`