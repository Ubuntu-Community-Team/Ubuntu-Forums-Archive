---
title: "Black screen with realtime kernel on Ubuntu 8.04"
date: 2008-05-13
forum: x86 64-bit Users
---

### Post by Le Farfadet Spatial on 2008-05-13
Hello everybody out there!

   As a start, please forgive me for not really mastering English, but I am French, and as everyone knows, French people are not good at all in using another language than their mother tongue!

   I have recently upgrade Feisty Fawn (7.10) to Hardy Heron (8.04), and a problem appears: when I boot the real-time kernel, the boot sequence does not finish properly and all I get is a black screen. The keyboard does not response either, even the caps lock, and num lock diodes do not light up. Maybe there is some conflict, I do not know and no one on the French Unbuntu forum had been able to help me. Maybe somebody here has some information.

   Here is my configuration:

      -- laptop Dell Latitude D820;

      -- processor Intel Core 2 Duo T7200 (2.0GHz 667MHz FSB);

      -- bi-canal memory 2x1024Mo DDR2-SDRAM 533MHz;

      -- video card NVIDIA Quadro NVS 110M 256MB;

      -- 15.4" screen WSXGGA+ (1680 x 1050) LCD;

      -- hard drive 100Go SATA (7200 TPM));

      -- DVD burner 8x +/- RW;

      -- long lasting battery 9 cells 85 WHr LI-ION;

      -- Bluetooth card for Latitude;

      -- Intel PRO/Wireless 3945 802.11a/g;

      -- Sound Blaster Audigy 2 ZS;

      -- Ubuntu Linux 8.04 Hardy Heron desktop 64 bits.

   I am running the NVidia proprietary driver.

   Regards.

                                                        The Spatial Sprite

---

### Post by cosh1 on 2008-05-14
I also have this problem.  I'm using an Asus Rampage Formula motherboard (Intel x48 chipset).  My video card is a BFG 8800GTS.  I have tried both the 64bit and 32bit versions on my Q6600.

---

### Post by Kernel_Krunch on 2008-05-14
try ctrl+alt+F4 at the blank screen, see if a login prompt appears. If yes login and run ```
init 5
``` remember any errors

If not... you can boot of the CD and mount your drive then look at your /var/log/dmesg & /var/log/Xorg.0.log for errors.

Someone said Xorg is bugged out and being fixed... that can also be the problem.

---

### Post by Le Farfadet Spatial on 2008-05-14
Hello everybody out there!

> **Kernel_Krunch said:**
> 
try ctrl+alt+F4 at the blank screen, see if a login prompt appears. If yes login and run ```
init 5
``` remember any errors


This was my very first idea, but there is no way I can get any virtual console.

> 
If not... you can boot of the CD and mount your drive then look at your /var/log/dmesg & /var/log/Xorg.0.log for errors.


Well, I have not burned a CD of Hardy Heron. But I can use the generic kernel (this is what I am doing just now). I have not found any information in the two files you are mentioning, but I can have failed to notice something important. Here is my /var/log/dmesg:

