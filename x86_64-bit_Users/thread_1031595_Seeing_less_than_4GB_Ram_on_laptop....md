---
title: "Seeing less than 4GB Ram on laptop..."
date: 2009-01-05
forum: x86 64-bit Users
---

### Post by JagerQ on 2009-01-05
I'm using a Sager NP8660 with the Montevina chipset, a dedicated NVidia 9800M GT w/ 512 MB of graphics memory and 4 gigabytes of ram. As far as I can tell the video card can only use the dedicated video memory and doesn't share the system memory.

I've got Vista x64 installed and am able to use the entire 4 GB of ram. During the POST, the BIOS shows a full 4096.

When I tried to install a linux partition, I couldn't get Ubuntu to install without adding a mem=4096m flag. I ended up installing it off the alternate CD and it works fine for the most part.

The problem is that I can only see 2.4 _Gibi_bytes of memory. I also see 1.3 Gibibytes in the Swap. 

That adds up to about 4 GB of total memory, but I'm not sure if it's possible that the swap partition is actually on my ram? It definitely made a 1.35 gigabyte swap partition during the install, but I'm not sure what's going on with it.

Regardless, does anyone have any idea how I can get at the rest of the memory? Thanks!

---

### Post by vgrisham on 2009-01-05
In your BIOS, go to memory management and look for something that will allow your memory aperture to be seen by your operating system. (I can't remember what the setting is called exactly. I'm at work right now and don't have access to my 64-bit system).

---

### Post by JagerQ on 2009-01-05
Yeah, sorry that's a no-go on the BIOS fix as I have no option for the memory hole/mapping.

---

### Post by vgrisham on 2009-01-05
Hopefully then, someone else will jump in with a solution.

Even if you had the mapping feature, there's no guarantee it'll work with Ubuntu (or Windows for that matter). I have an Asus A8N-SLI Deluxe mobo. Enabling either or both mapping features blows away my onboard ethernet card and causes numerous graphics errors. I have 4 gig, but Ubuntu nevers sees more than 3. I haven't yet tried it with Intrepid though.

---

### Post by JagerQ on 2009-01-05
Here is some more info.

cat /proc/meminfo 
MemTotal:      2568488 kB
MemFree:       2005360 kB
Buffers:         15100 kB
Cached:         201304 kB
SwapCached:          0 kB
Active:         321780 kB
Inactive:       125224 kB
SwapTotal:     1413680 kB
SwapFree:      1413680 kB
Dirty:             156 kB
Writeback:           0 kB
AnonPages:      230600 kB
Mapped:          60176 kB
Slab:            41156 kB
SReclaimable:    17432 kB
SUnreclaim:      23724 kB
PageTables:      15120 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   2697924 kB
Committed_AS:   564632 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    313224 kB
VmallocChunk: 34359424507 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:     43008 kB
DirectMap2M:   2576384 kB

free -l 
             total       used       free     shared    buffers     cached
Mem:       2568488     590084    1978404          0      15528     210780
Low:       2568488     590084    1978404
High:            0          0          0
-/+ buffers/cache:     363776    2204712
Swap:      1413680          0    1413680

dmesg data shown below...

---

### Post by felker2 on 2009-01-05
Which CPU are you using? You can check that with "grep name /proc/cpuinfo".

What's the output of "dmesg | head -25", "free -m" and of "uname -a"?

---

### Post by JagerQ on 2009-01-05
grep name /proc/cpuinfo
model name	: Intel(R) Core(TM)2 Duo CPU     P9500  @ 2.53GHz
model name	: Intel(R) Core(TM)2 Duo CPU     P9500  @ 2.53GHz

free -m
             total       used       free     shared    buffers     cached
Mem:          2508        730       1777          0         21        295
-/+ buffers/cache:        413       2094
Swap:         1380          0       1380

uname -a
Linux ubuntu 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

dmesg | head -52
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] Command line: root=UUID=0a24029a-0afd-4287-8d6a-7e52780d09d7 ro mem=4096m quiet splash quietboot 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000099400 (usable)
[    0.000000]  BIOS-e820: 0000000000099400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f8b1000 (usable)
[    0.000000]  BIOS-e820: 000000009f8b1000 - 000000009f8b7000 (reserved)
[    0.000000]  BIOS-e820: 000000009f8b7000 - 000000009f9b2000 (usable)
[    0.000000]  BIOS-e820: 000000009f9b2000 - 000000009fa0f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fa0f000 - 000000009fb07000 (usable)
[    0.000000]  BIOS-e820: 000000009fb07000 - 000000009fd0f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fd0f000 - 000000009fd18000 (usable)
[    0.000000]  BIOS-e820: 000000009fd18000 - 000000009fd1f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fd1f000 - 000000009fd67000 (usable)
[    0.000000]  BIOS-e820: 000000009fd67000 - 000000009fd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fd9f000 - 000000009fde3000 (usable)
[    0.000000]  BIOS-e820: 000000009fde3000 - 000000009fdfd000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009fdfd000 - 000000009fe00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000160000000 (usable)
[    0.000000] user-defined physical RAM map:
[    0.000000]  user: 0000000000000000 - 0000000000099400 (usable)
[    0.000000]  user: 0000000000099400 - 00000000000a0000 (reserved)
[    0.000000]  user: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  user: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  user: 0000000000100000 - 000000009f8b1000 (usable)
[    0.000000]  user: 000000009f8b1000 - 000000009f8b7000 (reserved)
[    0.000000]  user: 000000009f8b7000 - 000000009f9b2000 (usable)
[    0.000000]  user: 000000009f9b2000 - 000000009fa0f000 (reserved)
[    0.000000]  user: 000000009fa0f000 - 000000009fb07000 (usable)
[    0.000000]  user: 000000009fb07000 - 000000009fd0f000 (reserved)
[    0.000000]  user: 000000009fd0f000 - 000000009fd18000 (usable)
[    0.000000]  user: 000000009fd18000 - 000000009fd1f000 (reserved)
[    0.000000]  user: 000000009fd1f000 - 000000009fd67000 (usable)
[    0.000000]  user: 000000009fd67000 - 000000009fd9f000 (ACPI NVS)
[    0.000000]  user: 000000009fd9f000 - 000000009fde3000 (usable)
[    0.000000]  user: 000000009fde3000 - 000000009fdfd000 (ACPI data)
[    0.000000]  user: 000000009fdfd000 - 000000009fe00000 (usable)
[    0.000000] last_pfn = 0x9fe00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 009fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 9fe00000 @ 8000-c000
[    0.000000] last_map_addr: 9fe00000 end: 9fe00000
[    0.000000] RAMDISK: 377b7000 - 37fefeb4
[    0.000000] DMI present.

---

### Post by felker2 on 2009-01-05
> **JagerQ said:**
> 
[    0.000000]  BIOS-e820: 000000009fdfd000 - 000000009fe00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000160000000 (usable)
<snip>
[    0.000000] user-defined physical RAM map:
<snip>
[    0.000000]  user: 000000009fdfd000 - 000000009fe00000 (usable)
[    0.000000] last_pfn = 0x9fe00 max_arch_pfn = 0x3ffffffff


You're throwing away 0x60000000 = 1 610 612 736 bytes of RAM: the part 0000000100000000 - 0000000160000000 is usable, but not used.

It's (somehow) caused by the "user-defined physical RAM map". I've only seen that when giving something like "mem=3000m" as an boot option. But the strange thing is that I don't see such an option in your boot parameters.

What if you specify "mem=4000m" or "mem=3500m" in the boot or menu.lst? What do the dmesg and mem commands report then?

---

### Post by theozzlives on 2009-01-05
do you have ubuntu-desktop or AMD64?

---

### Post by JagerQ on 2009-01-05
mem=4000m" in the boot

free -m
             total       used       free     shared    buffers     cached
Mem:          2508        674       1833          0         18        252
-/+ buffers/cache:        403       2104
Swap:         1380          0       1380


Here's the entire dmesg:

[HTML][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] Command line: root=UUID=0a24029a-0afd-4287-8d6a-7e52780d09d7 ro mem=4000m quiet splash quietboot 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000099400 (usable)
[    0.000000]  BIOS-e820: 0000000000099400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f8b1000 (usable)
[    0.000000]  BIOS-e820: 000000009f8b1000 - 000000009f8b7000 (reserved)
[    0.000000]  BIOS-e820: 000000009f8b7000 - 000000009f9b2000 (usable)
[    0.000000]  BIOS-e820: 000000009f9b2000 - 000000009fa0f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fa0f000 - 000000009fb07000 (usable)
[    0.000000]  BIOS-e820: 000000009fb07000 - 000000009fd0f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fd0f000 - 000000009fd18000 (usable)
[    0.000000]  BIOS-e820: 000000009fd18000 - 000000009fd1f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fd1f000 - 000000009fd67000 (usable)
[    0.000000]  BIOS-e820: 000000009fd67000 - 000000009fd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fd9f000 - 000000009fde3000 (usable)
[    0.000000]  BIOS-e820: 000000009fde3000 - 000000009fdfd000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009fdfd000 - 000000009fe00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000160000000 (usable)
[    0.000000] user-defined physical RAM map:
[    0.000000]  user: 0000000000000000 - 0000000000099400 (usable)
[    0.000000]  user: 0000000000099400 - 00000000000a0000 (reserved)
[    0.000000]  user: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  user: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  user: 0000000000100000 - 000000009f8b1000 (usable)
[    0.000000]  user: 000000009f8b1000 - 000000009f8b7000 (reserved)
[    0.000000]  user: 000000009f8b7000 - 000000009f9b2000 (usable)
[    0.000000]  user: 000000009f9b2000 - 000000009fa0f000 (reserved)
[    0.000000]  user: 000000009fa0f000 - 000000009fb07000 (usable)
[    0.000000]  user: 000000009fb07000 - 000000009fd0f000 (reserved)
[    0.000000]  user: 000000009fd0f000 - 000000009fd18000 (usable)
[    0.000000]  user: 000000009fd18000 - 000000009fd1f000 (reserved)
[    0.000000]  user: 000000009fd1f000 - 000000009fd67000 (usable)
[    0.000000]  user: 000000009fd67000 - 000000009fd9f000 (ACPI NVS)
[    0.000000]  user: 000000009fd9f000 - 000000009fde3000 (usable)
[    0.000000]  user: 000000009fde3000 - 000000009fdfd000 (ACPI data)
[    0.000000]  user: 000000009fdfd000 - 000000009fe00000 (usable)
[    0.000000] last_pfn = 0x9fe00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 009fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 9fe00000 @ 8000-c000
[    0.000000] last_map_addr: 9fe00000 end: 9fe00000
[    0.000000] RAMDISK: 377b7000 - 37fefeb4
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F7680, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 9FDF5565, 0064 (r1 PTLTD  	 XSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 9FDE7000, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 9FDE8000, 77A3 (r2 Intel  CANTIGA   6040000 INTL 20050624)
[    0.000000] ACPI: FACS 9FD9EFC0, 0040
[    0.000000] ACPI: HPET 9FDFCEFC, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 9FDFCF34, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: APIC 9FDFCF70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 9FDFCFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 9FDE6000, 0655 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 9FDE5000, 0259 (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 9FDE4000, 020F (r1  PmRef    ApTst     3000 INTL 20050624)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000009fe00000
[    0.000000] Bootmem setup node 0 0000000000000000-000000009fe00000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000a000 -  000000000001dfbf] pages 14
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 009fe00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377b7000 - 0037fefeb4]          RAMDISK ==> [00377b7000 - 0037fefeb4]
[    0.000000]   #4 [0000099400 - 0000100000]    BIOS reserved ==> [0000099400 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [ffff8800000f7720] 000f7720
[    0.000000]  [ffffe20000000000-ffffe200027fffff] PMD -> [ffff880001200000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000099
[    0.000000]     0: 0x00000100 -> 0x0009f8b1
[    0.000000]     0: 0x0009f8b7 -> 0x0009f9b2
[    0.000000]     0: 0x0009fa0f -> 0x0009fb07
[    0.000000]     0: 0x0009fd0f -> 0x0009fd18
[    0.000000]     0: 0x0009fd1f -> 0x0009fd67
[    0.000000]     0: 0x0009fd9f -> 0x0009fde3
[    0.000000]     0: 0x0009fdfd -> 0x0009fe00
[    0.000000] On node 0 totalpages: 654037
[    0.000000]   DMA zone: 2100 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 639876 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000099000 - 000000000009a000
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009f8b1000 - 000000009f8b7000
[    0.000000] PM: Registered nosave memory: 000000009f9b2000 - 000000009fa0f000
[    0.000000] PM: Registered nosave memory: 000000009fb07000 - 000000009fd0f000
[    0.000000] PM: Registered nosave memory: 000000009fd18000 - 000000009fd1f000
[    0.000000] PM: Registered nosave memory: 000000009fd67000 - 000000009fd9f000
[    0.000000] PM: Registered nosave memory: 000000009fde3000 - 000000009fdfd000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: 9fe00000:60200000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 641976
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=0a24029a-0afd-4287-8d6a-7e52780d09d7 ro mem=4000m quiet splash quietboot 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2526.997 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2559532k/2619392k available (3112k kernel code, 56616k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.99 BogoMIPS (lpj=10107988)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 0/0 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] CPU0: Thermal monitoring enabled (TM2)
[    0.004000] using mwait in idle threads.
[    0.004013] ACPI: Core revision 20080609
[    0.008353] ACPI: Checking initramfs for custom DSDT
[    0.312415] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.352920] CPU0: Intel(R) Core(TM)2 Duo CPU     P9500  @ 2.53GHz stepping 06
[    0.352923] Using local APIC timer interrupts.
[    0.356023] APIC timer calibration result 16625026
[    0.356024] Detected 16.625 MHz APIC timer.
[    0.356126] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5054.05 BogoMIPS (lpj=10108107)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.444864] CPU1: Intel(R) Core(TM)2 Duo CPU     P9500  @ 2.53GHz stepping 06
[    0.444882] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.448057] Brought up 2 CPUs
[    0.448059] Total of 2 processors activated (10108.04 BogoMIPS).
[    0.448101] CPU0 attaching sched-domain:
[    0.448103]  domain 0: span 0-1 level MC
[    0.448105]   groups: 0 1
[    0.448108]   domain 1: span 0-1 level NODE
[    0.448109]    groups: 0-1
[    0.448113] CPU1 attaching sched-domain:
[    0.448114]  domain 0: span 0-1 level MC
[    0.448115]   groups: 1 0
[    0.448118]   domain 1: span 0-1 level NODE
[    0.448119]    groups: 0-1
[    0.448193] net_namespace: 1552 bytes
[    0.448193] Booting paravirtualized kernel on bare hardware
[    0.448240] Time: 19:21:19  Date: 01/05/09
[    0.448264] NET: Registered protocol family 16
[    0.448278] ACPI: bus type pci registered
[    0.448278] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.448278] PCI: Not using MMCONFIG.
[    0.448278] PCI: Using configuration type 1 for base access
[    0.448735] ACPI: EC: Look up EC in DSDT
[    0.454925] ACPI: BIOS _OSI(Linux) query ignored
[    0.454926] ACPI: DMI System Vendor: CLEVO CO.              
[    0.454928] ACPI: DMI Product Name: M860TU                 
[    0.454929] ACPI: DMI Product Version: Not Applicable
[    0.454930] ACPI: DMI Board Name: M860TU        
[    0.454931] ACPI: DMI BIOS Vendor: Phoenix Technologies LTD
[    0.454932] ACPI: DMI BIOS Date: 07/24/2008
[    0.454933] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
[    0.454934] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[    0.455721] ACPI: Interpreter enabled
[    0.455722] ACPI: (supports S0 S3 S4 S5)
[    0.455735] ACPI: Using IOAPIC for interrupt routing
[    0.455787] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.457049] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.464751] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.464761] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.488394] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.488394] ACPI: EC: driver started in interrupt mode
[    0.488394] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.488394] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.488394] pci 0000:00:01.0: PME# disabled
[    0.488394] PCI: 0000:00:1a.0 reg 20 io port: [1800, 181f]
[    0.488394] PCI: 0000:00:1a.1 reg 20 io port: [1820, 183f]
[    0.488394] PCI: 0000:00:1a.2 reg 20 io port: [1840, 185f]
[    0.488394] PCI: 0000:00:1a.7 reg 10 32bit mmio: [f4704800, f4704bff]
[    0.488394] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.488398] pci 0000:00:1a.7: PME# disabled
[    0.488426] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f4700000, f4703fff]
[    0.488458] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.488461] pci 0000:00:1b.0: PME# disabled
[    0.488502] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.488506] pci 0000:00:1c.0: PME# disabled
[    0.488547] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.488550] pci 0000:00:1c.1: PME# disabled
[    0.488592] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.488595] pci 0000:00:1c.2: PME# disabled
[    0.488637] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.488640] pci 0000:00:1c.4: PME# disabled
[    0.488682] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.488685] pci 0000:00:1c.5: PME# disabled
[    0.488725] PCI: 0000:00:1d.0 reg 20 io port: [1860, 187f]
[    0.488781] PCI: 0000:00:1d.1 reg 20 io port: [1880, 189f]
[    0.488836] PCI: 0000:00:1d.2 reg 20 io port: [18a0, 18bf]
[    0.488895] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f4704c00, f4704fff]
[    0.488939] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.488942] pci 0000:00:1d.7: PME# disabled
[    0.489082] PCI: 0000:00:1f.2 reg 10 io port: [18f0, 18f7]
[    0.489087] PCI: 0000:00:1f.2 reg 14 io port: [18e4, 18e7]
[    0.489091] PCI: 0000:00:1f.2 reg 18 io port: [18e8, 18ef]
[    0.489096] PCI: 0000:00:1f.2 reg 1c io port: [18e0, 18e3]
[    0.489101] PCI: 0000:00:1f.2 reg 20 io port: [18c0, 18df]
[    0.489106] PCI: 0000:00:1f.2 reg 24 32bit mmio: [f4704000, f47047ff]
[    0.489127] pci 0000:00:1f.2: PME# supported from D3hot
[    0.489129] pci 0000:00:1f.2: PME# disabled
[    0.489146] PCI: 0000:00:1f.3 reg 10 64bit mmio: [0, ff]
[    0.489158] PCI: 0000:00:1f.3 reg 20 io port: [1c00, 1c1f]
[    0.489206] PCI: 0000:01:00.0 reg 10 32bit mmio: [ce000000, ceffffff]
[    0.489213] PCI: 0000:01:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.489228] PCI: 0000:01:00.0 reg 1c 64bit mmio: [cc000000, cdffffff]
[    0.489234] PCI: 0000:01:00.0 reg 24 io port: [2000, 207f]
[    0.489240] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.489286] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.489288] PCI: bridge 0000:00:01.0 32bit mmio: [cc000000, ceffffff]
[    0.489292] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.489335] PCI: 0000:02:00.0 reg 10 32bit mmio: [f4100000, f41003ff]
[    0.489348] PCI: 0000:02:00.0 reg 18 io port: [3000, 30ff]
[    0.489373] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, ffff]
[    0.489424] PCI: bridge 0000:00:1c.0 io port: [3000, 3fff]
[    0.489427] PCI: bridge 0000:00:1c.0 32bit mmio: [f4100000, f41fffff]
[    0.489466] PCI: bridge 0000:00:1c.1 io port: [4000, 4fff]
[    0.489469] PCI: bridge 0000:00:1c.1 32bit mmio: [f8000000, fbffffff]
[    0.489474] PCI: bridge 0000:00:1c.1 64bit mmio pref: [f0000000, f3ffffff]
[    0.489544] PCI: 0000:06:00.0 reg 10 64bit mmio: [f4200000, f4201fff]
[    0.489620] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.489625] pci 0000:06:00.0: PME# disabled
[    0.489657] PCI: bridge 0000:00:1c.2 32bit mmio: [f4200000, f42fffff]
[    0.489708] PCI: 0000:07:00.0 reg 10 32bit mmio: [f4300800, f4300fff]
[    0.489718] PCI: 0000:07:00.0 reg 14 32bit mmio: [f4301000, f430107f]
[    0.489744] PCI: 0000:07:00.0 reg 20 32bit mmio: [f4300400, f430047f]
[    0.489754] PCI: 0000:07:00.0 reg 24 32bit mmio: [f4300000, f430007f]
[    0.489826] PCI: 0000:07:00.1 reg 10 32bit mmio: [f4301400, f43014ff]
[    0.489928] PCI: 0000:07:00.2 reg 10 32bit mmio: [f4301800, f43018ff]
[    0.490030] PCI: 0000:07:00.3 reg 10 32bit mmio: [f4301c00, f4301cff]
[    0.492069] PCI: bridge 0000:00:1c.4 32bit mmio: [f4300000, f43fffff]
[    0.492116] PCI: 0000:08:00.0 reg 10 io port: [5000, 50ff]
[    0.492134] PCI: 0000:08:00.0 reg 18 64bit mmio: [f4400000, f4400fff]
[    0.492142] PCI: 0000:08:00.0 reg 20 32bit mmio: [f4000000, f400ffff]
[    0.492155] PCI: 0000:08:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.492181] pci 0000:08:00.0: supports D1
[    0.492182] pci 0000:08:00.0: supports D2
[    0.492183] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.492188] pci 0000:08:00.0: PME# disabled
[    0.492218] PCI: bridge 0000:00:1c.5 io port: [5000, 5fff]
[    0.492221] PCI: bridge 0000:00:1c.5 32bit mmio: [f4400000, f44fffff]
[    0.492226] PCI: bridge 0000:00:1c.5 64bit mmio pref: [f4000000, f40fffff]
[    0.492269] pci 0000:00:1e.0: transparent bridge
[    0.492307] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.492547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.492655] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.492870] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.492978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.493083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.493191] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.504122] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.504228] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.504333] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.504440] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.504544] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.504648] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.504755] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.504859] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.504911] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.504911] pnp: PnP ACPI init
[    0.504911] ACPI: bus type pnp registered
[    0.508154] pnp: PnP ACPI: found 10 devices
[    0.508177] ACPI: ACPI bus type pnp unregistered
[    0.508232] PCI: Using ACPI for IRQ routing

