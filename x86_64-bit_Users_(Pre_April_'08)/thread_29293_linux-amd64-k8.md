---
title: "linux-amd64-k8"
date: 2005-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by domesticatewhat on 2005-04-23
I have read through the forums and it seems as if either this hasn't been answered or it was figured out with an explanation that I could use.

I tried to install the linux-amd64-k8 kernel and related packages. Everything goes well until reboot and I get this error message:

```

Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)
```

Grub updated successfully because my old kernel is there and everything seems to be pointing to the correct location.

I even went in and manually edited (at boot) the location of the new image but still got the same error.  

Any suggestions as what I have done wrong?

---

### Post by c_dog on 2005-04-24
Sounds like the modules are not loading for your drive controller. Either you are not loading the initrd image or the modules you have are not compiled to recognize the linux-amd64-k8 kernel. Post a copy your /boot/grub/menu.lst .

---

### Post by domesticatewhat on 2005-04-24
Still haven't gotten it to work. Here is my menu.lst
```

title		Ubuntu, kernel 2.6.10-5-amd64-k8 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-amd64-k8 root=/dev/hdc2 ro console=tty0 quiet splash
initrd		/boot/initrd.img-2.6.10-5-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-k8 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-amd64-k8 root=/dev/hdc2 ro console=tty0 single
initrd		/boot/initrd.img-2.6.10-5-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic Previous 
root		(hd0,1)
kernel		/boot/vmlinuz.old root=/dev/hdc2 ro console=tty0 quiet splash
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic Previous (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz.old root=/dev/hdc2 ro console=tty0 single
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by domesticatewhat on 2005-04-25
Does anyone have any suggestions?

---

### Post by endy on 2005-04-27
You could compile your own kernel and make sure that the needed drivers for booting up & filesystems are built in (not modules), this should also solve it.

---

### Post by Kareema on 2005-04-28
[QUOTE=domesticatewhat]Does anyone have any suggestions?[/QUOTE]

What version of Ubuntu are you using (Warty/Hoary/Breezy)? There's a known problem with Breezy, libc6 and initrd. If you use Breezy, you have to know: Use Breezy at your own risk - not recommended right now

---

