---
title: "Can someone with a working Ubuntu Gutsy AMD64 with a 8800GTS post their menu.lst pls"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by dnns123 on 2007-10-21
Does anyone with a 8800GTS NVidia card running AMD64 have a boot splash working?
If so, please post your menu.lst. I want to see whats wrong with mine. Ofcourse I wont copy it, but I need it for reference.

---

### Post by ubuntu dave on 2007-10-21
> **dnns123 said:**
> Does anyone with a 8800GTS NVidia card running AMD64 have a boot splash working?
If so, please post your menu.lst. I want to see whats wrong with mine. Ofcourse I wont copy it, but I need it for reference.

The boot splash problem with the x86_64 Gutsy/etc is afaik nothing to do with your gfx card and there's no way around it :neutral:

---

### Post by praxis22 on 2007-10-21
if you've got the "standard problem" of your monitor going into power save when you boot, then add *quiet* to the end of your kernel line, thus:

```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=xxxx ro quiet

```

It means you wont get a splash screen, but you can at least access GDM, and login.

---

### Post by diablo_man5666 on 2007-10-21
Most likely, your card is just having trouble displaying the Ubuntu splash screen, simply follow these steps:

1. Press escape to load the grub boot menu
2. Boot to the recovery kernel
3. Navigate to /boot/grub/
4. Type "vim menu.lst"
5. Hit the 'i' key to insert text
6. At the bottom of the file, add ```
noapic nolapic nosplash
``` to the end of the line that begins with "kernel"
7. Hit the escape key to exit insertion mode
8. Type ":wq" to save and and exit the file
9. Reboot.

The boot should now load without the splash screen.

For further explanation, check [this]("http://ubuntuforums.org/showthread.php?t=581683") thread.

Good luck.

---

### Post by dnns123 on 2007-10-23
Its really wierd. When I used fiesty, I used Startup Manager and it fixed everything. Now it doesnt. It boots up, but I really wish for the boot splash instead of waiting in front of a black screen.

---

