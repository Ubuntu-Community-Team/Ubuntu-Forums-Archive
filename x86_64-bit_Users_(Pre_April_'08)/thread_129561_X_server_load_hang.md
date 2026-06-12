---
title: "X server load hang"
date: 2006-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by friends on 2006-02-14
I have recently installed Ubuntu 5.10 on my AMD64 machine, with nVidia SLI graphics cards, 1024mb RAM.

The install goes fine, I am prompted to reboot and it displays the normal boot screen, etc. It then "copies the remaining packages" to my hard drive, and everything is OK, until it tries to start up X Server and display the login screen (I read the install support guide and it said that that was what it would do next).

What happens now is the screen goes blank except for a flashing _ at the top left hand corner that stops flashing after a few seconds. I can't type anything in or anything like that.

I don't really know whats wrong with it, but i think its probably my graphics card. I have tried to boot into recovery mode and install from the command line but i seem to not have the nvidia-glx package or whatever it is, and when i configure my x server's graphics settings, that doesnt change anything.

I have a triple partition setup, one NTFS for windows, one for files and a third ext3 for linux. I am fairly new to linux, having only used it on my dad's laptop a very long time ago before he switched to OS X, but I am familiar with the sorts of things like command lines, environment variables, etc that i would need to use in linux.

Thanks to anyone who can help me in this, and sorry if there is a really simple solution that I just haven't found, although i have searched the archives relatively well.

Thanks again.

---

### Post by uniko on 2006-02-14
Try changing the driver bit xorg.conf  (/etc/X11/xorg.conf) to vesa instead of whatever there is at the moment (I'm guessing it's either nv or nvidia). 

You can try pressing ALT+F1 after the hang to see if you can login using console if you don't want to use rescue mode. 

After you've changed that, type: startx 

This time you should at least see some error messages if it doesn't start.

---

### Post by friends on 2006-02-17
ok, thanks for this. I have tried setting some sort of setting to vesa, but this was in a gui interface thing so i'll try the text file and then get back to you

---

### Post by skwerl530 on 2006-09-25
I have the exact same problem.  I have tried the normal install as well as the alternate install.  I will try setting the driver to "vesa" from nv.

---

