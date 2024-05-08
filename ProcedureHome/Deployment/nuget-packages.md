---
title: nuget-packages
description: 
published: true
date: 2024-01-19T15:07:25.679Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:29:28.398Z
---

# NuGet Packages

This page describes the NuGet packages used by GHA Solutions' applications

Changes made to the `master` branch of the following applications will automatically trigger the following process

1. The package is built
2. The package's Unit Tests are ran
3. The package is packed
4. The package is published to the Azure Artifacts repository

This process can be found as CI pipelines within the `NuGet Packages` project in `Azure DevOps`

| NuGet Package                    | BitBucket Path                                | Description                                                                                                      |
| -------------------------------- | --------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `GHA.Common`                     | `GHASolutions/GHA.Common`                     | Contains common code such as authentication and interacting with the License Portal database                     |
| `GHA.Common.Logging`             | `GHASolutions/GHA.Common.Logging`             | Contains common code for logging to the License Portal database                                                  |
| `GHA.Common.HealthCheck`         | `GHASolutions/GHA.Common.HealthCheck`         | Contains common code for Health Checking                                                                         |
| `GHA.Common.POD`                 | `GHASolutions/GHA.Common.POD`                 | Contains common code for POD such as `DBContext`, Entities and Repositories                                      |
| `GHA.Common.POApproval`          | `GHASolutions/GHA.Common.POApproval`          | Contains common code for PO Approval such as `DBContext`, Entities and Repositories                              |
| `GHA.Common.MQSync`              | `GHASolutions/GHA.Common.MQSync`              | Contains common code for Message Queue Synchronization                                                           |
| `GHA.Common.AQS`                 | `GHASolutions/GHA.Common.AQS`                 | Contains common code for AQS such as `DBContext` and Entities                                                    |
| `GHA.Common.Tenant`              | `GHASolutions/GHA.Common.Tenant`              | Contains code for multi-tenant behavior such as identifying the tenant and providers for tenant-specific objects |
| `GHA.Common.Mail`                | `GHASolutions/GHA.Common.Mail`                | Contains common code for emailing                                                                                |
| `GHA.Common.Epicor`              | `GHASolutions/GHA.Common.Epicor`              | Contains common code for connecting to Epicor                                                                    |
| `GHA.Common.Epicor.FieldService` | `GHASolutions/GHA.Common.Epicor.FieldService` | Contains Field Service specific code for interacting with Epicor                                                 |
| `GHA.Common.FieldService`        | `GHASolutions/GHA.Common.FieldService`        | Contains common code for Field Service such as `DBContext`, Entities and Repositories                            |
