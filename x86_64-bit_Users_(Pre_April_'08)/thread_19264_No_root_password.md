---
title: "No root password"
date: 2005-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by speedbird on 2005-03-11
Having finaly sorted out that the ASUS A8V motherboard doesn't work with Ubuntu until you disable the onboard LAN in BIOS ( Marvell Yukon Gigabit Ethernet ) I now boot up and the login screen is just a jumble of colours. The first time I logged onto the system fine but on the second occassion this happened. To get around this I try to boot in recovery mode but this requires one to be logged on as root. This option appears to be specifically denied in this distro. Anyone any ideas how to get around this problem or what the default root password is?

---

### Post by bored2k on 2005-03-11
[QUOTE=speedbird]Having finaly sorted out that the ASUS A8V motherboard doesn't work with Ubuntu until you disable the onboard LAN in BIOS ( Marvell Yukon Gigabit Ethernet ) I now boot up and the login screen is just a jumble of colours. The first time I logged onto the system fine but on the second occassion this happened. To get around this I try to boot in recovery mode but this requires one to be logged on as root. This option appears to be specifically denied in this distro. Anyone any ideas how to get around this problem or what the default root password is?[/QUOTE]
 Ubuntu uses sudo instead of su [input your user password].
Any luck?

Another alternative: load up your install discs, and follow the steps to install, when the partition step comes up, alt ctrl f2 or f3 to load another terminal. This will log you in as root; allowing you to make any changes needed from here just in case.

---

### Post by FluffyElmo on 2005-03-13
Hello Speedbird, I think you emailed me about this problem? Sorry for the delay, I suffered a hard drive failure and am just getting back up and running. On the positive side, I have a very recent install experience to relate :? 

In short, I have no problem installing Ubuntu - AMD64 on an Asus A8V with onboard LAN enabled. If you're using Hoary, about a week ago there was an update to the k8 kernel that didn't like my LAN chip, I'm now running the current generic kernel without problems. This shouldn't affect the install, and Warty should work fine, so I'd guess your problems are BIOS or Video card related.

My BIOS version is 08.00.09, Built 12/22/04. All BIOS settings are set to the defaults with the following exceptions: SATA Boot ROM is Disabled (so it detects the SATA disk controller properly), Promise RAID Controller is Disabled (I don't use it). I did a default Warty install from the AMD64 disk, declining online updates. I then booted into Warty and did an upgrade to Hoary. 

I'm also using an antique AGP4x graphics card, so if you're using a more recent card this may be the problem. Have you tried installing the binary drivers for your card? You should be able to do it from a failsafe terminal without the GUI:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

So the good news is your motherboard should be fully Ubuntu ready. Try the graphics drivers, and if that doesn't help I can try a more recent BIOS to see if that is the problem. Good Luck!

---

### Post by GeBo on 2005-03-13
A simple option to set the root password, is to log in as a user and then on the command line type: sudo passwd root

First use your own password (for sudo)
Then you can set the password for root and confirm that.

---

