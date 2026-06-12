---
title: "Bug in PPC kernal"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by snooo on 2005-10-16
There seems to be a bug which prevents me from booting with the kernel and image provided by breezy. As a result, i've gone back to using the last version that came with hoary, with no immediate problems.

I'm using...

An apple Powermac G3, using a BootX as a bootstrapper
Breezy, which I have upgraded (through much pain) over the net.
vmlinuz-2.6.12-9-powerpc & initrd.img-2.6.12-9-powerpc

basically the boot up process reports I/O errors as it attempts to mount the file system. As a result, I end up dumped in a busybox. Has anyone seen a similar problem, is there something simple that I'm not doing? Or is this a bonafide bug?

---

### Post by tommyr on 2005-10-16
[QUOTE=snooo]There seems to be a bug which prevents me from booting with the kernel and image provided by breezy. As a result, i've gone back to using the last version that came with hoary, with no immediate problems.

I'm using...

An apple Powermac G3, using a BootX as a bootstrapper
Breezy, which I have upgraded (through much pain) over the net.
vmlinuz-2.6.12-9-powerpc & initrd.img-2.6.12-9-powerpc

basically the boot up process reports I/O errors as it attempts to mount the file system. As a result, I end up dumped in a busybox. Has anyone seen a similar problem, is there something simple that I'm not doing? Or is this a bonafide bug?[/QUOTE]


I tried loading it today on a G3 ibook 500 USB with 320m of RAM and I get as far as the brown screen but no logo and nothing else happens. 

I tried the "live" and "live powerpc" option with no joy so far. 

Any ideas?

Tom

---

### Post by Mark Mitchell on 2005-11-07
B/W G3, w/G4 upgrade, 1Gb RAM.
The install goes fine until the boot from hard drive is almost done. I get:
loading kernel...
/pci@80000000/pci-bridge@d/pci-ata@1/@0/disk@0:3,/boot/vmlinux:  input/output error
Any thoughts?

---

### Post by ssam on 2005-11-08
getting stuck at a brown screen can be because your clock is set very wrong (before 1970 i think). this may not be the case here, but its possible (and worth knowing). if you can get a terminal by pressing crt+alt+f1 and type "date" you can see what date and time the computer thinks it is.

sam

---

