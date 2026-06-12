---
title: "Kernel  issues on installation with ASUS p5n-e and Intel core 2 duo, 7.04"
date: 2007-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by philip13 on 2007-06-10
Tail of woe here, I have :
Motherboard	ASUS p5n-e 
CPU	Intel core 2 duo E6700
Video	Nvidia 8600 GTX
Memory 2 GB XMS2 (Corsair TwinX, NOT SLI – SLI and SLI aperture disabled)
1 SATA HD
Plextor PX-760A DVDRW.

Attempted to install Ubuntu 7.04 (x86_64) repeatedly, by standard and alternative ISOs. Unfortunately the kernel page faulted randomly (swap issue ?), randomly threw invalid op-codes, seg-faulted and panicked  !
For the standard desktop install, it repeatedly fell over some where in squashfs, with an invalid page fault (either processor).
For the alternate install disk it sometimes made it through to actually installing the modules (post formatting), but tended to die during formatting.
I managed to grab a console, scanned through dmesg, and found two nasties :

Probing IDE interface ide1
Bad page state in process ksoftirqd/0

Some more modules loaded fine then :

kernel BUG at mm/swapfile.c : 351
invalid opcode 0000[1] SMP
CPU 0 

I will try and capture a full dump, I do have network (sometimes !) so I believe I can capture the data to a RAM file and scp it over to another system (assuming scp is available).
To resolve I tried passing to the kernel :
pci=noacpi acpi=off ide=nodma (had the buffer I/O issue)  irqpoll.

This is my first real experience with dual processor systems, so I am at a loss at to how (and why) the kernel is spectacularly misbehaving with this setup.
A  cat of /proc/cpuinfo does show two Intel core duo processors.
I have see other issues reported by Asus users, but not on this level of failure.

Any help would be appreciated.     ](*,)

---

### Post by philip13 on 2007-06-11
*** NOTE This may affect other Asus users especially P5N-E and may be the cause of the random lockups ***
Problem due to memory corruption, due to incorrect automatic BIOS memory settings, fixed by setting memory to Linked, with FSB ratio set to sync, will post more details tomorrow.

---

### Post by philip13 on 2007-06-12
As promised !
My configuration is two 1 GB memory chips in the *yellow* sockets.

For P5N-E user (and possible other ASUS users)

 1. Boot/re-boot, press del to get into BIOS setup screen.
 2. Got to Advanced -> JumperFree Configuration.
 3. SET AI Tuning to Manual.
 4. SET FSB - Memory Clock Mode to Linked.
 5. SET FSB – Memory ration to Sync Mode.

Escape back to the main BIOS menu then select exit, and Save + Exit.

This allowed me to install Ubuntu from the alternative i86_64  disk.

Occasional random lock-ups :

In X, I was suffering from occasional lock-ups until I installed the NVIDIA drivers (from NVIDIA), following various procedures, but basically removing all NVIDIA kernel modules (outside of X !).
Setting DISABLED_MODULES="nv" in /etc/default/linux-restricted-modules-common, installing the kernel header module and finally running the NVIDIA x86_64 installer.

NOTE ! Select NO for  32 bit OpenGL drivers, when prompted, if installed they will foul X !!

---

### Post by Prince_Andrei on 2008-01-26
I made the bios change and have not had a lock up yet. I have the same motherboard. After weeks of pounding my head against the wall, this just might be my answer!

---

### Post by Neutron Flux on 2008-02-13
Thank you Philip13. I have an ASUS P5N-E SLI purchased Feb08 with Intel 6850 Core 2 Duo and was having a similar problem even after a format & reload using Patriot Signature Line PC2-6400 800 Mhz 1GB(2). Ran memtest86+ and found my system locking up unable to complete a memory test pass with default BIOS settings booting to CD, implemented your recommended changes to memory clock mode & ration & now rock solid 2+ days & no problem with memtest86+ . I also bumped the memory voltage up to the second from bottom 2.017V or something close. Previously would lock up every 5 - 10 minutes. Thanks for taking the time to post your fix! 
Matt in Menifee,CA. :)

---

