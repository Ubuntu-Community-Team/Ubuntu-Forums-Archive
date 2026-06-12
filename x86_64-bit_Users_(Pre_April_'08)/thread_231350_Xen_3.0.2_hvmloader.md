---
title: "Xen 3.0.2 hvmloader"
date: 2006-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by sles on 2006-08-07
Hello! I have processor with VT and want to run windows inside Xen.


I downloaded and installed xen 3.0.2 from binaries.

I found that hvmloader is not included in binary distribution :-(
So I try to compile it from sources.
I get following error:

cpp -P -DDEBUG -DTEXTADDR=0x000D0000 vmxassist.ld > vmxassist.tmp
ld -o vmxassist -m elf_i386 -nostdlib --fatal-warnings -N -T vmxassist.tmp head.o trap.o vm86.o setup.o util.o
nm -n vmxassist > vmxassist.sym
objcopy -p -O binary -R .note -R .comment -R .bss -S --gap-fill=0 vmxassist vmxassist.tmp
dd if=vmxassist.tmp of=vmxassist.bin ibs=512 conv=sync
37+1 records in
38+0 records out
make[1]: *** [vmxassist.bin] Segmentation fault
make[1]: *** &#1059;&#1076;&#1072;&#1083;&#1103;&#1077;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083; `vmxassist.bin'
make[1]: Leaving directory `/var/local/files/xen-3.0.2-2/tools/firmware/vmxassist'
make: *** [all] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2 

I also tested Xen unstable and testing with the same results.

Any ideas ?

---

### Post by RAOF on 2006-08-07
I seem to remember there being some bug in "dd" that made it segfault under some conditions when run as a normal user (but not root).  Maybe you're triggering that.

You could try doing the same thing, but prepending "sudo" to it?

---

### Post by sles on 2006-08-07
I did this as root.
But, anyway, this is bug in dd, I got dd from 32bit sles9 and it work OK.
Thank you!

---

### Post by galileon on 2006-08-20
hello, could you tell me how to get dd from suse please? did you download it? im trying to compile xen-testing in ubuntu dapper

thanks a lot,

galileon.

---

### Post by galileon on 2006-09-01
i got the good dd from coreutils in the gnu website i think, just google coreutils source anyone...

---

### Post by changlinn on 2007-01-03
I had this issue with the xen in the repos too, I was gettting Error: Kernel image does not exist: /usr/lib/xen/boot/hvmloader, have a look here: [https://launchpad.net/distros/ubuntu/+source/xen-3.0/+bug/65535](https://launchpad.net/distros/ubuntu/+source/xen-3.0/+bug/65535)
you need to do an: apt-get install xen-ioemu-3.0

---

