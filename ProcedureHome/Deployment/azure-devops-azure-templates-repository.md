---
title: azure-devops-azure-templates-repository
description: 
published: true
date: 2024-01-19T15:06:23.178Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:28:21.218Z
---

# `azure-templates` Repository

This repository contains the templates used for YAML pipelines in Azure DevOps.

## Guidance

Please refer to the [Azure Pipelines documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/?view=azure-devops) for guidance on how to use these templates.

The following pages are recommended for reading & reference:

- [YAML schema](https://docs.microsoft.com/en-us/azure/devops/pipelines/yaml-schema?view=azure-devops&tabs=schema)
- [Templates](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/templates?view=azure-devops)
- [Jobs](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/phases?view=azure-devops&tabs=yaml)
- [Stages](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/stages?view=azure-devops&tabs=yaml)
- [Deployment Jobs](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/deployment-jobs?view=azure-devops)
- [Environments](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/environments?view=azure-devops&tabs=yaml)

## Folder Structure

Please maintain the following folder structure for additional templates

- 📂`deployment` - Templates for deployment
  - 📂`strategy` - The given [Deployment Strategy](./deployment-strategies.md)
  - 📂`templateType` - The type of template (see [Template Parameters](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/templates?view=azure-devops#parameter-data-types))
    - 📄`template.yml` - The `.yml` template file

**Examples:**

- `deployment\docker\jobList\deploy_container.yml`
- `deployment\docker\steps\build_and_publish_docker_image.yml`
- `deployment\kubernetes\jobList\deploy_app.yml`

## Template List

This list contains documented templates that can be used in YAML pipelines

- **Undocumented templates can be found in this repository**

[Deploy And Publish Docker Image Template](./build-and-publish-docker-image-template.md)

[Deploy Docker Container](./deploy-docker-container-template.md)
