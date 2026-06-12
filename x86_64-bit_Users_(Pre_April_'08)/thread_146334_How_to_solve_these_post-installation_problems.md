---
title: "How to solve these post-installation problems?"
date: 2006-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hoffmann on 2006-03-18
Hello All,

I just installed Ubuntu on my EM64T machine. I think I did a nice choice by installing Ubuntu. However, I have a couple of post-installation questions:

(1) Now I have a lot of different kernels installed on my machine. Ok I should keep the most recent kernels-smp kernels. But I am confuse about the "previous", "recovery mode", and "memtest86+" kernels. What those kernels mean? Should I keep them? How can I remove the unecessary kernels?
Please, see below part of my /boot/grub/menu.lst file (My Windows partition is not shown to save space. I will keep this partition!):

title		Ubuntu, kernel 2.6.12-10-amd64-k8-smp Default 
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-k8-smp Default (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/sda3 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic Previous 
root		(hd0,2)
kernel		/boot/vmlinuz.old root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic Previous (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz.old root=/dev/sda3 ro single
initrd		/boot/initrd.img.old
boot

title		Ubuntu, kernel 2.6.12-10-amd64-k8-smp 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-amd64-k8-smp root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-k8-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-k8-smp (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-amd64-k8-smp root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-amd64-k8-smp
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

(2) How can I update some programs such as Firefox, Thunderbird, and ClamAV antivirus?

(3) Do I need to set a root password, or just my user password ("sudo") is enough?

(4) I realized that I have no sound. I took a look on alsamixer, and I have volume on my speakers, etc. However, I have no sound at all.

Many thanks!
Hoffmann

---

### Post by K.Mandla on 2006-03-18
Hi Hoffman. I can offer advice on a couple of your questions.

Personally, I comment out (not delete) the older kernel lines after I've seen that the updates will work for me. You probably know this already, but you can add number signs (#) before the older entries in /boot/grub/menu.lst and they won't appear when the computer starts up.

I don't completely remove old kernels. I know they take up space, but I like to know they are available, if anything ever goes wrong.

I keep the memtest and recovery mode entries as a safety measure. I've never had to use them, but I'd rather have them and not need them, than need them and not have them. ;)

There are some instructions in the wiki for updating Firefox and other programs. ...

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
[https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

I haven't used ClamAV, so I can't say much about it. :)

You can change the root password, but find sudo is enough for me and 95 percent of the problems I run into. I think this will change it, if you really must. ...

```
sudo passwd root
```
Good luck!

---

### Post by Hoffmann on 2006-03-18
Hi K.Mandla,

Many thanks for the informations. I already solved all of my problems. All is working fine.

Thanks!
Hoffmann

---

