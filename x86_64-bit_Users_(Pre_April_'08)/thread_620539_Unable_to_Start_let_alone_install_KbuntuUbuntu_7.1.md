---
title: "Unable to Start let alone install Kbuntu/Ubuntu 7.10"
date: 2007-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubu256 on 2007-11-22
I have tried downloading bith available version of Kbuntu and Ubuntu for 64bit systems, and I have bought a DVD of the combined Live and Install.

BUT Kubuntu fails to start.
I get the first screen - always, and then wait until the first choice - to start Kbuntu - but I always get :-

BusyBox V1.1.3 (Debian 1:1.1.3-5ubuntu7) Built in shell (ash)
Enter 'help' for a list of built in commands

(initramfs) [  68.178334] usb 1-1: device not accepting address 2, error -71
[  76.714416]  sd 3:0:0:0 [sdc] Assuming driver cache write thruough
[  76.715189] sd 3:0:0:0 [sdc] Assuming driver cache write thruough

I currently run SuSE 9.3 and cat /proc/cpuinfo
gives :-

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 44
model name      : AMD Sempron(tm) Processor 2600+
stepping        : 2
cpu MHz         : 1599.879
cache size      : 128 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 pni syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 3137.53
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts ttp [4] [5]

The System has :

1 ide disk [boot and / ]
3 SCSI
2 SATA
USB keyboard; mouse; phone; printer; backup disk
DVD re-writer

Can anyone offer advice as to where to go now ?
I realy would like to move from SuSE to Kbuntu and I have had no problems with earlier versions of Ubuntu/Kbuntu on the two 32 bit systems that I have

thanks in advance

---

### Post by rsambuca on 2007-11-22
Interesting.  I didn't even know there were 64-bit Semprons.  Anyways, it is likely your usb keyboard that it doesn't like.  Do you have a older PS/2 keyboard you can use for installation?

---

### Post by ubu256 on 2007-11-23
Cheers,
Yes I did try plugging in a PS/2 keyboard, but it made no difference.

I am just a bit stuck as to know what to try next :confused:

---

### Post by njparton on 2007-11-23
Maybe unplug any other USB devices you have?

---

### Post by rsambuca on 2007-11-23
Did you run the md5sum check prior to burning the disc?
Did you burn the disc at a low rate to help avoid single bit errors?
Are you using quality media?
Are you sure you have a 64bit system?

---

### Post by njparton on 2007-11-23
Aye, with a sempron you may be best off with a 32 bit version.

---