[    0.524037] NET: Registered protocol family 8

[    0.524039] NET: Registered protocol family 20
[    0.524050] NetLabel: Initializing
[    0.524050] NetLabel:  domain hash size = 128
[    0.524050] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.524057] NetLabel:  unlabeled traffic allowed by default
[    0.524074] PCI-GART: No AMD northbridge found.
[    0.524078] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.524081] hpet0: 4 64-bit timers, 14318180 Hz
[    0.526040] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.526042]    actual entries 65586
[    0.526102] AppArmor: AppArmor Filesystem Enabled
[    0.528038] Switched to high resolution mode on CPU 0
[    0.528908] Switched to high resolution mode on CPU 1
[    0.540020] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.540025] system 00:05: ioport range 0x680-0x69f has been reserved
[    0.540027] system 00:05: ioport range 0x400-0x47f has been reserved
[    0.540029] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.540030] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.540032] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.540034] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.540036] system 00:05: ioport range 0x1180-0x11ff has been reserved
[    0.540037] system 00:05: ioport range 0x164e-0x164f has been reserved
[    0.540039] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.540046] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.540048] system 00:09: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.540050] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.540052] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.540053] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.540055] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.540057] system 00:09: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.540059] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.544979] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.544982] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.544984] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.544987] pci 0000:00:01.0:   MEM window: 0xcc000000-0xceffffff
[    0.544989] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.544993] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.544995] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.544999] pci 0000:00:1c.0:   MEM window: 0xf4100000-0xf41fffff
[    0.545002] pci 0000:00:1c.0:   PREFETCH window: 0x000000a0000000-0x000000a00fffff
[    0.545008] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.545010] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.545014] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xfbffffff
[    0.545017] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
[    0.545022] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.545023] pci 0000:00:1c.2:   IO window: disabled
[    0.545027] pci 0000:00:1c.2:   MEM window: 0xf4200000-0xf42fffff
[    0.545030] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.545035] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:07
[    0.545037] pci 0000:00:1c.4:   IO window: disabled
[    0.545040] pci 0000:00:1c.4:   MEM window: 0xf4300000-0xf43fffff
[    0.545043] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.545049] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.545051] pci 0000:00:1c.5:   IO window: 0x5000-0x5fff
[    0.545055] pci 0000:00:1c.5:   MEM window: 0xf4400000-0xf44fffff
[    0.545058] pci 0000:00:1c.5:   PREFETCH window: 0x000000f4000000-0x000000f40fffff
[    0.545063] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.545064] pci 0000:00:1e.0:   IO window: disabled
[    0.545068] pci 0000:00:1e.0:   MEM window: disabled
[    0.545071] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.545081] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.545084] pci 0000:00:01.0: setting latency timer to 64
[    0.545090] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.545094] pci 0000:00:1c.0: setting latency timer to 64
[    0.545099] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.545102] pci 0000:00:1c.1: setting latency timer to 64
[    0.545108] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.545112] pci 0000:00:1c.2: setting latency timer to 64
[    0.545117] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.545120] pci 0000:00:1c.4: setting latency timer to 64
[    0.545126] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.545129] pci 0000:00:1c.5: setting latency timer to 64
[    0.545134] pci 0000:00:1e.0: setting latency timer to 64
[    0.545137] bus: 00 index 0 io port: [0, ffff]
[    0.545138] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.545140] bus: 01 index 0 io port: [2000, 2fff]
[    0.545141] bus: 01 index 1 mmio: [cc000000, ceffffff]
[    0.545142] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.545143] bus: 01 index 3 mmio: [0, 0]
[    0.545145] bus: 02 index 0 io port: [3000, 3fff]
[    0.545146] bus: 02 index 1 mmio: [f4100000, f41fffff]
[    0.545147] bus: 02 index 2 mmio: [a0000000, a00fffff]
[    0.545148] bus: 02 index 3 mmio: [0, 0]
[    0.545150] bus: 04 index 0 io port: [4000, 4fff]
[    0.545151] bus: 04 index 1 mmio: [f8000000, fbffffff]
[    0.545152] bus: 04 index 2 mmio: [f0000000, f3ffffff]
[    0.545153] bus: 04 index 3 mmio: [0, 0]
[    0.545155] bus: 06 index 0 mmio: [0, 0]
[    0.545156] bus: 06 index 1 mmio: [f4200000, f42fffff]
[    0.545157] bus: 06 index 2 mmio: [0, 0]
[    0.545158] bus: 06 index 3 mmio: [0, 0]
[    0.545159] bus: 07 index 0 mmio: [0, 0]
[    0.545160] bus: 07 index 1 mmio: [f4300000, f43fffff]
[    0.545162] bus: 07 index 2 mmio: [0, 0]
[    0.545163] bus: 07 index 3 mmio: [0, 0]
[    0.545164] bus: 08 index 0 io port: [5000, 5fff]
[    0.545165] bus: 08 index 1 mmio: [f4400000, f44fffff]
[    0.545166] bus: 08 index 2 mmio: [f4000000, f40fffff]
[    0.545168] bus: 08 index 3 mmio: [0, 0]
[    0.545169] bus: 09 index 0 mmio: [0, 0]
[    0.545170] bus: 09 index 1 mmio: [0, 0]
[    0.545171] bus: 09 index 2 mmio: [0, 0]
[    0.545172] bus: 09 index 3 io port: [0, ffff]
[    0.545173] bus: 09 index 4 mmio: [0, ffffffffffffffff]
[    0.545180] NET: Registered protocol family 2
[    0.584120] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.585078] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.588363] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.588887] TCP: Hash tables configured (established 524288 bind 65536)
[    0.588889] TCP reno registered
[    0.600094] NET: Registered protocol family 1
[    0.600194] checking if image is initramfs... it is
[    1.210544] Freeing initrd memory: 8419k freed
[    1.213289] Simple Boot Flag at 0x36 set to 0x1
[    1.214082] audit: initializing netlink socket (disabled)
[    1.214103] type=2000 audit(1231183279.213:1): initialized
[    1.218882] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.220771] VFS: Disk quotas dquot_6.5.1
[    1.220836] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.220914] msgmni has been set to 5015
[    1.221007] io scheduler noop registered
[    1.221009] io scheduler anticipatory registered
[    1.221011] io scheduler deadline registered
[    1.221104] io scheduler cfq registered (default)
[    1.221242] pci 0000:01:00.0: Boot video device
[    1.221343] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.221369] pcieport-driver 0000:00:01.0: found MSI capability
[    1.221393] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.221425] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.221455] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.221521] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.221548] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.221576] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.221607] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.221637] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.221710] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.221737] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.221765] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.221798] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.221830] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.221902] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.221929] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.221957] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.221989] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.222018] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.222089] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.222117] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.222145] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.222174] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.222205] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.222280] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.222308] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.222335] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.222364] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.222393] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.246660] hpet_resources: 0xfed00000 is busy
[    1.246723] Linux agpgart interface v0.103
[    1.246726] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.248285] brd: module loaded
[    1.248335] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.248419] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.252633] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.255069] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.255073] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.255075] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.255077] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.255078] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.276147] mice: PS/2 mouse device common for all mice
[    1.276238] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.276259] rtc0: alarms up to one month, y3k, hpet irqs
[    1.276286] cpuidle: using governor ladder
[    1.276287] cpuidle: using governor menu
[    1.276563] TCP cubic registered
[    1.276714] registered taskstats version 1
[    1.276833]   Magic number: 9:182:394
[    1.276929] rtc_cmos 00:06: setting system clock to 2009-01-05 19:21:20 UTC (1231183280)
[    1.276932] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.276933] EDD information not available.
[    1.276977] Freeing unused kernel memory: 536k freed
[    1.277182] Write protecting the kernel read-only data: 4348k
[    1.312207] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.449039] fuse init (API version 7.9)
[    1.485539] ACPI: SSDT 9FD1AC20, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.485939] ACPI: SSDT 9FD18620, 05C5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.563154] Monitor-Mwait will be used to enter C-1 state
[    1.563157] Monitor-Mwait will be used to enter C-2 state
[    1.563158] Monitor-Mwait will be used to enter C-3 state
[    1.563303] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.563346] processor ACPI0007:00: registered as cooling_device0
[    1.563349] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.563767] ACPI: SSDT 9FD19CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20050624)
[    1.564098] ACPI: SSDT 9FD19F20, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
[    1.605073] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.605107] processor ACPI0007:01: registered as cooling_device1
[    1.605110] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.606904] Marking TSC unstable due to TSC halts in idle
[    1.612330] thermal LNXTHERM:01: registered as thermal_zone0
[    1.620663] ACPI: Thermal Zone [TZ0] (45 C)
[    1.841551] usbcore: registered new interface driver usbfs
[    1.841570] usbcore: registered new interface driver hub
[    1.842563] usbcore: registered new device driver usb
[    1.848720] USB Universal Host Controller Interface driver v3.0
[    1.848762] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.848770] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.848773] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.848812] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.848843] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    1.848964] usb usb1: configuration #1 chosen from 1 choice
[    1.848983] hub 1-0:1.0: USB hub found
[    1.848988] hub 1-0:1.0: 2 ports detected
[    1.937446] No dock devices found.
[    1.962041] SCSI subsystem initialized
[    1.993150] libata version 3.00 loaded.
[    2.056244] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.056252] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.056254] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.056277] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.056307] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    2.056374] usb usb2: configuration #1 chosen from 1 choice
[    2.056392] hub 2-0:1.0: USB hub found
[    2.056397] hub 2-0:1.0: 2 ports detected
[    2.264203] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.264211] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.264214] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.264234] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.264264] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    2.264331] usb usb3: configuration #1 chosen from 1 choice
[    2.264349] hub 3-0:1.0: USB hub found
[    2.264354] hub 3-0:1.0: 2 ports detected
[    2.364360] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.364374] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.364377] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.364397] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.368302] ehci_hcd 0000:00:1a.7: debug port 1
[    2.368307] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.368313] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf4704800
[    2.384061] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.384114] usb usb4: configuration #1 chosen from 1 choice
[    2.384136] hub 4-0:1.0: USB hub found
[    2.384141] hub 4-0:1.0: 6 ports detected
[    2.500085] Clocksource tsc unstable (delta = -112039926 ns)
[    2.592986] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.592992] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.592995] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.593016] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.593044] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    2.593108] usb usb5: configuration #1 chosen from 1 choice
[    2.593127] hub 5-0:1.0: USB hub found
[    2.593132] hub 5-0:1.0: 2 ports detected
[    2.696860] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.696865] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.696867] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.696885] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.696905] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    2.696970] usb usb6: configuration #1 chosen from 1 choice
[    2.696988] hub 6-0:1.0: USB hub found
[    2.696993] hub 6-0:1.0: 2 ports detected
[    2.752067] usb 4-1: new high speed USB device using ehci_hcd and address 2
[    2.800214] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.800219] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.800221] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.800237] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.800262] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    2.800325] usb usb7: configuration #1 chosen from 1 choice
[    2.800344] hub 7-0:1.0: USB hub found
[    2.800349] hub 7-0:1.0: 2 ports detected
[    2.904383] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.904391] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.904394] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.904411] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    2.908318] ehci_hcd 0000:00:1d.7: debug port 1
[    2.908323] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.908326] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4704c00
[    2.925038] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.925500] usb usb8: configuration #1 chosen from 1 choice
[    2.925888] hub 8-0:1.0: USB hub found
[    2.925892] hub 8-0:1.0: 6 ports detected
[    3.031374] ahci 0000:00:1f.2: version 3.0
[    3.031383] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.031455] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x13 impl SATA mode
[    3.031458] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag led clo pmp pio slum part 
[    3.031461] ahci 0000:00:1f.2: setting latency timer to 64
[    3.031620] scsi0 : ahci
[    3.031719] scsi1 : ahci
[    3.031780] scsi2 : ahci
[    3.031833] scsi3 : ahci
[    3.031885] scsi4 : ahci
[    3.031916] ata1: SATA max UDMA/133 abar m2048@0xf4704000 port 0xf4704100 irq 2297
[    3.031919] ata2: SATA max UDMA/133 abar m2048@0xf4704000 port 0xf4704180 irq 2297
[    3.031920] ata3: DUMMY
[    3.031921] ata4: DUMMY
[    3.031923] ata5: SATA max UDMA/133 abar m2048@0xf4704000 port 0xf4704300 irq 2297
[    3.160620] usb 4-1: configuration #1 chosen from 1 choice
[    3.512068] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.513162] ata1.00: ATA-7: ST9120823AS, 3.AAB, max UDMA/133
[    3.513166] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.513894] ata1.00: configured for UDMA/133
[    3.616062] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.792818] usb 2-1: configuration #1 chosen from 1 choice
[    3.996101] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.009446] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, SX01, max UDMA/100, ATAPI AN
[    4.023788] ata2.00: configured for UDMA/100
[    4.340100] ata5: SATA link down (SStatus 0 SControl 300)
[    4.340235] scsi 0:0:0:0: Direct-Access     ATA      ST9120823AS      3.AA PQ: 0 ANSI: 5
[    4.341705] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560S  SX01 PQ: 0 ANSI: 5
[    4.341850] ohci1394 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.341857] ohci1394 0000:07:00.0: setting latency timer to 64
[    4.393549] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f4300800-f4300fff]  Max Packet=[512]  IR/IT contexts=[4/4]
[    4.400285] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.400298] r8169 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.400311] r8169 0000:08:00.0: setting latency timer to 64
[    4.400555] eth0: RTL8168c/8111c at 0xffffc20000644000, 00:90:f5:6f:d7:f8, XID 3c4000c0 IRQ 2296
[    4.414349] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.414378] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.431630] Driver 'sr' needs updating - please use bus_type methods
[    4.433869] Driver 'sd' needs updating - please use bus_type methods
[    4.433931] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.433945] sd 0:0:0:0: [sda] Write Protect is off
[    4.433947] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.433968] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.434020] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.434033] sd 0:0:0:0: [sda] Write Protect is off
[    4.434034] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.434056] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.434059]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.438638] Uniform CD-ROM driver Revision: 3.20
[    4.438721] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.481370]  sda1 sda2 < sda5 sda6 >
[    4.514747] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.776867] PM: Starting manual resume from disk
[    4.776870] PM: Resume from partition 8:6
[    4.776871] PM: Checking hibernation image.
[    4.777040] PM: Resume from disk failed.
[    4.805893] kjournald starting.  Commit interval 5 seconds
[    4.805920] EXT3-fs: mounted filesystem with ordered data mode.
[    5.673259] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[58745bf80090f514]
[   12.014573] udevd version 124 started
[   12.330005] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.359962] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.479162] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   12.501034] ACPI: Power Button (FF) [PWRF]
[   12.676968] ACPI: AC Adapter [AC] (on-line)
[   12.677314] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   12.705043] ACPI: Power Button (CM) [PWRB]
[   12.705109] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   12.733021] ACPI: Sleep Button (CM) [SLPB]
[   12.733083] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   12.753561] ACPI: Lid Switch [LID0]
[   12.807409] ACPI: Battery Slot [BAT0] (battery present)
[   12.807539] ACPI: WMI: Mapper loaded
[   13.320461] nvidia: module license 'NVIDIA' taints kernel.
[   13.573073] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.573085] nvidia 0000:01:00.0: setting latency timer to 64
[   13.573297] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   13.641076] sdhci: Secure Digital Host Controller Interface driver
[   13.641078] sdhci: Copyright(c) Pierre Ossman
[   13.653293] sdhci-pci 0000:07:00.1: SDHCI controller found [197b:2382] (rev 0)
[   13.653310] sdhci-pci 0000:07:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.653342] sdhci-pci 0000:07:00.1: setting latency timer to 64
[   13.653383] mmc0: SDHCI controller on PCI [0000:07:00.1] using DMA
[   13.653391] sdhci-pci 0000:07:00.2: SDHCI controller found [197b:2381] (rev 0)
[   13.653404] sdhci-pci 0000:07:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.653410] sdhci-pci 0000:07:00.2: Refusing to bind to secondary interface.
[   13.653416] sdhci-pci 0000:07:00.2: PCI INT A disabled
[   13.709147] Linux video capture interface: v2.00
[   13.851976] uvcvideo: Found UVC 1.00 device USB2.0 Camera (5986:0300)
[   13.868608] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb4/4-1/4-1:1.0/input/input6
[   13.888145] usbcore: registered new interface driver uvcvideo
[   13.888159] USB Video Class driver (v0.1.0)
[   13.913279] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.913281] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.913362] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.913369] iwlagn 0000:06:00.0: setting latency timer to 64
[   13.913388] iwlagn: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   13.941826] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.950071] iwlagn 0000:06:00.0: PCI INT A disabled
[   13.950538] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.252316] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x202000
[   14.287292] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   14.638424] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.638451] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.673943] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   14.956508] loop: module loaded
[   15.014100] lp: driver loaded but no devices found
[   15.177565] Adding 1413680k swap on /dev/sda6.  Priority:-1 extents:1 across:1413680k
[   15.904202] EXT3 FS on sda5, internal journal
[   17.020791] type=1505 audit(1231204896.138:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4304
[   17.114136] type=1505 audit(1231204896.234:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4309
[   17.114296] type=1505 audit(1231204896.234:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4309
[   17.255156] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.618188] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.787156] ppdev: user-space parallel port driver
[   21.704467] Bluetooth: Core ver 2.13
[   21.706379] NET: Registered protocol family 31
[   21.706388] Bluetooth: HCI device and connection manager initialized
[   21.706395] Bluetooth: HCI socket layer initialized
[   21.724984] Bluetooth: L2CAP ver 2.11
[   21.724996] Bluetooth: L2CAP socket layer initialized
[   21.753840] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.753852] Bluetooth: BNEP filters: protocol multicast
[   21.799790] Bridge firewalling registered
[   21.801698] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   21.820477] Bluetooth: SCO (Voice Link) ver 0.6
[   21.820489] Bluetooth: SCO socket layer initialized
[   21.917678] Bluetooth: RFCOMM socket layer initialized
[   21.917836] Bluetooth: RFCOMM TTY layer initialized
[   21.917841] Bluetooth: RFCOMM ver 1.10
[   26.117446] r8169: eth0: link down
[   26.157523] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.157587] iwlagn 0000:06:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   26.157708] firmware: requesting iwlwifi-5000-1.ucode
[   28.502069] Registered led device: iwl-phy0:radio
[   28.502247] Registered led device: iwl-phy0:assoc
[   28.502369] Registered led device: iwl-phy0:RX
[   28.502484] Registered led device: iwl-phy0:TX
[   29.690927] NET: Registered protocol family 17
[   34.500672] NET: Registered protocol family 10
[   34.503348] lo: Disabled Privacy Extensions
[   34.505587] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.508033] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.504092] ACPI: EC: missing confirmations, switch off interrupt mode.
[   37.008099] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[   37.008130] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.TZ0_._TMP] (Node ffff88009f236b00), AE_TIME
[   66.517292] CPU0 attaching NULL sched-domain.
[   66.517316] CPU1 attaching NULL sched-domain.
[   66.528192] CPU0 attaching sched-domain:
[   66.528209]  domain 0: span 0-1 level MC
[   66.528214]   groups: 0 1
[   66.528223]   domain 1: span 0-1 level NODE
[   66.528228]    groups: 0-1
[   66.528237] CPU1 attaching sched-domain:
[   66.528241]  domain 0: span 0-1 level MC
[   66.528245]   groups: 1 0
[   66.528252]   domain 1: span 0-1 level NODE
[   66.528257]    groups: 0-1
[   70.599060] wlan0: authenticate with AP 00:15:e9:d6:94:b4
[   70.675837] wlan0: authenticated
[   70.675857] wlan0: associate with AP 00:15:e9:d6:94:b4
[   70.703182] wlan0: RX AssocResp from 00:15:e9:d6:94:b4 (capab=0x431 status=0 aid=2)
[   70.703196] wlan0: associated
[   70.806687] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   81.616057] wlan0: no IPv6 routers present[/HTML]

