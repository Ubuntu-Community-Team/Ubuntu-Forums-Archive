---
title: "new monitor no more booting"
date: 2007-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by tibbar_eht on 2007-07-09
I have been running 7.04 since it was beta.  I got a new monitor and am using the DVI connection with out the converter to VGA.  It is the same video card I have had since I built the computer.  I am able to boot into my windows partition and Ubuntu in safe mode but not in the normal mode.  Any idea what I need to do?

Cheers

---

### Post by jespdj on 2007-07-09
Try this: [Ubuntu Linux: How to reconfigure X windows system (X.org server)](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

---

### Post by jon.carstens on 2007-07-09
This could be the same problem I just resolved. When the Ubuntu splash screen was supposed to come up my monitor would turn off and the system would not boot.

In short I had to disable the splash screen by editing /boot/grub/menu.lst and removing "quiet splash" in this line:

```
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=ac6bc287-3721-46fb-9485-8bfe687828cb ro quiet splash vga=795
```

Here is the whole thread if you want to read through all the other changes I made: 

[http://ubuntuforums.org/showthread.php?t=493595&page=3](http://ubuntuforums.org/showthread.php?t=493595&page=3)

---

### Post by Cappy on 2007-07-09
If you get crashing on logout remove that "vga=795"

---

### Post by tibbar_eht on 2007-07-10
Thanks for the info I will let you know as soon as I get a chance to work on it.

Cheers

---

### Post by tibbar_eht on 2007-08-26
:confused:  OK I know it has been a while but between real life has kept me busy.   I have tried to edit the line.  I can't figure out how to edit it?  I have booted in "safe" mode and I can work to the /boot and I see vmlinuz-2.6.20-16-generic but I can't open it.  This is getting real frustrating.  

I have also just added a KVM and another box that I have tried to load with 32-bit 7.04 but I have simillar issues with that.  So I am guessing it is just this monitor that it does not like.

Help

---

