---
title: "Not shutting down properly"
date: 2008-12-27
forum: x86 64-bit Users
---

### Post by theemperor on 2008-12-27
Hi,
I am using UBUNTU 7.10 on my Intel x86.64 bit. Mb. Intel Dp35Dp.

When ever i shutdown the machine, It stops half way through the unloading bar. and then screen goes black with command prompt cursor on top left of the screen.
Then i will have to switch the computer off completly. 

Pls help me to rectify this

Thanks in advance
Bijoy

---

### Post by cariboo on 2008-12-28
Turn off usplash by removing:

```
quiet splash
```

from the kernel line in /boot/grub/menu.lst, and see where it is getting stuck during the shutdown process.

To edit /boot/grub/menu.lst. press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

This will open the file as root, allowing you to edit it.

Please report back with where it is getting stuck.

Jim

---

### Post by theemperor on 2008-12-29
Hi,

There are 4 different places "quiet splash" appear in menu.lst file. Which one to be removed?. 
I am very beginner in any unix like OS.

# defoptions=**[COLOR="Yellow"]quiet splash[/COLOR]**

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,9)
kernel		/vmlinuz-2.6.22-16-generic root=UUID=8478eded-bcc8-4ed0-92e1-565bafbe0fb4 ro **[COLOR="Yellow"]quiet splash[/COLOR]**
initrd		/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,9)
kernel		/vmlinuz-2.6.22-16-generic root=UUID=8478eded-bcc8-4ed0-92e1-565bafbe0fb4 ro single
initrd		/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,9)
kernel		/vmlinuz-2.6.22-15-generic root=UUID=8478eded-bcc8-4ed0-92e1-565bafbe0fb4 ro **[COLOR="Yellow"]quiet splash[/COLOR]**
initrd		/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,9)
kernel		/vmlinuz-2.6.22-15-generic root=UUID=8478eded-bcc8-4ed0-92e1-565bafbe0fb4 ro single
initrd		/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,9)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=8478eded-bcc8-4ed0-92e1-565bafbe0fb4 ro **[COLOR="Yellow"]quiet splash[/COLOR]**
initrd		/initrd.img-2.6.22-14-generic
quiet
========================================================================

Thanks in Advance

Bijoy

---

### Post by Schuenemann on 2008-12-29
The kernel you're booting, which is probably the first one.
But you can leave quiet or else a lot of screen messages will be printed.

You can also remove the entries for older kernels so they won't be shown by grub anymore.

---

### Post by Yellow Pasque on 2008-12-29
> You can also remove the entries for older kernels so they won't be shown by grub anymore.
To clarify, this should NOT be done manually (i.e. by editing /boot/grub/menu.lst). It should be done by removing the corresponding kernel-image package with Syanptic/apt, which will automatically run update-initramfs and update menu.lst. Also, unless you're running low on disk space, it's a good idea to keep one old kernel around in case something happens that prevents the current kernel from booting.

---

### Post by theemperor on 2008-12-29
I am from Advertising Industry..I dont understand very details of kernel, etc.... I have been told that removing "quite splash" from menu.lst will solve the shutdown error.
And when i open menu.lst, there were 4 different instances of "quite splash". following are the instances.

===========================================================
# defoptions=[COLOR="Red"]quiet splash[/COLOR]

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-16-generic
root (hd0,9)
kernel /vmlinuz-2.6.22-16-generic root=UUID=8478eded-bcc8-4ed0-92e1-565bafbe0fb4 ro [COLOR="Red"]quiet splash[/COLOR]
initrd /initrd.img-2.6.22-16-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root (hd0,9)
kernel /vmlinuz-2.6.22-16-generic root=UUID=8478eded-bcc8-4ed0-92e1-565bafbe0fb4 ro single
initrd /initrd.img-2.6.22-16-generic

title Ubuntu 7.10, kernel 2.6.22-15-generic
root (hd0,9)
kernel /vmlinuz-2.6.22-15-generic root=UUID=8478eded-bcc8-4ed0-92e1-565bafbe0fb4 ro [COLOR="Red"]quiet splash[/COLOR]
initrd /initrd.img-2.6.22-15-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root (hd0,9)
kernel /vmlinuz-2.6.22-15-generic root=UUID=8478eded-bcc8-4ed0-92e1-565bafbe0fb4 ro single
initrd /initrd.img-2.6.22-15-generic

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,9)
kernel /vmlinuz-2.6.22-14-generic root=UUID=8478eded-bcc8-4ed0-92e1-565bafbe0fb4 ro [COLOR="Red"]quiet splash[/COLOR]
initrd /initrd.img-2.6.22-14-generic
quiet

==========================================================

I am little confused on which "quite splash" to be removed from menu.lst. Pls help

Thanks in Advance

Bijoy

---

### Post by jpkotta on 2008-12-29
> **theemperor said:**
> I have been told that removing "quite splash" from menu.lst will solve the shutdown error.

No, it will just help us diagnose the problem.

> I am little confused on which "quite splash" to be removed from menu.lst. Pls help
All of them.  You really only have to remove the ones for the kernel you're using, which is likely the first one, but it is completely safe to remove them all.  You just lose the pretty Ubuntu logo when you boot/shutdown.

---

### Post by theemperor on 2008-12-30
Hi,

Thanks a lot.

I tried removing quiet splash.

When the mechine is shutdown, following message came.

[COLOR="Red"]System is shutting down, please wait....[/COLOR]

It was in red colour. I waited for 10 mnts. and it didn't progress from there.

Bijoy

---

### Post by theemperor on 2008-12-30
Hi,

Okie I figured out...It stuck in as follows

====================================================
stoping gnome display manager                   [OK]
Stoping Avahi in DNS/DNS-SD Daemon avahi-daemon [OK]
stoping DHCP D-Bus daemon dhcpbd                [OK]
stoping consolekit daemon console-kit-daemon    [OK]
stoping the systemclock
shutting down ALSA                         
====================================================
It didn't proceed after that.

Pls help me on this

Thanks in Advance
Bijoy

---

