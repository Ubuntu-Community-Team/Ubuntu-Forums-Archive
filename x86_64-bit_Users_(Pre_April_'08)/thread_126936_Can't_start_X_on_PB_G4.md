---
title: "Can't start X on PB G4"
date: 2006-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by jlgoolsbee on 2006-02-07
Hi,

I've successfully booted Ubuntu off of an external firewire HD following the thread [here]("http://www.ubuntuforums.org/showthread.php?p=711905#post711905") and the run-through posted [here]("http://macubuntu.blogspot.com/").  The install was great, those instructions helped me out a ton, as I am somewhat of a newbie when it comes to this linux on the mac stuff.

But... I get issues when I try to start X, and I'm not sure what the cause is.  I've posted the Xorg.0.log [here]("http://s93111428.onlinehome.us/linux/Xorg.0.log").

I'm somewhat afraid this has something to do with the kernel that is supplied in the thread from above (which I used), but I really don't want to have to roll my own kernel... for some reason, it scares the crud out of me (I guess because I can never find definite answers to find out how to roll it the way I want it.)

**edit: From what I can tell, my issue has nothing to do with the kernel; rather it seems to stem from problems with the drivers it chose to use and maybe my xorg.conf... but I still wouldn't know what to change.

*****edit:** Well, after doing some digging here, there, and everywhere, I've somewhat fixed my X server issues.  Turns out during the initial install, it didn't really set up what graphics drivers to use, and after I re-ran that "sudo dpkg-reconfigure xserver-xorg" (telling it to use the nv drivers), I was finally able to start X.  Now... I can't get higher than 640x480.  I found a thread [here]("http://www.ubuntuforums.org/showthread.php?t=93719&highlight=640x480"), but that fix didn't work for me, and I'd rather not just start plugging in numbers and hope it works...

******edit:**
Solved.
[http://www.ubuntuforums.org/showthread.php?p=720306#post720306](http://www.ubuntuforums.org/showthread.php?p=720306#post720306)

---

