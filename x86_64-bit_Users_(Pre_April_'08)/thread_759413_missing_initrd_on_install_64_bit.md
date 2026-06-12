---
title: "missing initrd on install 64 bit"
date: 2008-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by elints on 2008-04-19
Tried 64 bit 7.10 install several times but initrd only shows as a .bak (initrd.img-2.6.22-14-generic.bak). This is amd64 multiboot system using grub. The 32 bit version doesn't have this difficulty. 

GRUB entry

title Ubuntu
    root (hd3,4)
    kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb5 vga=0x31a ro quiet splash
    initrd /boot/initrd.img-2.6.22-14-generic



Any ideas?  TIA

---

### Post by EnkiduinNZ on 2008-04-19
What happens when you rename it to the correct name?

Cheers,

Cliff

---