```

[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=0d21a147-855d-4347-a544-d16158675e12 ro quiet splash locale=fr_FR
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe81400 (usable)
[    0.000000]  BIOS-e820: 000000007fe81400 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 523905) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FC0B0 checksum 0
[    0.000000] ACPI: RSDP 000FC0B0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 7FE8198A, 0044 (r1 DELL    M07     27D60A0D ASL        61)
[    0.000000] ACPI: FACP 7FE82800, 0074 (r1 DELL    M07     27D60A0D ASL        61)
[    0.000000] ACPI: DSDT 7FE83400, 50B2 (r1 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7FE91C00, 0040
[    0.000000] ACPI: HPET 7FE82F00, 0038 (r1 DELL    M07            1 ASL        61)
[    0.000000] ACPI: APIC 7FE83000, 0068 (r1 DELL    M07     27D60A0D ASL        47)
[    0.000000] ACPI: ASF! 7FE82C00, 005B (r16 DELL    M07     27D60A0D ASL        61)
[    0.000000] ACPI: MCFG 7FE82FC0, 003E (r16 DELL    M07     27D60A0D ASL        61)
[    0.000000] ACPI: SLIC 7FE8309C, 0176 (r1 DELL    M07     27D60A0D ASL        61)
[    0.000000] ACPI: TCPA 7FE83300, 0032 (r1 DELL    M07     27D60A0D ASL        61)
[    0.000000] ACPI: SSDT 7FE81A11, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fe81000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 523905) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fe81000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   523905
[    0.000000] On node 0 totalpages: 523808
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1206 pages reserved
[    0.000000]   DMA zone: 2737 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7106 pages used for memmap
[    0.000000]   DMA32 zone: 512703 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515440
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=0d21a147-855d-4347-a544-d16158675e12 ro quiet splash locale=fr_FR
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[    8.275828] Marking TSC unstable due to TSCs unsynchronized
[    8.275830] time.c: Detected 1995.011 MHz processor.
[    8.277552] Console: colour VGA+ 80x25
[    8.277556] console [tty0] enabled
[    8.277573] Checking aperture...
[    8.277586] Calgary: detecting Calgary via BIOS EBDA area
[    8.277588] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    8.304570] Memory: 2053604k/2095620k available (2466k kernel code, 41628k reserved, 1309k data, 316k init)
[    8.304612] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    8.381755] Calibrating delay using timer specific routine.. 3994.17 BogoMIPS (lpj=7988356)
[    8.381791] Security Framework initialized
[    8.381799] SELinux:  Disabled at boot.
[    8.381812] AppArmor: AppArmor initialized
[    8.381816] Failure registering capabilities with primary security module.
[    8.382034] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    8.383711] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.384580] Mount-cache hash table entries: 256
[    8.384741] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.384744] CPU: L2 cache: 4096K
[    8.384747] CPU 0/0 -> Node 0
[    8.384748] using mwait in idle threads.
[    8.384750] CPU: Physical Processor ID: 0
[    8.384751] CPU: Processor Core ID: 0
[    8.384758] CPU0: Thermal monitoring enabled (TM2)
[    8.384774] SMP alternatives: switching to UP code
[    8.385573] Early unpacking initramfs... done
[    8.748672] ACPI: Core revision 20070126
[    8.748714] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.792669] Using local APIC timer interrupts.
[    8.842771] APIC timer calibration result 10390673
[    8.842772] Detected 10.390 MHz APIC timer.
[    8.842855] SMP alternatives: switching to SMP code
[    8.843529] Booting processor 1/2 APIC 0x1
[   11.017173] Initializing CPU#1
[   11.093855] Calibrating delay using timer specific routine.. 3990.03 BogoMIPS (lpj=7980076)
[   11.093862] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.093863] CPU: L2 cache: 4096K
[   11.093865] CPU 1/1 -> Node 0
[   11.093867] CPU: Physical Processor ID: 0
[   11.093868] CPU: Processor Core ID: 1
[   11.093874] CPU1: Thermal monitoring enabled (TM2)
[   11.094385] Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[    8.931345] Brought up 2 CPUs
[    8.931427] CPU0 attaching sched-domain:
[    8.931429]  domain 0: span 03
[    8.931430]   groups: 01 02
[    8.931433]   domain 1: span 03
[    8.931434]    groups: 03
[    8.931436] CPU1 attaching sched-domain:
[    8.931437]  domain 0: span 03
[    8.931439]   groups: 02 01
[    8.931441]   domain 1: span 03
[    8.931442]    groups: 03
[    8.931662] net_namespace: 120 bytes
[    8.932034] Time: 18:59:35  Date: 05/13/08
[    8.932059] NET: Registered protocol family 16
[    8.932236] ACPI: bus type pci registered
[    8.932307] PCI: Using configuration type 1
[    8.936844] ACPI: EC: Look up EC in DSDT
[    8.949346] ACPI Warning (tbutils-0217): Incorrect checksum in table [TCPA] -  00, should be 9A [20070126]
[    8.949350] ACPI: SSDT 7FE819CE, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
[    8.949487] ACPI: Interpreter enabled
[    8.949490] ACPI: (supports S0 S3 S4 S5)
[    8.949502] ACPI: Using IOAPIC for interrupt routing
[    8.979744] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.980515] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.980519] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    8.981795] PCI: Transparent bridge - 0000:00:1e.0
[    8.981890] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.982302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    8.982391] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    8.982526] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    8.982635] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    8.982747] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PXP0._PRT]
[    8.982817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    8.996056] ACPI: PCI Interrupt Link [LNKA] (IRQs *9 10 11)
[    8.996155] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *3
[    8.996251] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    8.996348] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    8.996444] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    8.996542] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    8.996640] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    8.996738] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    8.996868] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.996894] pnp: PnP ACPI init
[    8.996901] ACPI: bus type pnp registered
[    9.011660] pnpacpi: exceeded the max number of mem resources: 12
[    9.039424] pnp: PnP ACPI: found 14 devices
[    9.039426] ACPI: ACPI bus type pnp unregistered
[    9.039636] PCI: Using ACPI for IRQ routing
[    9.039638] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.050677] NET: Registered protocol family 8
[    9.050679] NET: Registered protocol family 20
[    9.050709] PCI-GART: No AMD northbridge found.
[    9.050715] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    9.050718] hpet0: 3 64-bit timers, 14318180 Hz
[    9.051750] AppArmor: AppArmor Filesystem Enabled
[    9.054660] Time: hpet clocksource has been installed.
[    9.054672] Switched to high resolution mode on CPU 0
[   11.218334] Switched to high resolution mode on CPU 1
[    9.062648] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    9.062651] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    9.062653] system 00:00: iomem range 0xc0000-0xcffff has been reserved
[    9.062655] system 00:00: iomem range 0xe0000-0xfffff has been reserved
[    9.062658] system 00:00: iomem range 0x100000-0x7fe813ff could not be reserved
[    9.062660] system 00:00: iomem range 0x7fe81400-0x7fefffff could not be reserved
[    9.062662] system 00:00: iomem range 0x7ff00000-0x7fffffff could not be reserved
[    9.062665] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
[    9.062667] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    9.062669] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    9.062671] system 00:00: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    9.062674] system 00:00: iomem range 0xfed45000-0xfed9ffff could not be reserved
[    9.062679] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    9.062681] system 00:02: ioport range 0x1000-0x1005 has been reserved
[    9.062684] system 00:02: ioport range 0x1008-0x100f has been reserved
[    9.062688] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    9.062690] system 00:03: ioport range 0x1006-0x1007 has been reserved
[    9.062693] system 00:03: ioport range 0x100a-0x1059 could not be reserved
[    9.062695] system 00:03: ioport range 0x1060-0x107f has been reserved
[    9.062697] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    9.062699] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    9.062701] system 00:03: ioport range 0x1010-0x102f has been reserved
[    9.062703] system 00:03: ioport range 0x809-0x809 has been reserved
[    9.062711] system 00:08: ioport range 0xc80-0xcaf has been reserved
[    9.062713] system 00:08: ioport range 0xcc0-0xcff could not be reserved
[    9.062715] system 00:08: ioport range 0x910-0x91f has been reserved
[    9.062717] system 00:08: ioport range 0x920-0x92f has been reserved
[    9.062719] system 00:08: ioport range 0xcbc-0xcbf has been reserved
[    9.062721] system 00:08: ioport range 0x930-0x97f has been reserved
[    9.062727] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    9.062732] system 00:0d: ioport range 0xcb0-0xcbb has been reserved
[    9.062734] system 00:0d: iomem range 0xfed40000-0xfed44fff could not be reserved
[    9.063117] PCI: Bridge: 0000:00:01.0
[    9.063119]   IO window: disabled.
[    9.063122]   MEM window: ed000000-efefffff
[    9.063124]   PREFETCH window: d0000000-dfffffff
[    9.063128] PCI: Bridge: 0000:00:1c.0
[    9.063129]   IO window: disabled.
[    9.063134]   MEM window: disabled.
[    9.063137]   PREFETCH window: disabled.
[    9.063142] PCI: Bridge: 0000:00:1c.1
[    9.063143]   IO window: disabled.
[    9.063148]   MEM window: ecf00000-ecffffff
[    9.063152]   PREFETCH window: disabled.
[    9.063157] PCI: Bridge: 0000:00:1c.2
[    9.063158]   IO window: disabled.
[    9.063164]   MEM window: ece00000-ecefffff
[    9.063167]   PREFETCH window: disabled.
[    9.063172] PCI: Bridge: 0000:00:1c.3
[    9.063175]   IO window: e000-efff
[    9.063180]   MEM window: ecc00000-ecdfffff
[    9.063184]   PREFETCH window: e0000000-e01fffff
[    9.063196] PCI: Bus 4, cardbus bridge: 0000:03:01.0
[    9.063198]   IO window: 00001400-000014ff
[    9.063203]   IO window: 00001800-000018ff
[    9.063207]   PREFETCH window: 88000000-8bffffff
[    9.063212]   MEM window: 8c000000-8fffffff
[    9.063216] PCI: Bridge: 0000:00:1e.0
[    9.063217]   IO window: disabled.
[    9.063222]   MEM window: ecb00000-ecbfffff
[    9.063226]   PREFETCH window: disabled.
[    9.063242] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.063246] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    9.063268] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.063273] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.063295] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    9.063301] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.063323] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    9.063328] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.063351] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[    9.063356] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    9.063369] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.063386] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
[    9.063389] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[    9.063402] NET: Registered protocol family 2
[    9.098691] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    9.099347] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    9.101353] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    9.102130] TCP: Hash tables configured (established 262144 bind 65536)
[    9.102132] TCP reno registered
[    9.110753] checking if image is initramfs... it is
[    9.823412] Freeing initrd memory: 7942k freed
[   11.992380] audit: initializing netlink socket (disabled)
[   11.992404] audit(1210705175.508:1): initialized
[   11.994576] VFS: Disk quotas dquot_6.5.1
[   11.994642] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   11.994757] io scheduler noop registered
[   11.994759] io scheduler anticipatory registered
[   11.994760] io scheduler deadline registered
[   11.994860] io scheduler cfq registered (default)
[   11.997175] Boot video device is 0000:01:00.0
[   11.997353] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   11.997386] assign_interrupt_mode Found MSI capability
[   11.997414] Allocate Port Service[0000:00:01.0:pcie00]
[   11.997493] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.997548] assign_interrupt_mode Found MSI capability
[   11.997592] Allocate Port Service[0000:00:1c.0:pcie00]
[   11.997624] Allocate Port Service[0000:00:1c.0:pcie02]
[   11.997720] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   11.997775] assign_interrupt_mode Found MSI capability
[   11.997819] Allocate Port Service[0000:00:1c.1:pcie00]
[   11.997852] Allocate Port Service[0000:00:1c.1:pcie02]
[   11.997949] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   11.998004] assign_interrupt_mode Found MSI capability
[   11.998048] Allocate Port Service[0000:00:1c.2:pcie00]
[   11.998082] Allocate Port Service[0000:00:1c.2:pcie02]
[   11.998178] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   11.998232] assign_interrupt_mode Found MSI capability
[   11.998276] Allocate Port Service[0000:00:1c.3:pcie00]
[   11.998309] Allocate Port Service[0000:00:1c.3:pcie02]
[   12.022677] Real Time Clock Driver v1.12ac
[   12.022828] hpet_resources: 0xfed00000 is busy
[   12.022876] Linux agpgart interface v0.102
[   12.022878] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.023030] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.023578] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.024255] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.024319] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   12.024409] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.864276] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.864281] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.874277] mice: PS/2 mouse device common for all mice
[    9.874312] cpuidle: using governor ladder
[    9.874313] cpuidle: using governor menu
[    9.874446] NET: Registered protocol family 1
[    9.874497] registered taskstats version 1
[    9.874599]   Magic number: 8:322:999
[    9.874605]   hash matches device ttyaf
[    9.874664]   hash matches device 00:01
[    9.874665]   hash matches device pnp0
[    9.874679] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    9.874682] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.874683] EDD information not available.
[    9.874690] Freeing unused kernel memory: 316k freed
[    9.877620] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   13.209441] fuse init (API version 7.9)
[   13.223724] ACPI: SSDT 7FE82138, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   13.223898] ACPI: SSDT 7FE81EED, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   11.061304] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.061308] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.061542] ACPI: SSDT 7FE8237C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   11.061702] ACPI: SSDT 7FE820B3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   13.225427] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   13.225431] ACPI: Processor [CPU1] (supports 8 throttling states)
[   13.229055] ACPI: Thermal Zone [THM] (47 C)
[   11.324616] usbcore: registered new interface driver usbfs
[   11.324637] usbcore: registered new interface driver hub
[   11.324986] usbcore: registered new device driver usb
[   11.325987] USB Universal Host Controller Interface driver v3.0
[   11.326039] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   11.326051] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.326054] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.326309] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.326343] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[   11.326454] usb usb1: configuration #1 chosen from 1 choice
[   11.326474] hub 1-0:1.0: USB hub found
[   11.326478] hub 1-0:1.0: 2 ports detected
[   11.382486] SCSI subsystem initialized
[   11.403286] libata version 3.00 loaded.
[   11.429320] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
[   11.429333] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.429337] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.429358] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.429390] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[   11.429494] usb usb2: configuration #1 chosen from 1 choice
[   11.429513] hub 2-0:1.0: USB hub found
[   11.429518] hub 2-0:1.0: 2 ports detected
[   11.533252] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 22
[   11.533264] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.533267] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.533288] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.533319] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[   11.533414] usb usb3: configuration #1 chosen from 1 choice
[   11.533433] hub 3-0:1.0: USB hub found
[   11.533438] hub 3-0:1.0: 2 ports detected
[   11.637184] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 23
[   11.637195] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   11.637199] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   11.637218] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   11.637251] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[   11.637347] usb usb4: configuration #1 chosen from 1 choice
[   11.637366] hub 4-0:1.0: USB hub found
[   11.637370] hub 4-0:1.0: 2 ports detected
[   11.669066] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   13.904290] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   13.905452] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.905458] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.905507] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   13.909428] ehci_hcd 0000:00:1d.7: debug port 1
[   13.909434] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.909441] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[   13.952113] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.952287] usb usb5: configuration #1 chosen from 1 choice
[   13.952322] hub 5-0:1.0: USB hub found
[   13.952328] hub 5-0:1.0: 8 ports detected
[   11.799565] tg3.c:v3.86 (November 9, 2007)
[   11.799598] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   11.799609] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   11.816319] eth0: Tigon3 [partno(BCM5752KFBG) rev 6002 PHY(5752)] (PCI Express) 10/100/1000Base-T Ethernet 00:15:c5:c9:fd:60
[   11.816325] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   11.816327] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   13.979511] ACPI: PCI Interrupt 0000:03:01.4[A] -> GSI 19 (level, low) -> IRQ 19
[   14.030620] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ecbff000-ecbff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   11.872092] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   11.872127] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   11.872138] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   11.873950] ata_piix 0000:00:1f.2: version 2.12
[   11.873956] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   11.873972] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   11.873994] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   11.874099] scsi0 : ata_piix
[   11.874139] scsi1 : ata_piix
[   11.875769] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[   11.875771] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[   11.896160] ata1.00: ATA-7: Hitachi HTS721010G9SA00, MCZOC10H, max UDMA/100
[   11.896165] ata1.00: 195371568 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   11.897255] ata1.00: configured for UDMA/100
[   11.899330] usb 1-2: device not accepting address 2, error -71
[   11.910284] Clocksource tsc unstable (delta = -383664741 ns)
[   11.924208] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L632D, DE03, max UDMA/33
[   11.940052] ata2.00: configured for UDMA/33
[   11.940137] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72101 MCZO PQ: 0 ANSI: 5
[   11.942769] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE03 PQ: 0 ANSI: 5
[   11.947651] Driver 'sd' needs updating - please use bus_type methods
[   11.947713] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   11.947723] sd 0:0:0:0: [sda] Write Protect is off
[   11.947725] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.947739] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.947783] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   11.947791] sd 0:0:0:0: [sda] Write Protect is off
[   11.947792] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.947806] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.947809]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   11.970982]  sda1 sda2 < sda5 >
[   11.995786] sd 0:0:0:0: [sda] Attached SCSI disk
[   11.999552] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.999569] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   12.058413] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   12.058416] Uniform CD-ROM driver Revision: 3.20
[   12.058457] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   12.168314] Attempting manual resume
[   12.168317] swsusp: Resume From Partition 8:5
[   12.168318] PM: Checking swsusp image.
[   12.168526] PM: Resume from disk failed.
[   12.179036] EXT3-fs: INFO: recovery required on readonly filesystem.
[   12.179038] EXT3-fs: write access will be enabled during recovery.
[   12.254428] kjournald starting.  Commit interval 5 seconds
[   12.254445] EXT3-fs: sda1: orphan cleanup on readonly fs
[   12.254453] ext3_orphan_cleanup: deleting unreferenced inode 4980749
[   12.254485] ext3_orphan_cleanup: deleting unreferenced inode 4980748
[   12.254497] ext3_orphan_cleanup: deleting unreferenced inode 4980747
[   12.254507] ext3_orphan_cleanup: deleting unreferenced inode 4980746
[   12.254517] ext3_orphan_cleanup: deleting unreferenced inode 4980745
[   12.254526] EXT3-fs: sda1: 5 orphan inodes deleted
[   12.254529] EXT3-fs: recovery complete.
[   12.257177] EXT3-fs: mounted filesystem with ordered data mode.
[   12.352078] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[334fc0002d02dc50]
[   12.515668] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   12.663389] usb 1-2: configuration #1 chosen from 1 choice
[   12.666351] hub 1-2:1.0: USB hub found
[   12.668312] hub 1-2:1.0: 4 ports detected
[   13.013304] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   13.160734] usb 2-1: configuration #1 chosen from 1 choice
[   13.162675] hub 2-1:1.0: USB hub found
[   13.164056] hub 2-1:1.0: 3 ports detected
[   13.497463] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   13.667652] usb 4-1: configuration #1 chosen from 1 choice
[   13.890398] usb 1-2.3: new full speed USB device using uhci_hcd and address 5
[   14.053962] usb 1-2.3: configuration #1 chosen from 1 choice
[   14.260718] usb 2-1.2: new full speed USB device using uhci_hcd and address 3
[   14.376873] usb 2-1.2: configuration #1 chosen from 1 choice
[   21.763113] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.794031] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   22.440886] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   22.485351] ACPI: AC Adapter [AC] (on-line)
[   24.770460] ACPI: Battery Slot [BAT0] (battery present)
[   24.770508] ACPI: Battery Slot [BAT1] (battery absent)
[   22.624755] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.632766] input: Lid Switch as /devices/virtual/input/input2
[   22.633223] ACPI: Lid Switch [LID]
[   22.633263] input: Power Button (CM) as /devices/virtual/input/input3
[   22.660649] ACPI: Power Button (CM) [PBTN]
[   22.660708] input: Sleep Button (CM) as /devices/virtual/input/input4
[   22.692611] ACPI: Sleep Button (CM) [SBTN]
[   22.692812] ACPI: WMI-Acer: Mapper loaded
[   22.741710] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input5
[   22.772572] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   22.773088] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
[   22.804548] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   22.804695] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
[   22.836532] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   25.431214] nvidia: module license 'NVIDIA' taints kernel.
[   25.823792] intel_rng: FWH not detected
[   25.877424] Yenta: CardBus bridge found at 0000:03:01.0 [1028:01cc]
[   25.877449] Yenta O2: res at 0x94/0xD4: 00/ea
[   25.877450] Yenta O2: enabling read prefetch/write burst
[   25.928136] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   25.928140] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   26.005063] Yenta: ISA IRQ mask 0x0cb8, PCI irq 19
[   26.005068] Socket status: 30000820
[   26.005071] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   26.005077] pcmcia: parent PCI bridge Memory window: 0xecb00000 - 0xecbfffff
[   26.005711] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   26.005726] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   26.006743] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   26.078478] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   26.223966] Bluetooth: Core ver 2.11
[   26.225115] NET: Registered protocol family 31
[   26.225117] Bluetooth: HCI device and connection manager initialized
[   26.225119] Bluetooth: HCI socket layer initialized
[   24.077528] usbcore: registered new interface driver hiddev
[   24.088448] iTCO_vendor_support: vendor-support=0
[   24.089932] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input9
[   24.090274] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   26.319329] Bluetooth: HCI USB driver ver 2.9
[   26.531892] input: PS/2 Mouse as /devices/virtual/input/input10
[   24.475560] pccard: CardBus card inserted into slot 0
[   24.483581] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.3-1
[   24.483665] usbcore: registered new interface driver usbhid
[   24.483668] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   26.649782] usbcore: registered new interface driver hci_usb
[   24.576636] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[   24.631633] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   24.631668] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   26.795377] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   27.409928] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.409939] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   27.410061] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   27.412007] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   27.412013] hda_intel: position_fix set to 1 for device 1028:01cc
[   27.412860] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   25.291195] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   25.295324] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   27.628171] udev: renamed network interface wlan0 to eth1
[   25.530155] PCI: Enabling device 0000:04:00.0 (0000 -> 0001)
[   25.530166] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   25.530241] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   25.597618] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:226: Audigy2 value: Special config.
[   26.453785] lp: driver loaded but no devices found
[   26.566902] Adding 4016208k swap on /dev/sda5.  Priority:-1 extents:1 across:4016208k
[   26.858509] EXT3 FS on sda1, internal journal
[   27.042442] device-mapper: uevent: version 1.0.3
[   27.042471] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com

```

