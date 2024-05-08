---
title: creating-pipelines-guide
description: 
published: true
date: 2024-02-22T15:15:07.530Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:28:56.466Z
---

# Creating Pipelines

**The best reference for creating pipelines is to reference existing projects since defining what the pipeline does and how it does it is up to the developer. This page will describe the overall process without going into too much detail about the pipelines themselves.**

It is recommended to define pipelines as a multi-stage pipeline [(Multi-Stage Pipelines)](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/stages?view=azure-devops&tabs=yaml#specify-stages).

- There should be a `Build` stage that produces an artifact for `Deploy` stages
- Separate `Deploy` stages by environment

As for unit testing, it can either be a part of the `Build` stage or it's own `Test` stage

- Either way, it should be uploaded using the [PublishTestResults@2 Task](https://learn.microsoft.com/en-us/azure/devops/pipelines/tasks/reference/publish-test-results-v2?view=azure-pipelines&tabs=trx%2Ctrxattachments%2Cyaml) so that the results can be seen on the pipeline page in Azure DevOps.

As for integration testing, it is recommended to create a stage after the relevant `Deploy` stage that `dependsOn` the relevant `Deploy` stage

- This is so that the tests will run **after** the deployment(s)

The following sections provide an overview of creating pipelines for particular projects / deployment strategies

## Docker Deployment Strategy

> This strategy applies to the majority of our pipelines currently

[Docker Deployment Strategy](./creating-pipelines-docker-deployment-strategy.md)

- Guidance on creating pipelines using the [Docker Deployment Strategy](./deployment-strategies.md#docker-deployment-strategy)

## NuGet Packages

[NuGet Packages](./creating-nuget-package-pipelines-guide.md)

- Guidance on creating pipelines for new NuGet packages
