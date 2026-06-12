---
title: "Can't save Nvidia settings"
date: 2009-11-17
forum: x86 64-bit Users
---

### Post by Gleem1 on 2009-11-17
I can't save any changes I make through nvidia-settings. I always receive this error. Yes I am trying to run through sudo. I've tried gksudo as well.

"Failed to parse existing X config file '/etc/X11/xorg.conf'!"

Because I can't change that file I can never change my video settings.

Any help is appreciated.

Card 2X Nvidia 8500GTs
driver NVidia accelerated graphics driver (version 185)
installed through Hardware Drivers

(Note: the changes I'm trying to make are to disable the video outputs on my 2nd graphics card which is being viewed as a primary graphics card)

*Edit* I noticed this in the terminal

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

---

### Post by Bonster on 2009-11-17
yea use sudo for nvidia settings but also delete or rename the old xorg.conf to something else 1st. then u can save

---

### Post by Confuzius on 2009-11-17
Try running "sudo nvidia-config" in the terminal first, this will give you nvidia's default xorg.conf to use as a starting point before using "gksudo nvidia-settings"

---

### Post by realzippy on 2009-11-17
> **Bonster said:**
> yea use sudo for nvidia settings but also delete or rename the old xorg.conf to something else 1st. then u can save

Always use gksudo instead of sudo when launching gui apps.
But,Bonster is right,you have to delete existing xorg.conf:

**sudo rm /etc/X11/xorg.conf**

then run :

**sudo nvidia-xonfig**    to create new xorg file

Log out/in to load new one,then edit settings.

**gksudo nvidia-settings**

---

### Post by Gleem1 on 2009-11-17
Thanks everyone, I have everything working. My one question, how can I change my primary monitor from my CRT to my LCD (VGA and DVI respectively)

---

### Post by realzippy on 2009-11-17
Could that not be done in nvidia-settings?

---

### Post by Gleem1 on 2009-11-17
Not that I could tell, no. It's not a big deal though. For the most part the two monitors act independently of each other, unlike under a Microsoft OS. The only real annoyance is putting in my password on my second monitor when logging into Ubuntu.

---

### Post by realzippy on 2009-11-17
Have a look at *xrandr* then:

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

### Post by HappyFeet on 2009-11-17
> **Gleem1 said:**
> Thanks everyone, I have everything working. My one question, how can I change my primary monitor from my CRT to my LCD (VGA and DVI respectively)

In nvidia-settings, go to x server display configuration to do that.

---

