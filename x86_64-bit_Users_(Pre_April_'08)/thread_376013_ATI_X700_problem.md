---
title: "ATI X700 problem?"
date: 2007-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ecs_pf5 on 2007-03-04
Linux newbie.

Downloaded Ubuntu 6.06.1 desktop for x64

I have:

ATI Radeon X700 graphics card
Gateway FPD1960 TFT lcd
Elitegroup ecs pf5 extreme v1.0a
FSB 1.2GHz
Dualcore intel 3.2GHz Socket 775
1 Gb 533MHz 240 pin DDR2
SATA HDD 3Gb/s 80Gb

I put in the CD and it goes to the boot menu just fine.
Run option 1, 'install or run from CD', fails trying to start X.

"Fatal Server error: no screens found" (I press ok) "The X server i now disabled.  Restart GDM when it is configured correctly."

Tried changing the driver from "default" to "vesa" in /etc/X11/xorg.cong, (a tip I found searching google) - no luck. Although the behaviour did change, the screen now goes black.. and stays that way.

The boot: prompt referred-to on the initial screen's f1 help is nowhere to be seen when running the CD. Is it hidden somewhere? (I did find a post that suggested it has been removed without updating the help)

I had hoped to type 'live-expert' at the boot: prompt, as I had read that that would let me manually specify graphics details whilst autodetecting all else.

There is an 'f6' options box, I tried entering live-expert in there a few times in different manners to try manually specifying graphics details, but didn't seem to have any luck.

Any suggestions? I am a bit lost now, thanks for any help.

---

### Post by ffxr on 2007-03-04
trry this:
[http://ubuntuforums.org/showpost.php?p=2239112&postcount=2](http://ubuntuforums.org/showpost.php?p=2239112&postcount=2)

---

### Post by ecs_pf5 on 2007-03-04
I haven't actually gotten it installed to disk as yet - I can't get it to boot fully into the X server off the live CD. The most I've been able to do is boot to a command line and use vi a bit to edit a copy of xorg.conf which I'm assuming is held in memory?

So I'm figuring there's nothing on disk to 'save' between boots.

The machine's got a one-partition copy of Windows Vista on it at the moment, so really I'm just exploring Ubuntu at this stage.. but as a beginner can't really see what I'm doing without X!




[edit]

Went and gave it a go, nearly worked.. got as far as specifying the colour depth, but then it gave an error "possibly overwriting reconfigured data, backing up to blah" or words to that effect (because it was writing to RAM not disk?)

Tried startx but it just crashed out to the same blue text screen and error as before, then.

One thing I was unsure of was the card bus identifier, I just accepted the default of PCI:1:0:0.. just discovered I can use scanpci for that. & it looks like 1:0:0 is ok

Or should I do a hard disk install (and try sudo dpkg-reconfigure xserver-xorg again) - if so how would I approach that given that I don't seem to be able to get to any other interface on the live CD, than the command line..


[final edit] looks like I'm not going to have any joy with the live cd on this machine, I'll try installing it to the disk.

---

### Post by ffxr on 2007-03-04
u can install from a text driven system if u use thew alternate cd..

---

### Post by ecs_pf5 on 2007-03-04
Sound, I'll give it a shot :)

---

### Post by ravenon on 2007-03-04
I also have a X700 on a Radeon Xpress 200 chipset. No live CD has ever worked on this machine save ones which have the proprietary drivers built in.
For Ubuntu, I install from the alternative CD, it will set up xorg.conf with the open source ati driver and the graphics card does not work. Boot to recovery mode and then run
apt-get install xorg-driver-fglrx

You will need the alternative CD for this.

Then run
dpkg-reconfigure xserver-xorg

and choose the fglrx driver.

---

### Post by ecs_pf5 on 2007-03-05
Cheers Ravenon. Will attempt that.

Last night I tried Kubuntu (had a little experience of KDE from Knoppix a couple of years ago), alternate CD &, no joy.

Tried the 64-bit live Ubuntu CD again. No joy.

Then on a whim, tried the 32-bit live Ubuntu CD - yay, worked. I let it go to the X server failure screen (command text on blue background), dropped back to a command prompt, and did sudo vi xorg.conf in /etc/X11/ to edit "ati" to "vesa" in the ATI card section.

After that, startx brought up the GUI just fine & allowed me to install fully from the CD & reboot into a HDD install just fine.

But that's no good, would like to get the 64-bit CD on there! At lest it is some kind of success and does at least verify it's possible to get this darned videocard to work.

So I am reinstalling Vista to partition 2 of 2 as I write, will then try and use the Ubuntu alternate 64-bit LTS to install Ubuntu to partition 1, do what Ravenon says, then edit grub's menu.lst to recognise both. I hope that sounds sensible.

Cheers for your help guys, Windows boy here appreciates it ;)

---

### Post by ecs_pf5 on 2007-03-05
And here I am, posting from Firefox in Ubuntu x64 \\:D/ 

I did use fglrx, had a slight problem with out-of-range monitor frequency at first but I ran dpkg-reconfigure xserver-xorg again with slightly different responses and that fixed it.

Good to see OpenGL mentioned in the modules list, as I'd like to try running the flightgear flightsim at some point.

Big thanks for helping me get up & running.

---

