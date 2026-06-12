---
title: "Question about kernels"
date: 2006-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by timelord726 on 2006-03-13
My GRUB menu.lst file contains the following options:

```
title        Ubuntu, kernel 2.6.12-10-amd64-k8 Default 
root        (hd1,0)
kernel        /boot/vmlinuz root=/dev/sdb1 ro quiet splash
initrd        /boot/initrd.img
savedefault
boot

title        Ubuntu, kernel 2.6.12-10-amd64-k8 Default (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz root=/dev/sdb1 ro single
initrd        /boot/initrd.img
boot

title        Ubuntu, kernel 2.6.12-10-amd64-k8 
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.12-10-amd64-k8 root=/dev/sdb1 ro quiet splash
initrd        /boot/initrd.img-2.6.12-10-amd64-k8
savedefault
boot

title        Ubuntu, kernel 2.6.12-10-amd64-k8 (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.12-10-amd64-k8 root=/dev/sdb1 ro single
initrd        /boot/initrd.img-2.6.12-10-amd64-k8
boot
```

I am curious to know, what is the difference between the kernel choices marked "Default" and those *not* marked "Default."  Probably a silly question but I have been wondering this ever since I installed the AMD64 version of Ubuntu.  Are either of these safe to remove?  If I wanted to remove one, which should I remove?

Thanks very much!

---

### Post by Sutekh on 2006-03-13
Can you boot these 'Default' kernels?  I was just noticing these lines (the 'Default')
```
kernel        /boot/vmlinuz root=/dev/sdb1 ro single
initrd        /boot/initrd.img
```
as opposed to these lines (those without 'Default')
```
kernel        /boot/vmlinuz-2.6.12-10-amd64-k8 root=/dev/sdb1 ro quiet splash
initrd        /boot/initrd.img-2.6.12-10-amd64-k8
```

I don't think those 'Default' entires could actually *do* anything as they don't specify a kernel image to boot.

---

### Post by RAOF on 2006-03-13
[QUOTE=Sutekh]Can you boot these 'Default' kernels?  I was just noticing these lines (the 'Default')
```
kernel        /boot/vmlinuz root=/dev/sdb1 ro single
initrd        /boot/initrd.img
```
as opposed to these lines (those without 'Default')
```
kernel        /boot/vmlinuz-2.6.12-10-amd64-k8 root=/dev/sdb1 ro quiet splash
initrd        /boot/initrd.img-2.6.12-10-amd64-k8
```

I don't think those 'Default' entires could actually *do* anything as they don't specify a kernel image to boot.[/QUOTE]
They **do** specify a kernel image to boot: they specify **/boot/vmlinuz**, which is a symlink which (should) always points to the most recently installed kernel.  There's (generally) no difference between the "default" option and the non-default option, although it's possible that you could set it up so that there would be.

---

### Post by Sutekh on 2006-03-13
[QUOTE=RAOF]They **do** specify a kernel image to boot: they specify **/boot/vmlinuz**, which is a symlink which (should) always points to the most recently installed kernel.  There's (generally) no difference between the "default" option and the non-default option, although it's possible that you could set it up so that there would be.[/QUOTE]
Ok, there you go.  Thanks for the info.  Are the 'Default' kernel entries setup from the installation by default?  

When a new kernel is installed, it usually updates the menu to include itself, doesn't it?  Is there any advantage to keeping the 'Default' entry in this case, as the most recent kernel should be in the menu anyway?

---

### Post by RAOF on 2006-03-13
[QUOTE=Sutekh]...When a new kernel is installed, it usually updates the menu to include itself, doesn't it?  Is there any advantage to keeping the 'Default' entry in this case, as the most recent kernel should be in the menu anyway?[/QUOTE]
I can't think of any good reason to keep the "default" around.  Except, perhaps, that if you've got a lot of kernels making the top entry say "default" makes a bit of user-interface sense.  The "Default" options don't give you access to anything you haven't already got.

---

### Post by timelord726 on 2006-03-13
Thank you guys very much!  That's valuable information and I appreciate your speedy response.  :)

---

