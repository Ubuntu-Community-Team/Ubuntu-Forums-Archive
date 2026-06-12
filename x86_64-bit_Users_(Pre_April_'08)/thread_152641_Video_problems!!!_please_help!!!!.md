---
title: "Video problems!!! please help!!!!"
date: 2006-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by hewlett2002000 on 2006-03-30
ok, i installed ubuntu 5.10 64-bit on my pc and everything went smoothly, im dual bootong windows XP pro and ubuntu. boot loader works fine, will boot to windows, and will also boot to ubuntu and after it loads everything and brings up the desktop, i cant see the screen, its just a yellow color. i cant see the mouse or nothing. i think it is the drivers for the video card. i am fairly new to linux. the specs on my computer as follows.  asus A8N-SLi deluxe, AMD Athlon 64 X2 4200,  PNY GeForce 6800GS 256mbDDR3, 1gig ram, dvd rom, DVD-RW CD-RW combo drive. just finished building it not to long ago. please help.

---

### Post by Flanker35M on 2006-03-30
S!

 I am try to give some pointers that MIGHT help, try them out and see...

 First of all update to latest BIOS, I think 1016 is the last official one. Then disable ALL devices from BIOS that you do not use, like COM ports, printer port etc. I think most devices are USB these days :) Less devices Ubuntu has to see the safer I think, for starters.

 I installed Ubuntu on a partition of it's own and the grub to MBR where windows resides. No glitches so far! In ubuntu I just updated the kernel to the supported (restricted) K8-SMP and voila, both CPU's are shown in system monitor. 

 Sorry my less than expert writing, but this is the way I got the system up and my system is very similar to yours except the graphics card being 7800GT and more RAM. Welcome to linux..there's no turning back!

---

### Post by Mr Darcy on 2006-05-02
Try this thread;
[http://www.ubuntuforums.org/showthread.php?t=138417&highlight=6800gs](http://www.ubuntuforums.org/showthread.php?t=138417&highlight=6800gs)
The nv driver that breezy installs by default doesn't like the GS.

---

### Post by smiley2billion on 2006-05-02
Nope,  the 6800GS does not play well at all with Ubuntu.  I went through this last night, as I have nearly EXACTLY the same setup. (X2 4400+, and an eVGA 6800 GS OC)

When whatever screen comes up (yellow boxes, crazy lines, general chaos) hit Ctrl+Alt+F6

This will kick you out to a command shell.  Log in if necessary with your normal login name, then this at the prompt:

sudo nano /etc/X11/xorg.conf

That command will open up your configuration file for x in nano (a simple text file editing program).  Find the information about your video card in there (might have to scroll down a bit) and look for the line that says:

Driver           "nv"

Change that nv to vesa then hit ctrl+x to save the file and hit yes to overwrite the existing xorg.conf file.  Then restart your machine and welcome to Ubuntu.  As for installing new nvidia drivers and getting 3d support, well I haven't gotten that far yet and plan to tackle it tonight.

---

