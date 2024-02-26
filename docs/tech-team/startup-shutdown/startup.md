---
layout: default
title: Startup
parent: Startup/Shutdown
grand_parent: Tech Team
has_children: false
has_toc: false
nav_order: 1
---

# Startup

{: .warning}
> ⚠️ Only for use by or with the express permission of the Technical Director ⚠️

The full startup procedure from a completely dead-power situation

## Server Room

1. Turn on the Air Conditioning using it's control panel, and then wait for it to start blowing cold air
1. Unlock the rack for easy access
1. Plug in the power cables, ensuring the two plugs for Paul O'Grady are in different gangs
1. Turn on the plugs
1. Check that the power button on Paul is illuminated in orange
1. Turn on the Type-G PDU in the middle of the rack (Open the cover and switch the nuclear-grade power switch)
1. Turn on the IEC MDU at the top of the rack (Rotate the switch into the ON/1 position)
1. Press the power button on the Netgear NAS
1. Press the power button on Clara Amfo
1. Press the power button on Jack Hayes
1. Check that the router is booting (The power button should illuminate white, and the drive activity light should flash)
1. Check that Paul is booting (The power button should have turned green, and the fans should be going brrrrr). If not,
press the power button
1. Wait for the router to have sung a lovely song for you, and for Paul to have beeped twice
1. Ensure that the mixer in the rack is muted on all channels, especially the channel from Studio 1

{: .warning}
> You **MUST** wait for Paul to have fully booted before moving on to Studio 1, as there is a known issue with the PCs
> failing to map their network drives

## Studio 1

1. Plug in PC 1 & 2, as well as their visual monitors
1. Turn on PC 1 & 2
1. Log into PC 1 with the `s1automation` account, then open PlayIt and log in
1. Enable the log scheduler
1. Plug in the other plugs, but do not switch them on
1. Ensure all of the channels on the desk are muted
1. Turn on the plugs in the following order:
  - Sound Desk
  - Compressor
  - Audio Monitors
1. Turn the monitors up until they are audible
1. Turn on the Wholer
  - If the screen flickers or does not turn on at all, try turning it off and on again. This is a known issue
1. Press the play button in PlayIt
1. Turn on the channel strip for PC 1, you should hear PlayIt coming from the monitors
1. Check the Wholer's input is set to Channel 2, use the input button to cycle if not
1. Check that the levels are coming through on the Wholer
1. Unmute channel `1/2` on the mixer in the server rack
1. Check that audio is coming through using the beige Wholer in the server rack (move the muting switch to the none
position)
1. Listen to the web player to check that the stream is working

{: .note }
> You have successfully brought PureFM from being completely offline to fully on-air. Give yourself a pat on the back 🙂