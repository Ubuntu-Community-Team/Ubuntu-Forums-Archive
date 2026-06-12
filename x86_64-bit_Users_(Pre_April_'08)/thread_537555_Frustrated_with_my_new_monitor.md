---
title: "Frustrated with my new monitor"
date: 2007-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by tibbar_eht on 2007-08-29
I have been having issues with getting Ubuntu to load with my new monitor.  I had a working box then swaped out my monitor for a larger flat screen that had DVI inputs.  As soon as I did that my linux would not boot up any more.  I can get my windows XP 64-bit to work like a champ.  In another thread it was suggested that I edit a line in grub but I could not figure out how to edit it.  I have tried reloading using the text loader and I was able to get things loaded up to the point of rebooting and then it was the same thing.  I made sure in the new load to include the higher resolutions but that didn't seem to work.  I really don't know what to do now.  I really want to use linux but I also want to get the most out of my video card.  

Cheers

---

### Post by Kilz on 2007-08-29
> **tibbar_eht said:**
> I have been having issues with getting Ubuntu to load with my new monitor.  I had a working box then swaped out my monitor for a larger flat screen that had DVI inputs.  As soon as I did that my linux would not boot up any more.  I can get my windows XP 64-bit to work like a champ.  **In another thread it was suggested that I edit a line in grub but I could not figure out how to edit it.**  I have tried reloading using the text loader and I was able to get things loaded up to the point of rebooting and then it was the same thing.  I made sure in the new load to include the higher resolutions but that didn't seem to work.  I really don't know what to do now.  I really want to use linux but I also want to get the most out of my video card.  

Cheers

```
gksudo gedit /boot/grub/menu.lst
``` Will open up the grub menu list as an admin. You will be able to edit it , and save it.

---

### Post by Jouke74 on 2007-08-29
1. When you start your computer log into the "recovery mode" of Ubuntu.
2. At the Login prompt type your normal username [enter] and password [enter].
3. Subsequently login as root with the commando: 

    su

Type your root password.
Now type:

    dpkg-reconfigure xserver-xorg

Follow the questions, make sure that your monitor is reconfigured.
Then type:

    reboot

Now check if the screen starts to work.

If this is already done, then try the Grub stuff.

---

### Post by tibbar_eht on 2007-08-29
Ok I tried both suggestions.  I was able to get into the xserver reconfigure and made the changes that I could that should have helped but upon reboot I still could not get past OS choser.

So I next tried to edit the grub and I got an error```
(gksudo:4747): Gtk-WARNING **: cannot open display:
```

](*,)

---

### Post by John.Michael.Kane on 2007-08-29
> **tibbar_eht said:**
> Ok I tried both suggestions.  I was able to get into the xserver reconfigure and made the changes that I could that should have helped but upon reboot I still could not get past OS choser.

So I next tried to edit the grub and I got an error```
(gksudo:4747): Gtk-WARNING **: cannot open display:
```

](*,)

Try booting the machine with the lcd connected using the analog/rgb/vga input, and try rerunning Jouke74 steps. This will allow you weed out if the issue is with using the dvi or something else .

Also before doing that you may want to reverse the editing your did under grub.

As a "last" resort you can either try to do a gurb recover or a reinstall
[GRUB Recover]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub#head-778ecd20f83f92ebaa5aaec5f1b4615539c2f8d3")

---

