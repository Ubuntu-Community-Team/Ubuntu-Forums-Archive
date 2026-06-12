---
title: "Why can't x86_64 see 4gb?"
date: 2009-01-27
forum: x86 64-bit Users
---

### Post by jkounis on 2009-01-27
I recently upgraded from 2GB to 4GB of memory, but somehow my machine only sees around 3.3GB. I was aware that this was a limitation of 32-bit OSs, which is why I selected 64-bit Ubuntu. Is there some other limitation I'm not aware of?

According Ubuntu, my motherboard can handle 4GB:
```
sudo dmidecode -t 16
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x001B, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 4 GB
        Error Information Handle: Not Provided
        Number Of Devices: 4

```

It also thinks I have 4 slots, with 1GB each:
```
sudo dmidecode -t 6
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A0
        Bank Connections: 0
        Current Speed: Unknown
        Type: Other
        Installed Size: 1024 MB (Single-bank Connection)
        Enabled Size: 1024 MB (Single-bank Connection)
        Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A1
        Bank Connections: 2
        Current Speed: Unknown
        Type: Other
        Installed Size: 1024 MB (Single-bank Connection)
        Enabled Size: 1024 MB (Single-bank Connection)
        Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A2
        Bank Connections: 4
        Current Speed: Unknown
        Type: Other
        Installed Size: 1024 MB (Single-bank Connection)
        Enabled Size: 1024 MB (Single-bank Connection)
        Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A3
        Bank Connections: 6
        Current Speed: Unknown
        Type: Other
        Installed Size: 1024 MB (Single-bank Connection)
        Enabled Size: 1024 MB (Single-bank Connection)
        Error Status: OK

```

And lshw agrees:

```
 sudo lshw -class memory
  *-firmware
       description: BIOS
       vendor: Phoenix Technologies, LTD
       physical id: 0
       version: 6.00 PG (05/22/2006)
       size: 128KiB
       capacity: 448KiB
       capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: a
       slot: Internal Cache
       size: 32KiB
       capacity: 32KiB
       capabilities: synchronous internal write-back
  *-cache:1
       description: L2 cache
       physical id: b
       slot: External Cache
       size: 2MiB
       capacity: 2MiB
       capabilities: synchronous external write-back
  *-memory
       description: System Memory
       physical id: 1b
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMM SDRAM Synchronous
          product: None
          vendor: None
          physical id: 0
          serial: None
          slot: A0
          size: 1GiB
          width: 64 bits
     *-bank:1
          description: DIMM SDRAM Synchronous
          product: None
          vendor: None
          physical id: 1
          serial: None
          slot: A1
          size: 1GiB
          width: 64 bits
     *-bank:2
          description: DIMM SDRAM Synchronous
          product: None
          vendor: None
          physical id: 2
          serial: None
          slot: A2
          size: 1GiB
          width: 64 bits
     *-bank:3
          description: DIMM SDRAM Synchronous
          product: None
          vendor: None
          physical id: 3
          serial: None
          slot: A3
          size: 1GiB
          width: 64 bits

```

But when I ask Ubuntu how much memory it's using, the answer is only around 3.2-3.3GB:

```
 free -m
             total       used       free     shared    buffers     cached
Mem:          3267        939       2328          0         35        360
-/+ buffers/cache:        543       2724
Swap:         4094          0       4094

```

```
cat /proc/meminfo
MemTotal:      3346368 kB
MemFree:       2384304 kB
Buffers:         36640 kB
Cached:         368756 kB
SwapCached:          0 kB
Active:         582932 kB
Inactive:       247844 kB
SwapTotal:     4192956 kB
SwapFree:      4192956 kB
Dirty:             708 kB
Writeback:           0 kB
AnonPages:      425528 kB
Mapped:          69692 kB
Slab:            62072 kB
SReclaimable:    35076 kB
SUnreclaim:      26996 kB
PageTables:      20576 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   5866140 kB
Committed_AS:   939376 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    281352 kB
VmallocChunk: 34359456919 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:      7040 kB
DirectMap2M:   3399680 kB

```

Just to make sure I'm not crazy, I am using the 64-bit version of Ubuntu:
```
 uname -a
Linux pgfs 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
```

