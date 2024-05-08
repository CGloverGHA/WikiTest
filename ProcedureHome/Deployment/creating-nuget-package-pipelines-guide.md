---
title: creating-nuget-package-pipelines-guide
description: 
published: true
date: 2024-01-19T15:06:49.049Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:28:48.491Z
---

# Creating NuGet Package Pipelines

To create a CI pipeline for publishing a new NuGet package, first create a new file in the root folder of the repository named `azure-pipelines.yml`

Next, paste the following content into the `azure-pipelines.yml` file

```yml
trigger:
- master

variables: 
  - group: 'NuGet Packages Variables'

pool:
  name: $(NuGet Agent Pool)

steps:
  - task: DotNetCoreCLI@2
    displayName: 'Restore'
    inputs:
      command: 'restore'
      feedsToUse: 'select'
      vstsFeed: '4523155f-8016-48ec-be78-27efab985fb1'

  - task: DotNetCoreCLI@2
    displayName: 'Build'
    inputs:
      command: 'build'

  - task: DotNetCoreCLI@2
    displayName: 'Test'
    inputs:
      command: 'test'

  - task: DotNetCoreCLI@2
    displayName: 'Pack'
    inputs:
      command: 'pack'
      packagesToPack: '**/*.csproj'
      includesymbols: true
      includesource: true
      versioningScheme: 'byPrereleaseNumber'
      majorVersion: '1'
      minorVersion: '0'
      patchVersion: '0'

  - task: NuGetCommand@2
    displayName: 'Push'
    inputs:
      command: 'push'
      packagesToPush: '$(Build.ArtifactStagingDirectory)/**/*.nupkg;!$(Build.ArtifactStagingDirectory)/**/*.symbols.nupkg'
      nuGetFeedType: 'internal'
      publishVstsFeed: '4523155f-8016-48ec-be78-27efab985fb1'
```

This file contains references to the `NuGet Packages Variables` variable group. This variable group is already defined within the `NuGet Packages` project (on Azure DevOps) and contains the `NuGet Agent Pool` variable which defines what agent this pipeline should run on

If the variable group does not exist, create it by navigating to `Pipelines > Library`

- Ensure that the Variable Group Name and Variable Name is the same as defined in the pipeline

This file also references the Azure Artifacts NuGet feed for GHA Solutions via a GUID.

- If the NuGet feed changes (such as deleting and recreating it), then this GUID will need to be updated **for all NuGet packages**

---
To create the CI pipeline within Azure DevOps, navigate to the `NuGet Packages` project on [Azure DevOps](https://dev.azure.com/GHASolutions)

Navigate to `Pipelines > Pipelines` and click `New pipeline`

Select `BitBucket` and then find and select the repository of the required NuGet package

The next page should show the `azure-pipelines.yml` file created earlier, click `Run` and verify that the pipeline runs correctly

The pipeline should now be triggered whenever changes are pushed to the `master` branch
