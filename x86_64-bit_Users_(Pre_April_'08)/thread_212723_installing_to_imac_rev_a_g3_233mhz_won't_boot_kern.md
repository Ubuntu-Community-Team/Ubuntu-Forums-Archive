---
title: "installing to imac rev a g3 233mhz won't boot kernel"
date: 2006-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by yeeking on 2006-07-10
Hi there

I am having trouble booting the 6.06 Ubuntu installer CD (as well as debian stable/ etch) on my imac 233 g3. The ubuntu installer fires up, I type install (or install video=ofonly) but then it fails, saying

  Can't read Elf e_ident/e_type/e_machine info

Any ideas?

Thanks for any clues...

- matthew

---

### Post by john_spiral on 2006-07-10
basic question: you using power pc CD?

---

### Post by namaui on 2006-07-11
he is using a ppc cd, if he wasnt it wouldnt even get that far. besides, you really cant boot 6.06 on oldworld imacs (the early tray loading ones). i tried Xubuntu with no success also, it would boot, but then it would jump to Open Firmware for some reason. Have you tried to download the "alternate" image for older or less supported configs. Also if anyone can help me with dual booting a tray loader and 5.10, i posted a thread here: [http://www.ubuntuforums.org/showthread.php?t=210387]("http://www.ubuntuforums.org/showthread.php?t=210387")

Nick

---

### Post by john_spiral on 2006-07-12
There must be at least 10 people out there who have managed to install some version of Ubuntu on a 'imac 233 g3' machine, the knowledge is out there but the will or way to contribute isn’t

The below list seems to be under utilized:

[https://wiki.ubuntu.com/HardwareSupportMachinesDesktops](https://wiki.ubuntu.com/HardwareSupportMachinesDesktops)

Is there a central hardware database with tweaks/settings to get a machine to run ubuntu besides the one above?

---

### Post by linear on 2006-07-12
Have you tried the alternate install CD? (Works better for some people on some machines.)

Have you tried the Breezy live CD?

---

### Post by mrtrblmkr1 on 2006-07-14
i'm currently using the xubuntu 6.06 livecd
and reach a point where kernel and all boot
fine, but when it comes time to show the desktop,
my monitor completely blanks out. i'm guessing,
from the old days of windows where is a resolution
or refresh rate were set too high, the monitor
would either shut (as is what's happening to me)
or would display erratically.

are there any commands to try to have the
image load with a 'safe' resolution/freq rate?

---

### Post by mrtrblmkr1 on 2006-07-14
[COLOR="Red"]I HAVE ACHIEVED SEMI-ENLIGHTENMENT![/COLOR]

using the Xubuntu 6.06 LiveCD
on a Rev.A G3 233mhz iMac,
i followed this method:

-power iMac
-hold down C key as with a regular Mac OS disk
-wait for xubuntu text to appear, when "Boot:"
appears, press enter.
-when the entire process completes and the
screen sets to black/off with the power button
sporting an orange tint, click the Control+Option+F1
keys.
-type in:

[SIZE="1"]**sudo pico /etc/X11/xorg.conf**[/SIZE]

-edit:
place a hash before Load "DRI"
[SIZE="1"][B]
       Section "Modules"
#      Load "DRI"[/B][/SIZE]

change horiz and vert like so
[SIZE="1"][B]Section "Monitor"
[INDENT]           Identifier   "General Monitor"
           Option       "DPMS"
           HorizSync    60-60
           VertRefresh  43-117[/INDENT]
EndSection[/B][/SIZE]

-click Control+X to quit, Y to save, and then press enter
-restart X

[SIZE="1"][B]sudo killall gdm
sudo /etc/init.d/gdm start[/B][/SIZE]

-enjoy in temporary gloriness

i'm still trying to work on the resolution,
but this for me alone sent me into shock. you know
us geeks. anywhew, hope someone can pick up from
here! and thanks to all those on UbuntuForums I
picked this from.:KS

---

### Post by wltrbny on 2006-08-21
On my imac rev a, I had the same blank-display problem with a xubuntu dapper live cd. The ctrl-opt-f1 fix worked for me, and i was able to boot into X, but when I installed the system, it wouldn't boot from the hard drive.  After surfing lots of forums, I discovered it had to do with how I partitioned the drive--your system must reside in the first 8 gigs of the drive. I have a streamlined and simple process for installing xubuntu on an imac rev a:

1) Download the xubuntu alternate install cd--the resource-light installer doesn't have the blank display problem discussed in this thread.

2) Manually partition your drive so that the Apple partition, the yaboot partition, the root partition and the swap all sit on the first 8 gigs of your drive.  You can create a partition on the rest of the drive--I mounted it to /home and it worked just fine.

3) Finish the install normally and boot your system!

---

