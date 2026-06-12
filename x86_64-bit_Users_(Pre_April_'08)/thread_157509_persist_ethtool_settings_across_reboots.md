---
title: "persist ethtool settings across reboots"
date: 2006-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by xwing on 2006-04-09
Hi, I've managed to get Dapper Flight 6 up and running. I've also got the official NFORCE drivers working (nvnet and nvsound modules)

I'm sharing a network connection at home, and since the ethernet cable is a tad long, my desktop doesn't work > 10Mbps although it is really a gigabit capable card. That aside, I've managed to figure out that the command:

```
$ sudo ethtool -s eth0 speed 10 duplex full autoneg off port mii
``` followed by
```
$ sudo dhclient
``` 
will do the job. The problem is, I have to do these 2 steps each time I reboot as Dapper "forgets" the settings.

Could someone guide me as to how these settings could be persisted?

---

### Post by Bjoern E Braathen Haaland on 2006-04-09
[QUOTE=Jussi Kukkonen]
--------------------
Originally posted by Sami Merchi:
Okay, I figured out how to hash out the mousewheel and thumb button so they work, but in order for them to work, I will always need to run a command at startup. Does Linux have a file like Amiga's startup-sequence where I can put cli commands that auto-execute at boot?
--------------------
Open System/Preferences/Sessions, add your command in the Startup commands tab. 

If you want to learn more about linux startup stuff, check out /etc/init.d/* (which contains the startup scripts) and /etc/rc?.d/* (One directory per runlevel. Directories contain links to the actual scripts). 

And no, writing to NTFS is not possible (not safely anyway).[/QUOTE]
[Here](http://ubuntuforums.org/showthread.php?t=75854&highlight=boot+autorun+terminal) is the original thread.

Hope this helps :;)

---

### Post by xwing on 2006-04-10
:-kHmm...ok so i need to write an initscript that will set this during boot. Is there anything I should take care of, or can I simply create a new script with the 2 commands in there one after another, and reference them within /etc/rc2.d/NNSetupETH0 ? Pardon me if this sounds absurd...never written an init script before...](*,)

---

