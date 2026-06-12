---
title: "PowerBook G3 &quot;Pismo&quot; tips and tricks"
date: 2006-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by jwbaker on 2006-03-09
I recently acquired a Pismo and installed OS 10.4 and Ubuntu 2005.10 thereupon.  I have a few tips, and a few questions, and would like to solicit your experiences and tips with this computer.

First, is there any way to swap the media bay device without panicking the kernel?  If I close the lid, remove the DVD drive, install the 2nd battery, then open the lid, the kernel goes into a loop.  It would be handy to be able to swap out this device without shutting down.  I guess I could manually remove the cdrom.ko module...

Some useful software that I found in the archive includes: 

laptop-mode-tools.  This handy package saves a lot of power.  Install laptop-mode-tools instead of laptop-mode, and install the version from the Dapper archive, if possible.  The Breezy version has a bug that makes the disk spin up and down continuously.  The Dapper version avoids this problem.  I found it necessary to adjust the default spindown time from 5 seconds (way too aggressive) to 60 seconds (just right).

gkrellm-pmu.  This plugin for gkrellm can show you the status of both batteries, if you have two, and uses the quite accurate method from pbbuttonsd to determine remaining discharge or charge time.

gtkpbbuttons-gnome.  Shows some graphics on the screen when you use the PowerBook's brightness, volume, and mute buttons.

xmodmap.  Obviously this handy program is always installed on an Ubuntu box.  I have the Command key and the Enter key remapped as Control.  I find this makes it easier to switch back and forth between Linux and MacOS.  For example Command-W will close a window in both operating systems with this configuration.

As far as the hardware goes, I installed a Samsung SpinPoint disk, which is nearly silent even when it's running, and spins up quickly.  I upgraded the memory to 1GB.  And I installed two batteries.  I have to say, in all seriousness, that this is the best laptop I have ever used for Linux, despite its advanced age.  The 400MHz G3 CPU is fast enough for basic tasks, Python development, listening to music, and watching movies.  The Airport reception is stellar.  With two NuPower replacement batteries installed, the battery life is an insane 15 hours.  About the only thing you could complain about is the weight, but I traded in a 12" PowerBook G4 for this Pismo, and I couldn't be happier.

---

### Post by ssam on 2006-03-09
sounds like a nice machine. 15 hours battery!

thanks for the good laptop tips.

does the dvd connect to a ide interface?
have a look in
```
man hdparm
```
it has -U and -R options to (un)register disks, but has warnings. if the drive is desinged to be hotplugable then i suppose it should work. make sure you have back ups before trying this, and unmount the device first.

---

### Post by mauijunk on 2006-08-14
JW,

  Thanks for the post, as this gave me a bit of confidence in my own pismo. I've been lookin for ways to get 10.4 on it without much luck, let alone Dapper. I'll keep pluggin away at it! Thanks again!

---

### Post by talkeetnik on 2006-10-06
Did any of you "Pismo People" get your internal modem working with dapper?
Mine works (though slow) with
5.10 "breezy" but "dapper" with latest upgrades as of
Oct '06 sees does not see it and cannot be forced to see it.

Any ideas ?

Thanks,

---

