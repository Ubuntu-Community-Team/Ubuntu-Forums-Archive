---
title: "Old Ubuntu 7.10, No Write-Combing inside /proc/mtrr"
date: 2009-10-23
forum: x86 64-bit Users
---

### Post by Tobis87 on 2009-10-23
Hi,

I already tried everything, but I can't get write combing enabled.

This is how my /proc/mtrr looks like:
```
reg00: base=0x00000000 (   0MB), size=65536MB: write-back, count=1
reg01: base=0xbff00000 (3071MB), size=   1MB: uncachable, count=1
reg02: base=0xc0000000 (3072MB), size=1024MB: uncachable, count=1
```

I "only" have 6gb of ram installed, so reg00 can't be right:

```
MemTotal:      6053704 kB
MemFree:       3197464 kB
Buffers:        207696 kB
Cached:        1586376 kB
SwapCached:          0 kB
Active:         968412 kB
Inactive:      1518340 kB
SwapTotal:     1566312 kB
SwapFree:      1566312 kB
Dirty:              92 kB
Writeback:           0 kB
AnonPages:      692664 kB
Mapped:          92464 kB
Slab:           213124 kB
SReclaimable:   173436 kB
SUnreclaim:      39688 kB
PageTables:      15788 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   4593164 kB
Committed_AS:  1399180 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    164640 kB
VmallocChunk: 34359564283 kB
```

I followed this guide [http://ubuntuforums.org/showthread.php?t=115104]("http://ubuntuforums.org/showthread.php?t=115104") and disabled reg00 and tried to enter reg00 in manually:
```
echo "disable=0" >| /proc/mtrr
echo "base=0x00000000 size=0x180000000 type=write-back" >| /proc/mtrr
```

But I only get "base is not aligned on a size boundary" entries inside dmesg.log and the entry is not saved to /proc/mtrr.

I also tried the program called mtrr-uncover, but it detects wrong entries, because reg00 has the size 65536MB.

Dell Precision 390
Intel 975X Motherboard
Intel Core 2 Quad Q6600
6144MB DDR2 667Mhz ECC Ram
Geforce 9600gt 1gb Green-edition

Ubuntu 7.10
Linux 2.6.23.14 #1 SMP PREEMPT x86_64 GNU/Linux
 
Thanks in advance.

**Edit:**
I now also tried the script fixmtrr.sh, which gives the command:
```
echo "base=0xc0000000 size=0x20000000 type=write-combining" >| /proc/mtrr
```

but base=0xc0000000 is already configured as:
```
reg02: base=0xc0000000 (3072MB), size=1024MB: uncachable, count=1
```

should I therefore delete reg02 and run fixmtrr?
reg02 has a size of 1024mb uncachable and 
fixmtrr gives a size of 512mb write-combining at the same base?!

---

### Post by Tobis87 on 2009-10-23
**Edit:**
I now got it working, /proc/iomem showed me the highest memory area:
```
100000000-1bbffffff : System RAM
```

```
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xbff00000 (3071MB), size=   1MB: uncachable, count=1
reg03: base=0xc0000000 (3072MB), size= 512MB: write-combining, count=1
reg04: base=0x100000000 (4096MB), size=2048MB: write-back, count=1
reg05: base=0x180000000 (6144MB), size=1024MB: write-back, count=1
reg06: base=0x1bc000000 (7104MB), size=  64MB: uncachable, count=1
```

And I created this script:
```
#! /bin/sh
echo "disable=2" > /proc/mtrr
echo "disable=1" > /proc/mtrr
echo "disable=0" > /proc/mtrr
echo "base=0x00000000 size=0x80000000 type=write-back" >| /proc/mtrr
echo "base=0x80000000 size=0x40000000 type=write-back" >| /proc/mtrr
echo "base=0xbff00000 size=0x100000 type=uncachable" >| /proc/mtrr
echo "base=0xc0000000 size=0x20000000 type=write-combining" >| /proc/mtrr
echo "base=0x100000000 size=0x80000000 type=write-back" >| /proc/mtrr
echo "base=0x180000000 size=0x40000000 type=write-back" >| /proc/mtrr
echo "base=0x1bc000000 size=0x4000000 type=uncachable" >| /proc/mtrr
```

---