And here, my /var/log/Xorg.0.log:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux farfadet-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64
Build Date: 15 April 2008  05:41:18PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 13 21:00:13 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Écran générique"
(**) |   |-->Device "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Custom-Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1028,01cc rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1028,01cc rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01cc rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01cc rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01cc rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1028,01cc rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01cc rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1028,01cc rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1028,01cc rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01cc rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d7 card 1028,01cc rev a1 class 03,00,00 hdr 00
(II) PCI: 03:01:0: chip 1217,7135 card 1401,0000 rev 21 class 06,07,00 hdr 82
(II) PCI: 03:01:4: chip 1217,00f7 card 1028,01cc rev 02 class 0c,00,10 hdr 00
(II) PCI: 04:00:0: chip 1102,0008 card 1102,2001 rev 00 class 04,01,00 hdr 00
(II) PCI: 09:00:0: chip 14e4,1600 card 1028,01cc rev 02 class 02,00,00 hdr 00
(II) PCI: 0c:00:0: chip 8086,4222 card 8086,1021 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,13), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xed000000 - 0xefefffff (0x2f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:1), (0,12,12), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xecf00000 - 0xecffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 9: bridge is at (0:28:2), (0,9,9), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 9 non-prefetchable memory range:
	[0] -1	0	0xece00000 - 0xecefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 13: bridge is at (0:28:3), (0,13,14), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 13 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 13 non-prefetchable memory range:
	[0] -1	0	0xecc00000 - 0xecdfffff (0x200000) MX[B]
