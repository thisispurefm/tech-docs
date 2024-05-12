---
layout: default
title: Updates
parent: Tech Team
has_children: true
has_toc: false
nav_order: 1
---

# Updates

Updates are a critical part of maintaining the Technical Infrastructure at PureFM. They should be applied *frequently*,
 the definition of this is up to the Technical Director. At a minimum, they should be applied during every Consolidation
 week, major holiday and at the start of each academic year.

{: .warning}
DO NOT procede with any of these updates if you have not been trained to complete them. This is arguably the most
 dangerous activity performed on PureNet and needs to be protected as such.  

{: .information}
This guide will involve shutting down all components of the PureFM network. You will need a laptop (or non-AD Joined)
 PC connected to the network to work from. 

## Order to Update
There is a precise art to doing the order of the Updates. This is listed below:
1. In the Server Rack - on the TX Mixer and Mute the Studio 1 feed (all channels should now be muted)
2. On Claraamfo
    - Stop BUTT from streaming
    - Close Elisa
3. Unplug the PS Send (`PS.S`) Ethernet from the Patch Panel in the rack to prevent it from streaming
4. Listen to the stream to confirm that the Emergency Tape is playing. The Emergency Tape should begin whenever you
 refresh the page. 
1. In Studio 1 - stop PlayIt Live playing on `PURE-S1-01` then shut that PC down. Then shut down `PURE-S1-02` and
 `PURE-S2-01`. 
1. Follow the instructions for [Updating claraamfo](claraamfo.html)
2. Follow the instructions for [Updating jackhayes](jackhayes.html)
3. Follow the instructions for [Updating nelshylton](nelshylton.html)
4. Follow the instructions for [Updating the VPS](vps.html)
5. We're now moving onto updating Virtualised Systems. It's helpful to login to Proxmox to be able to view the Console
 view of our VMs. We're not touching the Console through Proxmox, just looking at it.
1. Follow the instructions for [Updating jordannorth](jordannorth.html)
2. Follow the instructions for [Updating anniemac](anniemac.html)
3. Shutdown jordannorth
4. Follow the instructions for [Updating paulogrady](paulogrady.html)
5. Follow the instructions for [Updating craigcharles](craigcharles.html)
6. Follow the instructions for [Updating the Netgear NAS](netgearnas.html)
7. We have now updated all the central services, so we can reboot everything. Follow the instructions for 
 [Starting Up from Cold](../startup-shutdown/startup.html)
1. Follow the instructions for [Updating the Studio PCs](studio-pcs.html)