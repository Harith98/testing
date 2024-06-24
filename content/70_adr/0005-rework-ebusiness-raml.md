---
layout: default
title: eBusiness API RAML Rework
parent: ADRs
nav_order: 5
---
# 0005 eBusiness API RAML Rework

## Status
Accepted
{: .label .label-green }

## Context
As discussed during decision meeting our target is to rework eBusiness API RAML to keep a uniform structure of our critical and mostly updated APIs.

Example of current messy structure:

```yaml
/orders:
  type: ebussinessLibraryResourceTypes.postOrdersResourceExternal
  get:
    displayName: Get Order(s)
    description: Get Order details based on OrderIds passed comma separated as query param
    is: [ 200-item: {itemType: customtype.fetchOrderByOrderId , itemExample: !include examples/responses/fetchOrderByOrderId.json}, standard-еrror-response, orderIdQueryParam, applicationKeyQueryParam, viewIdQueryParam,salesAreaIdQueryParam, customerNumberQueryParam, customerIdentificationHeader ]
  /backorders:
    type: endpoints.backorders
```

## Decision
Rework External eBusiness API RAML structure to follow a folder structure, removing inline endpoints.


## Consequences
It will take a lot of effort to rework eBusiness External API as it's one of the biggest APIs currently. Also every change for an endpoint will need to be tested after to make sure we percieved all data: required / optional query parameters, types etc.