(II) Bus 13 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe01fffff (0x200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,7), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xecb00000 - 0xecbfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (3:1:0), (3,4,7), BCTRL: 0x0500 (VGA_EN is cleared)
(--) PCI:*(1:0:0) nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] rev 161, Mem @ 0xed000000/24, 0xd0000000/28, 0xee000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xecfff000 - 0xecffffff (0x1000) MX[B]
	[1] -1	0	0xecef0000 - 0xecefffff (0x10000) MX[B]
	[2] -1	0	0xecbfe800 - 0xecbfefff (0x800) MX[B]
	[3] -1	0	0xecbff000 - 0xecbfffff (0x1000) MX[B]
	[4] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[5] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[6] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[9] -1	0	0x00001400 - 0x0000143f (0x40) IX[B]
	[10] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[11] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[17] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[18] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[19] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xecfff000 - 0xecffffff (0x1000) MX[B]
	[1] -1	0	0xecef0000 - 0xecefffff (0x10000) MX[B]
	[2] -1	0	0xecbfe800 - 0xecbfefff (0x800) MX[B]
	[3] -1	0	0xecbff000 - 0xecbfffff (0x1000) MX[B]
	[4] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[5] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[6] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[9] -1	0	0x00001400 - 0x0000143f (0x40) IX[B]
	[10] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[11] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[17] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[18] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[19] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xecfff000 - 0xecffffff (0x1000) MX[B]
	[5] -1	0	0xecef0000 - 0xecefffff (0x10000) MX[B]
	[6] -1	0	0xecbfe800 - 0xecbfefff (0x800) MX[B]
	[7] -1	0	0xecbff000 - 0xecbfffff (0x1000) MX[B]
	[8] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[9] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[10] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001400 - 0x0000143f (0x40) IX[B]
	[16] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[17] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[23] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[24] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[25] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:34:02 PST 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:53:48 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xecfff000 - 0xecffffff (0x1000) MX[B]
	[5] -1	0	0xecef0000 - 0xecefffff (0x10000) MX[B]
	[6] -1	0	0xecbfe800 - 0xecbfefff (0x800) MX[B]
	[7] -1	0	0xecbff000 - 0xecbfffff (0x1000) MX[B]
	[8] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[9] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[10] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001400 - 0x0000143f (0x40) IX[B]
	[16] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[17] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[23] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[24] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[25] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xecfff000 - 0xecffffff (0x1000) MX[B]
	[5] -1	0	0xecef0000 - 0xecefffff (0x10000) MX[B]
	[6] -1	0	0xecbfe800 - 0xecbfefff (0x800) MX[B]
	[7] -1	0	0xecbff000 - 0xecbfffff (0x1000) MX[B]
	[8] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[9] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[10] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00001400 - 0x0000143f (0x40) IX[B]
	[19] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[20] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[26] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[27] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[28] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU Quadro NVS 110M (G72) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.21.fe
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro NVS 110M at PCI:1:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (129, 127); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xecfff000 - 0xecffffff (0x1000) MX[B]
	[5] -1	0	0xecef0000 - 0xecefffff (0x10000) MX[B]
	[6] -1	0	0xecbfe800 - 0xecbfefff (0x800) MX[B]
	[7] -1	0	0xecbff000 - 0xecbfffff (0x1000) MX[B]
	[8] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[9] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[10] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00001400 - 0x0000143f (0x40) IX[B]
	[19] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[20] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[26] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[27] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[28] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "1680x1050"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "fr"
