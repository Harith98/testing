---
layout: default
title: Jira Story Template
parent: Project Management
grand_parent: Organizational
nav_order: 4
file: content/10_organizational/10_projectmanagement/jira-story-template.md
date: 2024-05-22T10:52:51+00:00
commit: 1c67658f63765fea9864226228380f9c2657b4b4
---
# Jira Story Template
{: .no_toc }

The following template can be used to create a new user story in Jira in a structured and reusable way
{: .fs-6 .fw-300 }


##  Description
{: .no_toc }


```md
h1. Description
 
As the <role> I want to <functionality>, so that <reason>.
 
h1. MuleSoft API
h2. Experience Layer
 
API: *<API Name>*
Endpoint:
{code:json}
/api/v1/XXX
{code}
h3. Authentication
tbd
 
h3. Operations
 
*Get ...*
{code:json}
GET /api/v1/...
{code}
Display name: <display name>
Description: <description>
 
h4. Path Parameter 
||Parameter Name||Description (used for documentation in RAML)||Data type||Mandatory||Default Value||
|parameterName|Description...|string|yes|-|
h4. Query Parameter
||Parameter Name||Description (used for documentation in RAML)||Data type||Mandatory||Default Value||
|parameterName|Description...|integer|-|500|
h4. Header Parameter 
||Parameter Name||Description (used for documentation in RAML)||Data type||Mandatory||Default Value||
|client_id|MuleSoft Client ID|string|yes|-|
|client_secret|MuleSoft Client Secret|string|yes|-|  
 
h4. Body
{code:json}
TODO
{code}
 
h4. Sample Request
{code:json}
GET /api/v1/...
 
HTTP Header:
parameterName: parameterValue
{code}
h4. Sample Response
 
The original response from <application> is returned to the client
{code:json}
{
    "Objects": [
        {}
}
{code}
h3. System/Connector Layer
 
API/Connector: *<Name>*
Expose the following endpoints via the connector
h4. <Operation Name>:
{code:java}
POST  /...
{code}
 
h1. System - <System Name>
*System*: <System Name>
*URL*: [http://.../]
 
h2. Hosting
 
Type: on-premise / Cloud
||Environment||IP||Port||
|DEV|TODO|TODO|
|QAS|TODO|TODO|
|PRD|TODO|TODO|
h2. API
h3. Environments
||Environment||Base URL||
|DEV|TODO|
|QAS|TODO|
|PRD|TODO|
 
h3. API documentation
 
Vendor documentation:
 
h3. Postman Collection
 
see MuleSoft - In Development -> TODO
h3. Operations
h4. <Operation Name>
 
Request:
{code:java}
POST /...
Content-Type: application/x-www-form-urlencoded
  
grant_type=password&username=<username>&password=<password>
{code}
Response:
{code:java}
TODO
{code}
 
h1. Non-functional requirements
h2. Volume and Performance
As the service retrieves a single order by a unique identifier that should be indexed in the source system the call should not take longer than *2 seconds*
 
h2. Security
N/A
 
h2. Availability
N/A
 
h1. Test Data for Integration Tests
 
*QAS:*
 - user:
 - password: see Keepass
 - report name:
 
*PRD:*
 - user:
 - password: see Keepass
 - report name:
 
h1. Contact Persons
||Name||Role||
|<Name>|<Role>|
 
h1. Exchange and ACM asset
 
*API Owner*: <Name>
*E-Mail address:* <E-Mail>
*API Teaser Text*:
{quote}Discover the power of IT Enterprise Architecture Management - the key to unlocking the full potential of your organization's technology portfolio. With a strategic approach to IT architecture, you can align your technology solutions with your business objectives, streamline operations, and optimize resources. IT Architecture Management provides a comprehensive framework for assessing, designing, and implementing IT solutions that drive business success.{quote}
*API Icon*: <Icon>
 
h1. Acceptance criteria
 
Verify, that:
 # Raise a FWRCR so that CloudHub can connect to on-premise  instances
 # Introduce a new Experience API "<Name>"
 ## Expose the endpoint /api/v1/...
 ## Provide a proper RAML documentation of the new endpoint and all fields
 # Introduce a new Connector for <Name> and expose
 ## ... operation
  # Implement the session handing and token caching in the connector
 # Extend Postman collection
 # Add an integration tests ...
 # Apply a client id enforcement policy
 # Publish asset to Exchange and ACM
 ```