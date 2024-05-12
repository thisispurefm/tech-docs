---
layout: default
title: craigcharles
parent: Updates
grand_parent: Tech Team
has_children: false
has_toc: false
nav_order: 1
---

# Updating nelshylton

1. SSH into nelshylton
2. Stop the Libretime service using `sudo systemctl stop libretime.target`
3. Update Ubuntu using `sudo apt-get update`
4. Update Ubuntu again, but more differently this time using `sudo apt-get upgrade`
5. Follow [these instructions](https://libretime.org/docs/admin-manual/install/upgrade/) to update Libretime.
6. Once you have confirmed that the updates have worked - shutdown nelshylton.