(**) Generic Keyboard: XkbLayout: "fr"
(**) Option "XkbVariant" "oss"
(**) Generic Keyboard: XkbVariant: "oss"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(EE) Custom-Mouse: No Device specified.
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Custom-Mouse"
Atom 4, CARD32 4, unsigned long 8
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event11
(**) Option "Device" "/dev/input/event11"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event11
(**) Option "Device" "/dev/input/event11"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled

```

> 
Someone said Xorg is bugged out and being fixed... that can also be the problem.


I will test today's update right after sending this message!

   Best regards.

                                                        The Spacial Sprite

---

### Post by Le Farfadet Spatial on 2008-05-15
Hello everybody out there!

   I post one last time here, hoping that someone would be able to help me. No updating had solved the problem presently.

   Anyway, I thank very much everyone who have tried and help me.

   Best regards.

                                                                   The Spacial Sprite

---

### Post by knife_party on 2008-05-17
have you tried to reinstall the kernel? I've seen someone has problem with rt-kernel, and after he reinstalled it, everything's solved.

---

### Post by Le Farfadet Spatial on 2008-05-18
Hello everybody out there!

> **knife_party said:**
> 
have you tried to reinstall the kernel? I've seen someone has problem with rt-kernel, and after he reinstalled it, everything's solved.


   I have re-install the kernel and X.org. It is a bit better: now I can boot on the real-time kernel, but my screen is on 800x600 and 256 colors. A window has appeared at the end of the boot session to configure the screen, but I have not found out how to configure it.

   Best regards.

                                                        The Spacial Sprite

---

### Post by Le Farfadet Spatial on 2008-05-19
Hello everybody out there!

   I come back here, hoping that maybe somebody can help me to configure my screen.

   Regards.

                                                                   The Spatial Sprite

---

### Post by Man Eating Duck on 2008-05-19
> **Le Farfadet Spatial said:**
> Hello everybody out there!

   I come back here, hoping that maybe somebody can help me to configure my screen.

   Regards.

                                                                   The Spatial Sprite

I just installed the realtime kernel myself, and it sounds like you have encountered an issue I had. My update failed to install the correct module for the restricted Nvidia drivers, which results in X falling back to a generic vesa mode or some such, or failing completely.

I ran the following in a terminal:
$ sudo apt-get install linux-rt

It installed several rt-modules, among them the restricted nvidia driver. After a reboot all was well, and my desktop environment is a lot snappier (this was the issue I wanted to solve).

Hope this helps :)

If it doesn't I'm out of advice, good luck!

---

### Post by Le Farfadet Spatial on 2008-05-20
Hello everybody out there!

> **Man Eating Duck said:**
> 
I ran the following in a terminal:
$ sudo apt-get install linux-rt


Well, as I have told before in this thread, I have done this. Before, the screen was black, now the screen is badly configure. Thanks anyway.

   Best regards.

                                                          The Spacial Sprite

---

### Post by unutbu on 2008-05-20
Try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This should give you a way to select your driver and resolution. 

If you are using the vesa driver, you'll probably need to switch to the restricted NVidia driver. So if the above command does not work, try this selecting

System>Administration>Restricted Driver Manager

from the gnome panel menu. Make sure NVidia driver is enabled. Then run
```

sudo dpkg-reconfigure -phigh xserver-xorg
```
again.

If that does not work, you could try installing the driver with the following package from the official repository:

```
sudo apt-get install nvidia-glx-new
sudo dpkg-reconfigure -phigh xserver-xorg

```
The driver provided by nvidia-glx-new is not the newest driver, but it is from the official repo.

If that does not work, you could try using Alberto Milone's [URL="http://albertomilone.com/nvidia_scripts1.html"]
install script ENVY[/URL]
This will used the most up-to-date driver.

Hopefully one of these paths will get you to the solution.

---

### Post by Man Eating Duck on 2008-05-20
> **Le Farfadet Spatial said:**
> 

Well, as I have told before in this thread, I have done this. Before, the screen was black, now the screen is badly configure. Thanks anyway.

 

Sorry, I just had to do it twice for some reason, took me a while to figure out.

If you have a working X with the proprietary nvidia drivers, you probably tried 

$sudo nvidia-settings 

?
You should have it included with your driver, it's available via apt as well.

It's a nice gui tool for configuring your displays, reminiscent of the one in Windows. It handles resolution, refresh and dual monitors as well.

Cheers!

---

### Post by Le Farfadet Spatial on 2008-05-20
Hello everybody out there!

> **unutbu said:**
> 
If you are using the vesa driver, you'll probably need to switch to the restricted NVidia driver. So if the above command does not work, try this selecting


Actually, I have always used the restricted driver. But, as I have read your remark, I have taken a look: since an image appear back on my screen when I am using the real time kernel, the restricted kernel is not running. I have tried your three advices: the two first ones did not change anything.

   At last, I have installed the script ENVY (using the package from Multiverse Depot). After running it, back to the beginning: black screen and the keyboard does not respond.

   There is definitely a problem between my real-time Linux kernel, X.org server, and NVidia driver.

   Best regards.

                                                        The Spacial Sprite

---

### Post by unutbu on 2008-05-20
I'm sorry those suggestions did not work.
Now that you mention it, I see there is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197130") on this issue.

You might also want to post on the [Known Hardy bugs and workarounds sticky]("http://ubuntuforums.org/showthread.php?t=773851"). Mention the bug report and I think Frodon will add it to the sticky.

---

### Post by Le Farfadet Spatial on 2008-05-21
Hello everybody out there!

> **unutbu said:**
> 
You might also want to post on the [Known Hardy bugs and workarounds sticky]("http://ubuntuforums.org/showthread.php?t=773851"). Mention the bug report and I think Frodon will add it to the sticky.


So, if I understand you well, you say that this is not my installation which is wrong, but that there is a bug I shall report. All right, I will do it this afternoon. I just need a bit of help: I do not realy know where the problem lies, so I am not sure which information I have to give in the bug report. Can you tell me which information I must give?

   Best regards.

                                                        The Spacial Sprite

---

### Post by unutbu on 2008-05-21
Le Farfadet Spatial, I made a mistake: the ["Known Hardy bugs and workarounds sticky"]("http://ubuntuforums.org/showthread.php?t=773851") is only for bugs with solutions. Since we don't know the solution to this problem, there is no need to post a message there.

You might want to periodically check on [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197130](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197130)
however so that if/when a solution becomes known you'll be able to take advantage of it.

---

### Post by Le Farfadet Spatial on 2008-05-21
Hello everybody out there!

> **unutbu said:**
> 
You might want to periodically check on [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197130](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197130)
however so that if/when a solution becomes known you'll be able to take advantage of it.


According to the page you give the URL, it is a problem with the NVidia restrict driver, which make sense. If I have understood what is written there, the beta NVidia driver solves the problem with GeForce series, but not with the Quadro series. Hoping it will do so in a little while!

   Anyway, is it useful that I signal that the bug occurs on my configuration on this bug-track?

   Best regards.

                                                         The Spacial Sprite

---

### Post by unutbu on 2008-05-21
Hello, Le Farfadet Spatial, I agree from the bug report it sounds like the problem is in the NVIDIA driver, so posting to bugs.launchpad.net probably won't do a lot of good. 

Is the purpose of running the rt kernel to do faithful sound recording? If so, perhaps you can use the low-res configuration just to do the recording and boot a generic kernel for regular work?

Sorry I don't have a better answer.

---

### Post by Le Farfadet Spatial on 2008-05-21
Hello everybody out there!

> **unutbu said:**
> 
I agree from the bug report it sounds like the problem is in the NVIDIA driver, so posting to bugs.launchpad.net probably won't do a lot of good.


All right. Non-free components are definitely a calamity! Do you know any way to report the bug to NVidia?

> 
Is the purpose of running the rt kernel to do faithful sound recording?


Indeed.

> 
If so, perhaps you can use the low-res configuration just to do the recording and boot a generic kernel for regular work?


This is what I will be doing until the bug is fixed.

   If I am not mistaken, then Envy script downloads the newest driver from NVidia website. If so, I probably should run this script every day, until the bug is corrected, should not I?

   Regards.

                                                         The Spacial Sprite

---

### Post by unutbu on 2008-05-21
> **Le Farfadet Spatial said:**
> Hello everybody out there!

I love the enthusiasm. So: Hello, Le Farfadet Spatial!

> **Le Farfadet Spatial said:**
> 
If so, I probably should run this script every day, until the bug is corrected, should not I?

 
This might be excessive, but if it doesn't hurt, why not? You could run

```
crontab -e
``` And then add a line like this:

```
05 18 * * *  /usr/bin/env /path/to/envy/script
```

This will run the envy script at 6:05pm every day.

---

### Post by Le Farfadet Spatial on 2008-06-24
Hello everybody out there!

   Argh! Some kind of a catastrophe: yesterday update broke everything down, for nowadays even with generic kernel I cannot use the nVidia driver. I must use 800x600 resolution with 256 colors. All applications are meant to be used in a greater resolution. Therefore, it is quite impossible for me to use my computer! Even when I have activated the nVidia driver with the proprietary driver manager and typed in a console:
```