Finally, I am getting some interesting boot-up messages that may have something to do with the issue:
```
dmesg | head -40
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] Command line: root=UUID=f172eae6-f26e-4d4e-ba5b-2ba91230d5f5 ro acpi=off
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c000 (usable)
[    0.000000]  BIOS-e820: 000000000009c000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xcfee0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfee0000 page 4k
[    0.000000] kernel direct mapping tables up to cfee0000 @ 8000-e000
[    0.000000] last_map_addr: cfee0000 end: cfee0000
[    0.000000] RAMDISK: 37763000 - 37fefdfc
[    0.000000] DMI 2.3 present.
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000cfee0000
[    0.000000] Bootmem setup node 0 0000000000000000-00000000cfee0000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000c000 -  0000000000025fdf] pages 1a
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 00cfee0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [0037763000 - 0037fefdfc]          RAMDISK ==> [0037763000 - 0037fefdfc]
[    0.000000]   #4 [000009c000 - 0000100000]    BIOS reserved ==> [000009c000 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000] found SMP MP-table at [ffff8800000f36f0] 000f36f0
[    0.000000]  [ffffe20000000000-ffffe200033fffff] PMD -> [ffff880001200000-ffff8800045fffff] on node 0

```

If I'm reading the dmesg output correctly, then I assume that everything about CFEE0000 is "reserved"? Is this a BIOS limitation?

---

### Post by estyles on 2009-01-27
I don't know enough to help you with your problem, but are you sure that you don't have a video card that uses "Shared" memory?

---

### Post by piratejake on 2009-01-27
strange... i've got 4 gigs of RAM and ubuntu is registering 3.9

i'm running a 9800 GTX (512)

i wish i could help :/

---

### Post by sanderj on 2009-01-27
Your BIOS is not offering any memory above the 0000000100000000 = 4GB = 2^32 barrier. So, update your BIOS to the newest version. If that does not give more than 3.3 GB, look for something like "memory hoisting" or "memory remapping" in your BIOS settings.

BTW: as you're running X86_64 Linux, you must be using a X86_64 CPU. You could check that with "grep --color ' lm ' /proc/cpuinfo": it should give a highlighted "lm" (LongMode) text, meaning x86_64.

```

[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c000 (usable)
[    0.000000]  BIOS-e820: 000000000009c000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xcfee0 max_arch_pfn = 0x3ffffffff


```

---

### Post by jkounis on 2009-01-27
> **estyles said:**
> I don't know enough to help you with your problem, but are you sure that you don't have a video card that uses "Shared" memory?

I'm using a [EVGA e-GeForce7200GS DDR2 w/128MB on board]("http://www.evga.com/products/moreInfo.asp?pn=128-P2-N428-LR&family=GeForce%207%20Series%20Family"). (The machine is a server, so I really only need the most basic video card to drive a basic screen display that is logged out most of the time.)

When I had 2 GB memory, the system indicated that the full 2 GB of memory were available. The problem only arose after I upgraded from 2GB to 4GB, so I'm not sure about that.

I suspect it's some kind of a BIOS limitation. The dmesg output says something about memory above CFEE0000 being reserved, which is suspiciously very close to my 3.3GB limit.

---

### Post by OutOfReach on 2009-01-27
> **piratejake said:**
> strange... i've got 4 gigs of RAM and ubuntu is registering 3.9

i'm running a 9800 GTX (512)

i wish i could help :/

That's normal. BIOS and the kernel are using some memory. I'm running with 3 gigs, but it's only showing 2.9


Anyways, to the OP:
I am thinking that there might be a setting in BIOS that's causing this.

---

### Post by jespdj on 2009-01-28
As already hinted by others above, look for a setting named "memory remapping" or something similar in your BIOS and enable it.

Note that your question is a frequently asked question; if you search through the forums you'll find many other posts of users with a similar problem and you might find some more useful info.

---

### Post by Noo on 2009-01-28
I only have about 3.9 GiB available in a 4 GiB system. /proc/meminfo reports as MemTotal: 4054976 kB. That's over a 100 MiB less than there should be (4194304 kB). Is that a normal amount for the kernel and BIOS? In windows the full 4GiB is reported and the OP said that when he was using 2GiB of ram everything was reported.

---

### Post by jespdj on 2009-01-28
Noo: That's normal.

The fact that Windows reports the full 4 GB does not mean that the full 4 GB is available for applications. In fact, 32-bit Windows Vista with SP1 will report the full 4 GB, even though it cannot use more than 3.3 GB.

My Dell XPS M1530 also reports about 3.9 GB of 4 GB.

---

