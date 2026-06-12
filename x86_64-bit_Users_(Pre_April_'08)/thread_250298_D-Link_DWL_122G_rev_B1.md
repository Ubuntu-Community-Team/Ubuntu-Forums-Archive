---
title: "D-Link DWL 122G rev B1"
date: 2006-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Henry Rayker on 2006-09-03
I had this usb dongle working just fine in Breezy, but after upgrading to Dapper, it is all screwed up.

First, when I insert the usb stick into the drive, it registers as a rausb0. If I try to configure it, sometimes I will just have no essids that I can connect to and other times, I will recieve a hard lock of my system, and nothing, short of a reset, will bring it back around.

I tried blacklisting the rt2500 and rt2570 drivers, which caused the rausb0 to be detected, and then using ndiswrapper, like I did in Breezy, but to no avail. I can modprobe ndiswrapper all I like, but I can't seem to get wlan0 to come up, regardless of what I do.

Any suggestions? Anyone have this actually working?

After digging a little, I realized my driver isn't a 64bit driver.. Do I need the 64bit in order to get it working okay? Any ideas where I might find it?

EDIT!
Alright, I did a lot of things, but I think the best thing to do is install the ralink drivers for amd64 package in synaptic, then also install the ralink utility in synaptic. Restart the machine, and run 
sudo rutilt

After some fiddling (if I run rutilt without sudo priviledge, it won't take my root password, and also WEP doesn't seem to work at all) I got a connection. I had to use DHCP in order to activate the dongle (despite using static assignments on my router end).

Point is, I got it solved, after a LOT of work.

Now, if there is a way to force rutilt to autostart (and stay in the tray) I would love to hear about it.

---

