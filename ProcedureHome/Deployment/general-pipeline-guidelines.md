---
title: general-pipeline-guidelines
description: 
published: true
date: 2024-01-19T15:07:11.049Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:29:12.718Z
---

# General Pipeline Guidelines

## Branch Triggers

Depending on the environments that the application will deploy to, the YAML pipeline should include a branch trigger for the following branches

- `develop`
- `testing`
- `staging`
- `release`

The pipeline **should not** execute on the `master` branch to prevent unnecessary builds

## Naming

The CI pipeline should contain this line, at the top, to tag the artifact with the branch
`name: $(SourceBranchName)_$(Date:yyyyMMdd)$(Rev:.r)`
