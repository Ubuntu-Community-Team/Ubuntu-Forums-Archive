---
title: "Xserve dual G4 install CD panics"
date: 2006-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Khisanth on 2006-01-24
I was trying to install 5.10-PPC Install CD onto an Apple Xserve (dual G4 1.33 Ghz PPC), but after the kernel loads, it tries to mount a filesystem and gets the error:

"error -3 while decompressing"
illegal instruction

Then some hex addresses, and a kernel panic.  I will try to copy the full output tomorrow.

I tried the following boot parameters:
server
server-powerpc
server-powerpc text
rescue

The same CD boots fine with my Apple Powerbook.

---

### Post by Khisanth on 2006-01-25
[   49.835425] RAMDISK: Compressed image found at block 0
[   49.973571] crc error
[   49.980527] VFS: Mounted root (cramfs filesystem) readonly
[   49.986208] Freeing unused kernel memory: 172k init 4k chrp 32k prep
Setting up filesystem, please wait ...
[   50.025128] Error -3 while decompressing!
[   50.030700] c02fe624(2482)->fe0a4000(4096)
Illegal instruction
[   50.042684] Kernel panic - not syncing: Attempted to kill init!
[   50.048286]  <0>Rebooting in 180 seconds.._

---

