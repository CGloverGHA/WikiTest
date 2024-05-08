---
title: creating-pipelines-docker-deployment-strategy
description: 
published: true
date: 2024-02-22T15:34:22.542Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:28:52.414Z
---

# Docker Deployment Strategy

- [Docker Deployment Strategy](#docker-deployment-strategy)
  - [Preparing The Git Repository](#preparing-the-git-repository)
    - [NuGet Feed Authentication](#nuget-feed-authentication)
  - [Docker](#docker)
  - [Docker Compose](#docker-compose)
  - [YAML Pipelines](#yaml-pipelines)

## Preparing The Git Repository

### NuGet Feed Authentication

> *NOTE - This section only applies to C# APIs and Services*

The folder containing the `.csproj` file should contain a `nuget.config` file containing an entry to both `nuget.org` and the GHA Solutions internal NuGet Feed

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
 <packageSources>
  <add key="nuget.org" value="https://api.nuget.org/v3/index.json" protocolVersion="3" />
  <add key="GHASolutions" value="https://pkgs.dev.azure.com/GHASolutions/_packaging/GHASolutions/nuget/v3/index.json"/>
 </packageSources>
</configuration>
```

This is primarily done so that the project can be successfully restored when building the [Docker](#docker) docker image

- It is also done so that a direct link to the used NuGet feeds are stored in the project itself so other developers will know what feeds are required for this project explicitly

## Docker

A new repository should contain at least one `Dockerfile` to build the project as a docker image

This deployment strategy primarily use Windows containers, but this may change to Linux containers in the future

- Create a `Dockerfile.linux` file for building Linux containers
- Create a `Dockerfile.windows` file for building Windows containers

*If the project is a C# API or Service...*

- `Dockerfile.linux` & `Dockerfile.windows` should be placed next to the relevant `.csproj` file and should contain a `nuget.config` file for the reasons as described in [NuGet Feed Authentication](#nuget-feed-authentication)

## Docker Compose

A new service should be added to the relevant `docker-compose.yml` files in the [`Deployment` repository](./azure-devops-deployment-repository.md)

> - Ensure that the **port** does not conflict with any other service
> - Follow the [Naming Conventions](./naming-conventions.md) when adding a new service

### Secrets

If your application requires secrets, ensure that they are provided to the container by adding the `environment` section to the service.

The `environment` section will specify the environment variables that the container will use. ([Docker Compose Documentation](https://docs.docker.com/compose/environment-variables/set-environment-variables/#use-the-environment-attribute))

For example:
```yaml
    licence.api:
        image: license.api
        container_name: gha_licenseapi
        environment:
            - ASPNETCORE_URLS=http://+:80
            - ConnectionStrings__LicenseServerContext
            - Email__FromAddress
            - Email__FromName
            - Email__MailServerAddress
            - Email__MailServerPort
            - Email__ToAddress
            - Email__ToName
            - JwtConfig__Secret
```

The reason the variables are provided using underscores is because of [this](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-8.0&tabs=windows#environment-variables)

It is essentially a way of representing JSON values in a single line.

For example
```json
{
  "Secrets": {
    "Database": {
      "LicensePortal": "..."
    },
    "Secret1": "..."
  }
}
```

The above structure would be represented like
```
Secrets__Database__LicensePortal
Secrets__Secret1
```

## YAML Pipelines

> Please follow the [General Pipeline Guidelines](./general-pipeline-guidelines.md) when creating new pipelines

The goal of the pipeline is to build a docker image and deploy it on the server using docker compose

Two templates can assist with this process

- [Build and Publish Docker Image Template](./build-and-publish-docker-image-template.md)
- [Deploy Docker Container Template](./deploy-docker-container-template.md)

### Secrets

In order to provide the secrets to the container during the deployment, a variable group is required.

In the variable group, you will add the secrets you are using in your application to the variable group. These variables can be found in `appsettings.json` or `launchSettings.json`.

Make sure that the entries match the same name as discussed in [Docker Secrets](#secrets)

Example variable group

