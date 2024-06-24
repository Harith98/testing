---
layout: default
title: GitHub branch protection rules
parent: ADRs
nav_order: 3
---
# 0003 GitHub branch protection rules
Date: 2024-01-12

## Status
Accepted
{: .label .label-green }

## Context
Currently we have protection rules against pushing directly to `master` branch and we require a pull request review. We do not protect `develop` branch, we have only status checks enabled.

## Decision
We agreed to do not protect `develop` branch from direct push and we do not require a review while creating a pull request. Pull requests for new features and production fixes have to be reviewed by at least one developer even if this is not enforced by the branch protection rules.

## Consequences
Anyone can accidently push changes directly to `develop` branch causing some issues. Also the pull request approval is not required so we have to be careful while pushing our changes. The `master` branch is secured from potential accidents like the one described.