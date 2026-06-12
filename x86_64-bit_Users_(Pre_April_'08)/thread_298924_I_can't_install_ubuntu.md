---
title: "I can't install ubuntu"
date: 2006-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by klonner on 2006-11-13
first sorry, I can't speak english very vell.


I have a problem when I try to intall edgy on my computer. When live CD has been started, in  few moments, the screen desapears, and my monitor say "frequency unsuported". 


My Computer is AMD 64 bits +3500, Mother board Asus AV8 Deluxe, grafics, Ati 9600 series (AGP),512 Mb ram, 2 sata disks (70 & 120 gb)monitor Acer TFT 15"

what must I do?

PD: older versions(32 bits)I could install it witout problem.

---

### Post by earobinson on 2006-11-13
you can report this as a bug, or install the 32 bit version then manualy update the kernel after install (second option is probaly not a good one it could be hard)

---

### Post by klonner on 2006-11-14
I try it ubuntu 32bit, and kubuntu 64, and happens the same, the latest version that I used was 5.10 

How happens it??](*,) 

Help me:(

---

### Post by kuja on 2006-11-14
It could be a video driver issue, maybe. I recommend installing with the alternate cd, and after the install, editing this file: /etc/X11/xorg.conf

In this file, look for a section like this:
> 
Section "Device"
    Identifier     "MSI GeForce 7900GTX"
    Driver         "nvidia"
EndSection

The specific card will of course differ, but the idea is the same. There are three non-proprietary drivers that work with ati radeon cards, and they are: ati, radeon, vesa.

It will likely default to ati, try changing it to radeon, save, and restart. If this doesn't solve the issue, then try changing it to vesa, and restart. Let me know if these things don't fix it, I do have other ideas.

---

### Post by klonner on 2006-11-16
after install Alternate CD with firts option, how can I edit this file?? afer the sceen with logo, while system is charging, appears "frequency unsuported"

What must I do?

Thanks

---

### Post by kuja on 2006-11-16
Try booting into recovery mode. You can edit the file from there with the command:
```
sudo nano /etc/X11/xorg.conf
```
You can save with ctrl+o, and quit with ctrl+x.

---

### Post by klonner on 2006-11-17
the folder x11 (in etc) doesn't exist, and the config file xorg.conf, doesn't exist too  :confused:

---

### Post by RFScheer on 2006-11-17
The folder is /etc/X11 and the file to edit is xorg.conf.

The "X" in X11 is capitalized.

---

