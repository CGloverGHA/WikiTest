---
title: environments-and-servers
description: 
published: true
date: 2024-01-19T15:07:07.491Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:29:08.670Z
---

# Servers & Environments

## Development Environment

The development environment consists of two servers

- `GHAUKDV01`
- `GHAUKDV02`

The development environment is used for internal developer testing and for providing a way for Torchbearer to develop frontend's or app's against an API GHA develops

### Development Server 1

> Known as `GHAUKDV01`

This server is **not used for container deployment**, instead it is used for hosting development Epicor environments

### Development Server 2

> Known as `GHAUKDV01`

This server is **used for container deployments**

It is also the primary Azure DevOps agent (most if not all builds will occur on this server)

## Testing Environment

The testing environment consists of a single server

- `GHAUKDVCH02`

The testing environment is used for the testing of GHA Solutions' applications by the GHA Testing Team

### Testing Server 1

> Known as `GHAUKDVCH02`

This server is **used for container deployments**

## Staging Environment

The staging environment consists of a single server

- `GHAUKDVCH01`

The staging environment is the final stage before the [Live Environment](#live-environment) and is used for the final stage of testing

### Staging Server 1

> Known as `GHAUKDVCH01`

This server is **used for container deployments**

## Live Environment

The Live environment consists of two servers

- `GHAUKCH01`
- `GHAUKCH02`

The Live environment is the environment that hosts deployments that **customers can access**

API containers run both on [GHAUKCH01](#live-server-1) and [GHAUKCH02](#live-server-2)

### Live Server 1

> Known as `GHAUKCH01`

The following services are ran on this server

- `trimlogs.service`
- `fieldservicesync.service`
- `apautomation.service`

### Live Server 2

> Known as `GHAUKCH02`

The following services are ran on this server

- `fieldservicedatasync.service`
- `mqcheck.service`