---

### Post by JagerQ on 2009-01-05
> **theozzlives said:**
> do you have ubuntu-desktop or AMD64?

It's the 64-bit desktop version.

---

### Post by JagerQ on 2009-01-05
I can manually map it to less.

> **felker2 said:**
>  "mem=2048m" 

free -m
             total       used       free     shared    buffers     cached
Mem:          2009        540       1468          0         16        202
-/+ buffers/cache:        321       1687
Swap:         1380          0       1380


[HTML][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] Command line: root=UUID=0a24029a-0afd-4287-8d6a-7e52780d09d7 ro mem=2048m quiet splash quietboot 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000099400 (usable)
[    0.000000]  BIOS-e820: 0000000000099400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f8b1000 (usable)
[    0.000000]  BIOS-e820: 000000009f8b1000 - 000000009f8b7000 (reserved)
[    0.000000]  BIOS-e820: 000000009f8b7000 - 000000009f9b2000 (usable)
[    0.000000]  BIOS-e820: 000000009f9b2000 - 000000009fa0f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fa0f000 - 000000009fb07000 (usable)
[    0.000000]  BIOS-e820: 000000009fb07000 - 000000009fd0f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fd0f000 - 000000009fd18000 (usable)
[    0.000000]  BIOS-e820: 000000009fd18000 - 000000009fd1f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fd1f000 - 000000009fd67000 (usable)
[    0.000000]  BIOS-e820: 000000009fd67000 - 000000009fd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fd9f000 - 000000009fde3000 (usable)
[    0.000000]  BIOS-e820: 000000009fde3000 - 000000009fdfd000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009fdfd000 - 000000009fe00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000160000000 (usable)
[    0.000000] user-defined physical RAM map:
[    0.000000]  user: 0000000000000000 - 0000000000099400 (usable)
[    0.000000]  user: 0000000000099400 - 00000000000a0000 (reserved)
[    0.000000]  user: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  user: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  user: 0000000000100000 - 0000000080000000 (usable)
[    0.000000]  user: 000000009f8b1000 - 000000009f8b7000 (reserved)
[    0.000000]  user: 000000009f9b2000 - 000000009fa0f000 (reserved)
[    0.000000]  user: 000000009fb07000 - 000000009fd0f000 (reserved)
[    0.000000]  user: 000000009fd18000 - 000000009fd1f000 (reserved)
[    0.000000]  user: 000000009fd67000 - 000000009fd9f000 (ACPI NVS)
[    0.000000]  user: 000000009fde3000 - 000000009fdfd000 (ACPI data)
[    0.000000] last_pfn = 0x80000 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 0080000000 page 2M
[    0.000000] kernel direct mapping tables up to 80000000 @ 8000-b000
[    0.000000] last_map_addr: 80000000 end: 80000000
[    0.000000] RAMDISK: 377b7000 - 37fefeb4
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F7680, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 9FDF5565, 0064 (r1 PTLTD  	 XSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 9FDE7000, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 9FDE8000, 77A3 (r2 Intel  CANTIGA   6040000 INTL 20050624)
[    0.000000] ACPI: FACS 9FD9EFC0, 0040
[    0.000000] ACPI: HPET 9FDFCEFC, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 9FDFCF34, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: APIC 9FDFCF70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 9FDFCFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 9FDE6000, 0655 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 9FDE5000, 0259 (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 9FDE4000, 020F (r1  PmRef    ApTst     3000 INTL 20050624)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000080000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000080000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [0000000000009000 -  0000000000018fff] pages 10
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 0080000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377b7000 - 0037fefeb4]          RAMDISK ==> [00377b7000 - 0037fefeb4]
[    0.000000]   #4 [0000099400 - 0000100000]    BIOS reserved ==> [0000099400 - 0000100000]
[    0.000000]   #5 [0000008000 - 0000009000]          PGTABLE ==> [0000008000 - 0000009000]
[    0.000000] found SMP MP-table at [ffff8800000f7720] 000f7720
[    0.000000]  [ffffe20000000000-ffffe20001ffffff] PMD -> [ffff880001200000-ffff8800031fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000099
[    0.000000]     0: 0x00000100 -> 0x00080000
[    0.000000] On node 0 totalpages: 524185
[    0.000000]   DMA zone: 2101 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 512064 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000099000 - 000000000009a000
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: 9fdfd000:60203000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 514165
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=0a24029a-0afd-4287-8d6a-7e52780d09d7 ro mem=2048m quiet splash quietboot 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2526.977 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2048372k/2097152k available (3112k kernel code, 48368k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.95 BogoMIPS (lpj=10107908)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 0/0 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] CPU0: Thermal monitoring enabled (TM2)
[    0.004000] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20080609
[    0.006466] ACPI: Checking initramfs for custom DSDT
[    0.311347] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.351043] CPU0: Intel(R) Core(TM)2 Duo CPU     P9500  @ 2.53GHz stepping 06
[    0.351046] Using local APIC timer interrupts.
[    0.352023] APIC timer calibration result 16624918
[    0.352024] Detected 16.624 MHz APIC timer.
[    0.352127] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5053.97 BogoMIPS (lpj=10107953)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.440867] CPU1: Intel(R) Core(TM)2 Duo CPU     P9500  @ 2.53GHz stepping 06
[    0.440885] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.444057] Brought up 2 CPUs
[    0.444059] Total of 2 processors activated (10107.93 BogoMIPS).
[    0.444101] CPU0 attaching sched-domain:
[    0.444103]  domain 0: span 0-1 level MC
[    0.444105]   groups: 0 1
[    0.444108]   domain 1: span 0-1 level NODE
[    0.444109]    groups: 0-1
[    0.444113] CPU1 attaching sched-domain:
[    0.444114]  domain 0: span 0-1 level MC
[    0.444115]   groups: 1 0
[    0.444118]   domain 1: span 0-1 level NODE
[    0.444119]    groups: 0-1
[    0.444193] net_namespace: 1552 bytes
[    0.444193] Booting paravirtualized kernel on bare hardware
[    0.444240] Time: 20:31:42  Date: 01/05/09
[    0.444263] NET: Registered protocol family 16
[    0.444277] ACPI: bus type pci registered
[    0.444277] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.444277] PCI: Not using MMCONFIG.
[    0.444277] PCI: Using configuration type 1 for base access
[    0.444734] ACPI: EC: Look up EC in DSDT
[    0.450922] ACPI: BIOS _OSI(Linux) query ignored
[    0.450924] ACPI: DMI System Vendor: CLEVO CO.              
[    0.450925] ACPI: DMI Product Name: M860TU                 
[    0.450926] ACPI: DMI Product Version: Not Applicable
[    0.450927] ACPI: DMI Board Name: M860TU        
[    0.450928] ACPI: DMI BIOS Vendor: Phoenix Technologies LTD
[    0.450929] ACPI: DMI BIOS Date: 07/24/2008
[    0.450930] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
[    0.450932] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[    0.451717] ACPI: Interpreter enabled
[    0.451719] ACPI: (supports S0 S3 S4 S5)
[    0.451731] ACPI: Using IOAPIC for interrupt routing
[    0.451784] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.453047] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.459727] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.460043] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.480401] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.480401] ACPI: EC: driver started in interrupt mode
[    0.480401] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.480401] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.480401] pci 0000:00:01.0: PME# disabled
[    0.480401] PCI: 0000:00:1a.0 reg 20 io port: [1800, 181f]
[    0.480401] PCI: 0000:00:1a.1 reg 20 io port: [1820, 183f]
[    0.480401] PCI: 0000:00:1a.2 reg 20 io port: [1840, 185f]
[    0.480401] PCI: 0000:00:1a.7 reg 10 32bit mmio: [f4704800, f4704bff]
[    0.480401] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.480401] pci 0000:00:1a.7: PME# disabled
[    0.480417] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f4700000, f4703fff]
[    0.480449] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.480452] pci 0000:00:1b.0: PME# disabled
[    0.480493] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.480496] pci 0000:00:1c.0: PME# disabled
[    0.480538] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.480541] pci 0000:00:1c.1: PME# disabled
[    0.480583] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.480586] pci 0000:00:1c.2: PME# disabled
[    0.480628] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.480631] pci 0000:00:1c.4: PME# disabled
[    0.480673] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.480676] pci 0000:00:1c.5: PME# disabled
[    0.480716] PCI: 0000:00:1d.0 reg 20 io port: [1860, 187f]
[    0.480773] PCI: 0000:00:1d.1 reg 20 io port: [1880, 189f]
[    0.480830] PCI: 0000:00:1d.2 reg 20 io port: [18a0, 18bf]
[    0.480890] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f4704c00, f4704fff]
[    0.480933] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.480937] pci 0000:00:1d.7: PME# disabled
[    0.481077] PCI: 0000:00:1f.2 reg 10 io port: [18f0, 18f7]
[    0.481082] PCI: 0000:00:1f.2 reg 14 io port: [18e4, 18e7]
[    0.481087] PCI: 0000:00:1f.2 reg 18 io port: [18e8, 18ef]
[    0.481091] PCI: 0000:00:1f.2 reg 1c io port: [18e0, 18e3]
[    0.481096] PCI: 0000:00:1f.2 reg 20 io port: [18c0, 18df]
[    0.481101] PCI: 0000:00:1f.2 reg 24 32bit mmio: [f4704000, f47047ff]
[    0.481122] pci 0000:00:1f.2: PME# supported from D3hot
[    0.481125] pci 0000:00:1f.2: PME# disabled
[    0.481141] PCI: 0000:00:1f.3 reg 10 64bit mmio: [0, ff]
[    0.481153] PCI: 0000:00:1f.3 reg 20 io port: [1c00, 1c1f]
[    0.481202] PCI: 0000:01:00.0 reg 10 32bit mmio: [ce000000, ceffffff]
[    0.481208] PCI: 0000:01:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.481223] PCI: 0000:01:00.0 reg 1c 64bit mmio: [cc000000, cdffffff]
[    0.481229] PCI: 0000:01:00.0 reg 24 io port: [2000, 207f]
[    0.481235] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.481282] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.481284] PCI: bridge 0000:00:01.0 32bit mmio: [cc000000, ceffffff]
[    0.481287] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.481331] PCI: 0000:02:00.0 reg 10 32bit mmio: [f4100000, f41003ff]
[    0.481344] PCI: 0000:02:00.0 reg 18 io port: [3000, 30ff]
[    0.481370] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, ffff]
[    0.481421] PCI: bridge 0000:00:1c.0 io port: [3000, 3fff]
[    0.481424] PCI: bridge 0000:00:1c.0 32bit mmio: [f4100000, f41fffff]
[    0.481462] PCI: bridge 0000:00:1c.1 io port: [4000, 4fff]
[    0.481465] PCI: bridge 0000:00:1c.1 32bit mmio: [f8000000, fbffffff]
[    0.481470] PCI: bridge 0000:00:1c.1 64bit mmio pref: [f0000000, f3ffffff]
[    0.481539] PCI: 0000:06:00.0 reg 10 64bit mmio: [f4200000, f4201fff]
[    0.481615] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.481620] pci 0000:06:00.0: PME# disabled
[    0.481652] PCI: bridge 0000:00:1c.2 32bit mmio: [f4200000, f42fffff]
[    0.481704] PCI: 0000:07:00.0 reg 10 32bit mmio: [f4300800, f4300fff]
[    0.481713] PCI: 0000:07:00.0 reg 14 32bit mmio: [f4301000, f430107f]
[    0.481740] PCI: 0000:07:00.0 reg 20 32bit mmio: [f4300400, f430047f]
[    0.481749] PCI: 0000:07:00.0 reg 24 32bit mmio: [f4300000, f430007f]
[    0.481822] PCI: 0000:07:00.1 reg 10 32bit mmio: [f4301400, f43014ff]
[    0.481925] PCI: 0000:07:00.2 reg 10 32bit mmio: [f4301800, f43018ff]
[    0.482027] PCI: 0000:07:00.3 reg 10 32bit mmio: [f4301c00, f4301cff]
[    0.482131] PCI: bridge 0000:00:1c.4 32bit mmio: [f4300000, f43fffff]
[    0.482176] PCI: 0000:08:00.0 reg 10 io port: [5000, 50ff]
[    0.484055] PCI: 0000:08:00.0 reg 18 64bit mmio: [f4400000, f4400fff]
[    0.484062] PCI: 0000:08:00.0 reg 20 32bit mmio: [f4000000, f400ffff]
[    0.484075] PCI: 0000:08:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.484101] pci 0000:08:00.0: supports D1
[    0.484103] pci 0000:08:00.0: supports D2
[    0.484104] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.484108] pci 0000:08:00.0: PME# disabled
[    0.484138] PCI: bridge 0000:00:1c.5 io port: [5000, 5fff]
[    0.484141] PCI: bridge 0000:00:1c.5 32bit mmio: [f4400000, f44fffff]
[    0.484146] PCI: bridge 0000:00:1c.5 64bit mmio pref: [f4000000, f40fffff]
[    0.484190] pci 0000:00:1e.0: transparent bridge
[    0.484228] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.484467] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.484575] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.484789] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.484897] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.485002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.485110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.496122] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.496228] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.496333] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.496439] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.496544] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.496648] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.496755] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.496858] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.496910] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.496910] pnp: PnP ACPI init
[    0.496910] ACPI: bus type pnp registered
[    0.496910] pnp: PnP ACPI: found 10 devices
[    0.496910] ACPI: ACPI bus type pnp unregistered
[    0.500134] PCI: Using ACPI for IRQ routing
[    0.516038] NET: Registered protocol family 8
[    0.516039] NET: Registered protocol family 20
[    0.516050] NetLabel: Initializing
[    0.516050] NetLabel:  domain hash size = 128
[    0.516050] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.516057] NetLabel:  unlabeled traffic allowed by default
[    0.516074] PCI-GART: No AMD northbridge found.
[    0.516078] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.516081] hpet0: 4 64-bit timers, 14318180 Hz
[    0.518039] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.518041]    actual entries 65586
[    0.518101] AppArmor: AppArmor Filesystem Enabled
[    0.520038] Switched to high resolution mode on CPU 0
[    0.520910] Switched to high resolution mode on CPU 1
[    0.532020] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.532025] system 00:05: ioport range 0x680-0x69f has been reserved
[    0.532027] system 00:05: ioport range 0x400-0x47f has been reserved
[    0.532029] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.532030] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.532032] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.532034] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.532036] system 00:05: ioport range 0x1180-0x11ff has been reserved
[    0.532037] system 00:05: ioport range 0x164e-0x164f has been reserved
[    0.532039] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.532046] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.532048] system 00:09: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.532050] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.532052] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.532053] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.532055] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.532057] system 00:09: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.532059] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.536983] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.536985] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.536987] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.536990] pci 0000:00:01.0:   MEM window: 0xcc000000-0xceffffff
[    0.536993] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.536997] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.536999] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.537003] pci 0000:00:1c.0:   MEM window: 0xf4100000-0xf41fffff
[    0.537006] pci 0000:00:1c.0:   PREFETCH window: 0x000000a0000000-0x000000a00fffff
[    0.537011] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.537013] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.537018] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xfbffffff
[    0.537021] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
[    0.537026] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.537027] pci 0000:00:1c.2:   IO window: disabled
[    0.537031] pci 0000:00:1c.2:   MEM window: 0xf4200000-0xf42fffff
[    0.537034] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.537039] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:07
[    0.537040] pci 0000:00:1c.4:   IO window: disabled
[    0.537044] pci 0000:00:1c.4:   MEM window: 0xf4300000-0xf43fffff
[    0.537047] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.537053] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.537055] pci 0000:00:1c.5:   IO window: 0x5000-0x5fff
[    0.537059] pci 0000:00:1c.5:   MEM window: 0xf4400000-0xf44fffff
[    0.537062] pci 0000:00:1c.5:   PREFETCH window: 0x000000f4000000-0x000000f40fffff
[    0.537067] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.537068] pci 0000:00:1e.0:   IO window: disabled
[    0.537072] pci 0000:00:1e.0:   MEM window: disabled
[    0.537075] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.537085] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.537089] pci 0000:00:01.0: setting latency timer to 64
[    0.537095] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.537098] pci 0000:00:1c.0: setting latency timer to 64
[    0.537104] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.537107] pci 0000:00:1c.1: setting latency timer to 64
[    0.537113] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.537117] pci 0000:00:1c.2: setting latency timer to 64
[    0.537122] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.537125] pci 0000:00:1c.4: setting latency timer to 64
[    0.537131] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.537134] pci 0000:00:1c.5: setting latency timer to 64
[    0.537139] pci 0000:00:1e.0: setting latency timer to 64
[    0.537142] bus: 00 index 0 io port: [0, ffff]
[    0.537143] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.537145] bus: 01 index 0 io port: [2000, 2fff]
[    0.537146] bus: 01 index 1 mmio: [cc000000, ceffffff]
[    0.537147] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.537149] bus: 01 index 3 mmio: [0, 0]
[    0.537150] bus: 02 index 0 io port: [3000, 3fff]
[    0.537151] bus: 02 index 1 mmio: [f4100000, f41fffff]
[    0.537152] bus: 02 index 2 mmio: [a0000000, a00fffff]
[    0.537154] bus: 02 index 3 mmio: [0, 0]
[    0.537155] bus: 04 index 0 io port: [4000, 4fff]
[    0.537156] bus: 04 index 1 mmio: [f8000000, fbffffff]
[    0.537157] bus: 04 index 2 mmio: [f0000000, f3ffffff]
[    0.537158] bus: 04 index 3 mmio: [0, 0]
[    0.537160] bus: 06 index 0 mmio: [0, 0]
[    0.537161] bus: 06 index 1 mmio: [f4200000, f42fffff]
[    0.537162] bus: 06 index 2 mmio: [0, 0]
[    0.537163] bus: 06 index 3 mmio: [0, 0]
[    0.537164] bus: 07 index 0 mmio: [0, 0]
[    0.537165] bus: 07 index 1 mmio: [f4300000, f43fffff]
[    0.537167] bus: 07 index 2 mmio: [0, 0]
[    0.537168] bus: 07 index 3 mmio: [0, 0]
[    0.537169] bus: 08 index 0 io port: [5000, 5fff]
[    0.537170] bus: 08 index 1 mmio: [f4400000, f44fffff]
[    0.537171] bus: 08 index 2 mmio: [f4000000, f40fffff]
[    0.537173] bus: 08 index 3 mmio: [0, 0]
[    0.537174] bus: 09 index 0 mmio: [0, 0]
[    0.537175] bus: 09 index 1 mmio: [0, 0]
[    0.537176] bus: 09 index 2 mmio: [0, 0]
[    0.537177] bus: 09 index 3 io port: [0, ffff]
[    0.537178] bus: 09 index 4 mmio: [0, ffffffffffffffff]
[    0.537185] NET: Registered protocol family 2
[    0.576077] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.576606] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.577797] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.578202] TCP: Hash tables configured (established 262144 bind 65536)
[    0.578204] TCP reno registered
[    0.588072] NET: Registered protocol family 1
[    0.588163] checking if image is initramfs... it is
[    1.199084] Freeing initrd memory: 8419k freed
[    1.201829] Simple Boot Flag at 0x36 set to 0x1
[    1.202611] audit: initializing netlink socket (disabled)
[    1.202632] type=2000 audit(1231187503.201:1): initialized
[    1.207385] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.209278] VFS: Disk quotas dquot_6.5.1
[    1.209344] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.209422] msgmni has been set to 4017
[    1.209511] io scheduler noop registered
[    1.209513] io scheduler anticipatory registered
[    1.209514] io scheduler deadline registered
[    1.209608] io scheduler cfq registered (default)
[    1.209748] pci 0000:01:00.0: Boot video device
[    1.209848] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.209874] pcieport-driver 0000:00:01.0: found MSI capability
[    1.209898] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.209930] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.209960] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.210026] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.210053] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.210081] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.210113] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.210142] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.210215] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.210242] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.210270] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.210303] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.210334] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.210407] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.210434] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.210462] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.210494] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.210523] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.210594] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.210622] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.210649] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.210679] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.210709] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.210786] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.210813] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.210841] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.210870] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.210899] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.234926] hpet_resources: 0xfed00000 is busy
[    1.234990] Linux agpgart interface v0.103
[    1.234993] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.237004] brd: module loaded
[    1.237054] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.237138] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.241392] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.244194] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.244198] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.244200] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.244201] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.244203] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.260099] mice: PS/2 mouse device common for all mice
[    1.260190] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.260211] rtc0: alarms up to one month, y3k, hpet irqs
[    1.260238] cpuidle: using governor ladder
[    1.260240] cpuidle: using governor menu
[    1.260516] TCP cubic registered
[    1.260668] registered taskstats version 1
[    1.260790]   Magic number: 9:941:547
[    1.260883] rtc_cmos 00:06: setting system clock to 2009-01-05 20:31:43 UTC (1231187503)
[    1.260885] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.260886] EDD information not available.
[    1.260930] Freeing unused kernel memory: 536k freed
[    1.261135] Write protecting the kernel read-only data: 4348k
[    1.296952] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.373972] fuse init (API version 7.9)
[    1.434718] ACPI: SSDT 9FD1AC20, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.435122] ACPI: SSDT 9FD18620, 05C5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.437172] Monitor-Mwait will be used to enter C-1 state
[    1.437174] Monitor-Mwait will be used to enter C-2 state
[    1.437176] Monitor-Mwait will be used to enter C-3 state
[    1.564066] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.564108] processor ACPI0007:00: registered as cooling_device0
[    1.564111] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.564535] ACPI: SSDT 9FD19CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20050624)
[    1.564859] ACPI: SSDT 9FD19F20, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
[    1.565769] Marking TSC unstable due to TSC halts in idle
[    1.565896] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.565945] processor ACPI0007:01: registered as cooling_device1
[    1.565948] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.573519] thermal LNXTHERM:01: registered as thermal_zone0
[    1.582196] ACPI: Thermal Zone [TZ0] (43 C)
[    1.714687] usbcore: registered new interface driver usbfs
[    1.714703] usbcore: registered new interface driver hub
[    1.720113] usbcore: registered new device driver usb
[    1.721346] USB Universal Host Controller Interface driver v3.0
[    1.721381] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.721388] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.721391] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.721419] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.721449] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    1.721546] usb usb1: configuration #1 chosen from 1 choice
[    1.721564] hub 1-0:1.0: USB hub found
[    1.721569] hub 1-0:1.0: 2 ports detected
[    1.932214] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.932222] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.932225] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.932248] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    1.932279] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    1.932344] usb usb2: configuration #1 chosen from 1 choice
[    1.932363] hub 2-0:1.0: USB hub found
[    1.932368] hub 2-0:1.0: 2 ports detected
[    1.965048] No dock devices found.
[    1.981844] SCSI subsystem initialized
[    2.010178] libata version 3.00 loaded.
[    2.137189] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.137197] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.137199] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.137219] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.137248] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    2.137316] usb usb3: configuration #1 chosen from 1 choice
[    2.137336] hub 3-0:1.0: USB hub found
[    2.137341] hub 3-0:1.0: 2 ports detected
[    2.241232] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.241245] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.241248] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.241271] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.245167] ehci_hcd 0000:00:1a.7: debug port 1
[    2.245172] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.245178] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf4704800
[    2.261016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.261079] usb usb4: configuration #1 chosen from 1 choice
[    2.261099] hub 4-0:1.0: USB hub found
[    2.261104] hub 4-0:1.0: 6 ports detected
[    2.468354] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.468362] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.468365] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.468384] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.468415] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    2.468483] usb usb5: configuration #1 chosen from 1 choice
[    2.468501] hub 5-0:1.0: USB hub found
[    2.468507] hub 5-0:1.0: 2 ports detected
[    2.500085] Clocksource tsc unstable (delta = -113383431 ns)
[    2.572251] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.572256] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.572259] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.572274] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.572294] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    2.572364] usb usb6: configuration #1 chosen from 1 choice
[    2.572381] hub 6-0:1.0: USB hub found
[    2.572386] hub 6-0:1.0: 2 ports detected
[    2.676247] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.676252] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.676254] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.676269] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.676294] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    2.676355] usb usb7: configuration #1 chosen from 1 choice
[    2.676373] hub 7-0:1.0: USB hub found
[    2.676377] hub 7-0:1.0: 2 ports detected
[    2.752097] usb 4-1: new high speed USB device using ehci_hcd and address 2
[    2.781228] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.781239] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.781241] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.781257] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    2.785153] ehci_hcd 0000:00:1d.7: debug port 1
[    2.785158] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.785161] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4704c00
[    2.893042] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.893121] usb usb8: configuration #1 chosen from 1 choice
[    2.893151] hub 8-0:1.0: USB hub found
[    2.893158] hub 8-0:1.0: 6 ports detected
[    2.996393] ohci1394 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.996399] ohci1394 0000:07:00.0: setting latency timer to 64
[    2.998035] ahci 0000:00:1f.2: version 3.0
[    2.998044] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.998120] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x13 impl SATA mode
[    2.998122] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag led clo pmp pio slum part 
[    2.998125] ahci 0000:00:1f.2: setting latency timer to 64
[    2.998271] scsi0 : ahci
[    2.998347] scsi1 : ahci
[    2.998396] scsi2 : ahci
[    2.998444] scsi3 : ahci
[    2.998495] scsi4 : ahci
[    2.998529] ata1: SATA max UDMA/133 abar m2048@0xf4704000 port 0xf4704100 irq 2297
[    2.998532] ata2: SATA max UDMA/133 abar m2048@0xf4704000 port 0xf4704180 irq 2297
[    2.998533] ata3: DUMMY
[    2.998534] ata4: DUMMY
[    2.998536] ata5: SATA max UDMA/133 abar m2048@0xf4704000 port 0xf4704300 irq 2297
[    3.048097] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f4300800-f4300fff]  Max Packet=[512]  IR/IT contexts=[4/4]
[    3.160614] usb 4-1: configuration #1 chosen from 1 choice
[    3.484096] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.486214] ata1.00: ATA-7: ST9120823AS, 3.AAB, max UDMA/133
[    3.486217] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.486939] ata1.00: configured for UDMA/133
[    3.616095] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.788404] usb 2-1: configuration #1 chosen from 1 choice
[    3.968100] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.981746] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, SX01, max UDMA/100, ATAPI AN
[    3.996085] ata2.00: configured for UDMA/100
[    4.016692] ata2: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0
[    4.016696] ata2: irq_stat 0x40000008
[    4.316097] ata5: SATA link down (SStatus 0 SControl 300)
[    4.316212] scsi 0:0:0:0: Direct-Access     ATA      ST9120823AS      3.AA PQ: 0 ANSI: 5
[    4.317401] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560S  SX01 PQ: 0 ANSI: 5
[    4.317497] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.317521] r8169 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.317536] r8169 0000:08:00.0: setting latency timer to 64
[    4.317783] eth0: RTL8168c/8111c at 0xffffc2000033e000, 00:90:f5:6f:d7:f8, XID 3c4000c0 IRQ 2296
[    4.325978] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[58745bf80090f514]
[    4.326048] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.326075] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.335895] Driver 'sd' needs updating - please use bus_type methods
[    4.335964] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.335978] sd 0:0:0:0: [sda] Write Protect is off
[    4.335980] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.336003] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.336068] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.336080] sd 0:0:0:0: [sda] Write Protect is off
[    4.336081] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.336104] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.336106]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.378084]  sda1 sda2 < sda5 sda6 >
[    4.411460] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.421509] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.421512] Uniform CD-ROM driver Revision: 3.20
[    4.421565] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.702048] PM: Starting manual resume from disk
[    4.702050] PM: Resume from partition 8:6
[    4.702051] PM: Checking hibernation image.
[    4.702215] PM: Resume from disk failed.
[    4.735916] kjournald starting.  Commit interval 5 seconds
[    4.735927] EXT3-fs: mounted filesystem with ordered data mode.
[   11.803002] udevd version 124 started
[   12.104566] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.107864] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.252130] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   12.280035] ACPI: Power Button (FF) [PWRF]
[   12.385971] ACPI: AC Adapter [AC] (on-line)
[   12.386080] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   12.404023] ACPI: Power Button (CM) [PWRB]
[   12.404090] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   12.436024] ACPI: Sleep Button (CM) [SLPB]
[   12.436102] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   12.456830] ACPI: Lid Switch [LID0]
[   12.534241] ACPI: Battery Slot [BAT0] (battery present)
[   12.534306] ACPI: WMI: Mapper loaded
[   12.851270] nvidia: module license 'NVIDIA' taints kernel.
[   13.105921] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.105932] nvidia 0000:01:00.0: setting latency timer to 64
[   13.106133] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   13.297704] Linux video capture interface: v2.00
[   13.415184] sdhci: Secure Digital Host Controller Interface driver
[   13.415187] sdhci: Copyright(c) Pierre Ossman
[   13.423137] sdhci-pci 0000:07:00.1: SDHCI controller found [197b:2382] (rev 0)
[   13.423153] sdhci-pci 0000:07:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.423185] sdhci-pci 0000:07:00.1: setting latency timer to 64
[   13.423226] mmc0: SDHCI controller on PCI [0000:07:00.1] using DMA
[   13.423234] sdhci-pci 0000:07:00.2: SDHCI controller found [197b:2381] (rev 0)
[   13.423246] sdhci-pci 0000:07:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.423252] sdhci-pci 0000:07:00.2: Refusing to bind to secondary interface.
[   13.423258] sdhci-pci 0000:07:00.2: PCI INT A disabled
[   13.491554] uvcvideo: Found UVC 1.00 device USB2.0 Camera (5986:0300)
[   13.563689] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb4/4-1/4-1:1.0/input/input6
[   13.584131] usbcore: registered new interface driver uvcvideo
[   13.584134] USB Video Class driver (v0.1.0)
[   13.801717] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.801719] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.802358] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.802365] iwlagn 0000:06:00.0: setting latency timer to 64
[   13.802384] iwlagn: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   13.830932] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.851303] iwlagn 0000:06:00.0: PCI INT A disabled
[   13.851602] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.871395] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x202000
[   13.910724] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   14.426325] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.426347] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.457940] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   14.763300] loop: module loaded
[   14.819260] lp: driver loaded but no devices found
[   14.999215] Adding 1413680k swap on /dev/sda6.  Priority:-1 extents:1 across:1413680k
[   15.831289] EXT3 FS on sda5, internal journal
[   16.951372] type=1505 audit(1231209119.272:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4285
[   17.045427] type=1505 audit(1231209119.368:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4290
[   17.045585] type=1505 audit(1231209119.368:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4290
[   17.177197] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.556193] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.726252] ppdev: user-space parallel port driver
[   21.609483] Bluetooth: Core ver 2.13
[   21.610477] NET: Registered protocol family 31
[   21.610485] Bluetooth: HCI device and connection manager initialized
[   21.610491] Bluetooth: HCI socket layer initialized
[   21.630001] Bluetooth: L2CAP ver 2.11
[   21.630014] Bluetooth: L2CAP socket layer initialized
[   21.658887] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.658901] Bluetooth: BNEP filters: protocol multicast
[   21.706324] Bridge firewalling registered
[   21.707560] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   21.725359] Bluetooth: SCO (Voice Link) ver 0.6
[   21.725371] Bluetooth: SCO socket layer initialized
[   21.837658] Bluetooth: RFCOMM socket layer initialized
[   21.838102] Bluetooth: RFCOMM TTY layer initialized
[   21.838114] Bluetooth: RFCOMM ver 1.10
[   26.017542] r8169: eth0: link down
[   26.215274] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.215338] iwlagn 0000:06:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   26.215461] firmware: requesting iwlwifi-5000-1.ucode
[   29.645363] Registered led device: iwl-phy0:radio
[   29.645382] Registered led device: iwl-phy0:assoc
[   29.645395] Registered led device: iwl-phy0:RX
[   29.645413] Registered led device: iwl-phy0:TX
[   29.904141] NET: Registered protocol family 17
[   34.055179] NET: Registered protocol family 10
[   34.056688] lo: Disabled Privacy Extensions
[   34.058126] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.059876] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   74.225413] CPU0 attaching NULL sched-domain.
[   74.225420] CPU1 attaching NULL sched-domain.
[   74.240087] CPU0 attaching sched-domain:
[   74.240093]  domain 0: span 0-1 level MC
[   74.240096]   groups: 0 1
[   74.240100]   domain 1: span 0-1 level NODE
[   74.240103]    groups: 0-1
[   74.240107] CPU1 attaching sched-domain:
[   74.240109]  domain 0: span 0-1 level MC
[   74.240111]   groups: 1 0
[   74.240115]   domain 1: span 0-1 level NODE
[   74.240117]    groups: 0-1
[   75.318227] wlan0: authenticate with AP 00:15:e9:d6:94:b4
[   75.367104] wlan0: authenticated
[   75.367122] wlan0: associate with AP 00:15:e9:d6:94:b4
[   75.369848] wlan0: RX AssocResp from 00:15:e9:d6:94:b4 (capab=0x431 status=0 aid=2)
[   75.369858] wlan0: associated
[   75.394711] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   85.500010] wlan0: no IPv6 routers present
[/HTML]

