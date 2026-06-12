---
title: "Running 64 bit Intrepid with 6 gigs of RAM but only showing 3.2?"
date: 2009-04-08
forum: x86 64-bit Users
---

### Post by Jimbo5584 on 2009-04-08
I recently installed 64 Bit Intrepid on my machine (I used to be a gentoo user).  I was happy to see how easy everything was and how it all just worked it was a nice reprieve from gentoo where I had to compile everything.  

Anyway distros aside I recently made the discovery that I am only using 3.2 gigs of my 6 gig system.  In my bios it does show that I have 6 gigs available but for some reason when I run the ubuntu system monitor it only shows me as having 3.2gig available.  

Any ideas on what might be the issue? 

Should I recompile the kernel to try to pick up the memory increase?  I would think the 64 bit ubuntu would be able to handle larger RAM sizes than 4 gig thats the whole reason to switch to 64 bit.

---

### Post by Jimbo5584 on 2009-04-08
Oh also I should mention that I am running a Pentium D dual core 3ghz processor which is capable of running a 64 bit architecture.

---

### Post by kevmitch on 2009-04-08
What does it say when your run memtest (hit escape during boot to get the boot menu and select memtest86).

---

### Post by kevmitch on 2009-04-08
Sorry by that, I mean how much memory does it say you have, you don't necessarily have to run all the tests (though it might not hurt). 

How are you checking available memory from within Ubuntu?

What do 

```
sudo lshw -C memory 
```
and
```
cat /proc/meminfo
```

give you?

---

### Post by dcstar on 2009-04-08
> **Jimbo5584 said:**
> I recently installed 64 Bit Intrepid on my machine (I used to be a gentoo user).
........

Are you 100% sure, what does this show:

```
uname -m
```

---

### Post by Jimbo5584 on 2009-04-08
$ sudo lshw -C memory

  *-firmware              
       description: BIOS
       vendor: Dell Inc.
       physical id: 0
       version: A07 (01/08/2007)
       size: 64KiB
       capacity: 448KiB
       capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
  *-cache:0
       description: L1 cache
       physical id: 700
       size: 16KiB
       capacity: 16KiB
       capabilities: internal write-back data
  *-cache:1
       description: L2 cache
       physical id: 701
       size: 4MiB
       capacity: 4MiB
       capabilities: internal varies unified
  *-memory
       description: System Memory
       physical id: 1000
       slot: System board or motherboard
       size: 6GiB
     *-bank:0
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: CM2X2048-6400C5
          vendor: 7F7F9E0000000000
          physical id: 0
          serial: 00000000
          slot: DIMM_1
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:1
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          vendor: 0000000000000000
          physical id: 1
          serial: 00000000
          slot: DIMM_3
          size: 1GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:2
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: CM2X2048-6400C5
          vendor: 7F7F9E0000000000
          physical id: 2
          serial: 00000000
          slot: DIMM_2
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:3
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          vendor: 0000000000000000
          physical id: 3
          serial: 00000000
          slot: DIMM_4
          size: 1GiB
          width: 64 bits
          clock: 667MHz (1.5ns)

$ cat /proc/meminfo
MemTotal:      3345916 kB
MemFree:         20564 kB
Buffers:         24884 kB
Cached:        2456972 kB
SwapCached:        344 kB
Active:        2302148 kB
Inactive:       759924 kB
SwapTotal:     6385796 kB
SwapFree:      6380892 kB
Dirty:          153536 kB
Writeback:          60 kB
AnonPages:      580036 kB
Mapped:        1582348 kB
Slab:           112712 kB
SReclaimable:    63864 kB
SUnreclaim:      48848 kB
PageTables:      20916 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   8058752 kB
Committed_AS:  1317864 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    127400 kB
VmallocChunk: 34359610363 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:     57904 kB
DirectMap2M:   3348480 kB

haha yeah running uname -m was the first thing I did for a sanity check but anyways.

$ uname -m
x86_64

This is weird the lshw shows I have 6G of ram but then meminfo only shows me having 3.3G.  What can you guys make of it?

---

### Post by Jimbo5584 on 2009-04-08
Also I don't have memtest86 installed I can install it if you think it might give some indication as to what is going on but its late right now and I have to work in the morn.  

Thanks for the quick response.

---

### Post by kevmitch on 2009-04-08
Are you sure you don't have memtest installed, I think it gets installed by default. In any case, I'm not sure how useful it would be, but it would offer a third view of the hardware aside from linux or the bios.

This might tell you if there's an issue for example with your motherboard being able to address that much ram, or if it is something specific to the Linux kernel.

I think that the lshw output is closer to the bios. They are both aware that there are 6 gigs worth of ram physically installed in the computer. /proc/meminfo on the other hand tells you how much memory the kernel is in control of. 

The first question is really whether all of the ram is addressable by the hardware. For example, my laptop has 4g of ram and is seen as such by lshw, but I can only access 3 gigs of it even though I have a 64-bit processor and kernel due to limitations my motherboard chipset.

Speaking of which what kind of motherboard are you using?

```
sudo lshw -C bus
```

You also might try looking at the output of 

```
dmesg
```

after boot to see if any obvious memory problems are being reported.

---

### Post by jespdj on 2009-04-08
Your question is a frequently asked question.

Here are some other topics in which I tried to explain why you don't see all your RAM:

[http://ubuntuforums.org/showthread.php?t=1116244](http://ubuntuforums.org/showthread.php?t=1116244)
[http://ubuntuforums.org/showthread.php?t=1111941](http://ubuntuforums.org/showthread.php?t=1111941)

---

### Post by Jimbo5584 on 2009-04-08
Hmm looking in my BIOS I don't see a memory remapping ability I wonder if the max my board will support is 4g.  This is an older dell mobo so its very possible that that is the case I just wish it was easier to find the specs for this sucker.

---

### Post by Jimbo5584 on 2009-04-08
Oh yep I found it here

[http://support.dell.com/support/edocs/systems/xps410/en/SM_EN/specs.htm#wp1052333](http://support.dell.com/support/edocs/systems/xps410/en/SM_EN/specs.htm#wp1052333)

Says the maximum mem is 4 gig looks like I gotta go visit newegg;)

---

