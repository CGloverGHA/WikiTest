---
title: azure-devops-pipelines
description: 
published: true
date: 2024-01-19T15:06:38.061Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:28:36.775Z
---

# Pipelines

Pipelines are created using YAML utilizing the following Azure DevOps features

- "Pipelines/Pipelines"
- "Pipelines/Environments"
- "Pipelines/Library" *NOTE: This may be removed in the future, see [Secrets](#secrets)*

## YAML vs Classic Pipelines

YAML is preferred as it is more maintainable

- YAML pipelines are written using `.yml` files in the git repository of the relevant project
- Classic pipelines are created via the web editor on Azure Devops

Classic pipelines are not preferred because it is difficult to manage on a larger scale

There are a number of features available on Azure DevOps that are only available for Classic Pipelines

- "Pipelines/Releases"
- "Pipelines/Task groups"
- "Pipelines/Deployment groups"

As such, it is advised to ignore these features and focus on the YAML features

## Secrets

The "Pipelines/Library" section is currently used to store and pass secrets to the containers

This may change in the future with the adoption of Azure KeyVault

If Azure KeyVault is adopted, the use of library variables will be removed entirely
