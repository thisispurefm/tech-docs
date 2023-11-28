---
layout: default
title: Active Directory User Groups
parent: Active Directory
grand_parent: Tech Team
nav_order: 2
---

# Active Directory User Groups
Active Directory has a number of methods to organise and categorise users, one of these methods is through *Security Groups*. A user can be a member of multiple groups and a group can have multiple users as a member of it. This makes it really convenient to use groups to control policies that get applied to users. 

## PureFM's implementation of Security Groups
The group a user belongs to will depend on their role in PureFM. See the table below for how group membership relates to a users role at Pure.

| Group Name | Type | Membership |
|:---|:---|:---|
| `Domain Users` | Builtin | All accounts which users actively use |
| `Domain Administrators` | Builtin | Top level administrators. *Should only be given to competent people as this imposes no restrictions*. Should only ever be assigned to admin specific accounts |
| `GP-TECHTEAM` | Custom | Tech Team members (standard accounts) |
| `GP-MUSICTEAM` | Custom | All music team members |
| `GP-MUSICTEAMPLUS` | Custom | Senior Music Team members (provides edit access on Music drive) |
| `GP-COMMITTEE` | Custom | All committee members |
| `GP-COMMITTEEPLUS` | Custom | Senior committee members (provides access to all sensitive files) |