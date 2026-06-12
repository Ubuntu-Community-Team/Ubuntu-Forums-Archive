---
title: "Memory under Intrepid-amd64 - 2x2 Gigs = 3901?"
date: 2009-04-04
forum: x86 64-bit Users
---

### Post by graysky on 2009-04-04
Just wanted to ask other folks out there w/ 4 gigs on their boards... if you issue an 'free -m' from your shell, what do you get?

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3901       3878         22          0       1598       1749
-/+ buffers/cache:        531       3369
Swap:         2000          0       2000
```

Shouldn't the total = 4x1024=4096?

Furthermore, according to the output above, I only have 22 megs of memory left, yet when I compare that report to what my conky is reporting, there is a HUGE difference.

[img]http://img516.imageshack.us/img516/9602/50884043.gif[/img]

---

### Post by NazarXG on 2009-04-05
I get even less :P

```

             total       used       free     shared    buffers     cached
Mem:          3706       1509       2197          0        316        555
-/+ buffers/cache:        636       3070
Swap:          478          0        478


```

---

### Post by rbmorse on 2009-04-05
You lose some memory capacity to system overhead before the O/S gets to count what's available to it and applications.  Your numbers look OK to me.

---

### Post by graysky on 2009-04-05
Thanks for the replies, all.  Here is my /var/log/dmesg (below).  A few suspicious lines are:
```
[    0.003333] allocated 49807360 bytes of page_cgroup
[    0.003333] please try cgroup_disable=memory option if you don't want
[    0.003333] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.003333] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.003333] software IO TLB at phys 0x20000000 - 0x24000000
[    0.003333] Memory: 3985760k/4980736k available (2664k kernel code, 788040k absent, 205964k reserved, 1670k data, 364k init)
```

What's up with that 'please try cgroup_disable...' line?

Here is the /var/log/dmesg in its entirety:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.29-em64t (root@novelty) (gcc version 4.3.2) #1 SMP PREEMPT Mon Mar 30 19:40:04 EDT 2009
[    0.000000] Command line: root=/dev/sdb2 ro quiet
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e400 (usable)
[    0.000000]  BIOS-e820: 000000000009e400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI 2.5 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x100000000
[    0.000000] last_pfn = 0xcfee0 max_arch_pfn = 0x100000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfee0000
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfee0000 page 4k
[    0.000000] kernel direct mapping tables up to cfee0000 @ 10000-16000
[    0.000000] last_map_addr: cfee0000 end: cfee0000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 14000-1a000
[    0.000000] last_map_addr: 130000000 end: 130000000
[    0.000000] RAMDISK: 3788a000 - 37fef0f7
[    0.000000] ACPI: RSDP 000F86B0, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT CFEE3000, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP CFEE3080, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (16) does not match PM1_EVT_LEN (4)
[    0.000000] ACPI: DSDT CFEE3100, 5720 (r1 INTELR AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS CFEE0000, 0040
[    0.000000] ACPI: _HPT CFEE8900, 0038 (r1 IntelR AWRDACPI 42302E31 AWRD       98)
[    0.000000] ACPI: _WDT CFEE8940, 0047 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: MCFG CFEE89C0, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC CFEE8840, 0084 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT CFEE9320, 03A8 (r1  PmRef    CpuPm     3000 INTL 20050309)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 000096cef0]    TEXT DATA BSS ==> [0000200000 - 000096cef0]
[    0.000000]   #3 [003788a000 - 0037fef0f7]          RAMDISK ==> [003788a000 - 0037fef0f7]
[    0.000000]   #4 [000009e400 - 0000100000]    BIOS reserved ==> [000009e400 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
[    0.000000]   #6 [0000014000 - 0000015000]          PGTABLE ==> [0000014000 - 0000015000]
[    0.000000]  [ffffe20000000000-ffffe200043fffff] PMD -> [ffff880028200000-ffff88002c5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cfee0
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048174
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2005 pages reserved
[    0.000000]   DMA zone: 1921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833304 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Allocating 49152 bytes of per cpu data
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1029145
[    0.000000] Kernel command line: root=/dev/sdb2 ro quiet
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3400.092 MHz processor.
[    0.003333] Console: colour VGA+ 80x25
[    0.003333] console [tty0] enabled
[    0.003333] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003333] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.003333] allocated 49807360 bytes of page_cgroup
[    0.003333] please try cgroup_disable=memory option if you don't want
[    0.003333] Checking aperture...
[    0.003333] No AGP bridge found
[    0.003333] Calgary: detecting Calgary via BIOS EBDA area
[    0.003333] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.003333] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.003333] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.003333] software IO TLB at phys 0x20000000 - 0x24000000
[    0.003333] Memory: 3985760k/4980736k available (2664k kernel code, 788040k absent, 205964k reserved, 1670k data, 364k init)
[    0.003333] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.003341] Calibrating delay loop (skipped), value calculated using timer frequency.. 6802.52 BogoMIPS (lpj=11333640)
[    0.003353] Security Framework initialized
[    0.003356] SELinux:  Disabled at boot.
[    0.003363] Mount-cache hash table entries: 256
[    0.003458] Initializing cgroup subsys ns
[    0.003461] Initializing cgroup subsys cpuacct
[    0.003462] Initializing cgroup subsys memory
[    0.003472] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.003473] CPU: L2 cache: 6144K
[    0.003474] [ds] using Core 2/Atom configuration
[    0.003476] CPU: Physical Processor ID: 0
[    0.003477] CPU: Processor Core ID: 0
[    0.003482] CPU0: Thermal monitoring enabled (TM2)
[    0.003483] using mwait in idle threads.
[    0.004127] ACPI: Core revision 20081204
[    0.010029] Setting APIC routing to flat
[    0.010344] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.044500] CPU0: Intel(R) Xeon(R) CPU           X3360  @ 2.83GHz stepping 07
[    0.046666] Booting processor 1 APIC 0x1 ip 0x6000
[    0.003333] Initializing CPU#1
[    0.003333] Calibrating delay using timer specific routine.. 6802.82 BogoMIPS (lpj=11332517)
[    0.003333] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.003333] CPU: L2 cache: 6144K
[    0.003333] [ds] using Core 2/Atom configuration
[    0.003333] CPU: Physical Processor ID: 0
[    0.003333] CPU: Processor Core ID: 1
[    0.003333] CPU1: Thermal monitoring enabled (TM2)
[    0.137289] CPU1: Intel(R) Xeon(R) CPU           X3360  @ 2.83GHz stepping 07
[    0.137303] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.140067] Booting processor 2 APIC 0x3 ip 0x6000
[    0.003333] Initializing CPU#2
[    0.003333] Calibrating delay using timer specific routine.. 6802.86 BogoMIPS (lpj=11332588)
[    0.003333] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.003333] CPU: L2 cache: 6144K
[    0.003333] [ds] using Core 2/Atom configuration
[    0.003333] CPU: Physical Processor ID: 0
[    0.003333] CPU: Processor Core ID: 3
[    0.003333] CPU2: Thermal monitoring enabled (TM2)
[    0.233961] CPU2: Intel(R) Xeon(R) CPU           X3360  @ 2.83GHz stepping 07
[    0.233974] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.236722] Booting processor 3 APIC 0x2 ip 0x6000
[    0.003333] Initializing CPU#3
[    0.003333] Calibrating delay using timer specific routine.. 6802.85 BogoMIPS (lpj=11332560)
[    0.003333] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.003333] CPU: L2 cache: 6144K
[    0.003333] [ds] using Core 2/Atom configuration
[    0.003333] CPU: Physical Processor ID: 0
[    0.003333] CPU: Processor Core ID: 2
[    0.003333] CPU3: Thermal monitoring enabled (TM2)
[    0.330620] CPU3: Intel(R) Xeon(R) CPU           X3360  @ 2.83GHz stepping 07
[    0.330633] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.333349] Brought up 4 CPUs
[    0.333351] Total of 4 processors activated (27209.06 BogoMIPS).
[    0.333393] CPU0 attaching sched-domain:
[    0.333395]  domain 0: span 0-1 level MC
[    0.333396]   groups: 0 1
[    0.333398]   domain 1: span 0-3 level CPU
[    0.333399]    groups: 0-1 2-3
[    0.333402] CPU1 attaching sched-domain:
[    0.333403]  domain 0: span 0-1 level MC
[    0.333404]   groups: 1 0
[    0.333405]   domain 1: span 0-3 level CPU
[    0.333406]    groups: 0-1 2-3
[    0.333409] CPU2 attaching sched-domain:
[    0.333410]  domain 0: span 2-3 level MC
[    0.333411]   groups: 2 3
[    0.333412]   domain 1: span 0-3 level CPU
[    0.333413]    groups: 2-3 0-1
[    0.333416] CPU3 attaching sched-domain:
[    0.333417]  domain 0: span 2-3 level MC
[    0.333418]   groups: 3 2
[    0.333419]   domain 1: span 0-3 level CPU
[    0.333420]    groups: 2-3 0-1
[    0.333489] net_namespace: 1840 bytes
[    0.333489] Booting paravirtualized kernel on bare hardware
[    0.333489] NET: Registered protocol family 16
[    0.333489] ACPI: bus type pci registered
[    0.333489] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.333489] PCI: MCFG area at e0000000 reserved in E820
[    0.341294] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.341295] PCI: Using configuration type 1 for base access
[    0.341304] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.341304] mtrr: probably your BIOS does not setup all CPUs.
[    0.341304] mtrr: corrected configuration.
[    0.341304] bio: create slab <bio-0> at 0
[    0.343749] ACPI: EC: Look up EC in DSDT
[    0.348069] ACPI: Interpreter enabled
[    0.348071] ACPI: (supports S0 S3 S5)
[    0.348085] ACPI: Using IOAPIC for interrupt routing
[    0.350843] ACPI: No dock devices found.
[    0.350843] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.350843] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.350843] pci 0000:00:01.0: PME# disabled
[    0.350843] pci 0000:00:1a.0: reg 20 io port: [0xff00-0xff1f]
[    0.350843] pci 0000:00:1a.1: reg 20 io port: [0xfe00-0xfe1f]
[    0.350843] pci 0000:00:1a.2: reg 20 io port: [0xfd00-0xfd1f]
[    0.350843] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfdfff000-0xfdfff3ff]
[    0.350843] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.350843] pci 0000:00:1a.7: PME# disabled
[    0.350843] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdff4000-0xfdff7fff]
[    0.350843] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.350843] pci 0000:00:1b.0: PME# disabled
[    0.350843] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.350843] pci 0000:00:1c.0: PME# disabled
[    0.350843] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.350843] pci 0000:00:1c.3: PME# disabled
[    0.350843] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.350843] pci 0000:00:1c.4: PME# disabled
[    0.353354] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.353357] pci 0000:00:1c.5: PME# disabled
[    0.353393] pci 0000:00:1d.0: reg 20 io port: [0xfc00-0xfc1f]
[    0.353442] pci 0000:00:1d.1: reg 20 io port: [0xfb00-0xfb1f]
[    0.353491] pci 0000:00:1d.2: reg 20 io port: [0xfa00-0xfa1f]
[    0.353532] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdffe000-0xfdffe3ff]
[    0.353566] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.353569] pci 0000:00:1d.7: PME# disabled
[    0.353655] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.353658] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.353660] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.353663] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 003f)
[    0.353665] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0100 (mask 003f)
[    0.353668] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0290 (mask 000f)
[    0.353712] pci 0000:00:1f.2: reg 10 io port: [0xf900-0xf907]
[    0.353716] pci 0000:00:1f.2: reg 14 io port: [0xf800-0xf803]
[    0.353720] pci 0000:00:1f.2: reg 18 io port: [0xf700-0xf707]
[    0.353724] pci 0000:00:1f.2: reg 1c io port: [0xf600-0xf603]
[    0.353728] pci 0000:00:1f.2: reg 20 io port: [0xf500-0xf51f]
[    0.353732] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfdffd000-0xfdffd7ff]
[    0.353753] pci 0000:00:1f.2: PME# supported from D3hot
[    0.353755] pci 0000:00:1f.2: PME# disabled
[    0.353774] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfdffc000-0xfdffc0ff]
[    0.353783] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.353813] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.353819] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.353825] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    0.353828] pci 0000:01:00.0: reg 24 io port: [0xbf00-0xbf7f]
[    0.353832] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.353871] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
[    0.353873] pci 0000:00:01.0: bridge 32bit mmio: [0xf8000000-0xfbffffff]
[    0.353875] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.353900] pci 0000:00:1c.0: bridge io port: [0xa000-0xafff]
[    0.353902] pci 0000:00:1c.0: bridge 32bit mmio: [0xfda00000-0xfdafffff]
[    0.353906] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfd700000-0xfd7fffff]
[    0.353953] pci 0000:03:00.0: reg 10 64bit mmio: [0xfd6fc000-0xfd6fffff]
[    0.353959] pci 0000:03:00.0: reg 18 io port: [0x9e00-0x9eff]
[    0.353980] pci 0000:03:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.354021] pci 0000:03:00.0: supports D1 D2
[    0.354022] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.354025] pci 0000:03:00.0: PME# disabled
[    0.354053] pci 0000:00:1c.3: bridge io port: [0x9000-0x9fff]
[    0.354056] pci 0000:00:1c.3: bridge 32bit mmio: [0xfd600000-0xfd6fffff]
[    0.354060] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xfd500000-0xfd5fffff]
[    0.354132] pci 0000:04:00.0: reg 24 32bit mmio: [0xfdefe000-0xfdefffff]
[    0.354163] pci 0000:04:00.0: PME# supported from D3hot
[    0.354167] pci 0000:04:00.0: PME# disabled
[    0.354209] pci 0000:04:00.1: reg 10 io port: [0xdf00-0xdf07]
[    0.354216] pci 0000:04:00.1: reg 14 io port: [0xde00-0xde03]
[    0.354223] pci 0000:04:00.1: reg 18 io port: [0xdd00-0xdd07]
[    0.354230] pci 0000:04:00.1: reg 1c io port: [0xdc00-0xdc03]
[    0.354236] pci 0000:04:00.1: reg 20 io port: [0xdb00-0xdb0f]
[    0.354305] pci 0000:00:1c.4: bridge io port: [0xd000-0xdfff]
[    0.354307] pci 0000:00:1c.4: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.354311] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.354356] pci 0000:05:00.0: reg 10 64bit mmio: [0xfdcfc000-0xfdcfffff]
[    0.354362] pci 0000:05:00.0: reg 18 io port: [0xce00-0xceff]
[    0.354383] pci 0000:05:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.354415] pci 0000:05:00.0: supports D1 D2
[    0.354416] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.354419] pci 0000:05:00.0: PME# disabled
[    0.354447] pci 0000:00:1c.5: bridge io port: [0xc000-0xcfff]
[    0.354450] pci 0000:00:1c.5: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.354453] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xfdb00000-0xfdbfffff]
[    0.354481] pci 0000:06:03.0: reg 10 32bit mmio: [0xfd9ff000-0xfd9ff7ff]
[    0.354486] pci 0000:06:03.0: reg 14 io port: [0x8f00-0x8f7f]
[    0.354519] pci 0000:06:03.0: supports D2
[    0.354520] pci 0000:06:03.0: PME# supported from D2 D3hot D3cold
[    0.354523] pci 0000:06:03.0: PME# disabled
[    0.354553] pci 0000:00:1e.0: transparent bridge
[    0.354555] pci 0000:00:1e.0: bridge io port: [0x8000-0x8fff]
[    0.354557] pci 0000:00:1e.0: bridge 32bit mmio: [0xfd900000-0xfd9fffff]
[    0.354561] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xfd800000-0xfd8fffff]
[    0.354577] pci_bus 0000:00: on NUMA node 0
[    0.354581] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.354680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.354722] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.354759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.354796] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.354833] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.367331] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.367331] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.367331] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.367331] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.367331] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.367331] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.367331] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[    0.367331] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.367331] PCI: Using ACPI for IRQ routing
[    0.380004] NET: Registered protocol family 8
[    0.380006] NET: Registered protocol family 20
[    0.380020] NetLabel: Initializing
[    0.380020] NetLabel:  domain hash size = 128
[    0.380020] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.380020] NetLabel:  unlabeled traffic allowed by default
[    0.380104] hpet clockevent registered
[    0.380106] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.380109] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.380112] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.400006] pnp: PnP ACPI init
[    0.400013] ACPI: bus type pnp registered
[    0.402189] pnp 00:0b: mem resource (0x46e-0x56d) overlaps 0000:01:00.0 BAR 6 (0x0-0x1ffff), disabling
[    0.402192] pnp 00:0b: mem resource (0x46e-0x56d) overlaps 0000:03:00.0 BAR 6 (0x0-0x1ffff), disabling
[    0.402196] pnp 00:0b: mem resource (0x46e-0x56d) overlaps 0000:05:00.0 BAR 6 (0x0-0x1ffff), disabling
[    0.402254] pnp: PnP ACPI: found 12 devices
[    0.402255] ACPI: ACPI bus type pnp unregistered
[    0.402260] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.402262] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.402263] system 00:01: ioport range 0x290-0x30f has been reserved
[    0.402265] system 00:01: ioport range 0x290-0x297 has been reserved
[    0.402266] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.402270] system 00:08: ioport range 0x400-0x4bf could not be reserved
[    0.402274] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.402277] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[    0.402278] system 00:0b: iomem range 0xcff00000-0xcfffffff has been reserved
[    0.402280] system 00:0b: iomem range 0xfed00000-0xfed000ff has been reserved
[    0.402282] system 00:0b: iomem range 0xcfee0000-0xcfefffff could not be reserved
[    0.402283] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.402285] system 00:0b: iomem range 0x100000-0xcfedffff could not be reserved
[    0.402286] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.402288] system 00:0b: iomem range 0xfed14000-0xfed1dfff has been reserved
[    0.402289] system 00:0b: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.402291] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.402292] system 00:0b: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.402294] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[    0.402295] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
[    0.407433] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.407435] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    0.407437] pci 0000:00:01.0:   MEM window: 0xf8000000-0xfbffffff
[    0.407439] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.407442] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.407444] pci 0000:00:1c.0:   IO window: 0xa000-0xafff
[    0.407447] pci 0000:00:1c.0:   MEM window: 0xfda00000-0xfdafffff
[    0.407449] pci 0000:00:1c.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    0.407453] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    0.407455] pci 0000:00:1c.3:   IO window: 0x9000-0x9fff
[    0.407458] pci 0000:00:1c.3:   MEM window: 0xfd600000-0xfd6fffff
[    0.407461] pci 0000:00:1c.3:   PREFETCH window: 0x000000fd500000-0x000000fd5fffff
[    0.407464] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:04
[    0.407466] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    0.407469] pci 0000:00:1c.4:   MEM window: 0xfde00000-0xfdefffff
[    0.407472] pci 0000:00:1c.4:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.407476] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:05
[    0.407477] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.407480] pci 0000:00:1c.5:   MEM window: 0xfdc00000-0xfdcfffff
[    0.407483] pci 0000:00:1c.5:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.407487] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.407489] pci 0000:00:1e.0:   IO window: 0x8000-0x8fff
[    0.407492] pci 0000:00:1e.0:   MEM window: 0xfd900000-0xfd9fffff
[    0.407494] pci 0000:00:1e.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
[    0.407502] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.407504] pci 0000:00:01.0: setting latency timer to 64
[    0.407508] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.407510] pci 0000:00:1c.0: setting latency timer to 64
[    0.407515] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.407517] pci 0000:00:1c.3: setting latency timer to 64
[    0.407521] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.407524] pci 0000:00:1c.4: setting latency timer to 64
[    0.407529] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.407531] pci 0000:00:1c.5: setting latency timer to 64
[    0.407535] pci 0000:00:1e.0: setting latency timer to 64
[    0.407537] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.407538] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.407539] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.407541] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbffffff]
[    0.407542] pci_bus 0000:01: resource 2 mem: [0xd0000000-0xdfffffff]
[    0.407543] pci_bus 0000:01: resource 3 mem: [0x0-0x0]
[    0.407544] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.407545] pci_bus 0000:02: resource 1 mem: [0xfda00000-0xfdafffff]
[    0.407547] pci_bus 0000:02: resource 2 mem: [0xfd700000-0xfd7fffff]
[    0.407548] pci_bus 0000:02: resource 3 mem: [0x0-0x0]
[    0.407549] pci_bus 0000:03: resource 0 io:  [0x9000-0x9fff]
[    0.407550] pci_bus 0000:03: resource 1 mem: [0xfd600000-0xfd6fffff]
[    0.407551] pci_bus 0000:03: resource 2 mem: [0xfd500000-0xfd5fffff]
[    0.407552] pci_bus 0000:03: resource 3 mem: [0x0-0x0]
[    0.407553] pci_bus 0000:04: resource 0 io:  [0xd000-0xdfff]
[    0.407555] pci_bus 0000:04: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.407556] pci_bus 0000:04: resource 2 mem: [0xfdd00000-0xfddfffff]
[    0.407557] pci_bus 0000:04: resource 3 mem: [0x0-0x0]
[    0.407558] pci_bus 0000:05: resource 0 io:  [0xc000-0xcfff]
[    0.407559] pci_bus 0000:05: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.407561] pci_bus 0000:05: resource 2 mem: [0xfdb00000-0xfdbfffff]
[    0.407562] pci_bus 0000:05: resource 3 mem: [0x0-0x0]
[    0.407563] pci_bus 0000:06: resource 0 io:  [0x8000-0x8fff]
[    0.407564] pci_bus 0000:06: resource 1 mem: [0xfd900000-0xfd9fffff]
[    0.407565] pci_bus 0000:06: resource 2 mem: [0xfd800000-0xfd8fffff]
[    0.407566] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.407567] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.407581] NET: Registered protocol family 2
[    0.446708] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.446931] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.447705] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.447939] TCP: Hash tables configured (established 262144 bind 65536)
[    0.447941] TCP reno registered
[    0.456741] NET: Registered protocol family 1
[    0.456829] checking if image is initramfs... it is
[    0.828103] Freeing initrd memory: 7572k freed
[    0.831099] audit: initializing netlink socket (disabled)
[    0.831108] type=2000 audit(1238907957.829:1): initialized
[    0.831374] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.833565] VFS: Disk quotas dquot_6.5.2
[    0.833634] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.834238] msgmni has been set to 7801
[    0.834374] alg: No test for stdrng (krng)
[    0.834379] io scheduler noop registered
[    0.834380] io scheduler anticipatory registered
[    0.834381] io scheduler deadline registered
[    0.834452] io scheduler cfq registered (default)
[    0.834574] pci 0000:01:00.0: Boot video device
[    0.834672] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.834699] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.834832] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.834867] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.835066] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.835101] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.835294] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.835329] pcieport-driver 0000:00:1c.4: irq 27 for MSI/MSI-X
[    0.835521] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.835556] pcieport-driver 0000:00:1c.5: irq 28 for MSI/MSI-X
[    0.836333] ACPI: SSDT CFEE8A40, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20050309)
[    0.836521] processor ACPI_CPU:00: registered as cooling_device0
[    0.836706] ACPI: SSDT CFEE8F00, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20050309)
[    0.836876] processor ACPI_CPU:01: registered as cooling_device1
[    0.837048] ACPI: SSDT CFEE9060, 0152 (r1  PmRef  Cpu2Ist     3000 INTL 20050309)
[    0.837219] processor ACPI_CPU:02: registered as cooling_device2
[    0.837397] ACPI: SSDT CFEE91C0, 0152 (r1  PmRef  Cpu3Ist     3000 INTL 20050309)
[    0.837556] processor ACPI_CPU:03: registered as cooling_device3
[    0.839561] thermal LNXTHERM:01: registered as thermal_zone0
[    0.839896] ACPI: Thermal Zone [THRM] (14 C)
[    0.874344] Linux agpgart interface v0.103
[    0.874346] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.874459] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.874937] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.876606] brd: module loaded
[    0.876666] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.876835] PNP: No PS/2 controller found. Probing ports directly.
[    0.877155] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.877159] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.880749] Switched to high resolution mode on CPU 1
[    0.880839] Switched to high resolution mode on CPU 3
[    0.880866] Switched to high resolution mode on CPU 2
[    0.883423] Switched to high resolution mode on CPU 0
[    0.890094] mice: PS/2 mouse device common for all mice
[    0.890190] rtc_cmos 00:03: RTC can wake from S4
[    0.890260] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.890279] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.890332] cpuidle: using governor ladder
[    0.890333] cpuidle: using governor menu
[    0.890526] TCP cubic registered
[    0.891462] registered taskstats version 1
[    0.891567] rtc_cmos 00:03: setting system clock to 2009-04-05 05:05:58 UTC (1238907958)
[    0.891596] Freeing unused kernel memory: 364k freed
[    0.959278] fuse init (API version 7.11)
[    1.033006] usbcore: registered new interface driver usbfs
[    1.033023] usbcore: registered new interface driver hub
[    1.033046] usbcore: registered new device driver usb
[    1.034191] uhci_hcd: USB Universal Host Controller Interface driver
[    1.034242] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.034248] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.034251] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.034280] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.034308] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[    1.034402] usb usb1: configuration #1 chosen from 1 choice
[    1.034425] hub 1-0:1.0: USB hub found
[    1.034429] hub 1-0:1.0: 2 ports detected
[    1.034519] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.034524] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.034526] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.034546] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    1.034570] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[    1.034641] usb usb2: configuration #1 chosen from 1 choice
[    1.034663] hub 2-0:1.0: USB hub found
[    1.034668] hub 2-0:1.0: 2 ports detected
[    1.034744] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.034748] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.034751] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.034770] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    1.034794] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fd00
[    1.034861] usb usb3: configuration #1 chosen from 1 choice
[    1.034884] hub 3-0:1.0: USB hub found
[    1.034888] hub 3-0:1.0: 2 ports detected
[    1.034969] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.034974] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.034976] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.034995] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    1.035019] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[    1.035085] usb usb4: configuration #1 chosen from 1 choice
[    1.035107] hub 4-0:1.0: USB hub found
[    1.035112] hub 4-0:1.0: 2 ports detected
[    1.035190] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.035194] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.035197] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.035214] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    1.035233] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[    1.035301] usb usb5: configuration #1 chosen from 1 choice
[    1.035323] hub 5-0:1.0: USB hub found
[    1.035328] hub 5-0:1.0: 2 ports detected
[    1.035409] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.035414] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.035416] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.035434] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    1.035458] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[    1.035527] usb usb6: configuration #1 chosen from 1 choice
[    1.035548] hub 6-0:1.0: USB hub found
[    1.035553] hub 6-0:1.0: 2 ports detected
[    1.050911] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.050914] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    1.050929] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.050949] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.050951] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.050974] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[    1.054886] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.054891] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
[    1.067925] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.068002] usb usb7: configuration #1 chosen from 1 choice
[    1.068027] hub 7-0:1.0: USB hub found
[    1.068032] hub 7-0:1.0: 6 ports detected
[    1.068127] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.068136] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.068138] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.068160] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    1.072069] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.072073] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
[    1.084592] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.084655] usb usb8: configuration #1 chosen from 1 choice
[    1.084680] hub 8-0:1.0: USB hub found
[    1.084687] hub 8-0:1.0: 6 ports detected
[    1.099550] SCSI subsystem initialized
[    1.114639] libata version 3.00 loaded.
[    1.115781] sky2 driver version 1.22
[    1.115805] sky2 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.115812] sky2 0000:03:00.0: setting latency timer to 64
[    1.115835] sky2 0000:03:00.0: Yukon-2 EC chip revision 2
[    1.147975] sky2 0000:03:00.0: Marvell Yukon 88E8053 Gigabit Ethernet Controller
[    1.147977]  Part Number: Yukon 88E8053
[    1.147978]  Engineering Level: Rev. 2.2
[    1.147979]  Manufacturer: Marvell
[    1.148024] sky2 0000:03:00.0: irq 29 for MSI/MSI-X
[    1.148231] sky2 eth0: addr 00:01:29:a2:df:f5
[    1.148247] sky2 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.148255] sky2 0000:05:00.0: setting latency timer to 64
[    1.148274] sky2 0000:05:00.0: Yukon-2 EC chip revision 2
[    1.153039] pata_jmicron 0000:04:00.1: enabling device (0000 -> 0001)
[    1.153043] pata_jmicron 0000:04:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.153065] pata_jmicron 0000:04:00.1: setting latency timer to 64
[    1.155348] ahci 0000:00:1f.2: version 3.0
[    1.155358] ahci 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.155394] ahci 0000:00:1f.2: irq 30 for MSI/MSI-X
[    1.155445] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.155447] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part ems 
[    1.155451] ahci 0000:00:1f.2: setting latency timer to 64
[    1.155648] scsi0 : pata_jmicron
[    1.155664] scsi1 : ahci
[    1.155752] scsi2 : pata_jmicron
[    1.155777] ata1: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
[    1.155779] ata2: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
[    1.155784] scsi3 : ahci
[    1.155828] scsi4 : ahci
[    1.155868] scsi5 : ahci
[    1.155915] scsi6 : ahci
[    1.155954] scsi7 : ahci
[    1.156046] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 30
[    1.156048] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 30
[    1.156050] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 30
[    1.156052] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 30
[    1.156054] ata7: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 30
[    1.156055] ata8: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 30
[    1.157073] ohci1394 0000:06:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.180476] sky2 0000:05:00.0: Marvell Yukon 88E8052 Gigabit Ethernet Controller
[    1.180477]  Part Number: Yukon 88E8052
[    1.180478]  Engineering Level: Rev. 2.2
[    1.180479]  Manufacturer: Marvell
[    1.180517] sky2 0000:05:00.0: irq 31 for MSI/MSI-X
[    1.180689] sky2 eth1: addr 00:01:29:a2:e0:3f
[    1.212470] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fd9ff000-fd9ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.310616] ata1.01: NODEV after polling detection
[    1.317924] ata1.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
[    1.331189] ata1.00: configured for UDMA/33
[    1.334363] scsi 0:0:0:0: CD-ROM            BENQ     DVD DD DW1640    BSRB PQ: 0 ANSI: 5
[    1.505318] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    1.512429] Driver 'sr' needs updating - please use bus_type methods
[    1.515285] sr0: scsi3-mmc drive: 125x/94x writer cd/rw xa/form2 cdda tray
[    1.515288] Uniform CD-ROM driver Revision: 3.20
[    1.515367] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.603341] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    1.633344] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.634592] ata3.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
[    1.634594] ata3.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.636187] ata3.00: configured for UDMA/133
[    1.636247] scsi 1:0:0:0: Direct-Access     ATA      ST3640323AS      SD1B PQ: 0 ANSI: 5
[    1.636360] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    1.780375] usb 1-1: configuration #1 chosen from 1 choice
[    1.796518] usbcore: registered new interface driver hiddev
[    1.796580] usbcore: registered new interface driver usbhid
[    1.796582] usbhid: v2.6:USB HID core driver
[    2.010006] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    2.113342] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.114669] ata4.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
[    2.114671] ata4.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.116328] ata4.00: configured for UDMA/133
[    2.116388] scsi 3:0:0:0: Direct-Access     ATA      ST3640323AS      SD1B PQ: 0 ANSI: 5
[    2.116475] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[    2.176618] usb 2-1: configuration #1 chosen from 1 choice
[    2.192732] input: Kensington USB Input Device as /devices/pci0000:00/0000:00:1a.1/usb2/2-1/2-1:1.0/input/input1
[    2.203394] generic-usb 0003:047D:1013.0003: input,hidraw0: USB HID v1.00 Mouse [Kensington USB Input Device] on usb-0000:00:1a.1-1/input0
[    2.483447] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000129200006b6b2]
[    2.993343] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.007318] ata5.00: ATA-8: WDC WD7501AALS-00J7B0, 05.00K05, max UDMA/133
[    3.007320] ata5.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.008265] ata5.00: configured for UDMA/133
[    3.008324] scsi 4:0:0:0: Direct-Access     ATA      WDC WD7501AALS-0 05.0 PQ: 0 ANSI: 5
[    3.008409] scsi 4:0:0:0: Attached scsi generic sg3 type 0
[    3.326677] ata6: SATA link down (SStatus 0 SControl 300)
[    3.646676] ata7: SATA link down (SStatus 0 SControl 300)
[    3.966676] ata8: SATA link down (SStatus 0 SControl 300)
[    3.966704] ahci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.980444] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    3.980447] ahci 0000:04:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    3.980452] ahci 0000:04:00.0: setting latency timer to 64
[    3.980548] scsi8 : ahci
[    3.980609] scsi9 : ahci
[    3.980644] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
[    3.980647] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
[    4.300020] ata9: SATA link down (SStatus 0 SControl 300)
[    4.646687] ata10: SATA link down (SStatus 0 SControl 300)
[    4.674622] Driver 'sd' needs updating - please use bus_type methods
[    4.674692] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.674704] sd 1:0:0:0: [sda] Write Protect is off
[    4.674705] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.674723] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.674778] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.674789] sd 1:0:0:0: [sda] Write Protect is off
[    4.674791] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.674811] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.674813]  sda: sda1 sda2 sda3
[    4.686014] sd 1:0:0:0: [sda] Attached SCSI disk
[    4.686067] sd 3:0:0:0: [sdb] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.686078] sd 3:0:0:0: [sdb] Write Protect is off
[    4.686080] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.686098] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.686143] sd 3:0:0:0: [sdb] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.686155] sd 3:0:0:0: [sdb] Write Protect is off
[    4.686156] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.686175] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.686177]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 sdb6 sdb7 >
[    4.732950] sd 3:0:0:0: [sdb] Attached SCSI disk
[    4.732996] sd 4:0:0:0: [sdc] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    4.733007] sd 4:0:0:0: [sdc] Write Protect is off
[    4.733009] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.733026] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.733067] sd 4:0:0:0: [sdc] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    4.733078] sd 4:0:0:0: [sdc] Write Protect is off
[    4.733080] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.733098] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.733101]  sdc: sdc1
[    4.736139] sd 4:0:0:0: [sdc] Attached SCSI disk
[   10.093911] kjournald starting.  Commit interval 5 seconds
[   10.093920] EXT3-fs: mounted filesystem with ordered data mode.
[   16.007418] udevd version 124 started
[   16.121131] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   16.133342] ACPI: Power Button (FF) [PWRF]
[   16.133404] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   16.146672] ACPI: Power Button (CM) [PWRB]
[   16.170241] nvidia: module license 'NVIDIA' taints kernel.
[   16.324066] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0/input/input4
[   16.346734] microsoft 0003:045E:00DB.0001: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:1a.0-1/input0
[   16.366990] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.1/input/input5
[   16.397625] microsoft 0003:045E:00DB.0002: input,hidraw2: USB HID v1.11 Device [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:1a.0-1/input1
[   16.437282] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.437288] nvidia 0000:01:00.0: setting latency timer to 64
[   16.437439] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   16.440662] iTCO_vendor_support: vendor-support=0
[   16.441459] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   16.441548] iTCO_wdt: Found a ICH9R TCO device (Version=2, TCOBASE=0x0460)
[   16.441627] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.454874] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   16.533027] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.533060] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.579240] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   21.019131] it87: Found IT8718F chip at 0x290, revision 2
[   21.019138] it87: in3 is VCC (+5V)
[   21.019140] it87: in7 is VCCH (+5V Stand-By)
[   21.019160] ACPI: I/O resource it87 [0x295-0x296] conflicts with ACPI region IP__ [0x295-0x296]
[   21.019161] ACPI: Device needs an ACPI driver
[   21.023232] coretemp coretemp.0: Using relative temperature scale!
[   21.023267] coretemp coretemp.1: Using relative temperature scale!
[   21.023301] coretemp coretemp.2: Using relative temperature scale!
[   21.023350] coretemp coretemp.3: Using relative temperature scale!
[   21.118615] Adding 2048248k swap on /dev/sdb6.  Priority:-1 extents:1 across:2048248k 
[   21.465812] EXT3 FS on sdb2, internal journal
[   21.974213] kjournald starting.  Commit interval 5 seconds
[   21.974545] EXT3 FS on sdb5, internal journal
[   21.974549] EXT3-fs: mounted filesystem with ordered data mode.
[   22.717594] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.743016] sky2 eth1: enabling interface
[   22.824735] NET: Registered protocol family 10
[   22.825077] lo: Disabled Privacy Extensions
[   22.825612] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

---

### Post by Slim Odds on 2009-04-05
People get fooled by the difference in memory reporting tools all of the time. Take some time to learn how linux uses memory.

free is combining different types of memory usage into the "used" category. This include actual memory used by programs and also the disk cache.

Try installing htop.

It has a nice way of showing how the memory is used.

Also, my 8G machine looks like this:
```
             total       used       free     shared    buffers     cached
