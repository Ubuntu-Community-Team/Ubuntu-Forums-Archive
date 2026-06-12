---
title: "Intel HD Audio not working in 64-bit Ubuntu 8.10"
date: 2008-12-24
forum: x86 64-bit Users
---

### Post by rodzlinux on 2008-12-24
Hello all,

For reference,  here are my specs:

M/B: Gigabyte GA EP35 DS3L BIOS revision 6a
CPU: Intel E2180 OC'd to 3.2 Ghz (Stable in windows for ~6 months)
Sound card: on-board Intel HD Audio ICH9 something or other 
Video card: MSI Geforce 8800 GTX 512 MB
RAM: 2 gigs of G.Skill F2-6400CL5D-2GBNQ
HDD: Western Digital 7K 8M SATA2 WD2500AAJS
500W PSU

I just did a fresh install of Ubuntu 8.10 64-bit on my machine and everything runs near-perfect.  Only problem is dual-booting windows (which I've almost got fixed) and no sound.  I ran the following command:

lspci -v

and it's showing my sound card as Intel HD Audio ICH9 or something along those lines.  It's the on-board sound for the Gigabyte GA-EP35 DS3L mobo.

I've searched some threads and tried uninstalling/reinstalling ALSA drivers, and even uninstalling ALSA completely and installing OSS4 drivers.  Nothing works.  I've un-installed OSS4 and am trying out the ALSA drivers again, but still no luck.

The only change I noticed was that with the OSS4 drivers, linux was telling me that I had no sound card, but when I checked which drivers I had installed, it was showing OSS4.

I've run Ubuntu from a live CD before and audio worked then.  I'm not sure if it was because I ran a 32-bit version, or even which Live CD it was.

I also just updated my BIOS to the latest beta driver.  Maybe I should try the last release revision?  I'm really at a loss.  Any help is greatly appreciated.

---

### Post by 2hot6ft2 on 2008-12-24
It's a know issue look here for the solution.
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by 2hot6ft2 on 2008-12-24
> **rodzlinux said:**
> 
I've searched some threads and tried uninstalling/reinstalling ALSA drivers, and even uninstalling ALSA completely and installing OSS4 drivers.  Nothing works.  I've un-installed OSS4 and am trying out the ALSA drivers again, but still no luck.

The only change I noticed was that with the OSS4 drivers, linux was telling me that I had no sound card, but when I checked which drivers I had installed, it was showing OSS4.


Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa [COLOR="Blue"](Before deciding to remove pulse you should read the warning here as to what the result could be)[/COLOR].
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

There are more but this gives you some alternatives that are being used.

---

