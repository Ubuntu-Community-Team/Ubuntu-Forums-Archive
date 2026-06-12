---
title: "Keyboard lock playing Robokill2"
date: 2014-10-04
forum: Wine
---

### Post by NuxNik on 2014-10-04
Lubuntu 14.04LTS
Wine 1.6 Amd64
Dell Optiflex 755 SFF

Trying to run a simple game called Robokill2.exe
It runs in Flash
Started with :
wine "C:/Robokill/Robokill2/Robokill2.exe"

Use  WASD as direction controls, mouse as fire-control.

On a regular basis, in a random fashion
One of the direction keys gets locked, effectively locking the robot to go one way only.

I have seen no pattern of one direction more often than the other
I have seen no pattern of when the problem occurs 

I am new to Wine and still relatively new to Linux.

HELP !?!



ADDENDUM:

The following lines appeared in the Terminal window for the most recent keyboard fail..
------------------------------------------
XXX@YYY:~$ wine "C:/Robokill/Robokill2/Robokill2.exe"
err: pulse: pulse_contextcallback Context failed: Connection refused
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: semi-stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: semi-stub!
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: semi-stub!
------------------------------------------

The first line is the command I use to start it
The second line appears to be some bad connection to pulse_audio. But I am not having any trouble with the sound coming through.
It is lines 3-5 that are worrisome.

---

