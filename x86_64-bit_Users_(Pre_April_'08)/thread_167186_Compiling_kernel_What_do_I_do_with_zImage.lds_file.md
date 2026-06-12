---
title: "Compiling kernel: What do I do with zImage.lds file?"
date: 2006-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by shorty0927 on 2006-04-27
I'm trying to compile a 2.6.15 kernel that I downloaded from kernel.org. I've gotten to the point where I need to install the kernel, but the README in the powerpc boot directory says:

> To extract the kernel vmlinux, System.map, .config or initrd from the zImage binary:

objcopy -j .kernel:vmlinux -O binary zImage vmlinux.gz
objcopy -j .kernel:System.map -O binary zImage System.map.gz
objcopy -j .kernel:.config -O binary zImage config.gz
objcopy -j .kernel:initrd -O binary zImage.initrd initrd.gz

There is a file in the boot directory called zImage.lds. I tried copying and pasting the first line of the README into the terminal (with .lds added to zImage), but it says that it doesn't recognize the file format. I've scoured the internet and I can't find a program that will let me into that .lds file. Objcopy info isn't much help, either, because the syntax of the argument of the README doesn't match up with the syntax used in objcopy info. Any ideas out there?

Thanks!

---

### Post by Ptero-4 on 2006-04-28
IIRC, that info is for Pegasos PPC. for Mac PPC is a bit different (Can't quite remember, long since last kernel I compiled).

---

