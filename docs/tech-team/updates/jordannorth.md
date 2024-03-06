---
layout: default
title: jordannorth
parent: Updates
grand_parent: Tech Team
has_children: false
has_toc: false
nav_order: 1
---

# Updating jordannorth
1. Remote into jordannorth using Domain Administrator credentials
1. Open "Settings"
1. Open "Updates & Security"
1. Review the updates which are waiting to be installed, then press "Install Now". 
1. Prepare to wait a while, this is Windows we're updating. 
1. While you are waiting - log into Proxmox, and open the Console view for jordannorth. (We're not touching anything
 here, just using it to view the display in a moment)
1. Once all updates are either complete, pending restart or throwing an error which doesn't go away when you retry 
 them (thanks Windows!) - restart the Server. While this is in progress, use the Proxmox console view to monitor it's 
behaviour.
1. When the server comes back up, RDP back into the server (using Domain Admin credentials again), then check for 
 updates again. If there are more, follow the instructions above to do them.
1. Once Windows Server has managed to update itself and once you've restarted to complete the final update, log out