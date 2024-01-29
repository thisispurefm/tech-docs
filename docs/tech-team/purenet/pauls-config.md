---
layout: default
title: Paul's Config
parent: PureNet
grand_parent: Tech Team
has_children: false
has_toc: false
nav_order: 1
---

# Paul's Config

Because HP is a lovely company, the BIOS settings required to make PCIe passthrough work on Gen 8 servers are very
 strange. Below is a set of instructions for setting this up, should it ever need to be done.

## BIOS Config

1. Press F9 to enter the Setup Menu when prompted during hte boot process
2. In `System Options` then `Processor Options`, set the following to `On` or `Enabled`: 
`Intel Virtualization Technology`, `Intel Hyperthreading Options`, `Intel Turbo Boost Technology` and `Intel VT-d`
3. In `Power Management Options`, set the following: `HP Power Profile` to `Maximum Performance`, `HP Power Regulator`
 to `HP Static High Performance Mode` and `Redundant PSU` to `Balanced Mode`
4. In `Standard Boot Order (IPL)`, set `Hard Drive C:` to `IPL Boot Device 1`
5. In `Date and Time`, check the date and time is set correctly
6. In `Server Availability`, set `Automatic Power On` to `Always Power On`
7. In `Advanced Options`, set `SR-IOV` to `Enabled`
8. Press `Exit` or `ESC` to close, and `F10` to confirm. This will cause a hard reset and reboot

## PCIe Passthrough Config

Once again, there is some special HP sauce required to make PCIe passthrough work. Use the button below to open a guide
 I found somewhere on the internet :)

[Open PDF](/assets/tech-team/purenet/proxmox-pcie-passthrough.pdf){: .btn }