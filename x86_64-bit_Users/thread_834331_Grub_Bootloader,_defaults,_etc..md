---
title: "Grub Bootloader, defaults, etc."
date: 2008-06-19
forum: x86 64-bit Users
---

### Post by cinohpa on 2008-06-19
So dualbooting vista and Hardy.

I'm wondering if there's anyway to hide my vista partition. 

Also is there something in bios that will allow grub to just automatically boot ubuntu without going through the boot screen at start up every time? 

Thanks.

---

### Post by obsrv on 2008-06-19
Edir your /boot/grub/grub.conf

write:
```
nano /boot/grub/grub.conf
```

find "timeout=30"
and change 30 to 0

---

### Post by cinohpa on 2008-06-19
hmmm mysteriously, when I do that command it takes me to a blank terminal that looks like I should be writing code for something. . . Can't find what you're talking about. 

"GNU nano 2.0.7 File: /boot/grub/grub.conf" blank with some options on the bottom for inputs I can use, but when I try them nothing actually happens so I don't know what they're for. .

---

### Post by milia on 2008-06-19
> **cinohpa said:**
> hmmm mysteriously, when I do that command it takes me to a blank terminal that looks like I should be writing code for something. . . Can't find what you're talking about. 

"GNU nano 2.0.7 File: /boot/grub/grub.conf" blank with some options on the bottom for inputs I can use, but when I try them nothing actually happens so I don't know what they're for. .

Do as obsrv said but edit the 

**/boot/grub/menu.lst** file.
It should be in /boot/grub, check it by

```
ls -l /boot/grub
```


There is another solution however, without changing the boot time 
(you might want to choose one of several kernels diplayed):

You can edit the above mentioned file and find at the end of it a portion 
of code like:

```

...
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=c1885f4d-6fb8-44b6-9e14-6fd6763228ea ro splash xforcevesa vga=791
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=c1885f4d-6fb8-44b6-9e14-6fd6763228ea ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

[B]title        Windows Vista
root		(hd0,0)
makeactive
chainloader +1
[/B]

```

Then convert it to:

```


title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=c1885f4d-6fb8-44b6-9e14-6fd6763228ea ro splash xforcevesa vga=791
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=c1885f4d-6fb8-44b6-9e14-6fd6763228ea ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

[B]#title       Windows Vista
#root		(hd0,0)
#makeactive
#chainloader +1
[/B]



```

The '#' before WIndows partition will comment out your Vista partition.
It will stay in your hard drive but won't be displayed in grub bootloader.

---

### Post by pixel :-) on 2008-06-19
I'm wondering if there's anyway to hide my vista partition

If you mean hide it in the menu of grub,follow the above advise.If you mean hide it from linux while in linux,you have to edit /etc/fstab and comment (#) the line with the partition of vista.

---

### Post by cinohpa on 2008-06-20
oh wow. Figured out my mistake. This is embarrassing. My mistake was that I was typing gedit boot/grub/menu.**1st** and not gedit boot/grub/menu.**lst**

Anyways I learned a few new things now. Thanks everyone.

---

### Post by drs305 on 2008-06-20
To avoid mistakes editing routine grub menu settings, I recommend Startup-Manager. It can make most of the changes editing menu.lst can without the risk of messing it up.

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

