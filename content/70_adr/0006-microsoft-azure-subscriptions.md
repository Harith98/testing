---
layout: default
title: Microsoft Azure subscriptions
parent: ADRs
nav_order: 6
---
# 0006 Microsoft Azure subscriptions

## Status
Accepted
{: .label .label-green }

## Context
As discussed during decisions meeting in Microsoft Azure we have 2 subscriptions IT-BS-MuleSoft and BBraun-MuleSoft. Both of them are described as "Candidates to migrate" in BBC. Few months ago we wanted to have different subscriptions per stage and now it's possible by requesting new instances in BBC. We will have to migrate anyway at some point of time.

## Decision
Request 3 new subscriptions per stage and migrate everything from our old subsriptions. On sbx we can create everything manually but on qas and prd we are going to create all of the resources by Terraform.

## Naming convention

Resource group name: per use case and also with the stage, for example `catalog-cache-sbx`

Storage account (unique) name: we can't use special characters and it has to be unique, for example `mulcatalogcachesbx`

Containers, tables, etc.: `catalog-cache-sbx`

## Consequences
It will require help from everyone in the team to migrate all of the resources.