---

### Post by felker2 on 2009-01-06
@JagerQ: sorry to say, but I can't think of any further analysis steps. Hopefully someone else can help to solve this.

---

### Post by ericy on 2009-01-06
I noticed your BIOS does report this region above 4GB boundry:

> BIOS-e820: 0000000100000000 - 0000000160000000 (usable) 

This amounts to: 1536 MB(*1)(above 4GB) + 4096MB(below 4GB) = 
5632MB

So, you can try to pass "mem=5632m" instead.

But I'd recommend you try it without "mem=..." boot option first. You did mention you failed to install ubuntu without it, but it might work now that the OS is installed.

Another boot option to try is "pci=nommconf"


(*1) I'm just thinking. It's over 1GB... kinda high. Maybe a hardware bug?

=================
My system's case:
(Athlon64x2 2.3G Brisbane, 4GB RAM, ECS 780GM-A/AMD 780G/ATI 3200HD/shared mem set to 256MB, no mem remap option in Bios)

[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)

[    0.004000] Memory: 3787592k/4718592k available

4718592k / 1024 = 4608m (512 + 4096)
512MB -->  0x020000000
4096MB -> 0x0100000000

free -m : total 3701

---

### Post by JagerQ on 2009-01-06
> **ericy said:**
> But I'd recommend you try it without "mem=..." boot option first. 

