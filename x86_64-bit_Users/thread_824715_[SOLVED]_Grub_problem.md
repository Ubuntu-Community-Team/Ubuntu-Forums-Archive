---
title: "[SOLVED] Grub problem"
date: 2008-06-10
forum: x86 64-bit Users
---

### Post by geum on 2008-06-10
Read most of the threads on grub problems,and tried most of the solutions.But cant seem to get it right,its driving me crazy,Ive spent a couple of days wrestling with this,turning to you guys is my last throw of the dice.I installed Ubuntu hardy on hda first,then Mepis on hdb last,when Mepis install asked where to put grub I said in mbr(hdb)can you confirm if that was right,or should it be in hda.

This is my Ubuntu menu.lst


```
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0eceb855-eeed-4267-a190-c3184c7d923d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title           mepis 7.0
root            (hd1,0)
makeactive
chainloader     +1

```

---

### Post by KingTermite on 2008-06-10
Yes, I believe so.

It looks like everything else was put on hd0 (hda) and likely all their boot information is on hda. The computer is probably not booting from hdb, so its not reading the mbr on hdb.

You need to find a way to add Mepis to the MBR on hda, I think.

---

### Post by meierfra. on 2008-06-10
you need to use

title           mepis 7.0
root            (hd1)
chainloader     +1


(hd1,0) would be correct if you installed the Mepis grub  to the boot sector of the first partition  (/dev/sdb1). But you installed the Mepis grub to the MBR (/dev/sdb). So you need to use (hd1).  And since you cannot put a boot flag on a hard drive (only on partitions), you cannot use "makeactive"

---

### Post by geum on 2008-06-10
meierfra

Spot on my friend,thank you so much,I can now put the headache pills away.
If the same situation occurs again,where should I put the grub when asked by the second install.

---

### Post by meierfra. on 2008-06-10
> If the same situation occurs again,where should I put the grub when asked by the second install.

I usually put grub on the partition of the new OS.

---

