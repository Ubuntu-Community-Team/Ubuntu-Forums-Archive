---
title: "ECIAdsl: Anyone compiled it on AMD64 ?"
date: 2007-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Opteron78 on 2007-11-01
Hello, 
I am looking for a compiled AMD64 ECI Adsl driver. You can find sources here:
[http://eciadsl.flashtux.org/](http://eciadsl.flashtux.org/)

I tried compiling it on Ubuntu 7.10 but it doesn't work on my Ericsson HM120DP modem. Instead my modem works correctly on eciadsl and ubuntu 32bit. Anyone has already compiled it?

---

### Post by tim_wright on 2008-05-24
I got it compiles but I get the following error when trying to use it:

> eciadsl-start

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is missing... trying to mount

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

pusb_control_msg: Inappropriate ioctl for device
*** glibc detected *** /usr/local/bin/eciadsl-synch: double free or corruption (fasttop): 0x0000000000607240 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fa638f7b08a]
/lib/libc.so.6(cfree+0x8c)[0x7fa638f7ec1c]
/usr/local/bin/eciadsl-synch[0x4032f3]
/usr/local/bin/eciadsl-synch[0x402953]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7fa638f251c4]
/usr/local/bin/eciadsl-synch[0x401419]
======= Memory map: ========
00400000-00407000 r-xp 00000000 fe:02 27198165                           /usr/local/bin/eciadsl-synch
00606000-00607000 rw-p 00006000 fe:02 27198165                           /usr/local/bin/eciadsl-synch
00607000-00628000 rw-p 00607000 00:00 0                                  [heap]
40c93000-40c94000 ---p 40c93000 00:00 0 
40c94000-41494000 rw-p 40c94000 00:00 0 
41494000-41495000 ---p 41494000 00:00 0 
41495000-41c95000 rw-p 41495000 00:00 0 
7fa634000000-7fa634021000 rw-p 7fa634000000 00:00 0 
7fa634021000-7fa638000000 ---p 7fa634021000 00:00 0 
7fa638cf9000-7fa638d06000 r-xp 00000000 fe:02 19324944                   /lib/libgcc_s.so.1
7fa638d06000-7fa638f06000 ---p 0000d000 fe:02 19324944                   /lib/libgcc_s.so.1
7fa638f06000-7fa638f07000 rw-p 0000d000 fe:02 19324944                   /lib/libgcc_s.so.1
7fa638f07000-7fa63905f000 r-xp 00000000 fe:02 19324951                   /lib/libc-2.7.so
7fa63905f000-7fa63925f000 ---p 00158000 fe:02 19324951                   /lib/libc-2.7.so
7fa63925f000-7fa639262000 r--p 00158000 fe:02 19324951                   /lib/libc-2.7.so
7fa639262000-7fa639264000 rw-p 0015b000 fe:02 19324951                   /lib/libc-2.7.so
7fa639264000-7fa639269000 rw-p 7fa639264000 00:00 0 
7fa639269000-7fa63927f000 r-xp 00000000 fe:02 19324965                   /lib/libpthread-2.7.so
7fa63927f000-7fa63947f000 ---p 00016000 fe:02 19324965                   /lib/libpthread-2.7.so
7fa63947f000-7fa639481000 rw-p 00016000 fe:02 19324965                   /lib/libpthread-2.7.so
7fa639481000-7fa639485000 rw-p 7fa639481000 00:00 0 
7fa639485000-7fa6394a2000 r-xp 00000000 fe:02 19324945                   /lib/ld-2.7.so
7fa639688000-7fa63968a000 rw-p 7fa639688000 00:00 0 
7fa63969c000-7fa63969d000 rw-p 7fa63969c000 00:00 0 
7fa63969e000-7fa6396a2000 rw-p 7fa63969e000 00:00 0 
7fa6396a2000-7fa6396a4000 rw-p 0001d000 fe:02 19324945                   /lib/ld-2.7.so
7fff4168f000-7fff416a4000 rw-p 7ffffffea000 00:00 0                      [stack]
7fff417fe000-7fff41800000 r-xp 7fff417fe000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
 Please Wait.. Synchronisation in progress [-]/usr/local/bin/eciadsl-start: line 517:  7467 Aborted                 "$BIN_DIR/eciadsl-synch" $synch_options
ERROR: failed to get synchronization


x64 Ubuntu 8.04

BT Voyager 105

Using tutorial given here: 
[http://lack-of.org.uk/viewarticle.php?article=114](http://lack-of.org.uk/viewarticle.php?article=114)

Any help would be greatly appreciated!

---

