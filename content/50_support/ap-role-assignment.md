---
layout: default
title: AP Role Assignment Request
parent: Support
nav_order: 1
file: content/50_support/ap-role-assignment.md
date: 2024-05-28T14:22:20+00:00
commit: 03bf06df5157940c5c142cc442e177bdce77b6cd
---

# Anypoint Platform Role Assignment Request

## Support Case
A user needs a special role in Anypoint platform (like Monitoring Viewer). He needs to request that role in [Service Now](https://bbraunp.service-now.com/serviceportal?id=sc_cat_item&sys_id=9cb90fd0db339090ae6330d6f49619a6){:target="_blank"}.

## Support Trigger
E-Mail about requested role with Subject **IT Shop Task TASKXYZ -- Assigned to your team**

## Support Process
1. Check if the user is known and authorized to get the desired access (if in doubt, ask the team) 
1. Open ServiceNow Task and assign it to you and set it to `Work  In Progress`
![Service Now](./images/AP_ServiceNow.png "Service Now")
1. Assign the User to the desired team in Anypoint Platform (Access Management > [Teams](https://eu1.anypoint.mulesoft.com/accounts/teams){:target="_blank"})
1. Assign the user to the Azure AD Group **AAD_EA_Mulesoft_Anypoint_StandardUser** in MyID
![MyID](./images/AP_MyID.png "MyID")
1. Set ServiceNow ticket to Status `Closed Complete`