$ sudo nvidia-xconfig

```
it has been impossible to get back to a greater resolution.

   Just after sending this message, I will try to use the open-source driver, but if somebody can help me, I will be grateful!

   Best regards.

                                                        The Spacial Sprite

---

### Post by unutbu on 2008-06-24
Run
```
tail -n100 /var/log/dpkg.log | less
```
to see what packages you've installed or upgraded lately. Can you narrow it down to which package is the likely culprit? It it was a kernel upgrade, can you enter your grub boot menu and boot the previous kernel? That might get you back to a workable state.

If you are not sure what package is the problem, please post the output of ```

tail -n100 /var/log/dpkg.log
```

---

### Post by Le Farfadet Spatial on 2008-06-25
Hello everybody out there!

   Thank you so much, Unutbu, for always answer when I need it.

   I have not been able to use the open-source driver.

> 
It it was a kernel upgrade, can you enter your grub boot menu and boot the previous kernel? That might get you back to a workable state.


It was a kernel update, version 2.6.24-19. I cannot exactly boot on the previous one, as 2.6.24-19 had been installed by a previous update that had worked. Anyway, I can boot on 2.6.24-18, and I will do it just after sending this reply.

> 
```
tail -n100 /var/log/dpkg.log
```


```

2008-06-24 21:26:12 status half-configured nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:26:12 status half-installed nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:26:12 status config-files nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:26:12 purge nvidia-settings 1.0+20080304-0ubuntu1 1.0+20080304-0ubuntu1
2008-06-24 21:26:12 status config-files nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:26:12 status config-files nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:26:12 status config-files nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:26:12 status config-files nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:26:12 status config-files nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:26:12 status not-installed nvidia-settings <néant>
2008-06-24 21:26:12 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2008-06-24 21:26:12 status half-configured libc6 2.7-10ubuntu3
2008-06-24 21:26:13 status installed libc6 2.7-10ubuntu3
2008-06-24 21:26:14 startup packages configure
2008-06-24 21:26:14 configure postgresql-8.3 8.3.3-0ubuntu0.8.04 8.3.3-0ubuntu0.8.04
2008-06-24 21:26:14 status half-configured postgresql-8.3 8.3.3-0ubuntu0.8.04
2008-06-24 21:26:26 startup packages configure
2008-06-24 21:26:26 configure postgresql-8.3 8.3.3-0ubuntu0.8.04 8.3.3-0ubuntu0.8.04
2008-06-24 21:26:26 status half-configured postgresql-8.3 8.3.3-0ubuntu0.8.04
2008-06-24 21:26:31 startup archives unpack
2008-06-24 21:26:31 install nvidia-new-kernel-source-envy <néant> 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:31 status half-installed nvidia-new-kernel-source-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:33 status unpacked nvidia-new-kernel-source-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:33 status unpacked nvidia-new-kernel-source-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:33 install nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:33 status half-installed nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:37 status unpacked nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:37 status unpacked nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:37 install nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:37 status half-installed nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:37 status unpacked nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:37 status unpacked nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:38 startup packages configure
2008-06-24 21:26:38 configure postgresql-8.3 8.3.3-0ubuntu0.8.04 8.3.3-0ubuntu0.8.04
2008-06-24 21:26:38 status half-configured postgresql-8.3 8.3.3-0ubuntu0.8.04
2008-06-24 21:26:39 configure nvidia-new-kernel-source-envy 173.14.05+2.6.24.501-501.30 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:39 status unpacked nvidia-new-kernel-source-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:26:39 status half-configured nvidia-new-kernel-source-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:27:14 status installed nvidia-new-kernel-source-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:27:14 configure nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30 173.14.05+2.6.24.501-501.30
2008-06-24 21:27:14 status unpacked nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:27:14 status unpacked nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:27:14 status half-configured nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:27:15 status installed nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:27:15 status triggers-pending libc6 2.7-10ubuntu3
2008-06-24 21:27:15 configure nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30 173.14.05+2.6.24.501-501.30
2008-06-24 21:27:15 status unpacked nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:27:15 status half-configured nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:27:15 status installed nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:27:15 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2008-06-24 21:27:15 status half-configured libc6 2.7-10ubuntu3
2008-06-24 21:27:16 status installed libc6 2.7-10ubuntu3
2008-06-24 21:27:19 startup archives unpack
2008-06-24 21:27:20 install nvidia-settings <néant> 1.0+20080304-0ubuntu1
2008-06-24 21:27:20 status half-installed nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:27:20 status unpacked nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:27:20 status unpacked nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:27:21 startup packages configure
2008-06-24 21:27:21 configure postgresql-8.3 8.3.3-0ubuntu0.8.04 8.3.3-0ubuntu0.8.04
2008-06-24 21:27:21 status half-configured postgresql-8.3 8.3.3-0ubuntu0.8.04
2008-06-24 21:27:22 configure nvidia-settings 1.0+20080304-0ubuntu1 1.0+20080304-0ubuntu1
2008-06-24 21:27:22 status unpacked nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:27:22 status half-configured nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:27:22 status installed nvidia-settings 1.0+20080304-0ubuntu1
2008-06-24 21:42:25 startup packages remove
2008-06-24 21:42:25 status installed nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:50 remove nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:50 status half-configured nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:50 status half-installed nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:50 status config-files nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:50 status config-files nvidia-glx-new-dev-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:50 status installed nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:51 remove nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:51 status half-configured nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:51 status half-installed nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:52 status triggers-pending libc6 2.7-10ubuntu3
2008-06-24 21:42:52 status config-files nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:52 status config-files nvidia-glx-new-envy 173.14.05+2.6.24.501-501.30
2008-06-24 21:42:52 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2008-06-24 21:42:52 status half-configured libc6 2.7-10ubuntu3
2008-06-24 21:42:53 status installed libc6 2.7-10ubuntu3
2008-06-24 21:42:53 startup archives unpack
2008-06-24 21:42:54 install nvidia-glx-new <néant> 169.12+2.6.24.13-19.42
2008-06-24 21:42:54 status half-installed nvidia-glx-new 169.12+2.6.24.13-19.42
2008-06-24 21:42:57 status unpacked nvidia-glx-new 169.12+2.6.24.13-19.42
2008-06-24 21:42:57 status unpacked nvidia-glx-new 169.12+2.6.24.13-19.42
2008-06-24 21:42:58 startup packages configure
2008-06-24 21:42:58 configure postgresql-8.3 8.3.3-0ubuntu0.8.04 8.3.3-0ubuntu0.8.04
2008-06-24 21:42:58 status half-configured postgresql-8.3 8.3.3-0ubuntu0.8.04
2008-06-24 21:43:00 configure nvidia-glx-new 169.12+2.6.24.13-19.42 169.12+2.6.24.13-19.42
2008-06-24 21:43:00 status unpacked nvidia-glx-new 169.12+2.6.24.13-19.42
2008-06-24 21:43:00 status half-configured nvidia-glx-new 169.12+2.6.24.13-19.42
2008-06-24 21:43:00 status installed nvidia-glx-new 169.12+2.6.24.13-19.42
2008-06-24 21:43:00 status triggers-pending libc6 2.7-10ubuntu3
2008-06-24 21:43:00 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2008-06-24 21:43:00 status half-configured libc6 2.7-10ubuntu3
2008-06-24 21:43:00 status installed libc6 2.7-10ubuntu3
2008-06-24 21:43:01 startup packages configure
2008-06-24 21:43:01 configure postgresql-8.3 8.3.3-0ubuntu0.8.04 8.3.3-0ubuntu0.8.04
2008-06-24 21:43:01 status half-configured postgresql-8.3 8.3.3-0ubuntu0.8.04

