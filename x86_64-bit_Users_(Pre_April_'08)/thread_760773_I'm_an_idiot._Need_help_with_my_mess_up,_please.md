---
title: "I'm an idiot. Need help with my mess up, please?"
date: 2008-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by xakh on 2008-04-20
Okay, I tried to install some restricted drivers, for my Atheros wireless. I accidentally installed the server edition, and now my laptop boots to the server edition of ubuntu, and I have to change it to boot from the other version every time I turn on the computer, or else sound doesn't work. Someone help?

---

### Post by J-raff on 2008-04-20
Did you mean you installed the server edition of ubuntu or the atheros drivers? If its ubuntu you need and you have internet access try "sudo apt-get install ubuntu-dektop" (w/o quotes), and see if that works.

---

### Post by xakh on 2008-04-20
installed the server drivers.

---

### Post by wdaniels on 2008-04-21
Server Atheros drivers?  Do you mean the Windows Server drivers for the Atheros card via ndiswrapper?

---

### Post by xakh on 2008-04-21
I guess so.

---

### Post by flaggh on 2008-04-21
If all you want to do is change the default kernel that boots, just edit your /boot/grub/menu.lst file

```
sudo gedit /boot/grub/menu.lst
```

and rearrange the boot order in the section near the end of the file where you see something like this:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ff6ae512-5824-43ca-9008-8811436e9355 ro 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

---

### Post by wdaniels on 2008-04-21
OK, sorry, I think I understand what you meant now. If you just want to remove the server kernel, try:

```
sudo apt-get remove 'linux-image.*.server'
```

(after booting into the desktop one)

---

