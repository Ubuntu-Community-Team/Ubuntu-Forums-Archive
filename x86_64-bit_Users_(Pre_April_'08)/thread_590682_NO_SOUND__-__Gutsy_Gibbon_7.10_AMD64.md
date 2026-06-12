---
title: "NO SOUND  -  Gutsy Gibbon 7.10 AMD64"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by otac0n on 2007-10-25
Hey guys, what's up?

This is my first time installing Linux on my Home PC,
(I've done it at work on servers fairly infrequently...)
and I'm having real trouble getting my audio working...

I have two sound devices:
[LIST]
[*] ASUS A8N-SLI Premium (I think) on-board audio
[*] Creative Labs Sound Blaster X-FI
[/LIST]
Neither of which work.  :(

```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GT/GTO] (rev a1)
05:06.0 Multimedia audio controller: Creative Labs SB X-Fi
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```

And, so I have a few questions:
[LIST]
[*] What should I do to try to get my sound working? 
[/LIST]
Of course, I would like to use my X-Fi, but I understand there are only beta drivers for it, and I would have to downgrade my kernel...

[LIST]
[*] What are some good audio studio applications for linux?
[/LIST]
I'm currently using Audacity in Windows...

[LIST]
[*] Is the NTFS support in gutsy gibbon STABLE?
[/LIST]

And, if so,
[LIST]
[*] How do I mount directories persistently?
[/LIST]
For example mounting "C:\Documents and Settings\otac0n\Application Data\gnupg" to "~\.gnupg" etc... every time I start my system...

**THANKS in advance for the help! It is much appreciated!**

---

### Post by otac0n on 2007-10-25
Any help? My dude at work said he had to install an Intel audio driver for his onboard (same series of board)...?

---

### Post by Therion on 2007-10-26
Some quick help with getting your X-Fi working, but that's all I'm going to be good for.

First and foremost, enter you system's BIOS and disable the onboard sound.

Secondly, boot up and open the Volume Control in Gutsy.
Click on Edit and go to Preferences.
Scroll down and put a check mark in the box labeled:  Audigy Analog/Digital Output Jack.
A new tab should appear on the Volume Control panel called "Switches".
Go into that "Switches" tab and unmute the channels.

---

### Post by otac0n on 2007-10-26
:/
Audigy Analog/Digital Output doesnt show up... (I havent installed the beta drivers yet...)

I dont really want buggy sound drivers... but if I must...

---

### Post by Therion on 2007-10-26
Odd... I have the same mobo, 64bit Gutsy running and an Audigy 2ZS installed, and I certainly don't remember having to install drivers for it either.  You're SURE there's no Audigy Analog/Digital Jack thing listed?  You have scroll down for it...  <shrug>

Not sure what to tell you... 

Oh wait, yes I do.  

Check out this thread: [[COLOR="Blue"]Sound Problems Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide").  I found the section on Installing From a Fresh Kernel got me up and running but only sporadically.  Once I got turned on to the Analog/Digital Output Jack thing, that solved the problem for me permanently.

---

### Post by otac0n on 2007-10-26
thx a bunch.

---

### Post by jusmurph on 2007-10-26
Audacity is available on Linux

sudo apt-get install audacity


NTFS has been stable for years.

---

### Post by otac0n on 2007-10-26
> **jusmurph said:**
> NTFS has been stable for years.

Thanks.  now, how would I mount:

C:\Documents and Settings\otac0n\Application Data\gnupg
to
/home/otac0n/.gnupg

and
E:\Storage\Torrents
to
/home/otac0n/Torrents

EVERY time I start my system?
Regardless of If I log on or not...

---

