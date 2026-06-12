---
title: "64-bit not seeing 4 GB of RAM"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by sci-fi guy on 2008-12-02
I just installed 4 GB of RAM (up from 1), and I went into System Monitor to see and celebrate. But for some reason, only 3.2 GB are seen by the OS. Since I only have 2 RAM slots, it can't be a (completely) bad slot.
Yes, I am using 64-bit OS and processor.

---

### Post by Waappu on 2008-12-02
Hi
Check this
[http://ubuntuforums.org/showthread.php?t=999679](http://ubuntuforums.org/showthread.php?t=999679)

---

### Post by Guilden_NL on 2008-12-02
I am replying from my Treo, so no quick access to the links you need to check out.

This happens when your BIOS isn't set up to open up a memory hole that tends to be dedicated by default by Phoenix and a few other BIOS vendors.

It's pretty easy if you have the functionality that usually exists if you have a nice motherboard. On many mid and low end systems, you don't have the ability to open it up.

Will come back in 12 hrs to post a few good links if others haven't done so already.

---

### Post by sci-fi guy on 2008-12-02
> **Guilden_NL said:**
> I am replying from my Treo, so no quick access to the links you need to check out.

This happens when your BIOS isn't set up to open up a memory hole that tends to be dedicated by default by Phoenix and a few other BIOS vendors.

It's pretty easy if you have the functionality that usually exists if you have a nice motherboard. On many mid and low end systems, you don't have the ability to open it up.

Will come back in 12 hrs to post a few good links if others haven't done so already.

Doesn't seem to be an option in the BIOS (latest version). I am using a Toshiba Satellite A205-S4587

---

### Post by felker2 on 2008-12-03
> **sci-fi guy said:**
> Doesn't seem to be an option in the BIOS (latest version). I am using a Toshiba Satellite A205-S4587

Then you're out of luck. ;-)

But seriously, as Waappu says: post the output of

```
uname -a
free -m
dmesg | head -25
```

What is the version of your BIOS. Where (URL) did you download it from?

---

### Post by sci-fi guy on 2008-12-03
> **felker2 said:**
> Then you're out of luck. ;-)

But seriously, as Waappu says: post the output of
```
$ uname -a
free -m
dmesg | head -25
```

What is the version of your BIOS. Where (URL) did you download it from?

BIOS version 5.20, from [Toshiba]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=1702259&rpn=PSAF0U&modelFilter=&selCategory=3&selFamily=1073768663&selModel=1702259|PSAF0U").

Also, I am running Debian Testing

```
$ uname -a
Linux hal9000 2.6.26-1-amd64 #1 SMP Sat Nov 8 18:25:23 UTC 2008 x86_64 GNU/Linux

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3267        866       2401          0         57        261
-/+ buffers/cache:        547       2720
Swap:         1906          0       1906

$ dmesg | head -25
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.26-1-amd64 (Debian 2.6.26-10) (waldi@debian.org) (gcc version 4.1.3 20080623 (prerelease) (Debian 4.1.2-23)) #1 SMP Sat Nov 8 18:25:23 UTC 2008
[    0.000000] Command line: root=/dev/sda2 ro quiet
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf670000 (usable)
[    0.000000]  BIOS-e820: 00000000cf670000 - 00000000cf700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf700000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 849520) 1 entries of 3200 used
[    0.000000] max_pfn_mapped = 1048576
[    0.000000] init_memory_mapping
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F7140, 0024 (r2 TOSINV)
[    0.000000] ACPI: XSDT CF67C4A0, 008C (r1 TOSINV TOSINV00  6040000  INV        0)
[    0.000000] ACPI: FACP CF683BF8, 00F4 (r3 TOSINV TOSINV00  6040000 ALAN        1)

```

---

### Post by felker2 on 2008-12-03
> **sci-fi guy said:**
> 
```
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
```


Yep: your memory that's mapped above the 0000000100000000 = 4GB limit is not shown to your 64-bit OS. 
That is a hardware / BIOS problem. You have the newest BIOS and Toshiba says it's 64-bit compatible, so that can't be the problem. Can you once again check your BIOS for something like "memory hole remapping" or "memory hoisting"?

---

### Post by sci-fi guy on 2008-12-03
> **felker2 said:**
> Yep: your memory that's mapped above the 0000000100000000 = 4GB limit is not shown to your 64-bit OS. 
That is a hardware / BIOS problem. You have the newest BIOS and Toshiba says it's 64-bit compatible, so that can't be the problem. Can you once again check your BIOS for something like "memory hole remapping" or "memory hoisting"?

Double Checked: The *only* mention of RAM in the BIOS is```
Total Memory: 4096 MB
```

Coreboot claims to be able to run on Intel 945 chipsets. I assume that it won't work on my 945GM?

---