```

Well, it appears that nvidia-glx-new is half configured, but I do not know how to fix it, as I have already tried this:

```

$ sudo nvidia-xconfig

```

Best regards.

                                         The Spacial Sprite

---

### Post by Le Farfadet Spatial on 2008-06-25
Hello everybody out there!

   Boot on 2.6.24-18 does not change anything at all. Anyway, I am not sure it is connected, but there is some problem with my installation of postgresql, something about the size of a variable. I have not understood how to fix it by reading the error message.

   Best regards.

                                                          The Spacial Sprite

---

### Post by unutbu on 2008-06-25
Please post
```
COLUMNS=150 dpkg --list nvidia-*
```

---

### Post by Le Farfadet Spatial on 2008-06-26
Hello everybody out there!

> **unutbu said:**
> Please post
```
COLUMNS=150 dpkg --list nvidia-*
```

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nom                             Version                         Description
+++-===============================-===============================-==============================================================================
rc  nvidia-glx                      1:96.43.05+2.6.24.13-18.41      NVIDIA binary XFree86 4.x/X.Org driver
un  nvidia-glx-dev                  <néant>                        (aucune description n'est disponible)
un  nvidia-glx-ia32                 <néant>                        (aucune description n'est disponible)
un  nvidia-glx-legacy               <néant>                        (aucune description n'est disponible)
un  nvidia-glx-legacy-dev           <néant>                        (aucune description n'est disponible)
ii  nvidia-glx-new                  169.12+2.6.24.13-19.42          NVIDIA binary XFree86 4.x/X.Org 'new' driver
pn  nvidia-glx-new-dev              <néant>                        (aucune description n'est disponible)
rc  nvidia-glx-new-dev-envy         173.14.05+2.6.24.501-501.30     NVIDIA binary XFree86 4.x/X.Org 'new' driver development files
rc  nvidia-glx-new-envy             173.14.05+2.6.24.501-501.30     NVIDIA binary XFree86 4.x/X.Org 'new' driver
un  nvidia-glx-src                  <néant>                        (aucune description n'est disponible)
un  nvidia-kernel-1.0.7185          <néant>                        (aucune description n'est disponible)
un  nvidia-kernel-1.0.9639          <néant>                        (aucune description n'est disponible)
un  nvidia-kernel-100.14.19         <néant>                        (aucune description n'est disponible)
un  nvidia-kernel-169.12            <néant>                        (aucune description n'est disponible)
un  nvidia-kernel-71.86.04          <néant>                        (aucune description n'est disponible)
un  nvidia-kernel-96.43.05          <néant>                        (aucune description n'est disponible)
ii  nvidia-kernel-common            20051028+1ubuntu8               NVIDIA binary kernel module common files
un  nvidia-kernel-source            <néant>                        (aucune description n'est disponible)
un  nvidia-kernel-src               <néant>                        (aucune description n'est disponible)
un  nvidia-legacy-kernel-source     <néant>                        (aucune description n'est disponible)
pn  nvidia-new-kernel-source        <néant>                        (aucune description n'est disponible)
ii  nvidia-new-kernel-source-envy   173.14.05+2.6.24.501-501.30     NVIDIA binary 'new' kernel module source
ii  nvidia-settings                 1.0+20080304-0ubuntu1           Tool of configuring the NVIDIA graphics driver
un  nvidia-xconfig                  <néant>                        (aucune description n'est disponible)

```

As some part are in French, please note that "néant" means "nothing," and "aucune description n'est disponible" means "no description available."

   Best regards.

                                                        The Spacial Sprite

---

### Post by Le Farfadet Spatial on 2008-06-26
Hello everybody out there!

   I have more information about my problem with postgresql: something about the parameter "shared_buffer" (nowadays set to 4096) or the parameter "max_connections" (103). Or, it may be the kernel parameter SHMMIN that is too low. I do not know how to change any of these.

   Anyway, if it has nothing to do with my video problem, do not worry about it, I will solve it later.

   Best regards.

                                                          The Spacial Sprite

---

