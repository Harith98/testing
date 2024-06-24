---
layout: default
title: Ignore integration tests
parent: ADRs
nav_order: 2
---
# 0002 Introduce Feature to ignore integration tests permanently
Date: 2024-01-04

## Status
Accepted
{: .label .label-green }

## Context
We use integration tests to monitor the functionality of our APIs in the target environment. For various reasons, some tests have to be deactivated. These can be temporary reasons, such as missing test data or errors in the backend system. Permanent reasons include, for example, that we do not want to write or change data on production systems.

The number of deactivated tests therefore always includes these two types of reasons for deactivation. However, only the temporary deactivations are of interest, as these must be monitored and should be resolved promptly so that they ideally always equal 0.

## Decision
In the `RunOnStage` annotation, we can mark tests as "permanently deactivated". These tests are no longer listed in the test report with the status "Skipped", but with the status "Successful".

## Consequences
Tests are marked as "Successful", even if they have not really run successfully as integration tests, but are skipped.