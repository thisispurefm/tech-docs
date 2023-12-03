---
layout: default
title: NAS Shares
parent: NAS
grand_parent: Tech Team
nav_order: 1
---

# NAS Shares

We have a number of different shares on our NAS - each for a different purpose. Each share has a different set of users who can access the share, with different permissions.

By default - no one gets any permissions for anything. We assign permissions to users by assigning permissions to Active Directory groups which the users are members of.

## Access Types
Listed below are TrueNAS's basic permissions. The permissions are listed from least-to-most and they inherit from those listed above them.

| ID | Name | Permissions |
|:---|:---|:---|
| T | Traverse | Navigate through directories and execute files. Can't read files but can see they exist|
| R | Read | Read file contents, directories and file attribute. Cannot edit anything |
| M | Modify | Modify file & folder contents & attributes |
| F | Full Control | All permissions including changing ownership and permission of files & folders |

## Shares
Shown in the table below are the shares we have and the users who can access them. 

{: .warning}
This list is up to date as at 2023-11-28. The most up to date list will always be within TrueNAS itself. 

| Letter | Share Name | Purpose | Permissions |
|:---|:---|:---|:---|
| `Z` | `archive` | Archived PureFM Files | M `GP-COMMITTEEPLUS` |
| `Q` | `blackbox` | A blackbox of all live broadcast content | M `GP-COMMITTEEPLUS` |
| `O` | `committee` | Committee Storage | M `GP-COMMITTEE` |
| `H` | `home` | All users shared storage | M `Domain Users` |
| `M` | `music` | Current Music Library | M `GP-MUSICTEAMPLUS` <br> R `Domain Users` |
| `N` | `music-archive` | Non-Current Music Library | M `GP-MUSICTEAM` <br> M `GP-MUSICTEAMPLUS` |
| `T` | `tech` | Tech team storage | M `GP-TECHTEAM` |
| `V` or `U` | `user` | User personal storage | See below |

The `Domain Admins` group has `F` access to all shares.  

## User Personal Storage
Users have a folder setup in the `user` share which is their personal networked storage. This folder is created manually when the user is created, naming it their username.  
All domain users have Traverse access to the share, with individual users being assigned Modify access to their folder.  
As usual, Domain Admins have Full Control over the share and the share maps for Domain Admins using the letter `V` (as to not conflict with their own user drive).  
User individual storage maps to the letter `U`, and folder redirection is setup for Documents, Downloads, Photos, Videos and Desktop to point to the root directory of the users' individual folder. 