### Post by unutbu on 2008-06-26
Boujour Le Faradet.
I've been reading 
[http://ubuntuforums.org/showthread.php?t=221313](http://ubuntuforums.org/showthread.php?t=221313) trying to pick up tips on how people solve their nvidia problems. (I recommend you take a look at this page too). I searched for Quadro NVS 110M, but nobody with that particular card seems to have posted. However, it seems to me that sometimes people get their nvidia card working by first uninstalling all things related to nvidia, and then reinstalling the particular driver they want.

Following this idea, I suggest

```
sudo apt-get purge nvidia-new-kernel-source-envy nvidia-kernel-common nvidia-glx-new
sudo apt-get install nvidia-glx-new
```

I don't think the video problem is related to the postgresql problem, so let's ignore that for now.

Also, is there a reason why you wish to run the 64-bit version of Hardy rather than the 32-bit version? From what I gather on this forum, people who run the 64-bit version face more problems with hardware and software than those who run the 32-bit version. There may be some benefit to the 64-bit version if you have > 4GB of ram, or some applications may run faster, but given that I am not an expert at solving the hardware and software issues that might arise while running 64-bit (and because I find it rather terrifying when no one other than dumb ol' me is chipping in with suggestions), I'd choose a functioning 32-bit system over a slightly faster but harder to maintain 64-bit system.

I can't guarantee your video problem will go away if you ran the 32-bit version of Hardy, but it might be something for you to think about.

---

### Post by Le Farfadet Spatial on 2008-06-26
Hello everybody out there!

> **unutbu said:**
> Boujour Le Faradet.

So you speak French! Bonjour, Unutbu!

> 
I've been reading 
[http://ubuntuforums.org/showthread.php?t=221313](http://ubuntuforums.org/showthread.php?t=221313) trying to pick up tips on how people solve their nvidia problems. (I recommend you take a look at this page too).


I certainly would, but not this night, as I am too much tired.

> 
I searched for Quadro NVS 110M, but nobody with that particular card seems to have posted.


Then, I shall post in after my problem is solved.

> 
Following this idea, I suggest

```
sudo apt-get purge nvidia-new-kernel-source-envy nvidia-kernel-common nvidia-glx-new
sudo apt-get install nvidia-glx-new
```


I have done this, but I cannot see any improvement. Moreover, I have just checked it out and, for now on, my nVidia card does not appear any more on the proprietary driver manager.

> 
I don't think the video problem is related to the postgresql problem, so let's ignore that for now.


Yes, so do I think. I just wanted to inform about all the problems I face, sometimes there are some strange connexions.

> 
Also, is there a reason why you wish to run the 64-bit version of Hardy rather than the 32-bit version? From what I gather on this forum, people who run the 64-bit version face more problems with hardware and software than those who run the 32-bit version. There may be some benefit to the 64-bit version if you have > 4GB of ram, or some applications may run faster, but given that I am not an expert at solving the hardware and software issues that might arise while running 64-bit (and because I find it rather terrifying when no one other than dumb ol' me is chipping in with suggestions), I'd choose a functioning 32-bit system over a slightly faster but harder to maintain 64-bit system.


I have not made any test about it, but I do not think that using a 64 bits system involve noticeably faster running. The reason that I am using a 64 bits system is that I am a pHd candidate that work on scientific computing (you can have more information about it on [http://www.legos.obs-mip.fr/~lebars/]("http://www.legos.obs-mip.fr/~lebars/")). Of course, I do not make my computing on my laptop, but I am developing on it, and therefore, I enjoy being able to test my codes on a bi-core (for parallelism) 64 bits computer.

   Anyway, I am running 64 bits Ubuntu version since 6.10, and it is the first time I have a hardware problem.

   Well, I would probably rather switch to Debian --- or, worse, Gentoo --- than getting back to the 32 bits version. Anyway, I have not given up yet.

   Best regards.

                                                        The Spacial Sprite

---

### Post by Le Farfadet Spatial on 2008-07-07
Hello everybody out there!

   Well, I have solved some of my problems: I have re-install Ubuntu from scratch, and now I am back to the situation at the very beginning of this topic: everything alright when I use the generic kernel, black screen when using real-time kernel.

   But I have made this decision: I will not use Envy anymore!

   Best regards.

                                                          The Spacial Sprite

---

### Post by AndersGnistrup on 2008-08-03
Hi All

I have had exactly the problems you describe and I currently have kind of a "solution" that fixes the problem.

The hardware I use is a new M3N-H/HDMI using a nvidia GeForce 8300 chipset. This is the output from uname -a

Linux mc 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

First: I have tried running using the following ubuntu/debian packages
- nvidia-glx-new
- nvidia-glx-new-dev
- nvidia-glx-new-dev-envy
- nvidia-glx-new-envy
Just for completeness :lolflag:

The only one that works is "nvidia-glx-new-dev-envy". The rest is given the result black screen. It is possible to log in via SSH (sudo apt-get install openssh-server is recommended).

One other issue is that I had serious problems uninstalling nvidia-glx-new and nvidia-glx-new-dev.

But now all seems to work just fine. I have seen post about instability on the net but have not seen this at present.

---

### Post by Le Farfadet Spatial on 2008-10-15
Hello everybody out there!

> **AndersGnistrup said:**
> 
This is the output from uname -a

Linux mc 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux


Well, for my part, I have no problem with the generic kernel. The problem occurs when using the real time kernel. So it is not exactly the same problem.

   Anyway, in the updates done today where all kernel (generic and real time) and also N-Vidia drivers. I have hoped that after updating my configuration the problem will be solved, but not at all. Am I the only one who still has troubles using the real time kernel with N-Vidia driver?

   Best regards.

                                                        The Spacial Sprite

---

### Post by briandu on 2008-10-15
Me thinks many folks have this problem with .21 kernel update. See other threads. Going back to .19 solved the problem for me as well.

Seems no one has idea about the .21 kernel.

---

### Post by Le Farfadet Spatial on 2008-10-15
Hello everybody out there!

> **briandu said:**
> Me thinks many folks have this problem with .21 kernel update. See other threads. Going back to .19 solved the problem for me as well.

Seems no one has idea about the .21 kernel.

Thank you for replying, moreover so quickly.

   I have just tried .19 real time kernel: this time, no black screen, but only low resolution and no 3D acceleration available. No problem with .21 generic kernel, but I need real time...

   Best regards.

                                                        The Spacial Sprite

---

### Post by trece8 on 2008-10-20
Hi... I have the very same problem, with a ViewSonic 2216w and nVidia GForce 6200... I have already spent about 30 hours trying to solve this and the best I have got is 1024*768 with some nvidia package...

I hoped the updated kernel could somehow have fixed this problem, but it didn't...
Anyone has some clue?

---

### Post by trece8 on 2008-11-03
I just got tired of reading and just installed all nvidia-stuff things in synaptic and surprisingly got this running with no problem with linux-rt!

I executed EnvyNG and reinstalled nvidia-glx-new and got it running right away, Le Farfadet Spacial, try it for yourself

---

### Post by battlesound on 2008-11-10
I have just about the same problem, here.  Dell laptop same processor and graphics card.  I also want to use the 64 bit rt kernel.  Hopefully something works.  I'm currently giving it a shot right now.  I put up with just using the generic 64 bit kernel.  I'll see if any of this stuff works.

---

### Post by battlesound on 2008-11-17
Sweet.  Nice job, trece8.  It worked out beautifully.  

I installed all the newest rt kernel stuff and the envyNG stuff.  I started EnvyNG from the main menu to install the latest nvidia stuff.  Restart computer.  Sure enough, it worked.  I tried to follow the process that EnvyNG does, but I would have to do it again to understand what is going on.

Is this working for more people, too?  Anyway, this is worth trying.

---

### Post by Le Farfadet Spatial on 2009-05-17
Hello everybody out there!

   I am now running Ubuntu 9.04. 15th may update have solved the problem.

   Best regards.

                                                          The Spatial Sprite

---

