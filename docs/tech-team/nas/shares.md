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
| `M` | `music` | Current Music Library | M `GP-MUSICTEAMPLUS` R `Domain Users` |
| `N` | `music-archive` | Non-Current Music Library | M `GP-MUSICTEAM` |
| `T` | `tech` | Tech team storage | M `GP-TECHTEAM` |

The `Domain Admins` group has `F` access to all shares.  

User individual storage, once working, will be mapped to `U`. 