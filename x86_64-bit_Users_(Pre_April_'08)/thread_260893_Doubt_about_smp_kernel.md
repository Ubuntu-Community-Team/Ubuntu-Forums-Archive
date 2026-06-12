---
title: "Doubt about smp kernel"
date: 2006-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by jsvidyad on 2006-09-19
Hi!!!

    i have some doubts that the smp kernel I installed from the ubuntu repositories is actually working. The kernel I installed was linux-amd64-k8-smp. But the output of uname -a is 
Linux garuda 2.6.15-27-amd64-k8 #1 SMP PREEMPT Sat Sep 16 01:57:42 UTC 2006 x86_64 GNU/Linux

The output from the smp kernel on the SUSE partition I installed is 
Linux garuda 2.6.16.13-4-smp #1 SMP Wed May 3 04:53:23 UTC 2006 x86_64 x86_64x86_64 GNU/Linux.

As you can see, for ubuntu, just one processor is shown by uname -a

Does this mean the ubuntu kernel is not supporting smp??

I have a core 2 duo processor. Will i have to compile my own custom kernel??  It supports Intel EM64T.

Oh, BTW, a non-smp kernel I installed from the ubuntu repositories showsthe following output for uname -a

Linux garuda 2.6.15-26-amd64-generic #1 SMP PREEMPT Fri Sep 8 19:55:50 UTC 2 006 x86_64 GNU/Linux

Note similarity with the supposedly smp kernel from the ubuntu repositories

---

### Post by kuja on 2006-09-19
You don't need to install a special smp kernel. All of the amd64 kernels support smp.

Type in "cat /proc/cpuinfo", how many cpus do you see listed? Two (identicle cpus) should be listed.

---

### Post by jsvidyad on 2006-09-19
Exactly which kernel should i install??? There are many 64 bit kernels??  I have an intel core 2 duo which supports EM64T. So, I am not sure which one I should use

---

### Post by kuja on 2006-09-19
> **jsvidyad said:**
> Exactly which kernel should i install??? There are many 64 bit kernels??  I have an intel core 2 duo which supports EM64T. So, I am not sure which one I should use

I'm not 100% sure, but I believe the linux-amd64-xeon kernel may be optimal for that processor. If not, the generic works just fine for any 64-bit processor.

---

### Post by ipc on 2006-09-25
I'm having a similar problem.  Note below that cpuinfo is only showing one processor.


root@ipc:~# uname -a
Linux ipc 2.6.15-27-amd64-k8 #1 SMP PREEMPT Sat Sep 16 01:57:42 UTC 2006 x86_64 GNU/Linux

root@ipc:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165
stepping        : 2
cpu MHz         : 2591.956
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 5192.59
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

### Post by ipc on 2006-09-25
Hrm, found some more clues via dmesg.  I'll futz with my bios and see if I missed anything obvious.  Windows XP and OpenSuse have no problem detecting both cores with the same BIOS settings.

[    0.000000] Bootdata ok (command line is root=/dev/sdb5 ro single)
[    0.000000] Linux version 2.6.15-27-amd64-k8 (buildd@king) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Sep 16 01:57:42 UTC 2006
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffa0000 - 00000000bffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffae000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x00000000000fad00
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x03000629 MSFT 0x00000097) @ 0x00000000bffa0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x03000629 MSFT 0x00000097) @ 0x00000000bffa0200
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x03000629 MSFT 0x00000097) @ 0x00000000bffa03f0
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x03000629 MSFT 0x00000097) @ 0x00000000bffae040
[    0.000000] ACPI: DSDT (v001  A0466 A0466001 0x00000001 INTL 0x02002026) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 0000000140000000
[    0.000000] Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000] No mptable found.
[    0.000000] On node 0 totalpages: 1029538
[    0.000000]   DMA zone: 3018 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 767960 pages, LIFO batch:31
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages, LIFO batch:0
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x908
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3f700000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ 8000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 8000000
[    0.000000] SMP: Allowing 2 CPUs, 2 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sdb5 ro single
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
[    0.000000] time.c: Using 3.579545 MHz PM timer.
[    0.000000] time.c: Detected 2591.956 MHz processor.
[   61.452540] Console: colour VGA+ 80x25
[   61.456062] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   61.458980] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   61.490448] Memory: 4039020k/5242880k available (2151k kernel code, 154512k reserved, 754k data, 180k init)
[   61.569409] Calibrating delay using timer specific routine.. 5192.59 BogoMIPS (lpj=10385189)
[   61.569537] Security Framework v1.0.0 initialized
[   61.569586] SELinux:  Disabled at boot.
[   61.569646] Mount-cache hash table entries: 256
[   61.570109] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   61.570157] CPU: L2 Cache: 1024K (64 bytes/line)
[   61.570203] CPU 0(2) -> Node 0 -> Core 0
[   61.570253] mtrr: v2.0 (20020519)
[   61.570302] SMP alternatives: switching to UP code
[   61.570554] checking if image is initramfs... it is
[   61.995517] Freeing initrd memory: 7098k freed
[   61.999770] ACPI: Looking for DSDT ... not found!
[   62.001628] ACPI: setting ELCR to 0200 (from 0cb8)
[   62.002127] weird, boot CPU (#0) not listed by the BIOS.
[   62.002174] SMP motherboard not detected.
[   62.002223] Using local APIC timer interrupts.
[   62.040843] Detected 17.999 MHz APIC timer.
[   62.040903] testing NMI watchdog ... OK.
[   62.081039] SMP disabled
[   62.081122] Brought up 1 CPUs

---

### Post by ipc on 2006-09-25
Problem Solved: BIOS Settings "ACPI 2.0 Support" and "ACPI APIC Support" were set to 'No' and 'Disabled'.  After setting them to 'Yes' and 'Enabled' both cores were detected.

ipc@ipc:~$ uname -a
Linux ipc 2.6.15-27-amd64-k8 #1 SMP PREEMPT Sat Sep 16 01:57:42 UTC 2006 x86_64 GNU/Linux
ipc@ipc:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165
stepping        : 2
cpu MHz         : 2591.973
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 5215.97
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165
stepping        : 2
cpu MHz         : 2591.973
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 5184.20
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

ipc@ipc:~$ dmesg
[    0.000000] Bootdata ok (command line is root=/dev/sdb5 ro quiet splash)
[    0.000000] Linux version 2.6.15-27-amd64-k8 (buildd@king) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Sep 16 01:57:42 UTC 2006
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffa0000 - 00000000bffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffae000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] ACPI: RSDP (v002 ACPIAM                                ) @ 0x00000000000fad00
[    0.000000] ACPI: XSDT (v001 A M I  OEMXSDT  0x03000629 MSFT 0x00000097) @ 0x00000000bffa0100
[    0.000000] ACPI: FADT (v003 A M I  OEMFACP  0x03000629 MSFT 0x00000097) @ 0x00000000bffa0290
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x03000629 MSFT 0x00000097) @ 0x00000000bffa0390
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x03000629 MSFT 0x00000097) @ 0x00000000bffa03f0
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x03000629 MSFT 0x00000097) @ 0x00000000bffae040
[    0.000000] ACPI: DSDT (v001  A0466 A0466001 0x00000001 INTL 0x02002026) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 0000000140000000
[    0.000000] Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000] On node 0 totalpages: 1029536
[    0.000000]   DMA zone: 3016 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 767960 pages, LIFO batch:31
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages, LIFO batch:0
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x908
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3f700000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ 8000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 8000000
[    0.000000] SMP: Allowing 3 CPUs, 1 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sdb5 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
[    0.000000] time.c: Using 3.579545 MHz PM timer.
[    0.000000] time.c: Detected 2591.973 MHz processor.
[   96.078780] Console: colour VGA+ 80x25
[   96.080690] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   96.083542] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   96.115255] Memory: 4038988k/5242880k available (2151k kernel code, 154544k reserved, 754k data, 180k init)
[   96.191658] Calibrating delay using timer specific routine.. 5215.97 BogoMIPS (lpj=10431956)
[   96.191697] Security Framework v1.0.0 initialized
[   96.191701] SELinux:  Disabled at boot.
[   96.191717] Mount-cache hash table entries: 256
[   96.191804] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)[   96.191806] CPU: L2 Cache: 1024K (64 bytes/line)
[   96.191808] CPU 0(2) -> Node 0 -> Core 0
[   96.191813] mtrr: v2.0 (20020519)
[   96.191818] SMP alternatives: switching to UP code
[   96.192026] checking if image is initramfs... it is
[   96.617240] Freeing initrd memory: 7098k freed
[   96.621136] ACPI: Looking for DSDT ... not found!
[   96.664525] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   96.664572]  failed.
[   96.664573] timer doesn't work through the IO-APIC - disabling NMI Watchdog!
[   96.667308] Uhhuh. NMI received for unknown reason 3d.
[   96.667309] Dazed and confused, but trying to continue
[   96.667311] Do you have a strange power saving mode enabled?
[   96.705374]  works.
[   96.705376] Using local APIC timer interrupts.
[   96.743952] Detected 17.999 MHz APIC timer.
[   96.744049] SMP alternatives: switching to SMP code
[   96.744183] Booting processor 1/2 APIC 0x1
[   96.754785] Initializing CPU#1
[   96.835704] Calibrating delay using timer specific routine.. 5184.20 BogoMIPS (lpj=10368411)
[   96.835712] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)[   96.835713] CPU: L2 Cache: 1024K (64 bytes/line)
[   96.835715] CPU 1(2) -> Node 0 -> Core 1
[   96.835797] Dual Core AMD Opteron(tm) Processor 165 stepping 02
[   96.835802] CPU 1: Syncing TSC to CPU 0.
[   96.835743] CPU 1: synchronized TSC with CPU 0 (last diff 0 cycles, maxerr 539 cycles)
[   96.835748] Brought up 2 CPUs

---

