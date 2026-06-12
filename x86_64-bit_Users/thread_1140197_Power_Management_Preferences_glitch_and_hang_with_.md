---
title: "Power Management Preferences glitch and hang with 9.04 &amp; 8.10"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by Icm76 on 2009-04-27
**System:** Asus P5N7A-VM (nvidia 730i/9300) integrated graphics motherboard.


**ubuntu [COLOR="Navy"]9.04[/COLOR] + nvidia [COLOR="DarkGreen"]180[/COLOR] driver**
Opening power management from the system -> preferences menu causes the computer to hang 100% of the time. The mouse pointer moves, but nothing is selectable and the computer has to be reset via the power switch.

**ubuntu [COLOR="Navy"]9.04[/COLOR] + nvidia [COLOR="Green"]173[/COLOR] driver**
Power management will open but appears as a completely blank window. Minimising & reopening a few times gets the sleep time slider bars to appear, but nothing *appears* to work. However dragging the sliders with the mouse *does* change the setting - it just isn't visible until you minimise and reopen the window again. *[SIZE="1"]N.B. The 173 graphics driver is no good for me, lots of corruption and web pages don't show properly[/SIZE]*

**ubuntu [COLOR="Blue"]8.10[/COLOR] + nvidia [COLOR="SeaGreen"]177[/COLOR] driver**
Opening power management causes a system freeze and the sliders don't work, or the window appears blank


**QUESTION 1**
[COLOR="DarkSlateGray"]Is it possible to set the hibernate and monitor sleep times from the terminal? or from a different configuration editor?[/COLOR]
***edit:** seems the configuration editor can be used! apps -> gnome-power-manager*

**QUESTION 2**
Is it possible to install the nvidia 177 graphics driver with ubuntu 9.04? The option isn't available in the hardware drivers menu, but as 8.10 was more stable for me maybe the solution is get the slightly older graphics driver?


***Note:** apart from the power management issue, 8.10 was _very_ stable, but I'm finding 9.04 hangs occasionally. EXT4 install was very bad, but reinstalled with EXT3 and it seems better, though have still seen a couple of hangs with the nvidia 180 graphics driver*

---

### Post by knattlhuber on 2009-06-23
Had exactly the same issue on my 24" iMac 9,1 when using the v180 nVIDIA driver. After downloading and compiling the v185 driver from nvidia.com, the issue was fixed.

---

