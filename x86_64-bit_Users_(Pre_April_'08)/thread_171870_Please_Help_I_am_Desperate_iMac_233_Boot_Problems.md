---
title: "Please Help I am Desperate iMac 233 Boot Problems"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by bgolden12345 on 2006-05-07
I have a rev b iMac Bondi 233 w/96MB Ram.  I have just installed a new 80GB hard drive.  When I run the install I take the recommendations on hard drive partition, the install runs fine until the reboot.  When the computer goes to reboot it reboots to a Folder w/?.  I know that this means the mac can't find a bootable partition.  I am at a loss here, I have reinstalled 3 times with same result.  Trying to run 5.10 any help would be greatly appreciated.  Thanks in adavance.

Billy

---

### Post by kingred on 2006-05-08
i managed to boot mine using a hoary install disk and then apt-upgrading when i finally managed to boot.

i know it sounds funny but ALWAYS keep a hard drive with hoary installed on it as my breezy installation always seems to botch whenever i update.

could be the old hardware i dont know...

currently running all original tray loading 233mhz imac, 64mb ram, original 4gb hard drive on xcfe ubuntu linux :)

---

### Post by oswaldkelso on 2006-05-08
If you cant find the system on startup and you have just replaced the hard drive check if the hard drive is set to master, it maybe  slave or  cable select. (master or cs usually work but check with maker)
Also the imac 233 can only see 8 gb on the first partition [http://ubuntuforums.org/showthread.php?t=108266&highlight=oswald](http://ubuntuforums.org/showthread.php?t=108266&highlight=oswald)

---

### Post by Theo-Ubu on 2006-05-08
Hey there,

I feel your pain.  I am trying to do the same exact thing.   At first I had bad problems with even getting an install CD to work, then I tried burning the CD at a much slower rate and then the install finally worked just today.   It went all the way through to the "ejecting CD and rebooting" stage.  I was excited for a test drive, but when it rebooted, it came to the blinking folder and question-mark like you hare having.

I suspect very much that 5.10 is not writing to the main boot record correctly and there is something fishy going on with how the mac system boots and finds the boot recored of the HD.  I installed about 96Mb of RAM, and upgraded my HD to a 9Gig also.

Anyway, I'm trying to find some info on "zapping the PRAM" which seems to be  a common catch-all fix when you were installing or upgrading older MAC-OS's, but I'm a bit afraid to try it right now.

Does anybody out there know what kind of info besides video settings the PRAM holds?  Does it hold boot-up information also?

Help us please!!   Seems like it could be such a beautiful solution to run linux on these old machines..

Thanks in Advance....

---

### Post by 3rdalbum on 2006-05-09
Boot-up information is held in the NV-RAM, not the PRAM. If you've got a Mac OS startup CD, you can start up off that to set the NV-RAM back to your Mac partition. Otherwise, hold down "Command-Option-N-V" to reset it.

Then you can try starting up Yaboot manually. Hold down Command-Option-O-F while starting up, and you'll be taken to the OpenFirmware interpreter. Type:

```
boot hd:*x*,yaboot
```
Where *x* is the bootstrap partition number (if you don't know it, just try the numbers 1 to 13). If Yaboot starts, just hit Enter to start up Ubuntu.

---

### Post by Theo-Ubu on 2006-05-09
Thanks for the tips.  I tried that, but still nothing.

Here are some fact that hopefully might help.  On the drive, the partitioning was set up like this:

#1     32.3Kb               APPLE
#2     1.0Mb     boot     untitled
#3     7.0Gb     ext3      untitled
         2.7Gb     FREE SPACE
#4    282Mb     swap
       512.0B     FREE SPACE

I assume that #2 is where the boot is supposed to start from, but it's only 1Mb.  Is that enough for yaboot to be writtten to at install?  I couldn't adjust it any larger through the partitioning install menus.  I brought down #3 to 7Gb because I heard a rumor that these machines will not "see" more than 8Gigs of HD.   That #1 also worries me... APPLE formatted?

Any clues on all this would be much abliged.  I'm rather a greenie on linux file-systems and figuring all this out.

Thanks!

---

### Post by Peter76 on 2006-05-10
I had a problem once that the 'bootable' flag was not set on the yaboot partition. I think I solved this by going through the installer again, till the disk partitioner; set the bootable flag to on and leave other partitions as they are, and then reboot.

---