That causes me to reboot. I reckon I could take the quiet off and check the info, but let me try the other stuff first. 

I was thinking to try manually mapping everything with multiple mem commands, but I'm not sure how to exactly do that.

---

### Post by JagerQ on 2009-01-06
> **ericy said:**
> "mem=5632m" 
That leads me to reboot.

I was able to get mem=4100m to go but the results are odd as I have slighly less memory free. 2445 vs 2508. 

free -m
             total       used       free     shared    buffers     cached
Mem:          2445        608       1837          0         17        227
-/+ buffers/cache:        363       2082
Swap:         1380          0       1380


[HTML][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] Command line: root=UUID=0a24029a-0afd-4287-8d6a-7e52780d09d7 ro mem=4100m quiet splash quietboot 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000099400 (usable)
[    0.000000]  BIOS-e820: 0000000000099400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f8b1000 (usable)
[    0.000000]  BIOS-e820: 000000009f8b1000 - 000000009f8b7000 (reserved)
[    0.000000]  BIOS-e820: 000000009f8b7000 - 000000009f9b2000 (usable)
[    0.000000]  BIOS-e820: 000000009f9b2000 - 000000009fa0f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fa0f000 - 000000009fb07000 (usable)
[    0.000000]  BIOS-e820: 000000009fb07000 - 000000009fd0f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fd0f000 - 000000009fd18000 (usable)
[    0.000000]  BIOS-e820: 000000009fd18000 - 000000009fd1f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fd1f000 - 000000009fd67000 (usable)
[    0.000000]  BIOS-e820: 000000009fd67000 - 000000009fd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fd9f000 - 000000009fde3000 (usable)
[    0.000000]  BIOS-e820: 000000009fde3000 - 000000009fdfd000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009fdfd000 - 000000009fe00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000160000000 (usable)
[    0.000000] user-defined physical RAM map:
[    0.000000]  user: 0000000000000000 - 0000000000099400 (usable)
[    0.000000]  user: 0000000000099400 - 00000000000a0000 (reserved)
[    0.000000]  user: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  user: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  user: 0000000000100000 - 000000009f8b1000 (usable)
[    0.000000]  user: 000000009f8b1000 - 000000009f8b7000 (reserved)
[    0.000000]  user: 000000009f8b7000 - 000000009f9b2000 (usable)
[    0.000000]  user: 000000009f9b2000 - 000000009fa0f000 (reserved)
[    0.000000]  user: 000000009fa0f000 - 000000009fb07000 (usable)
[    0.000000]  user: 000000009fb07000 - 000000009fd0f000 (reserved)
[    0.000000]  user: 000000009fd0f000 - 000000009fd18000 (usable)
[    0.000000]  user: 000000009fd18000 - 000000009fd1f000 (reserved)
[    0.000000]  user: 000000009fd1f000 - 000000009fd67000 (usable)
[    0.000000]  user: 000000009fd67000 - 000000009fd9f000 (ACPI NVS)
[    0.000000]  user: 000000009fd9f000 - 000000009fde3000 (usable)
[    0.000000]  user: 000000009fde3000 - 000000009fdfd000 (ACPI data)
[    0.000000]  user: 000000009fdfd000 - 000000009fe00000 (usable)
[    0.000000]  user: 0000000100000000 - 0000000100400000 (usable)
[    0.000000] last_pfn = 0x100400 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0x9fe00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 009fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 9fe00000 @ 8000-c000
[    0.000000] last_map_addr: 9fe00000 end: 9fe00000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0100400000 page 2M
[    0.000000] kernel direct mapping tables up to 100400000 @ a000-10000
[    0.000000] last_map_addr: 100400000 end: 100400000
[    0.000000] RAMDISK: 377b7000 - 37fefeb4
[    0.000000] DMI present.[/HTML]

