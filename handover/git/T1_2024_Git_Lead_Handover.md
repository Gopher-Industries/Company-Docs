# Git Lead Handover Document - T1 2024

**Company**: Gopher Industries

**Git Lead**: Tim Butler

# Table of Contents

1. [Overview](#overview)
2. [Repository Overview](#repository-overview)
3. [Adding New Team Members](#adding-new-team-members)
4. [Teams and Permissions](#teams-and-permissions)
5. [Instructions on Contributing for New Members](#instructions-on-contributing-for-new-members)
6. [Repository Setup](#repository-setup)
   1. [Branch Protection](#branch-protection)
   2. [Access Controls](#access-controls)


## Overview

This document serves as a handover guide for the Git Lead role at Gopher Industries.
The Git Lead is responsible for managing the version control system, ensuring the team follows best practices,
and maintaining the integrity of the codebase.
The role requires strong collaboration with the development team, project leads, and other stakeholders to streamline
the development process and promote efficient workflows.

This document is intended to brief the incoming Git Lead on the current state of the repositories, teams, and access
controls within the organisation.

## Repository Overview

At present, the organisation contains the following in-use repositories:

1. **NutriHelp**: A health and nutrition monitoring application.
    * **Docs** - https://github.com/Gopher-Industries/Nutrihelp
    * **Frontend** - https://github.com/Gopher-Industries/Nutrihelp-web
    * **Backend** - https://github.com/Gopher-Industries/Nutrihelp-api
2. **Guardian**: A safety monitoring and alert application.
    * **App** - https://github.com/Gopher-Industries/Guardian
3. **Food Remedy API**: An API serving wholefood nutritional data.
    * **Frontend & Backend** - https://github.com/Gopher-Industries/foodremedy-main
4. **SRV Phone Screening**: A phone screening application for an industry partner.
    * **Frontend, Backend, Docs** - https://github.com/Gopher-Industries/PhoneScreeningSystem2024
5. **Company Docs**: A central repository for company documentation.
    * **Docs** - https://github.com/Gopher-Industries/Company-Docs

## Adding New Team Members

Ensure new team members are added to the organisation and granted access to the relevant repositories.
Invitations for new members can be sent from the [People](https://github.com/orgs/Gopher-Industries/people) tab in the
organisation settings.
These invitations will expire after seven days, so it is important to follow up with new members to ensure they accept
the invitation promptly.

## Teams and Permissions

New team members will also need to be added to the appropriate teams within the organisation.
Inviting members to teams can be done from the [Teams](https://github.com/orgs/Gopher-Industries/teams) tab in the
organisation settings.
By assigning members to teams, you can control access to specific repositories so that team members have only the
permissions they need.
Some team members may need to be added to multiple teams depending on their role and responsibilities.

At current, the organisation has the following teams:

- **Food Remedy API**
- **Guardian**
- **NutriHelp**
- **SRV Phone Screening**

You may need to create additional teams as new projects are initiated.

## Instructions on Contributing for New Members

A helpful guide has been prepared for new team members to get started with Git and GitHub.
Refer them
to [How to Contribute](https://github.com/Gopher-Industries/company-docs/blob/master/docs/how-to-contribute.md).

In brief, for all repositories with branch protection enabled the workflow involves the following steps:
- Clone the repository to your local machine.
- Create a new branch for your work.
- Make changes to the codebase.
- Commit your changes to the branch.
- Push the branch to the remote repository.
- Create a pull request to merge your changes into the main branch.
- Request a code review from a team member.
- Address any feedback and make necessary changes.
- Once approved, merge the pull request into the main branch.

## Repository Setup

At the beginning of T1 2024 most repositories were set up with branch protection and access controls.
The exceptions to this are the **SRV Phone Screening** repository which was created later in the trimester and
the **Food Remedy API** repository which is private and cannot be configured for branch protection.

It is recommended to review these settings and ensure they align with the team's requirements.

### Branch Protection
Main branch is protected to prevent direct commits and require code reviews. 
Any member of a team may perform a code review, except for the submitter of the pull request.

Branch protection rules can be configured in each repositories settings under **_Code and Automation->Branches_**.

### Access Controls
Rather than granting direct access to repositories, team members are added to teams which have access to
specific repositories. This allows for more granular control over permissions and access levels. These teams have
write access to the repositories they are associated with, which means they can create branches directly within
the repository (ie no fork required) and push changes to those branches. In some cases, the team lead may have
additional permissions. 

Access can be managed from the repository settings under **_Access->Collaborators and teams_**.



