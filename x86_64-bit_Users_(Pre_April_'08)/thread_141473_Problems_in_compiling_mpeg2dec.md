---
title: "Problems in compiling mpeg2dec"
date: 2006-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by tim67 on 2006-03-08
Hi,

I'll get these errors while compiling ( with make ) :

/tmp/cciRUDHa.s: Assembler messages:
/tmp/cciRUDHa.s:72: Error: suffix or operands invalid for `pop'
/tmp/cciRUDHa.s:75: Error: suffix or operands invalid for `push'
/tmp/cciRUDHa.s:78: Error: suffix or operands invalid for `pop'
make[2]: *** [libmpeg2arch_la-cpu_accel.lo] Error 1
make[2]: Leaving directory `/home/timo67/mpeg2dec-0.4.1-cvs/libmpeg2'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/timo67/mpeg2dec-0.4.1-cvs/libmpeg2'
make: *** [all-recursive] Error 1

can anybody help me with this ? 

bootstart & configure seem to work Ok

-timo

---