---

### Post by JagerQ on 2009-01-06
If I go to mem=3072m, I see only 2508m as before. It appears to max out there.

 free -m
             total       used       free     shared    buffers     cached
Mem:          2508        561       1946          0         16        205
-/+ buffers/cache:        340       2167
Swap:         1380          0       1380

[HTML][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] Command line: root=UUID=0a24029a-0afd-4287-8d6a-7e52780d09d7 ro mem=3072m quiet splash quietboot 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000099400 (usable)
[    0.000000]  BIOS-e820: 0000000000099400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f8b1000 (usable)
[    0.000000]  BIOS-e820: 000000009f8b1000 - 000000009f8b7000 (reserved)
[    0.000000]  BIOS-e820: 000000009f8b7000 - 000000009f9b2000 (usable)
[    0.000000]  BIOS-e820: 000000009f9b2000 - 000000009fa0f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fa0f000 - 000000009fb07000 (usable)
[    0.000000]  BIOS-e820: 000000009fb07000 - 000000009fd0f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fd0f000 - 000000009fd18000 (usable)
[    0.000000]  BIOS-e820: 000000009fd18000 - 000000009fd1f000 (reserved)
[    0.000000]  BIOS-e820: 000000009fd1f000 - 000000009fd67000 (usable)
[    0.000000]  BIOS-e820: 000000009fd67000 - 000000009fd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fd9f000 - 000000009fde3000 (usable)
[    0.000000]  BIOS-e820: 000000009fde3000 - 000000009fdfd000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009fdfd000 - 000000009fe00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000160000000 (usable)
[    0.000000] user-defined physical RAM map:
[    0.000000]  user: 0000000000000000 - 0000000000099400 (usable)
[    0.000000]  user: 0000000000099400 - 00000000000a0000 (reserved)
[    0.000000]  user: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  user: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  user: 0000000000100000 - 000000009f8b1000 (usable)
[    0.000000]  user: 000000009f8b1000 - 000000009f8b7000 (reserved)
[    0.000000]  user: 000000009f8b7000 - 000000009f9b2000 (usable)
[    0.000000]  user: 000000009f9b2000 - 000000009fa0f000 (reserved)
[    0.000000]  user: 000000009fa0f000 - 000000009fb07000 (usable)
[    0.000000]  user: 000000009fb07000 - 000000009fd0f000 (reserved)
[    0.000000]  user: 000000009fd0f000 - 000000009fd18000 (usable)
[    0.000000]  user: 000000009fd18000 - 000000009fd1f000 (reserved)
[    0.000000]  user: 000000009fd1f000 - 000000009fd67000 (usable)
[    0.000000]  user: 000000009fd67000 - 000000009fd9f000 (ACPI NVS)
[    0.000000]  user: 000000009fd9f000 - 000000009fde3000 (usable)
[    0.000000]  user: 000000009fde3000 - 000000009fdfd000 (ACPI data)
[    0.000000]  user: 000000009fdfd000 - 000000009fe00000 (usable)
[    0.000000] last_pfn = 0x9fe00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 009fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 9fe00000 @ 8000-c000
[    0.000000] last_map_addr: 9fe00000 end: 9fe00000
[    0.000000] RAMDISK: 377b7000 - 37fefeb4
[    0.000000] DMI present.[/HTML]

