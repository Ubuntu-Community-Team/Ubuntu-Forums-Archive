---
title: "graphical boot problems"
date: 2006-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryan86corolla on 2006-03-08
Hey. I just installed Ubuntu on my G4 Powerbook, now I have a dual-boot with OS X. Everything is working more or less how I want it except the graphical boot screen has somehow broken. It worked fine for a while, but I must have screwed something up. Now when i boot into Ubuntu, I get the "ubuntu" graphic with the progress bar and "loading modules" underneath it, but after a few seconds it goes away and I see all of these error messages. What did I do, and how can I fix it?
> insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/bitblit.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/font.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/tileblit.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/fbcon.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/cfbcopyarea.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/cfbfillrect.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/cfgimgblt.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/softcursor.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/vgastate.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/vga16fb.ko' : no such file or directory
And then this stuff, but I think that's a different problem...?
> 
[    40.221589] usb1-1:device descriptor read/64, error -71
[    40.545727] usb1-1:device descriptor read/64, error -71
[    40.797721] usb1-1:device descriptor read/64, error -71
[    40.976719] usb1-1:device descriptor read/64, error -71
[    41.165734] usb1-1:device descriptor read/64, error -71
[    41.278731] usb1-1:device descriptor read/64, error -71

After all that, the boot processes continue from here (no graphics) with "starting RAID, setting clock," etc. Then I get to back to the graphic stuff when the login screen is ready. Everything else works fine as far as I can tell (not too far...:???:)
I am completely new to all of this, so any and all help is greatly appreciated...thanks! :)

---

### Post by felix_stegerman on 2006-03-08
Hi,

The same thing happened to my iBook G4 some time ago. I think it was related to the iBook not properly coming back up from sleep mode when having USB devices plugged in.
The problem went away after several successful "wakeups".


Felix

---

### Post by ssam on 2006-03-08
you may not need to worry about it if everything is working ok. the graphical splash screen bails out to a text boot quite easily.

is it possible that the machine was switched off while running the package manager? this might have resulted in some files being missing. opening synaptic package manager and clicking reload, mark all upgrades and apply may fix it.

---

