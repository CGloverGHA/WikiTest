---
title: build-and-publish-docker-image-template
description: 
published: true
date: 2024-01-19T15:06:45.366Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:28:44.664Z
---

# Build And Publish Docker Image Template

> This template is apart of the [Docker Deployment Strategy](./deployment-strategies.md#docker-deployment-strategy)

This template is used to build a docker image, using a given `Dockerfile`, save the image to a TAR file and publish the TAR file as an artifact.

**Example:**

```yml
- template: deployment\docker\steps\build_and_publish_docker_image.yml@azure-templates
  parameters:
    dockerFilePath: '$(Build.SourcesDirectory)\HealthCheck.API\Dockerfile.windows'
    dockerImageName: healthcheck.api
```
