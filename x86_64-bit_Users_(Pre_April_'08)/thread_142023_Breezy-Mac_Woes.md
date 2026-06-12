---
title: "Breezy-Mac Woes"
date: 2006-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Alisdair Kelly on 2006-03-09
Well, I'm another newbie with a problem. I have a Mac Quicksilver DP800 that I am resurecting. The box has no OS installed a used WD 80gb hdd, 384mb RAM, an NVIDEA 32mb video card. I'm using a 19inch Gateway  than I have been using on a PII-450 box that runs Ubuntu 5.04. 

Here is my problem: I'm trying out one of the free/ready-made CDs as a diagnostic for the Mac. When I attempt to run the live Ubuntu CD 5.10 for Mac yaboot goes through all the configurations, I set the X-server for the lowest resolution offered, and end up with a black screen. The only thing that shows on the screen is the cursor. I think that I can rule out the monitor since it was hooked up and running a high resolution with no problems. The video card could be suspect, even though I get the happy mac face/widget on boot.

Any suggestions? Ideas on what is happening.

---

### Post by sulobanks on 2006-03-09
Have you tried higher resolutions?  A lot of times just playing with the resolutions will give you a gui.

---

### Post by spaceballl on 2006-03-09
Have you tried a dapper liveCD? one of the flight releasess? i've had better luck w/ those on macs than breezy.

---

### Post by BoneKracker on 2006-03-10
Two suggestions:

Quick fix: Pick a common resolution ( like 1024x768 ).

Better: Check the specifications for your monitor (user manual or on the web) and note what resolutions it supports.  When you reach that screen in the installation process, select those (and only those) resolutions.

If that doesn't work, here's what I'd try.  Smarter people may give you better advice or correct my stupidity:

Reboot the computer using the live CD, get to a command prompt and enter the following commands to back up your main X-windows configuration file and then edit it:

[I]cd /etc/X11
cp xorg.conf xorg.conf.old
nano -w xorg.conf
[/I]
Look for *Section "Device"*.  This should reflect your graphics card and the driver (e.g. Radeon and ATI).

Go to the "Monitors" section:
Make sure the vertical and horizontal refresh numbers match the frequency ranges for your monitor exactly.  (While my installation worked, this was automagically wrong on mine.)

Go to the "Screens" section:
There will be several "Display" subsections (for alternative color depths), each of which will list several "modes" (for alternative resolutions).  Make sure these modes match the resolutions your monitor supports. (While my installation worked, these were way out of wack on mine and limited me to below 1280x1024 or below).

Save the file with "ctrl+o" and try to reboot from your hard drive.
Documentation for xorg.conf is available on the web and I think there's a man page for it too (from command line type man *xorg.conf*.

I hope these suggestions help some and that I haven't sent you too far afield of whatever the real problem turns out to be.

---

