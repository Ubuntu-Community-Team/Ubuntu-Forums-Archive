---
title: "[SOLVED] Cannot boot anymore!!!"
date: 2008-12-01
forum: x86 64-bit Users
---

### Post by Tilex on 2008-12-01
Hi.

I am writing from my laptop because I suddenly cannot boot my PC (home business!!!).

I remember two things that might have caused this:

1-  When watching videos, the screen was flickering so I added a line in xorg.conf (I'd backed it up) that had to do with "[...]textures = off".  I pressed crtl+alt+backspace to restart xorg.conf (that's what I do on my laptop to switch from single to dual display) and I got a black screen.  So I rebooted, I see it loads but it goes blank again!

2-  I upgraded my system but had not rebooted since then.  So the blank screen might be caused by some update today.  Don't remember the updates though.

I'm running Kubuntu 8.10 Intrepid amd64 on a Core 2 with ATI Radeon 3450.

I have the installation CD that allows me to enter the Rescue Mode.  So I choose to be given a shell access to my / partition, but I don't know what to do.  I tried to replace my Xorg.conf but it wouldn't let me rename my "xorg.conf.bak to xorg.conf".

What should I do at this point guys??
Any help would be very appreciated!!!  My business depends on this sytem!

---

### Post by evildragon2 on 2008-12-02
Try the command:
```

sudo dpkg-reconfigure xserver-xorg
```

This will reset your xorg.conf since it seems that you messed it up. (or update did I don't know)

---

### Post by utnubuuser on 2008-12-02
And if you can't boot at all, use a live cd to access your hdd and restore your x.org file

...and did you try renaming as root?  sudo su

...also,  I used to get a blank screen in 7.10 after booting, and the only way to get anything from the monitor was with ctrl+F1, or ctrol+alt+F1 or F2, or ctrl+esc.

---

### Post by Tilex on 2008-12-02
Thanks for your answers guys!

Since I had installed the /home on another partition, I gave it a try to re-install the / partition with the installation CD.

In 10 minutes the installation was finished and I could boot in my system.  To my great surprise, everything was the same as before except for the software I'd installed system-wide that weren't there anymore.

Oh well, thanks for the help, but I'm still pretty pissed at 8.10's instability (or is it amd64 verison only ?).

Have a good day,

Alex

---

