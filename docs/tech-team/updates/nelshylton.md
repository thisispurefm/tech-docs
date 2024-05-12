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
3. Update Ubuntu & Libretime using `sudo apt update && sudo apt upgrade -y`
5. Once you have confirmed that the updates have worked - shutdown nelshylton.