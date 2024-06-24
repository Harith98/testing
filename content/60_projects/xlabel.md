---
layout: default
title: Label API
parent: Integrations & APIs
file: content/60_projects/xlabel.md
date: 2024-05-15T08:54:11+00:00
commit: 655c031ee60fac667a9ba7dd02990cafe5e98f2d
---
# Label API

[Design Center](https://eu1.anypoint.mulesoft.com/designcenter/designer/#/project/ba9dcdea-cb62-4aa8-bcfc-47fe060a3035)  
[Exchange](https://eu1.anypoint.mulesoft.com/exchange/cb729472-528f-4190-9f6f-01c272917b9e/x-label)  
[ACM](https://developer.api.bbraun.io/s/communityapi/a020900000OBKehAAH/braun-api-developer-hublabelapi)    
[Jira Epic](https://jira.bbraun.com/browse/MUL-238)  
[Integration tests](https://code.bbraun.io/IT-BS-MuleSoft/x-label-api-integration-test)  
[User guide for extending the classification mapping in SharePoint](https://bbraun.sharepoint.com/:w:/r/sites/PEMIT/BLING%20-%20Process%20Design/_layouts/15/Doc.aspx?sourcedoc=%7B9A334B6B-440D-4992-A22B-681FFAF360E1%7D&file=BLING_HowToIncludeNewVariables.docx&wdLOR=c9DDF403D-DD97-3B49-8DC0-6771AD575200&action=default&mobileredirect=true)

## Endpoints


### POST: /setWorkflowStep Set workflow step

```mermaid
flowchart LR;
    Start(PEGA) --> MulesoftEndpoint["POST: /setWorkflowStep"];
    
    MulesoftEndpoint --> NiceLabelRequest["/setWorkflowStep @nice-label-connector"];
    
    NiceLabelRequest --> End(NiceLabel);
```



### POST: /getLabelPreview 
### POST: /createLabelVariant 
### POST: /print 

```mermaid
flowchart LR;
    Start(PEGA) --> MulesoftEndpoint["<div>/getLabelPreview or </div><div>/createLabelVariant or </div><div>/print</div>"]
    
    MulesoftEndpoint --> GetProductDataFlow[Get product data from SAP];

    GetProductDataFlow --> GetMatData["Z_CA09_GET_MAT_DATA@s-sap-po-api"];
    GetProductDataFlow --> GetClassication["BAPI_OBJCL_GETDETAIL@s-sap-po-api"];
    GetProductDataFlow --> GetAdditionalMasterdata["AdditionalMasterdata@s-sap-po-api"];
    GetProductDataFlow --> GetReadText["ReadText@s-sap-po-api"];
    GetProductDataFlow --> GetShortText["BAPI_MATERIAL_GET_ALL@s-sap-cms-api"];
    
    GetMatData --> NiceLabelRequest;
    GetClassication --> NiceLabelRequest;
    GetAdditionalMasterdata --> NiceLabelRequest;
    GetReadText --> NiceLabelRequest;
    GetShortText -->  NiceLabelRequest;

    NiceLabelRequest["Request to NiceLabel @nice-label-connector"];
    
    NiceLabelRequest --> End(NiceLabel);
```



### POST: /documentCreate Document Info Record (DIR) creation

```mermaid
flowchart TD;
    A(Start)-->B[Create DIR];
    B-->C{status?};
    
    C--status == 30-->D[Change status to 35];
    D-->G
    
    C--status == 40-->E[Change status to 44];
    E-->F[Change status to 45];
    
    F-->G{has URL?};
    G--yes-->H[Set URL];
    G--no-->I;
    H-->I(End);
```



### POST: /events Label notification event

```mermaid
flowchart LR;
   
    NiceLabel(NiceLabel) --> MuleSoft["POST: /events"];
    
    MuleSoft --> MQ[("label-fifo@AnypointMQ")];
    
    MQ --> PEGA(PEGA);
    
```
