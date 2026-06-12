---
title: "64bit Ubuntu hides 32bit ubuntu"
date: 2007-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravinsp on 2007-05-16
I had Ubuntu 7.04 (32bit) installed. Then I installed 7.04 64 bit edition on a separate partition. Now when grub comes up, the entry for Ubuntu boots from the 64bit one. I cannot boot into the 32bit installation.

I think the problem is both editions use the same filenames on the grub.

vmlinuz-2.6.20-15-generic
initrd.img-2.6.20-15-generic
config-2.6.20-15-generic
abi-2.6.20-15-generic
System.map-2.6.20-15-generic

I have a backup of my old grub partition. So I have the old versions of these files (used by the 32bit ubuntu) just in case. How can I resolve this conflict?

Thanks in advance
-RavinSP-

---

### Post by Case_f on 2007-05-16
Use different /boot partitions for 64bit and 32bit, copy your backed-up files into their own directory on your /boot partition (for example /boot/32bit or whatever) or simply rename the files from one install. Then add the 32bit Ubuntu boot item into GRUB's menu.lst manually.

The latter two mentioned options could get a bit tricky, though, in case you ever upgrade kernel (i.e. because of a critical security fix).

Naming the files the same way in 32bit and 64bit wasn't really the best idea for dual booting 32bit and 64bit Ubuntu, the old kernel naming convention was much better in this regard.

---

### Post by rsambuca on 2007-05-16
You are probably better of chainloading the grub entries so that you don't have to bother manually updating one of the grub entries after kernel updates.

---

### Post by ravinsp on 2007-05-16
Thanks guys,

I renamed the files for 32 bit ubuntu and copied them to grub. Now my file list look like this.

vmlinuz-2.6.20-15-generic
initrd.img-2.6.20-15-generic
config-2.6.20-15-generic
abi-2.6.20-15-generic
System.map-2.6.20-15-generic
vmlinuz-2.6.20-15-generic-32       <--Files for old (32 bit) ubuntu
initrd.img-2.6.20-15-generic-32

Then I added new entries to menu.lst to use these files. Now I can boot into both editions.

Thanks
-RavinSP-

---

### Post by Case_f on 2007-05-17
Just bear that in mind if you are ever going to update kernel in 32bit and backup the 64bit files, as they would get overwritten by the new 32bit ones.

---

