---
title: deploy-docker-container-template
description: 
published: true
date: 2024-01-19T15:07:00.072Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:29:00.662Z
---

# Deploy Docker Container Template

> This template is apart of the [Docker Deployment Strategy](./deployment-strategies.md#docker-deployment-strategy)

This template is a helper [Deployment Job](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/deployment-jobs?view=azure-devops) for deploying containers using the [Docker Deployment Strategy](./deployment-strategies.md#docker-deployment-strategy)

## Parameters

`environment`: Environment to deploy to, defined in Azure DevOps

`buildArtifactType`: "Current" or "Specific" - Use current if running from the same pipeline, as "specific" will not work

`buildArtifactProject`: The project to retrieve the build artifact from

`buildArtifactPipeline`: The pipeline to retrieve the build artifact from

`buildArtifactBranch`: The branch to retrieve the build artifact from

`buildArtifactName`: The name of the build artifact

`dockerImageName`: The name of the docker image (used for locating the tar file)

`dockerServiceName`: The name of the docker service (used for locating the service in docker-compose)

`dockerComposeFile`: The name of the docker-compose.yml file to use (.yml is required)

`environmentVariables`: Environment variables to pass to the deployed container

`deployAPIGateway`: Determines whether to deploy the API Gateway as well

`suspendGrafana`: Suspend the Grafana agent during deployment, starting it again after deployment (needed for the testing, staging and live servers)

`suspendIIS`: Suspend the default IIS pool during deployment, starting it again after deployment (needed for the live servers)

## Example

```yml
- template: deployment\docker\jobList\deploy_container.yml@azure-templates
parameters:
    environment: "Development"
    buildArtifactType: "current"
    buildArtifactProject: "Wiki Outgoing Service"
    buildArtifactPipeline: "Deploy"
    buildArtifactBranch: "develop"
    buildArtifactName: "Docker Image"
    dockerImageName: "wikioutgoing.service"
    dockerServiceName: "wikioutgoing.service"
    dockerComposeFile: "docker-compose-development.yml"
    environmentVariables:
    ConnectionStrings__LicenseServerContext: $(ConnectionStrings__LicenseServerContext)
    ConnectionStrings__ServiceBrokerContext: $(ConnectionStrings__ServiceBrokerContext)
    Email__FromAddress: $(Email__FromAddress)
    Email__FromName: $(Email__FromName)
    Email__MailServerAddress: $(Email__MailServerAddress)
    Email__MailServerPort: $(Email__MailServerPort)
    Email__ToName: $(Email__ToName)
    Wiki__Api__Key: $(Wiki__Api__Key)
    deployAPIGateway: false
    suspendGrafana: true
    suspendIIS: false
```
