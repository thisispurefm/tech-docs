---
layout: default
title: Shutdown
parent: Startup/Shutdown
grand_parent: Tech Team
has_children: false
has_toc: false
nav_order: 2
---

# Shutdown

{: .warning}
> ⚠️ Only for use by or with the express permission of the Technical Director ⚠️
> In the event an emergency shutdown is required, the Technical Director should be consulted with first.

1. In Studio 1, on PC `PURE-S1-01`, stop PlayIt Live playing out using the red stop button then mute all channels on the Studio 1 sound desk. 
2. Shut down PC `PURE-S1-01`
3. Turn off the Wholer at the plug on the wall
4. In the server rack, mute all channels on the TX mixer
5. Login to Proxmox, using the `root` account, from `PURE-S1-02` 
   1. Then select `paulogrady` in the left-hand-side *Datacentre* menu
   2. Then click the `Shutdown` button in the top right hand corner
   3. Wait for the output shown at the bottom of the screen to show that `VM 100` and `VM 102` have shutdown.
6. Login to the Netgear NAS' web interface and shut that down using the power icon in the top right hand corner
7. SSH into the Blackbox (`jackhayes`) - note you'll need to use it's IP address as DNS will be broken by this point
   1. Enter the command `sudo shutdown now` to shut it down
8. SSH into the LibreTime Server (`nelshylton`) - not you'll need to use it's IP address as DNS will be broken by then
   1. Enter the command `sudo shutdown now` to shut it down
9.  Shutdown PC `PURE-S1-02`
10. Turn off and unplug PC monitors and mood lighting in Studio 1
11. Turn off and unplug in the following order, in Studio 1:
    1.  Monitoring Speakers
    2.  `PURE-S1-01` and `PURE-S1-02`
    3.  Compressors
    4.  Sound Desk
12. Shutdown Studio 2 PC `PURE-S2-01`
13. Move into the server room, you may find it easiest to roll the Large OB kit out of the server room and into Studio 2 to make space; unlock the Server Rack if you haven't done so already.
14. Press the power button on `claraamfo` to shut that down. It might try to start up again, if it does this - press & hold the power button again
15. Press the power button on the router and it should beep then turn off
16. Turn the switch on the IEC PDU to the 0 position
17. Wait some time
18. Turn off the switch on the Type-G PDU
19. Close and lock the rack
20. Turn off the plug labelled `SVR PSU 1`
21. Turn off the plug labelled `SVR PSU 2`
22. Turn off the two PDU's plugs
23. Unplug all plugs, do not leave them on the floor
24. Press the power button on the AC unit and wait for it to turn off.