---
title: "adding an AMD64 kernel to a normal i386 xubuntu"
date: 2007-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by tetrafuran on 2007-12-27
Is it possible to add an AMD64 kernel to a regular i386 installation? This way I could boot to with a 64 bit kernel when I wish to use that extra power for some seriously high-res image manipulation. On other days I would like to enjoy the use of a normal i386 system.

**Why? Here's the long story.**
I have used AMD64 ubuntu 8 months, but things got a little messed up. It's time for a clean re-install. During my first dive in the linux world I ran accross several little issues that would be easily avoided had I just installed the normal i386 version in the first place. Stubbornly i marched on and solved most of them. It took a lot of reading and patience. Now I have run into a dead end and it's time to do something better this time. I have realized that the benefits of using a 64 bit OS are a bit theoretical during most days. I read an article about this. In it the difference was actually measured and the greatest advantage was achieved in image manipulationd and that benefit was around 20% increase in speed. Not much IMO. Other branches of computing got even smaller benefits. Fortunately I happen to use GIMP quite a bit. However it's quite unfortunate that i386 would have been the better choise for a newbie like me.

---

### Post by mihaiv on 2007-12-27
Probably you can load an amd64 kernel but the system will halt after the kernel load. On your system all applications are compiled for i386. They don't work when the processor works on 64 bits mode.

---

### Post by Victormd on 2007-12-27
I did the same as Tetrafuran and am now, as I type, installing the 32bit version. I too had to go through a lot to get my system running smooth... and all of the sudden, something happened (of course, probably my fault) and I had to format... I didn't really see any benefits in having the 64bit version, except for a slower boot up time (so I've read on a forum somewhere)... Let's see how the 32bit ubuntu goes!

---

### Post by tetrafuran on 2007-12-28
> **mihaiv said:**
> Probably you can load an amd64 kernel but the system will halt after the kernel load. On your system all applications are compiled for i386. They don't work when the processor works on 64 bits mode.

That's what I feared. Perhaps this could be solved by using a dual boot ubuntu. I reason that if it's possible to make two windows versions or linux and windows fit in one computer why not two linux OSs.

---

### Post by Kilz on 2007-12-28
> **mihaiv said:**
> Probably you can load an amd64 kernel but the system will halt after the kernel load. On your system all applications are compiled for i386. They don't work when the processor works on 64 bits mode.

Actually, it is theoretically possible. But its a lot of work for nothing. The reason is that the kernel then only run in 32bit mode. It wont be able to run 64bit applications because it wont have the 64bit libraries, and adding them is way more manual work than any human wants to do. You may as well just run the 32bit install, same difference.

---

### Post by argie on 2007-12-30
Just dual boot Ubuntu x86 and Ubuntu x86_64 and then remove everything but GIMP from the latter. It shouldn't be too hard to do that.

---

### Post by Kilz on 2007-12-30
> **argie said:**
> Just dual boot Ubuntu x86 and Ubuntu x86_64 and then remove everything but GIMP from the latter. It shouldn't be too hard to do that.

I ddint really read the first post in this topic all that well. Your post has made me read it again. Why because what your suggesting is a huge waste of time and space.

tetrafuran is looking for a magic cure all. They must thinking that there is a perfect , no setup linux.  The animal doesnt exist. All versions of linux need some setup. They all have some minor issues the user must solve. This is because its installed by the user. If it were pre installed like Windows the computer manufacturer would solve them. Anyone who thinks that the 32bit version is perfect and needs no setup better open their eyes and read the rest of the forum. Its full of people with 32bit issues. Thousands of posts daily.

---

