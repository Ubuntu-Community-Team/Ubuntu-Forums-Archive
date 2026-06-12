---
title: "Intrepid x64: Firefox: Inconsistency detected by ld.so"
date: 2009-03-29
forum: x86 64-bit Users
---

### Post by iivanov on 2009-03-29
When I try to run Firefox 3.0.8 on my Intrepid x64, I get the error:

```
Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 416: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!

```

I had a segmentation fault and did a sudo rm /var/cache/apt/*.bin. That fixed the segmentation fault, but my Firefox is still showing that error from above. Most of my apps are working.

Can anyone point me in the direction of solving this problemn?

---

### Post by Paintrick on 2009-06-06
hey man,

I have a similar issue only my issue concerns Apache on Ubuntu server and i can't delete any .bin files in the apache folder in cache.

how did you find out it's an segmentation error ?

---

### Post by iivanov on 2009-06-06
As far as I remember a message showed up on restart.

---

### Post by uskerhay on 2009-09-07
This problem isn't just firefox. I'm getting the same thing with matlab. I've been searching all the various forums I can and haven't found a solution. Were any of the previous posts able to fix this?

---

### Post by uskerhay on 2009-09-07
It seems just rebooting the computer fixes this problem....

---