Mem:          7991       7732        258          0        200       5199
-/+ buffers/cache:       2333       5658
Swap:         7812          5       7807

```The vast majority of the "used" memory is disk cache.

---

### Post by graysky on 2009-04-05
Yeah, I have htop and I understand that now... I'm actually more interested in learning where that extra 195 megs went.  4096-195=3901

---

### Post by jespdj on 2009-04-05
People frequently ask questions about this in the forums here.

Your computer contains a number of devices such as the graphics card, I/O interfaces etc. that all need part of the address space of the computer to be able to communicate with the CPU.

A 32-bit CPU is limited to an address space of 4 GB (2^32 bytes). The addresses for the graphics card and other devices need to be within that 4 GB address space to be usable by a 32-bit CPU. That's why, with a 32-bit CPU and 32-bit OS, you will never be able to use the full 4096 MB RAM.

When you use a 64-bit OS, then normally the address space for the graphics card and devices will still be within the 4 GB address space and so you'll still not be able to use the whole 4096 MB RAM. Newer motherboard chipsets have the ability to relocate the address space of the graphics card and other devices to another location above the 4 GB limit to make more of the RAM visible to the CPU. Look for a "memory remapping" feature in the BIOS setup of your computer and enable it.

But don't expect the full 4096 MB to ever be visible; even with memory remapping enabled, there's still a small part of the address space which is reserved and unreachable by the CPU.

I currently can't check what 'free' displays on my laptop, because I discovered this weekend that one of the memory modules in my laptop is broken. :( (I've taken it out and I'm currently running with 2 instead of 4 GB).

---

### Post by privatejarhead on 2009-07-08
> **king1111 said:**
> mi essey about 9/11

on 9/11 a terrebel ting happnd, a planes crashed into da wurld tred senturs and da witehouse. it waz verry scury, lots of ppl dyed and ppl where runnin evrywere scurrd for der lifes. r presedent gorge bush standed up in front of da wurld and told da wurld dat he wud catch da bad boys woo did dis and dat hed safe da day. evry1 waz happi, i saw it on my tv and i cryed cuz i new we wer safed but i waz sad cuz al da ppl had dyed, lyk my mommy and daddy woo where in da wurld tred senturs wen da muselms bomd dem. [enterrement de vie de garçon original](http://www.lamosca.fr/enterrementdeviedegarcon.htm) [Free Online Games](http://www.playhub.com) 
sinse den da wurld has chanjd a lot. cuz off presendent bush and da ppl in da guvremet who dat helpd him, da wurld is safed.


uhhh, wtf? this has anything to do with computer memory?

---

### Post by RD1 on 2009-07-08
> 
Quote:
Originally Posted by king1111 View Post
mi essey about 9/11

on 9/11 a terrebel ting happnd, a planes crashed into da wurld tred senturs and da witehouse. it waz verry scury, lots of ppl dyed and ppl where runnin evrywere scurrd for der lifes. r presedent gorge bush standed up in front of da wurld and told da wurld dat he wud catch da bad boys woo did dis and dat hed safe da day. evry1 waz happi, i saw it on my tv and i cryed cuz i new we wer safed but i waz sad cuz al da ppl had dyed, lyk my mommy and daddy woo where in da wurld tred senturs wen da muselms bomd dem. enterrement de vie de garçon original Free Online Games
sinse den da wurld has chanjd a lot. cuz off presendent bush and da ppl in da guvremet who dat helpd him, da wurld is safed.

uhhh, wtf? this has anything to do with computer memory?


Spammer ... user has only 3 posts, all with the same links in them.

back to topic ... my free with 2GB ram:

```
rodger@Bodhisattva:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004       1368        635          0         68        908
-/+ buffers/cache:        392       1612
Swap:         4094          0       4094

```

---

### Post by sdlynx on 2009-07-08
heres my 4 gigs in free:

```
             total       used       free     shared    buffers     cached
Mem:          3863       1846       2017          0        213        958
-/+ buffers/cache:        673       3189
Swap:         2055          0       2055
```

obviously everyone's system is like that, so I think it's fine.

as for the conky thing I don't think conky shows the RAM that is being used for cache, while free does

---

