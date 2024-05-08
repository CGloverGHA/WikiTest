---
title: Epicor Sync
description: 
published: true
date: 2024-01-19T15:06:36.795Z
tags: 
editor: markdown
dateCreated: 2023-08-02T15:06:35.536Z
---

# Epicor Sync

### Flow Chart
![untitled_diagram.drawio.png](/untitled_diagram.drawio.png)



The epicor sync service runs every minute. This can be changed in the AppSettings under the setting : EpicorSync - RestartTime(ms)

First the service gets a list of every customer who has the flag "EpicorSyncEmail" set to true.

Then every application that the customer owns is used to grab that customer's epicor connection. 

The connection is tested by calling the "ABCCodes" API call. If the API call returns an error response or the API call itself fails then the epicor connection is marked as an error.

A new Sync Log is then created if it doesn't exist already and an email is sent out to all the admin users for that customer and to GHA's support email. The GHA support email can be changed in the AppSettings table under the setting : EpicorSync - SupportEmail, the ValueString creates a list from all the emails seperated using a semicolon ( ; )

If a Sync Log already exists then the step above is ommited. 

If a Sync Log already exists and the request doesn't fail then the Sync Log is marked as Successful.

