---
layout: default
title: Forcing Icecast Etape
parent: Transmission
grand_parent: Tech Team
nav_order: 12
---

# Forcing the Etape on Icecast

Within Icecast, there are the two main mountpoints, two O.B. mountpoints, and an MP3 of the full Emergency Tape track.
 If you should need to take the entire transmission chain offline (for example, if the power goes out or devices need to
 be restarted), the main stream will automatically fall-back to the emergency tape stored on the Icecast VPS. In the
 event that you need to immediately kill the stream remotely, these are the steps you should follow.

## Disconnecting the Streams

{: .warning}
> This will disconnect anyone listening to the stream, but if you need to stop the streams, you probably don't care...

Since Icecast does not have an actual killswitch, the easiest method of killing the streams is to ssh into the Icecast
 server, change the mountpoint password, and restart the service. The steps for this are listed below

- SSH into the [VPS](../purenet/computers.html#icecast-testpurefmxyz) with the `root` account
  - You will experience issues if you use a terminal other than `xterm` (don't ask), so after logging in, run the command
   `export TERM=xterm`
- Open the file `/etc/icecast2/icecast.xml` in an editor of your choice (`nano` is installed so probably use that)
- Edit the following section, and change the password in `<source-password></source-password>`, preferably just add some
 characters before the existing password :), e.g.
```xml
<authentication>
    <!-- Sources log in with username 'source' -->
    <source-password>CHANGEDthisIsNotTheActualPassword:D</source-password>
    <!-- Relays log in with username 'relay' -->
    <relay-password></relay-password>

    <!-- Admin logs in with the username given below -->
    <admin-user>admin</admin-user>
    <admin-password>thisIsAlsoNotTheActualPassword:D</admin-password>
</authentication>
```
- Save the changes to the file
- Restart the Icecast 2 server with `sudo systemctl restart icecast2`, then check the status of the service with
 `sudo systemctl status icecast2`
- Also, log into the admin interface of Icecast 2 ([icecast-test.purefm.xyz](icecast-test.purefm.xyz)) and check that
 the streams are not running