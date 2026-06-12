---
title: "64 bit &amp; Dual Core Question"
date: 2008-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by gubemton on 2008-02-05
I'm currently running Ubuntu 7.10 32-bit on a dual boot system with Windows.  My system is an AMD 64 2.80 Ghz Athlon X2, with an nVidia 8600GT.  I've read posts about Ubuntu loading in <15 seconds, but mine loads just a bit faster than Windows.  I've also read about 64 bit being faster, and that an i386 kernel doesn't use both cores, whereas a k7 kernel does?

So, this leads to the question:  Is it worth it to change to 64 bit?  If so, is there an easy way to make all my configurations stay the same, and make sure my Windows partition stays intact?  Also, does an i386 kernel take advantage of both cores, and if not, can I switch to a different kernel which does?

Thanks!

---

### Post by wieman01 on 2008-02-06
Wrong support category... Moved to "x86 64-bit Users" section.

---

### Post by NightwishFan on 2008-02-06
Check the system monitor to see if you are using both cores. I advise 64-bit, however there are some issues with java and flash (there are workarounds). There is no way (to my knowledge) to keep your current configuration. In order to get 64-bit you will have to delete your ubuntu partition and reinstall the 64-bit one. (Windows will remain intact)

---

### Post by Jouke74 on 2008-02-06
**Boot:**
I don't think the bootup will be a lot faster. The harddisk is the main bottle neck when starting up a computer. There are some tricks though. 

1. One is to add the option "profile" to your Grub kernel startup line as a startup option. This will profile your whole boot, and then place files in the right order to make them be read more quickly. Note, while profiling the boot is slower so don't leave this option at your kernel line, it's just for one boot. After profiling, during the next boot things will / might go quicker.

2. Concurrent booting allows Ubuntu to take full advantage of dual-core processors, as well as processors that hyperthread or multithread.

These settings are located in your /etc/init.d/rc file.
sudo gedit /etc/init.d/rc
Look for CONCURRENCY=none and change it to:
CONCURRENCY=shell

3.... more in the "Tutorials & tricks" section of this forum.


**For the new install of 64 bit:**

This depends a lot on your experience using linux and it depends also alot on what files and what settings you have adjusted.

You could safe most of your program configuration files that are made in your home directory. Copy the whole directory including hidden files to another disk or DVD. After the new install of the AMD64 version you can first see which files you still need. If you have installed many programs and don't use them anymore then now is the time to clean it out. Compare the old files to the new files made in your new AMD64 home directory by the system. If there are no weird things of paths being different then in many cases your can copy your old files over it. It is however often simpeler and safer to just re-configure the program! 

The same goes for many files in the /etc/ directory. E.g. sensors.conf from lm-sensors. Xorg.conf from the X-server. Copy the files and compare them with the new files of the AMD64 OS, make a backup if unsure, and overwrite the originals with your old files. This won't always work e.g. with the FSTAB Ubuntu will assign new identifiers to your disks so the old one cannot be used. So also here, only when you are sure, otherwise it is easier to reconfigure.

**8*00 Nvidia card = trouble with 64 bit install**
Your hardware has a 8*00 Nvidia video card which means you'll probably wind up with a black screen when you try to install AMD64 Ubuntu from the desktop CD. Therefore take the alternate AMD64 CD instead and use the text based install. Or, use the "nosplash" option change as been mentioned already in many earlier posts.

[http://ubuntuforums.org/showthread.php?t=687406&highlight=blank+screen](http://ubuntuforums.org/showthread.php?t=687406&highlight=blank+screen)

**Afterwards**
Use kilz install script for Flash. The rest goes almost automatically with Synaptic.

Java in a browser is a bit of an issue, here you have to choose what you want. 
I deleted the /usr/java directory and installed SUNs JRE 64 Bit version 6. Plus the 32 bit extension libraries. 
I am however not using Java enough in a Firefox to notice anything going wrong, I can run Java programs from my harddrive.

---

### Post by mmxbass on 2008-02-06
I put the blame for having to kill your settings squarely on Ubuntu itself. Putting the whole system on one giant partition has ALWAYS been a bad idea.

Next time you set up a system, let me recommend putting at least /, /boot, and /home on separate partitions.

---

