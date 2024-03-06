---
layout: default
title: jackhayes
parent: Updates
grand_parent: Tech Team
has_children: false
has_toc: false
nav_order: 1
---

# Updating jackhayes
1. SSH into jackhayes
1. Stop the blackbox recording using the following command `sudo systemctl stop blackbox.service`
1. Run the command `sudo dnf update -y`
1. Enter the user password when prompted
1. Reboot using the command `sudo reboot now`, this will kick you out of the SSH session
1. Wait a few minutes then SSH back into jackhayes
1. Run the command `sudo systemctl status blackbox.service` to confirm that the blackbox is running; confirm that the
 "Active" line says "active (running)", if it does not - troubleshooting time!

