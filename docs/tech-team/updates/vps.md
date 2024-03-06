---
layout: default
title: Icecast VPS
parent: Updates
grand_parent: Tech Team
has_children: false
has_toc: false
nav_order: 1
---

# Updating the Icecast VPS
1. SSH into the VPS
1. Run the command `apt-get update && apt-get upgrade -t Debian_10` **Check that icecast is not listed in the list of
 packages you are updating** (yes, this does look strange - see Icecast Installation instructions for more here)
1. Run the command `reboot now` to reboot the VPS
1. This should take less than 5 minutes to come back up. If after this time, you cannot SSH into the VPS, login to the
 Linode web panel and confirm what the VPS is doing.
1. Once you have been able to SSH into the VPS - run the command `systemctl status icecast2.service` and confirm that
 the "Active" is "active (running)"
1. Go to the Icecast web interface and confirm that the page loads. (There should not be anything streaming to it, if
 there is - you did a bad and need to fix it now)