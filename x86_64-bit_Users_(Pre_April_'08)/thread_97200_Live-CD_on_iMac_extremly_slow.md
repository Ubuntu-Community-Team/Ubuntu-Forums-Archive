---
title: "Live-CD on iMac extremly slow"
date: 2005-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Azyx on 2005-11-30
Hi. I just get Ubuntu 5.10 CD and tried the live-cd on my iMac 500MHz 512M sdram (international)

[http://www.lowendmac.com/imacs/2001-int.html](http://www.lowendmac.com/imacs/2001-int.html)

It take a long time to start, first it's a grey field 5 cm in the upper sceen and then a very long time before It's possible to move the mouse. Then I try to open a filebroser, half off it don't open..It's not possilble to use the live-CD.

something is very wrong. Ubuntu 5.04 works fine on the same iMac.
I have tried 2 CD, so it, don't seem to be any problem with the CD.

---

### Post by Peter76 on 2005-11-30
Hi, your problems might be due to the following:
a cd is always much slower than your normal hd install, especially if you are low on ram.
Apparantly dma is off by default which slows the cd-rom down more than you are used to.
So do a normal install, if you want to try out breezy... Worked fine with me on a 900 mHz 256 MB iBook...

---

### Post by Azyx on 2005-11-30
But it´s work very well with Ubuntu 5.04 live-CD! I only say 5.04, but is also a live-CD.

It´s my two new 5.10 CDs I have problem with.

/Azyx

[QUOTE=Peter76]Hi, your problems might be due to the following:
a cd is always much slower than your normal hd install, especially if you are low on ram.
Apparantly dma is off by default which slows the cd-rom down more than you are used to.
So do a normal install, if you want to try out breezy... Worked fine with me on a 900 mHz 256 MB iBook...[/QUOTE]

---

### Post by linear on 2005-11-30
Based on other people's experience, I'm surprised you have a screen image at all.

Try this:

Edit xorg.conf to disable DRI (put a hash mark (#) at the beginning of the line).

If you don't know how to do this:

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome

---

### Post by Azyx on 2005-12-01
Is it in the end of the xorg.conf ? It don't seems to help.

When I run 'top' on the 5.04 the system use about 300MB RAM, but in 5.10 it's use everyting but about 15MB. There is not any CPU-eating process, but maybe the process get released, when I enter the terminal?

/azyx

---

### Post by linear on 2005-12-01
No, not at the end. Look under Section "Module".

Put # at the beginning of the line that reads: Load "dri"

---

### Post by Azyx on 2005-12-01
I worked. But it's not so funny to boot up with that slow thing...
I think it's possible to use alternative booth-option and change it earlier, but who do that, if they will try ubuntu?
/Azyx

---

