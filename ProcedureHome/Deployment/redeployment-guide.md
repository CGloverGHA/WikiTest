---
title: redeployment-guide
description: 
published: true
date: 2024-01-19T15:07:29.646Z
tags: 
editor: markdown
dateCreated: 2023-06-26T09:25:11.450Z
---

# Redeployment Guide

This page will detail the process for restarting existing container builds using the [Azure DevOps Pipelines](azure-devops-pipelines.md)

## Contents

- [Redeployment Guide](#redeployment-guide)
  - [Contents](#contents)
  - [Guide](#guide)
    - [Find The Pipeline](#find-the-pipeline)
    - [YAML Pipeline Guide](#yaml-pipeline-guide)
    - [Classic Pipeline Guide](#classic-pipeline-guide)

## Guide

### Find The Pipeline

Go to [Azure DevOps](https://dev.azure.com/GHASolutions), and find the project to be deployed
![Selecting "License API" on the Azure DevOps Portal](assets/2023-06-26%20092455.png)

Go to `Pipelines > Pipelines` and review the pipelines
![Selecting the latest deployment pipeline for "License API"](assets/2023-06-26%20092728.png)

> - If there is a "Deploy" pipeline, follow the [YAML Pipeline Guide](#yaml-pipeline-guide)
> - If there is a "Build" pipeline, follow the [Classic Pipeline Guide](#classic-pipeline-guide)

### YAML Pipeline Guide

Select the "Deploy" pipeline and review the latest runs
![The latest runs of the "Deploy" pipeline](assets/2023-06-26%20092920.png)

> - The runs are sorted in descending order by the latest run
> - Each run description is prefixed with the branch it ran against, which is an initial indication of the environment
>   - `develop` = Development Environment
>   - `testing` = Testing Environment
>   - `staging` = Staging Environment
>   - `release` = Live Environment
>
> ![Latest pipeline runs with the branch highlighted](assets/2023-06-26%20095720.png)

Once a pipeline run is selected, redeploy the software using the "Rerun Stage" button for the required environment
![Pipeline Run Page](assets/2023-06-26%20093003.png)

If the "Rerun Stage" button cannot be found, ensure that the stage is expanded
![Expand Button](assets/2023-06-26%20100513.png)

### Classic Pipeline Guide

Go to `Pipelines > Releases`, and select the relevant release pipeline
![Classic Release Pipelines](assets/2023-06-26%20100841.png)

- Each pipeline is prefixed with the environment

Select the stage of the latest pipeline run. If there are multiple stages, such as for each the live servers, select both and perform the following steps for each.
![Latest stage of a Release Pipeline](assets/2023-06-26%20101309.png)

Click "Deploy" in the ribbon, and then click "Deploy" in the sidebar
![Clicking the "Deploy" button in the ribbon](assets/2023-06-26%20101545.png)

![Clicking the "Deploy" button in the sidebar](assets/2023-06-26%20101718.png)
