---
title: "Startup problems"
date: 2006-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonttix on 2006-05-25
When I startup ubuntu it all looks fine until i should write my user name and password, the only thing I can see is a white picture. I have tryed writing my user name and password anyway, and when I have done that the intro music starts but nothing happends to the picture. I have a Acer 5024WLMi with a Ati x700 graphics card. Can somebody help mee please?

---

### Post by simonn on 2006-05-25
Can you paste your /etc/X11/xorg.conf here?

Instead of typing in your user id password as above, press CTRL + ALT + F1.

This should bring up a terminal.

Log into this using your your user id and password and copy aforementioned file to a floppy or usbstick etc etc. You should then be able to read it on another PC and post here. (You will probably need to use wordpad if using windows).

---

### Post by Ribs on 2006-05-25
It looks to me that your graphical driver has issues.

I can't help with that, but I can help you change to the generic 'vesa' driver which you can use in the mean time until your ATI driver is fixed.

Once the machine boots, go into a virtual terminal with Ctrl + Alt + F1 key combination. Log in. Now do:
sudo nano -w /etc/X11/xorg.conf
It will ask for your password again. This is normal.

This file is for your "X11 server" configuration. It controls drawing stuff to your graphics card. You need to find the part which tells it to use your ATI card, and change that to. I don't have a ATI card, but the section should be similar to mine. On my system, it looks like this:
Section "Device"
        Identifier      "NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
        Driver          "nvidia"
You need to change the Driver part to read "vesa". On my system, it will look like this:
Section "Device"
        Identifier      "NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
        Driver          "vesa"
Once you've done that, press Ctrl + X. You will get the following appear at the bottom:
Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?
Press y, then enter. This will save the modified file.

Now do:
sudo /etc/init.d/gdm restart
This will make the changes take affect, and you should be able to login now. This will at least get you to a usable (but ugly) setup where you can run firefox and find out what the problem is :) Remember you'll need to change the driver back from vesa to whatever it was before once you've figured it out.

Good luck.

---

### Post by jonttix on 2006-05-25
how doo I copy the file too my usb stick?

---

### Post by jonttix on 2006-05-25
Ribs

It worked when i did what you told!
Thank you!!

---

### Post by Ribs on 2006-05-25
Glad that helped.

But remember, you need to fix your ATI driver, as the vesa driver is very very slow in comparison and you'll loose 3D accerlation. I can't help you with that, as I use NVidia stuff... Good luck!

---

