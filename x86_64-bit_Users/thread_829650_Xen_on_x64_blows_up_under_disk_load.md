---
title: "Xen on x64 blows up under disk load"
date: 2008-06-15
forum: x86 64-bit Users
---

### Post by mushinspace on 2008-06-15
Hi.

Brand new install of 8.04 Server x64 LTS on a Sun Ultra 20 (AMD Opteron 148) ... install went smooth and seemed to have no problem.

Installed ubuntu-xen-server package and the install seems to have succeeded and it booted -- YAY!

Trying to do any sort of significant disk I/O, I get errors on the console followed by a reboot.

Error messages:

[ 1839.394603] ata2.00 status: {DRDY}

there's a longer line about it, but I can't copy it quick enough.

Everything works fine under the default kernel.  The Xen kernel that installed is:

Linux ubuntu 2.6.24-18-xen #1 SMP Wed May 28 22:50:01 UTC 2008 x86_64 GNU/Linux

Any clues?

--Sam

---

### Post by mushinspace on 2008-06-15
Following up with more info ...

Reinstalled the same server with 8.04 x86 and did a baseline disk load test with:

dd if=/dev/zero of=/test bs=1024 count=1000000

No explosions.

apt-get install ubuntu-xen-server and reboot into xen.

Linux ubuntu 2.6.24-18-xen #1 SMP Thu May 29 00:39:30 UTC 2008 i686 GNU/Linux

Retry the disk load test ... boom

I managed to catch something about PCI-DMA: OUT OF SW-IOMMU space for 65535 bytes at address xxxx

So, it seems that I'm running into the same issues for x86 and i386 with the ubuntu-xen-server stuff on 8.04.

--Sam

---

### Post by reeja on 2008-07-11
Hi mushinspace,

I got rid of the problem by appending 
[INDENT][FONT="Courier New"]swiotlb=128M[/FONT][/INDENT]
to xen's menu.lst entry.

Maybe this helps...
Regards,
reeja.

---

