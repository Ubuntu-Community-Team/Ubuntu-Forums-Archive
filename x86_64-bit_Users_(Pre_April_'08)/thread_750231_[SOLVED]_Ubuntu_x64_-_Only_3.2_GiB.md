---
title: "[SOLVED] Ubuntu x64 - Only 3.2 GiB?"
date: 2008-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Slushdoot on 2008-04-09
I'm making this post on behalf of someone without a Ubuntu forums account.  He recently bought a Dell Vostro 400 mini tower PC that came with 4 GiB RAM from the factory.  He installed 64-bit 7.10 then 8.04 beta and both are only recognizing 3.2 GiB RAM.

uname -r returns:```
Linux hostname 2.6.24-15-generic #1 SMP Mon Apr 7 16:37:53 UTC 2008 x86_64 GNU/Linux
```

cat /proc/meminfo returns:```
MemTotal:      3345496 kB
MemFree:       2610984 kB
Buffers:         12724 kB
Cached:         300120 kB
SwapCached:          0 kB
Active:         310920 kB
Inactive:       236328 kB
SwapTotal:     9799608 kB
SwapFree:      9799608 kB
Dirty:             304 kB
Writeback:           0 kB
AnonPages:      234552 kB
Mapped:          57848 kB
Slab:            29004 kB
SReclaimable:    16164 kB
SUnreclaim:      12840 kB
PageTables:      13576 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:  11472356 kB
Committed_AS:   642372 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     24132 kB
VmallocChunk: 34359713787 kB
```
So it would appear that indeed some of the RAM isn't being recognized by his 64-bit kernel.  Any idea why this might be?  More importantly, have you fine ladies and gents any idea how to remedy the problem?

On the off chance that the solution lie somewhere in the BIOS, he checked for any options that seemed relevant to no avail.

---

### Post by fjgaude on 2008-04-09
The normal situation here it that the video adapter and other memory using devices share memory addresses with the main RAM. Thus we have address spaces reserved for these items. The BIOS is the normal place for the relocation of address spaces so that main memory sees its full space.

Most of these devices are 32-bit in nature and the BIOS is the only place to fix this issue.

---

### Post by felker2 on 2008-04-09
Look at the first 15 lines of dmesg, espicially the last line with e820. Here's the output of my 64-bit 4GB system:

> sander@sander-AMD64 :~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] Command line: root=UUID=c74f5407-1b4c-4af2-98f1-1f8806e58fe2 ro quiet pci=nomsi mem=3950M
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dbee0000 (usable)
[    0.000000]  BIOS-e820: 00000000dbee0000 - 00000000dbee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dbee3000 - 00000000dbef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dbef0000 - 00000000dbf00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used


The last e820 line ("0000000100000000 - 0000000120000000 (usable)") is the famous memory hole remapping / memory hoisting stuff. The 0x20000000 is 512 MB, so if that line is not there or not there with "usable", that's the explanation for the missing memory. If so, I would once again look in the BIOS.
The strange thing is that the Vostro 400 sounds like a new system, and I would expect that new systems would have a correct BIOS / BIOS setting... :(


Sander

---

### Post by Slushdoot on 2008-04-09
I'll have him check dmesg for that.

Perhaps a newer BIOS is out that might fix this.  We'll check.

---

### Post by Slushdoot on 2008-04-09
> I've sorted the issue now, it was in fact a BIOS issue. I was using revision 1.0.11, since my last post have updated to 1.0.13 and it now works a treat, it sees the whole 4GB. Many thanks for your efforts!

I did contact Dell and the first guy that I spoke to was trying to tell my that the limitation was an issue in Ubuntu x64, I did try to explain that this occurred on both Linux (x64) and Windows (32bit, using the /pae switch), which ruled out there being any issues with the installed OS. But, it's fixed now, never mind eh!It was indeed a BIOS version problem.  Amusing that they tried to blame it on Ubuntu... ;)

---

