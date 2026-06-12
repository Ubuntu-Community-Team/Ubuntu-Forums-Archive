---
title: "My mouse gets hanged in Ubuntu, but not in Vista or XP"
date: 2007-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by sunilattri on 2007-10-04
Dear Sir, I am in trouble that after every click my usb mouse gets hanged, but I am in passion of Ubuntu.  My configuration is as below. PLEASE SUGGEST ME.

sunil@ubuntu:~$ uname -r
2.6.20-15-generic

sunil@ubuntu:~$ sudo lshw -C CPU
  *-cpu                   
       description: CPU
       product: Intel(R) Pentium(R) D CPU 2.80GHz
       vendor: Intel Corp.
       physical id: 0
       bus info: cpu@0
       version: Intel(R) Pentium(R) D CPU 2.80GHz
       slot: LGA 775
       size: 2800MHz
       capacity: 4GHz
       width: 64 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl est cid cx16 xtpr lahf_lm cpufreq

sunil@ubuntu:~$ cat /proc/meminfo
MemTotal:      1017900 kB
MemFree:        276040 kB
Buffers:         59232 kB
Cached:         360732 kB
SwapCached:          0 kB
Active:         363004 kB
Inactive:       248172 kB
SwapTotal:     1172704 kB
SwapFree:      1172704 kB
Dirty:             236 kB
Writeback:           0 kB
AnonPages:      191224 kB
Mapped:          55500 kB
Slab:            48324 kB
SReclaimable:    31788 kB
SUnreclaim:      16536 kB
PageTables:      11488 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1681652 kB
Committed_AS:   500984 kB
VmallocTotal: 34359738367 kB
VmallocUsed:      2788 kB
VmallocChunk: 34359735291 kB

THANKS IN ADVANCE.

---