---

### Post by JagerQ on 2009-01-06
Should I do something with the CONFIG_HIGHMEM flag or is that not necessary on 64-bit kernels?

---

### Post by hyperdude111 on 2009-01-06
I have ubuntu 64 bit, AMD Athlon 64x2 with 4gb of ram and it all works  fine

---

### Post by JagerQ on 2009-01-07
> **hyperdude111 said:**
> I have ubuntu 64 bit, AMD Athlon 64x2 with 4gb of ram and it all works  fine

Thanks, I'll keep the swapping to a slower AMD Athlon option open. I've talked to a few other people with the Montevina chipset and they have had a similar issue.

---

### Post by vgrisham on 2009-01-07
What specific file are you editing? I'd like to give this a shot on mine since the aperture settings on the motherboard cause Ubuntu all kinds of hurt.

---

### Post by JagerQ on 2009-01-07
> **vgrisham said:**
> What specific file are you editing?

I'm just putting the mem flags in through the boot loader. For my setup, I could also edit /boot/grub/menu.lst

---

### Post by ConRong on 2009-05-08
> **JagerQ said:**
> I'm using a Sager NP8660 with the Montevina chipset, a dedicated NVidia 9800M GT w/ 512 MB of graphics memory and 4 gigabytes of ram. As far as I can tell the video card can only use the dedicated video memory and doesn't share the system memory.

I've got Vista x64 installed and am able to use the entire 4 GB of ram. During the POST, the BIOS shows a full 4096.

When I tried to install a linux partition, I couldn't get Ubuntu to install without adding a mem=4096m flag. I ended up installing it off the alternate CD and it works fine for the most part.

The problem is that I can only see 2.4 _Gibi_bytes of memory. I also see 1.3 Gibibytes in the Swap. 

That adds up to about 4 GB of total memory, but I'm not sure if it's possible that the swap partition is actually on my ram? It definitely made a 1.35 gigabyte swap partition during the install, but I'm not sure what's going on with it.

Regardless, does anyone have any idea how I can get at the rest of the memory? Thanks!

You need to update your new bios for this laptop. I have the same laptop as yours and Ubuntu 9.04 installed perfectly. 
This is where you can find all the latest BIOS:
[http://www.clevo.com.tw/en/e-services/esupport/MarketDLOut.asp?model=M86xTU&go=GO&type=BIOS](http://www.clevo.com.tw/en/e-services/esupport/MarketDLOut.asp?model=M86xTU&go=GO&type=BIOS)
This is where you can find instructions to flash it.
[http://forum.notebookreview.com/showthread.php?t=246530](http://forum.notebookreview.com/showthread.php?t=246530)

---

### Post by rgknox on 2009-08-19
Hi JagerQ,

I seem to have the exact same setup as you,  clevo m860tu.
model name    : Intel(R) Core(TM)2 Duo CPU     P9500  @ 2.53GHz
4GM RAM
dedicated NVidia 9800M GT w/ 512 MB of graphics memory 

I have not found a solution to the case of the missing ram either.  I just settled for the 32 bit 8.10 release and use the first 2GB.  Sounds like this is what you did.

Aside from that, my only other (but significant) issue is screen brightness.  I can seem to find a way to control the back light!  I looked around and tried various hacks, I think one was called vclock or something.

Ill pop my head back in if I ever find solutions to these two issues.

EDIT: Just saw ConRong's response.  Thanks! Look forward to flashing.


Cheers

---

