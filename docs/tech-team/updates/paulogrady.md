---
layout: default
title: paulogrady
parent: Updates
grand_parent: Tech Team
has_children: false
has_toc: false
nav_order: 1
---

# Updating paulogrady
1. Login to the Proxmox web interface
1. Ensure that all VMs are shut down (if they're not - a green something shows up in their icon). If any are still
 running - shut them down.
1. Select "paulogrady" in the left hand column
1. Select the Updates category
1. Press "Refresh" in the top left corner, above the package list
1. You will be presented with a dialogue box saying "You do not have a valid subscription for this server". Press "OK".
1. It will now open a Task View and give you the console output of it updating the package repositories. It has finished
 when the last line reads "TASK OK". 
1. Press the X in the top right hand corner of that dialogue box.
1. Press the "Upgrade" button located next to the "Refresh" button. This will open an entirely new instance of the
 browser containing the console doing updates. Enter `y` when prompted.
1. Once completed, it will say "Your system is up to date" and drop you back to a shell. 
1. Close the pop-out-shell browser window
1. Shutdown paulogrady