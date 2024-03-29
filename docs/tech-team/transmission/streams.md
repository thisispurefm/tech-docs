---
layout: default
title: Streams
parent: Transmission
grand_parent: Tech Team
nav_order: 1
---

# Streams

PureFM streams to it's Icecast2 server from within the server room. We have two streams running as this builds in redudancy should a piece of hardware fail.

## Primary Stream
The Primary stream (to the mountpoint `/stream`) is transmitted from the PS Send. This is specialist, professional-grade broadcast hardware and as such is ultra-reliable and "just works". The stream is sent into the PS Send via it's dual analogue XLR input on it's back. 

## Backup Stream
The Backup stream (to the mountpoint `/backup`) is transmitted from claraamfo. This is the PC in the Server Rack which is also used to play the emergency tape. This PC runs a piece of software called BUTT (standing for Broadcast Using This Tool), which is free. 