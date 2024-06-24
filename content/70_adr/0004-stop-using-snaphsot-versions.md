---
layout: default
title: Snapshot versions
parent: ADRs
nav_order: 4
---
# 0004 Stop using snapshot versions and include branch into deployed artifact file name
Date: 2024-01-26

## Status
Accepted
{: .label .label-green }

## Context
Currently, we add `-SNAPSHOT` to the version of all APIs in the develop, release and feature branches. 
We also remove `-SNAPSHOT` from the version before the merge to master.
This requires manual work from the developers and is not necessary.

The only benefit of using snapshot versions is that we can distinguish between artifacts built from `master` vs artifacts built from other branches.
We can improve on that by adding the branch to the artifact name produced by our deployment pipelines.

## Decision
- Stop adding `-SNAPSHOT` to the API versions in develop, release, and feature branches.
- Extend the following deployment jobs with the ability to add the branch to the file name of the jar artifact:
    - 01-build-and-deploy.yml


Artifact name format:
```
{api-name}-{version}-{branch}-{commit-hash}-mule-application.jar
```

Artifact name examples:
- Prod: x-order-api-1.38.0-mule-application.jar
- Test: x-order-api-1.38.0-release-1.38.0-609a160-25012024-092925-mule-application.jar
- Test: x-xref-api-1.3.0-develop-609a160-25012024-092925-mule-application.jar
- Sandbox: x-order-api-1.38.0-feature-mul-1234-609a160-25012024-092925-mule-application.jar
- Sandbox: x-order-api-1.38.0-bugfix-mul-1234-609a160-25012024-092925-mule-application.jar

## Consequences
By removing the `-SNAPSHOT` from the version we rely entirely on the deployment workflow to correctly include the branch name in the file name of the jar artifact.