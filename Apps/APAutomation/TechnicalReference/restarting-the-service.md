---
title: Restarting The Service
description: 
published: true
date: 2024-02-09T16:08:32.523Z
tags: 
editor: markdown
dateCreated: 2024-02-09T16:08:30.174Z
---

# Restarting The Service
> In order to restart the service, you will need RDP access to `GHAUKCH01`

1. RDP onto `GHAUKCH01`
2. Open a PowerShell prompt as an Administrator
3. Enter `docker ps -a`

This lists all containers on the server. Locate the container with the **IMAGE** `apautomation.service`. Take note of the **CONTAINER ID** in the left-hand column.

4. Enter the command `docker container restart <container-id>`

Replace `<container-id>` with the noted **CONTAINER ID**

This will restart the container, thus restarting the service