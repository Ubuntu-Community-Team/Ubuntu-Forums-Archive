---
title: "Disabling/uninstalling powernow"
date: 2007-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by underwog on 2007-12-14
I have a Q6600 system that was working fine until I enabled EIST in the bios (previously was disabled to insure that my OC was stable). Works fine under XP64, but ubuntu 7.10 (all updates) it gets laggy and takes forever to launch anything. I then disabled EIST in the bios and now it is no longer laggy and works just like before. Except that /proc/cpuinfo shows the CPU Mhz to be at a 6x multi (6 x 412) vice the manually set 9x multi. Even after loading all four cores to near 100% with Folding@Home, it still shows 2472Mhz vice 3708Mhz. The folding times indicate that it is in fact running at 2472Mhz. After about an hour or so /proc/cpuinfo shows that it is now running at the correct CPU freq. of 3708Mhz. I don't know the exact time it "switched," but I do know that after a couple of 8.5min frames it still was showing 2472Mhz. Searching I found this command to disable the powernow service:

Found here: [http://ubuntuforums.org/showthread.php?t=247188&highlight=uninstall+eist](http://ubuntuforums.org/showthread.php?t=247188&highlight=uninstall+eist)
"sudo /etc/init.d/powernowd stop"

However, I get the following error: "command not found"

Based on system behavior and that I fold 24x7, I don't want EIST/Powernow. I want to disable it and uninstall it. Please help me with explicit directions (fairly new to Ubuntu). Thanks.

---

### Post by underwog on 2007-12-14
After much searching I have found that most users are recommending just uninstalling it vice stopping or modifying boot files. I will be trying this command tonight:

sudo apt-get remove powernowd

---

### Post by LO Matt on 2007-12-14
You using Gnome? Try this:

```
sudo gconf-editor
```

It'll bring up alot of option to configure gnome.  Go to Apps/Gnome Power Manager

You can either try toggling the "consider nice" option or to remove scaling completely change "ondemand" to "performance"

---

### Post by nutz on 2007-12-15
> **LO Matt said:**
> You using Gnome? Try this:

```
sudo gconf-editor
```

It'll bring up alot of option to configure gnome.  Go to Apps/Gnome Power Manager

You can either try toggling the "consider nice" option or to remove scaling completely change "ondemand" to "performance"


Very cool. Thanks for sharing.

---

### Post by thebinz on 2007-12-15
if you are looking for a graphical way to change the CPU scaling to something like "on demand" "power save" or even just set the CPU to run @ "2" or "3" GHz for example then check out this page.
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/]("http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/")

You must have the CPU frequency applet enabled and run the following command: 
```
$sudo chmod +s /usr/bin/cpufreq-selector

```
but the webpage will give you more details on this. Read it.

i'm not sure if this is something you are looking for but i thought i would just give some input.

---

### Post by bobpaul on 2007-12-16
> **thebinz said:**
> 
You must have the CPU frequency applet enabled and run the following command: 


Nice! I thought I was using the same applet as I did on Gentoo. They must use setuid by default.

---

