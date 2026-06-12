---
title: "Ubuntu 5.10 on iMac G3/700 (snow) really slow"
date: 2006-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by limey on 2006-01-10
Hello,

have installed Ubuntu in dualboot with OS X on my old iMac (2001). (G3 700 512 ram) Installation went fine but the login in gnome (graphical modus) is really slow. The login screen freezes for several minutes and and I am able to log into gnome. Within gnome the same!!! :-(

Mouse and Keyboard are very slow. Cannot even do the updates or open a console. Have tried to reconfigure the xfree86 as follows but this package doesnt seem to be installed. 

dpkg-reconfigure xserver-xfree86

Maybe you can submit a newbie instruction for changing the resolution or other things to fasten up the ubuntu in graphical mode 

Also during boot the resolution? is not good. I dont see the first 3-4 numbers and letters on the left side. In Gnome I can not see the full desktop. Some part are cut on both sides. The imac does't have manual resolution change.
(sorry because of my bad english) 

I am a newbie to linux and need some help. 

How can I configure the right resoution and have a not so slow system.

Btw: I have configured a swap with approx. 500 MB as my memory is 512 mb RAM.

Ubuntu looks very good but the performance is really bad!!!

I have had installed ubuntu on an intel pIII as I wanted to eliminate windows from my home use and this has been really fast. 
 
Thanks a lot!

---

### Post by Qrk on 2006-01-10
Ubuntu uses x.org,

sudo dpkg-reconfigure xserver-xorg


An improperly configured xorg can cause those performance problems. I had similiar problems on my desktop (not nearly as slow, but its a faster computer) and changing drivers in xorg cleared everything up.

---

### Post by linear on 2006-01-10
Try disabling dri in xorg.conf. While you're in there, have a look at the resolution and horizontal/vertical frequency settings to see if they make sense.

Since you say you're new to Linux:

1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome

To disable dri, put a hash mark (#) at the beginning of the line containing "load dri" (in the modules section).

---

### Post by racymind on 2006-01-11
A few days ago I installed Kubuntu Breezy on my iMac G3 350 w/ 192 meg memory.  Deleting the DRI module in xorg really helped a great deal.  I'm surfing wireless now, very acceptable performance for most things.

---

### Post by limey on 2006-01-11
Thanks a lot for kind help! 

I will try your suggestions.

---

### Post by Thirsteh on 2006-01-11
I recommend installing the 'xubuntu-desktop' package, logging out and switching to "Xfce session" (Xubuntu) if you have a low-end computer. Very pleasing desktop and runs smooth on older hardware.

---

### Post by limey on 2006-01-11
reconfigured xorg, dri hashed, perfekt! 

Just the desktop is a little bigger than my physical screen! Hopefully I can set it up that it fits!?

keyboard and mouse are now incredible faster! login in ultra fast, incredible! very fast linux system!

---

### Post by schmigz on 2006-03-17
I have an iMac 400 and 500 and needed to perform this fix also.  I could not even login on either as it would just freeze after typing my password.  Once I made the change, everything is perfect.  Thanks.

---

