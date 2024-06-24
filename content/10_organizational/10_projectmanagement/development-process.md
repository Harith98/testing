---
layout: default
title: Development Process
parent: Project Management
grand_parent: Organizational
nav_order: 2
file: content/10_organizational/10_projectmanagement/development-process.md
date: 2024-05-29T13:33:10+00:00
commit: 9d3535fab21e53e819c9e62632bee83eb66d1d95
---
# Development Process
{: .no_toc }

The following process describes all steps from a user requirement to a deployed API. Please follow all these steps to guarantee a harmomized development process and a steady good quality.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

##  Development

| No | Step                                                                      | Resources                                                                                               | Remarks                                                                                                                                                                             |
|----|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 01 | Pick Jira Ticket from Backlog                                             | [MuleSoft Jira Backlog](https://jira.bbraun.com/secure/RapidBoard.jspa?rapidView=829){:target="_blank"} | **Never start development without a proper ticket**                                                                                                                                 |
| 02 | Set Ticket into `IN PROGRESS`                                             |                                                                                                         |                                                                                                                                                                                     |
| 03 | Create a feature branch inside API git project.                           | [GitHub](https://code.bbraun.io/IT-BS-MuleSoft){:target="_blank"}                                       | e.g. `feature/MUL-100-My-Development`                                                                                                                                               |
| 04 | Implementation                                                            | [GitHub](https://code.bbraun.io/IT-BS-MuleSoft){:target="_blank"}                                       | Push frequently to central git repo<br/>Pull latest changes from `origin/develop` frequently in your feature branch to prevent a lot of merge conflicts in a single merge</li></ul> |
| 05 | Once implemented and tested locally build and deploy API to Sandbox stage |                                                                                                         | Use GitHub Action workflow `01 | A/M | Test deployment`                                                                                                                             |
| 06 | Schedule *Dev Approval* Meeting                                           | Teams Session                                                                                           | Create meeting with all available team members to present the requirement and its implementation<br>One attendee has to be selected as approver                                     |
| 07 | Create a Pull Request                                                     |                                                                                                         | Create PR from `feature/X` to `develop`<br>Assign the selected approver as reviewer                                                                                                 |
| 08 | Pull Request Approval                                                     |                                                                                                         | Approver checks PR and rejects or approves it<br>In case approver find issues they should be commented in the PR and developer is going to fix them<br>Delete the feature branch    |
| 09 | Set Jira ticket to status `DONE`                                          |                                                                                                         |                                                                                                                                                                                     |

## Deployment

| No | Step                                     | Resources | Remarks                                                                                                                        |
|----|------------------------------------------|-----------|--------------------------------------------------------------------------------------------------------------------------------|
| 10 | Merge from `develop` to `master`         |           | Once all developments planned in the sprint for this API are done merge all changes that were approved by PRs to MASTER branch |
| 11 | Deploy API to TEST and PROD stage        |           | Use GitHub Action workflow `02 | A/M | Build artifact / Upload Artifactory` and `03 | M | Deploy artifact`                     |
| 12 | Notify Stakeholders about PRD deployment |           |                                                                                                                                |

No development should reach PROD stage without approved Pull Request from other developer!
{: .warning }