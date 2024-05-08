---
title: azure-devops-agent-maintenance
description: 
published: true
date: 2024-01-19T15:06:19.497Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:28:17.495Z
---

# Agent Maintenance

Each agent pool has a Maintenance Task set up that will clean up the `C:\agent` folder on each agent

The below screenshot shows the settings used on each agent
![Agent Maintenance Task Configuration](assets/2023_02_16_10_23_17.png)

## Docker System Prune Task

Each agent has a Task, setup in Task Scheduler, that will run the `docker system prune -f` command as `NT AUTHORITY\SYSTEM` with Administrator privileges

This is done to reduce the size taken by `D:\dockerdata`
