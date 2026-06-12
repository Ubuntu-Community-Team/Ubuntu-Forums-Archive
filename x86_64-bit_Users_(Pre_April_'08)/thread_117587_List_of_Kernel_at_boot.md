---
title: "List of Kernel at boot"
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Trinità on 2006-01-15
Hello!
I' want to say the difference of kernel at the boot of pc...
at the start grub show:
Ubuntu, kernel 2.6.12-9-amd64-generic Default
and
Ubuntu, kernel 2.6.12-9-amd64-generic 
What's the difference?

I'm sorry for my english ...
Thanks;)

---

### Post by localzuk on 2006-01-15
I don't think there is a difference in this case. What usually happens is that the list is added to when new kernels are installed. Each of the kernels has an entry like the second one you have shown and the default one has an extra entry such as the first one.

To check, you can take a look at the /boot/grub/menu.lst file and compare the 2 sections near the bottom of the file.

---

### Post by Trinità on 2006-01-15
In the menu.lst i'm find this
> title		Ubuntu, kernel 2.6.12-9-amd64-generic Default 
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Default (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/sda3 ro single
initrd		/boot/initrd.img
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

### END DEBIAN AUTOMAGIC KERNELS LIST



I'm not installed new kernel but is new installation of kubuntu (last was ubuntu):cool: 
Thanks

---

### Post by tktreload on 2006-01-15
As I se it the only difference is that the first entry boots vmlinuz (aka a sym link to vmlinuz-2.6.12-9-amd64-generic)
the second entry boots vmlinuz-2.6.12-9-amd64-generic directly.
other than that there seems to be no differnce in the boot arguments...

---

### Post by Trinità on 2006-01-15
Ok! Thank you very much ;)

---

### Post by localzuk on 2006-01-15
Yes that is what I meant. The 2 are always the same (bar the symlink - as this keeps the option pointing to the default kernel).

What I meant by the 'when you install a new kernel' is that if you run 'sudo apt-get dist-upgrade' and it installs a new kernel package, it will add entries to that list - so you will see things like:
```

Ubuntu, kernel 2.6.12-9-amd64-generic Default
Ubuntu, kernel 2.6.12-9-amd64-generic
Ubuntu, kernel 2.6.12-8-amd64-generic
Ubuntu, kernel 2.6.12-7-amd64-generic

```

plus the recovery mode options. The default one is just the one that always points to the (usually) latest version.

---

### Post by Trinità on 2006-01-15
Ok I have understood :D 
Thank you ;)

---

