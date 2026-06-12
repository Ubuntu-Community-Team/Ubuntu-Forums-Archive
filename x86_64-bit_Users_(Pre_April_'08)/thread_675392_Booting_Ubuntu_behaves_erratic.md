---
title: "Booting Ubuntu behaves erratic"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by dverhoeven on 2008-01-22
Hi,

upfront my excuses for the verbose posting, but due to inconsistent behaviour, I think it is best to be verbose.

I recently decided to move to Ubuntu 64 bit, and installed it on my AMD 3000+ with k8t800 mobo with Nvidia geforce FX 5200 128 Mb video and onboard sound

Except for an installer glitch with an existing ext2 partition not being allowed somehow (solved by choosing "do not use") and installing Ubuntu on a different ext3 partition. So I had XP and ubuntu.

All was working well except the sound, and I installed all patches and Nvidia driver. 

I started trying with the desktop goodies, and I had a serious hang.

Since that time I have serious booting problems. They are extremely erratic. Sometimes it stops at loading the restricted drivers, sometimes it stops somewhere else. Most of the times it fails at restricted drivers (two blocks on the splash before it stops)

I tried booting in recovery mode, which worked a few times. I de-installed the desktop goodies and nvidia driver. It worked again, but a reboot brought me back to square 0.

So far the live cd was always working, and I tried several postings on the net ( i followed [http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281) )

None of the options brought me any luck. Once it booted again, but starting eclipse froze everything, and a reboot brought me back to my starting position.

I reset my bios as well, I updated it to the latest level, all no luck.

Now it became even stranger as my live CD did not want to boot either. This is baffling me, as I thought my filesystem was corrupted, and I wanted to re-install, but clearly there is more to it, as the livecd fails as well, so it can not be my filesystem.

One thing that is remarkable is that right after the grub screen I get a message "PCI: cannot allocate resource region of device 0000:00:00.0"

If I use the program SIW in windows XP (sorry) I can see under PCI : 00/00/00 PCI PCI to Host bridge. Apollo K8T800 CPU to pci bridge. Not sure if this is related to this message. 

I would love to post logs, but I can't reach my system now (have to download another livecd to do that)

Anyone have a clue to what is happening ?

---

### Post by dverhoeven on 2008-01-23
Hi, today managed to boot up with 64 bit, but got a system stall in 5 minutes. Now I booted over 32 bit live cd, and that seems to work.

For additional info, I add the kern.log of my 64 bit system that I booted with the noapic flag on as it seems to help a little:

Jan 23 23:31:42 dimitri-desktop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Jan 23 23:31:42 dimitri-desktop kernel: Loaded 26085 symbols from /boot/System.map-2.6.22-14-generic.
Jan 23 23:31:42 dimitri-desktop kernel: Symbols match kernel version 2.6.22.
Jan 23 23:31:42 dimitri-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Command line: root=UUID=bbb8e309-4768-4d94-973d-9b3236f7a5d6 ro quiet splash noapic
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] end_pfn_map = 1048576
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] DMI 2.3 present.
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6A70 checksum 0
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: RSDP 000F6A70, 0014 (r0 VIAK8 )
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: RSDT 7FFF3000, 002C (r1 VIAK8  AWRDACPI 42302E31 AWRD  1010101)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: FACP 7FFF3040, 0074 (r1 VIAK8  AWRDACPI 42302E31 AWRD  1010101)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: DSDT 7FFF30C0, 4A19 (r1 VIAK8  AWRDACPI     1000 MSFT  100000C)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: FACS 7FFF0000, 0040
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: APIC 7FFF7B00, 005A (r1 VIAK8  AWRDACPI 42302E31 AWRD  1010101)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] No NUMA configuration found
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Faking a node at 0000000000000000-000000007fff0000
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007fff0000
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Zone PFN ranges:
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]   DMA             0 ->     4096
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]   DMA32        4096 ->  1048576
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]   Normal    1048576 ->  1048576
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]     0:        0 ->      159
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]     0:      256 ->   524272
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] On node 0 totalpages: 524175
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]   DMA zone: 1125 pages reserved
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]   DMA zone: 2818 pages, LIFO batch:0
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]   DMA32 zone: 7111 pages used for memmap
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]   DMA32 zone: 513065 pages, LIFO batch:31
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Using ACPI for processor (LAPIC) configuration information
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] MPTABLE: OEM ID: OEM00000 MPTABLE: Product ID: PROD00000000 MPTABLE: APIC at: 0xFEE00000
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] I/O APIC #2 at 0xFEC00000.
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Setting APIC routing to flat
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Processors: 1
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Built 1 zonelists.  Total pages: 515883
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Kernel command line: root=UUID=bbb8e309-4768-4d94-973d-9b3236f7a5d6 ro quiet splash noapic
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] Initializing CPU#0
Jan 23 23:31:42 dimitri-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.445253] time.c: Detected 2010.076 MHz processor.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.446480] Console: colour VGA+ 80x25
Jan 23 23:31:42 dimitri-desktop kernel: [   29.446495] Checking aperture...
Jan 23 23:31:42 dimitri-desktop kernel: [   29.446499] CPU 0: aperture @ d0000000 size 128 MB
Jan 23 23:31:42 dimitri-desktop kernel: [   29.473510] Memory: 2056164k/2097088k available (2274k kernel code, 40536k reserved, 1181k data, 296k init)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.473563] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Jan 23 23:31:42 dimitri-desktop kernel: [   29.551169] Calibrating delay using timer specific routine.. 4023.81 BogoMIPS (lpj=8047634)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.551207] Security Framework v1.0.0 initialized
Jan 23 23:31:42 dimitri-desktop kernel: [   29.551216] SELinux:  Disabled at boot.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.551377] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.553294] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.554215] Mount-cache hash table entries: 256
Jan 23 23:31:42 dimitri-desktop kernel: [   29.554371] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.554374] CPU: L2 Cache: 512K (64 bytes/line)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.554377] CPU 0/0 -> Node 0
Jan 23 23:31:42 dimitri-desktop kernel: [   29.554396] SMP alternatives: switching to UP code
Jan 23 23:31:42 dimitri-desktop kernel: [   29.554590] Freeing SMP alternatives: 24k freed
Jan 23 23:31:42 dimitri-desktop kernel: [   29.554951] Early unpacking initramfs... done
Jan 23 23:31:42 dimitri-desktop kernel: [   29.854301] ACPI: Core revision 20070126
Jan 23 23:31:42 dimitri-desktop kernel: [   29.854363] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.855807] ACPI: setting ELCR to 0200 (from 0e20)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.856636] Using local APIC timer interrupts.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.906350] result 12562972
Jan 23 23:31:42 dimitri-desktop kernel: [   29.906351] Detected 12.562 MHz APIC timer.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.906931] Brought up 1 CPUs
Jan 23 23:31:42 dimitri-desktop kernel: [   29.907119] NET: Registered protocol family 16
Jan 23 23:31:42 dimitri-desktop kernel: [   29.907199] ACPI: bus type pci registered
Jan 23 23:31:42 dimitri-desktop kernel: [   29.907206] PCI: Using configuration type 1
Jan 23 23:31:42 dimitri-desktop kernel: [   29.907978] ACPI: EC: Look up EC in DSDT
Jan 23 23:31:42 dimitri-desktop kernel: [   29.912111] ACPI: Interpreter enabled
Jan 23 23:31:42 dimitri-desktop kernel: [   29.912117] ACPI: (supports S0 S1 S4 S5)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.912142] ACPI: Using PIC for interrupt routing
Jan 23 23:31:42 dimitri-desktop kernel: [   29.917033] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.917040] PCI: Probing PCI hardware (bus 00)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.917621] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 23 23:31:42 dimitri-desktop kernel: [   29.943351] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.943478] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
Jan 23 23:31:42 dimitri-desktop kernel: [   29.943605] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.943716] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.943822] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.943925] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.944028] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.944130] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.944278] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
Jan 23 23:31:42 dimitri-desktop kernel: [   29.944426] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
Jan 23 23:31:42 dimitri-desktop kernel: [   29.944593] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
Jan 23 23:31:42 dimitri-desktop kernel: [   29.944742] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.944819] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 23 23:31:42 dimitri-desktop kernel: [   29.944829] pnp: PnP ACPI init
Jan 23 23:31:42 dimitri-desktop kernel: [   29.944837] ACPI: bus type pnp registered
Jan 23 23:31:42 dimitri-desktop kernel: [   29.947936] pnp: PnP ACPI: found 15 devices
Jan 23 23:31:42 dimitri-desktop kernel: [   29.947938] ACPI: ACPI bus type pnp unregistered
Jan 23 23:31:42 dimitri-desktop kernel: [   29.947996] PCI: Using ACPI for IRQ routing
Jan 23 23:31:42 dimitri-desktop kernel: [   29.947999] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jan 23 23:31:42 dimitri-desktop kernel: [   29.948008] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
Jan 23 23:31:42 dimitri-desktop kernel: [   29.948112] NET: Registered protocol family 8
Jan 23 23:31:42 dimitri-desktop kernel: [   29.948114] NET: Registered protocol family 20
Jan 23 23:31:42 dimitri-desktop kernel: [   29.948169] agpgart: Detected AGP bridge 0
Jan 23 23:31:42 dimitri-desktop kernel: [   29.953960] agpgart: AGP aperture is 128M @ 0xd0000000
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954039] pnp: 00:00: iomem range 0xd4400-0xd7fff has been reserved
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954042] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954045] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954048] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954055] pnp: 00:02: ioport range 0x4000-0x407f has been reserved
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954057] pnp: 00:02: ioport range 0x40f0-0x40ff has been reserved
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954060] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954315] PCI: Bridge: 0000:00:01.0
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954317]   IO window: disabled.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954321]   MEM window: e0000000-e1ffffff
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954324]   PREFETCH window: d8000000-dfffffff
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954338] PCI: Setting latency timer of device 0000:00:01.0 to 64
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954374] NET: Registered protocol family 2
Jan 23 23:31:42 dimitri-desktop kernel: [   29.954842] Time: tsc clocksource has been installed.
Jan 23 23:31:42 dimitri-desktop kernel: [   29.986882] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.987621] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.993215] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.994130] TCP: Hash tables configured (established 262144 bind 65536)
Jan 23 23:31:42 dimitri-desktop kernel: [   29.994134] TCP reno registered
Jan 23 23:31:42 dimitri-desktop kernel: [   30.002936] checking if image is initramfs... it is
Jan 23 23:31:42 dimitri-desktop kernel: [   30.581753] Freeing initrd memory: 7205k freed
Jan 23 23:31:42 dimitri-desktop kernel: [   30.588676] audit: initializing netlink socket (disabled)
Jan 23 23:31:42 dimitri-desktop kernel: [   30.588690] audit(1201131081.100:1): initialized
Jan 23 23:31:42 dimitri-desktop kernel: [   30.590466] VFS: Disk quotas dquot_6.5.1
Jan 23 23:31:42 dimitri-desktop kernel: [   30.590519] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jan 23 23:31:42 dimitri-desktop kernel: [   30.590611] io scheduler noop registered
Jan 23 23:31:42 dimitri-desktop kernel: [   30.590613] io scheduler anticipatory registered
Jan 23 23:31:42 dimitri-desktop kernel: [   30.590615] io scheduler deadline registered
Jan 23 23:31:42 dimitri-desktop kernel: [   30.590699] io scheduler cfq registered (default)
Jan 23 23:31:42 dimitri-desktop kernel: [   30.590709] PCI: VIA PCI bridge detected. Disabling DAC.
Jan 23 23:31:42 dimitri-desktop kernel: [   30.591040] Boot video device is 0000:01:00.0
Jan 23 23:31:42 dimitri-desktop kernel: [   30.612084] Real Time Clock Driver v1.12ac
Jan 23 23:31:42 dimitri-desktop kernel: [   30.612158] Linux agpgart interface v0.102 (c) Dave Jones
Jan 23 23:31:42 dimitri-desktop kernel: [   30.612161] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jan 23 23:31:42 dimitri-desktop kernel: [   30.612251] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 23 23:31:42 dimitri-desktop kernel: [   30.612394] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jan 23 23:31:42 dimitri-desktop kernel: [   30.612825] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 23 23:31:42 dimitri-desktop kernel: [   30.613040] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jan 23 23:31:42 dimitri-desktop kernel: [   30.613640] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jan 23 23:31:42 dimitri-desktop kernel: [   30.613832] input: Macintosh mouse button emulation as /class/input/input0
Jan 23 23:31:42 dimitri-desktop kernel: [   30.613896] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 23 23:31:42 dimitri-desktop kernel: [   30.614202] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 23 23:31:42 dimitri-desktop kernel: [   30.614206] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 23 23:31:42 dimitri-desktop kernel: [   30.614404] mice: PS/2 mouse device common for all mice
Jan 23 23:31:42 dimitri-desktop kernel: [   30.614591] TCP cubic registered
Jan 23 23:31:42 dimitri-desktop kernel: [   30.614653] NET: Registered protocol family 1
Jan 23 23:31:42 dimitri-desktop kernel: [   30.614833] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jan 23 23:31:42 dimitri-desktop kernel: [   30.614841] Freeing unused kernel memory: 296k freed
Jan 23 23:31:42 dimitri-desktop kernel: [   30.686281] input: AT Translated Set 2 keyboard as /class/input/input1
Jan 23 23:31:42 dimitri-desktop kernel: [   31.788018] AppArmor: AppArmor initialized<5>audit(1201131082.300:2):  type=1505 info="AppArmor initialized" pid=1200
Jan 23 23:31:42 dimitri-desktop kernel: [   31.793612] fuse init (API version 7.8)
Jan 23 23:31:42 dimitri-desktop kernel: [   31.797812] Failure registering capabilities with primary security module.
Jan 23 23:31:42 dimitri-desktop kernel: [   32.337117] SCSI subsystem initialized
Jan 23 23:31:42 dimitri-desktop kernel: [   32.341876] libata version 2.21 loaded.
Jan 23 23:31:42 dimitri-desktop kernel: [   32.347127] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jan 23 23:31:42 dimitri-desktop kernel: [   32.347134] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jan 23 23:31:42 dimitri-desktop kernel: [   32.347707] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
Jan 23 23:31:42 dimitri-desktop kernel: [   32.348049] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Jan 23 23:31:42 dimitri-desktop kernel: [   32.348052] PCI: setting IRQ 11 as level-triggered
Jan 23 23:31:42 dimitri-desktop kernel: [   32.348057] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Jan 23 23:31:42 dimitri-desktop kernel: [   32.348063] PCI: VIA VLink IRQ fixup for 0000:00:0f.1, from 255 to 11
Jan 23 23:31:42 dimitri-desktop kernel: [   32.348088] VP_IDE: chipset revision 6
Jan 23 23:31:42 dimitri-desktop kernel: [   32.348090] VP_IDE: not 100%% native mode: will probe irqs later
Jan 23 23:31:42 dimitri-desktop kernel: [   32.348100] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
Jan 23 23:31:42 dimitri-desktop kernel: [   32.348108]     ide0: BM-DMA at 0xa800-0xa807, BIOS settings: hda:pio, hdb:pio
Jan 23 23:31:42 dimitri-desktop kernel: [   32.348119]     ide1: BM-DMA at 0xa808-0xa80f, BIOS settings: hdc:pio, hdd:pio
Jan 23 23:31:42 dimitri-desktop kernel: [   32.348125] Probing IDE interface ide0...
Jan 23 23:31:42 dimitri-desktop kernel: [   32.367106] usbcore: registered new interface driver usbfs
Jan 23 23:31:42 dimitri-desktop kernel: [   32.367132] usbcore: registered new interface driver hub
Jan 23 23:31:42 dimitri-desktop kernel: [   32.367154] usbcore: registered new device driver usb
Jan 23 23:31:42 dimitri-desktop kernel: [   32.367925] USB Universal Host Controller Interface driver v3.0
Jan 23 23:31:42 dimitri-desktop kernel: [   32.448816] 8139too Fast Ethernet driver 0.9.28
Jan 23 23:31:42 dimitri-desktop kernel: [   32.536199] Floppy drive(s): fd0 is 1.44M
Jan 23 23:31:42 dimitri-desktop kernel: [   32.573184] FDC 0 is a post-1991 82077
Jan 23 23:31:42 dimitri-desktop kernel: [   32.928274] Probing IDE interface ide1...
Jan 23 23:31:42 dimitri-desktop kernel: [   33.795602] hdc: ASUS DVD-ROM E608, ATAPI CD/DVD-ROM drive
Jan 23 23:31:42 dimitri-desktop kernel: [   34.131540] ide1 at 0x170-0x177,0x376 on irq 15
Jan 23 23:31:42 dimitri-desktop kernel: [   34.132649] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Jan 23 23:31:42 dimitri-desktop kernel: [   34.132653] PCI: setting IRQ 10 as level-triggered
Jan 23 23:31:42 dimitri-desktop kernel: [   34.132658] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Jan 23 23:31:42 dimitri-desktop kernel: [   34.132669] uhci_hcd 0000:00:10.0: UHCI Host Controller
Jan 23 23:31:42 dimitri-desktop kernel: [   34.132958] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Jan 23 23:31:42 dimitri-desktop kernel: [   34.132983] uhci_hcd 0000:00:10.0: irq 10, io base 0x0000ac00
Jan 23 23:31:42 dimitri-desktop kernel: [   34.133359] usb usb1: configuration #1 chosen from 1 choice
Jan 23 23:31:42 dimitri-desktop kernel: [   34.133500] hub 1-0:1.0: USB hub found
Jan 23 23:31:42 dimitri-desktop kernel: [   34.133507] hub 1-0:1.0: 2 ports detected
Jan 23 23:31:42 dimitri-desktop kernel: [   34.142862] hdc: ATAPI 40X DVD-ROM drive, 128kB Cache, UDMA(33)
Jan 23 23:31:42 dimitri-desktop kernel: [   34.142870] Uniform CD-ROM driver Revision: 3.20
Jan 23 23:31:42 dimitri-desktop kernel: [   34.239275] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Jan 23 23:31:42 dimitri-desktop kernel: [   34.239290] uhci_hcd 0000:00:10.1: UHCI Host Controller
Jan 23 23:31:42 dimitri-desktop kernel: [   34.239312] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Jan 23 23:31:42 dimitri-desktop kernel: [   34.239335] uhci_hcd 0000:00:10.1: irq 10, io base 0x0000b000
Jan 23 23:31:42 dimitri-desktop kernel: [   34.239444] usb usb2: configuration #1 chosen from 1 choice
Jan 23 23:31:42 dimitri-desktop kernel: [   34.239468] hub 2-0:1.0: USB hub found
Jan 23 23:31:42 dimitri-desktop kernel: [   34.239473] hub 2-0:1.0: 2 ports detected
Jan 23 23:31:42 dimitri-desktop kernel: [   34.347447] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Jan 23 23:31:42 dimitri-desktop kernel: [   34.347454] PCI: VIA VLink IRQ fixup for 0000:00:10.2, from 5 to 11
Jan 23 23:31:42 dimitri-desktop kernel: [   34.347479] uhci_hcd 0000:00:10.2: UHCI Host Controller
Jan 23 23:31:42 dimitri-desktop kernel: [   34.347618] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Jan 23 23:31:42 dimitri-desktop kernel: [   34.347642] uhci_hcd 0000:00:10.2: irq 11, io base 0x0000b400
Jan 23 23:31:42 dimitri-desktop kernel: [   34.347980] usb usb3: configuration #1 chosen from 1 choice
Jan 23 23:31:42 dimitri-desktop kernel: [   34.348137] hub 3-0:1.0: USB hub found
Jan 23 23:31:42 dimitri-desktop kernel: [   34.348143] hub 3-0:1.0: 2 ports detected
Jan 23 23:31:42 dimitri-desktop kernel: [   34.455367] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Jan 23 23:31:42 dimitri-desktop kernel: [   34.455374] PCI: VIA VLink IRQ fixup for 0000:00:10.3, from 5 to 11
Jan 23 23:31:42 dimitri-desktop kernel: [   34.455399] uhci_hcd 0000:00:10.3: UHCI Host Controller
Jan 23 23:31:42 dimitri-desktop kernel: [   34.455561] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Jan 23 23:31:42 dimitri-desktop kernel: [   34.455583] uhci_hcd 0000:00:10.3: irq 11, io base 0x0000b800
Jan 23 23:31:42 dimitri-desktop kernel: [   34.455945] usb usb4: configuration #1 chosen from 1 choice
Jan 23 23:31:42 dimitri-desktop kernel: [   34.456112] hub 4-0:1.0: USB hub found
Jan 23 23:31:42 dimitri-desktop kernel: [   34.456118] hub 4-0:1.0: 2 ports detected
Jan 23 23:31:42 dimitri-desktop kernel: [   34.563388] sata_via 0000:00:0f.0: version 2.2
Jan 23 23:31:42 dimitri-desktop kernel: [   34.563763] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Jan 23 23:31:42 dimitri-desktop kernel: [   34.563766] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jan 23 23:31:42 dimitri-desktop kernel: [   34.563809] sata_via 0000:00:0f.0: routed to hard irq line 11
Jan 23 23:31:42 dimitri-desktop kernel: [   34.564349] scsi0 : sata_via
Jan 23 23:31:42 dimitri-desktop kernel: [   34.564625] scsi1 : sata_via
Jan 23 23:31:42 dimitri-desktop kernel: [   34.564808] ata1: SATA max UDMA/133 cmd 0x0000000000019000 ctl 0x0000000000019402 bmdma 0x000000000001a000 irq 11
Jan 23 23:31:42 dimitri-desktop kernel: [   34.564813] ata2: SATA max UDMA/133 cmd 0x0000000000019800 ctl 0x0000000000019c02 bmdma 0x000000000001a008 irq 11
Jan 23 23:31:42 dimitri-desktop kernel: [   34.770668] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 23 23:31:42 dimitri-desktop kernel: [   34.959627] ata1.00: ATA-7: Maxtor 6B200M0, BANC19J0, max UDMA/133
Jan 23 23:31:42 dimitri-desktop kernel: [   34.959630] ata1.00: 398297088 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jan 23 23:31:42 dimitri-desktop kernel: [   34.979611] ata1.00: configured for UDMA/133
Jan 23 23:31:42 dimitri-desktop kernel: [   35.186304] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Jan 23 23:31:42 dimitri-desktop kernel: [   35.196981] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6B200M0   BANC PQ: 0 ANSI: 5
Jan 23 23:31:42 dimitri-desktop kernel: [   35.197486] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jan 23 23:31:42 dimitri-desktop kernel: [   35.197597] ehci_hcd 0000:00:10.4: EHCI Host Controller
Jan 23 23:31:42 dimitri-desktop kernel: [   35.197913] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Jan 23 23:31:42 dimitri-desktop kernel: [   35.197954] ehci_hcd 0000:00:10.4: irq 11, io mem 0xe2000000
Jan 23 23:31:42 dimitri-desktop kernel: [   35.197960] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 23 23:31:42 dimitri-desktop kernel: [   35.198279] usb usb5: configuration #1 chosen from 1 choice
Jan 23 23:31:42 dimitri-desktop kernel: [   35.198428] hub 5-0:1.0: USB hub found
Jan 23 23:31:42 dimitri-desktop kernel: [   35.198435] hub 5-0:1.0: 8 ports detected
Jan 23 23:31:42 dimitri-desktop kernel: [   35.206543] sd 0:0:0:0: [sda] 398297088 512-byte hardware sectors (203928 MB)
Jan 23 23:31:42 dimitri-desktop kernel: [   35.206556] sd 0:0:0:0: [sda] Write Protect is off
Jan 23 23:31:42 dimitri-desktop kernel: [   35.206559] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 23 23:31:42 dimitri-desktop kernel: [   35.206571] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 23 23:31:42 dimitri-desktop kernel: [   35.206642] sd 0:0:0:0: [sda] 398297088 512-byte hardware sectors (203928 MB)
Jan 23 23:31:42 dimitri-desktop kernel: [   35.206649] sd 0:0:0:0: [sda] Write Protect is off
Jan 23 23:31:42 dimitri-desktop kernel: [   35.206651] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 23 23:31:42 dimitri-desktop kernel: [   35.206662] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 23 23:31:42 dimitri-desktop kernel: [   35.206666]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
Jan 23 23:31:42 dimitri-desktop kernel: [   35.294983] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 23 23:31:42 dimitri-desktop kernel: [   35.299071] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 23 23:31:42 dimitri-desktop kernel: [   35.302476] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jan 23 23:31:42 dimitri-desktop kernel: [   35.302901] eth0: RealTek RTL8139 at 0xffffc20000324000, 00:0f:ea:5a:4d:46, IRQ 11
Jan 23 23:31:42 dimitri-desktop kernel: [   35.302906] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Jan 23 23:31:42 dimitri-desktop kernel: [   35.304720] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jan 23 23:31:42 dimitri-desktop kernel: [   35.816194] Attempting manual resume
Jan 23 23:31:42 dimitri-desktop kernel: [   35.816198] swsusp: Resume From Partition 8:10
Jan 23 23:31:42 dimitri-desktop kernel: [   35.816200] PM: Checking swsusp image.
Jan 23 23:31:42 dimitri-desktop kernel: [   35.816382] PM: Resume from disk failed.
Jan 23 23:31:42 dimitri-desktop kernel: [   35.844529] kjournald starting.  Commit interval 5 seconds
Jan 23 23:31:42 dimitri-desktop kernel: [   35.844540] EXT3-fs: mounted filesystem with ordered data mode.
Jan 23 23:31:42 dimitri-desktop kernel: [   43.148287] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jan 23 23:31:42 dimitri-desktop kernel: [   44.246215] NET: Registered protocol family 10
Jan 23 23:31:42 dimitri-desktop kernel: [   44.246305] lo: Disabled Privacy Extensions
Jan 23 23:31:42 dimitri-desktop kernel: [   44.851163] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 23 23:31:42 dimitri-desktop kernel: [   44.967812] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 23 23:31:42 dimitri-desktop kernel: [   45.559846] nvidia: module license 'NVIDIA' taints kernel.
Jan 23 23:31:42 dimitri-desktop kernel: [   45.824385] input: PC Speaker as /class/input/input2
Jan 23 23:31:42 dimitri-desktop kernel: [   45.934976] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Jan 23 23:31:42 dimitri-desktop kernel: [   45.935233] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
Jan 23 23:31:42 dimitri-desktop kernel: [   46.317961] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jan 23 23:31:42 dimitri-desktop kernel: [   46.318094] PCI: Setting latency timer of device 0000:00:11.5 to 64
Jan 23 23:31:42 dimitri-desktop kernel: [   46.430551] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
Jan 23 23:31:42 dimitri-desktop kernel: [   46.433742] parport_pc 00:0b: reported by Plug and Play ACPI
Jan 23 23:31:42 dimitri-desktop kernel: [   46.433790] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jan 23 23:31:42 dimitri-desktop kernel: [   47.512527] lp0: using parport0 (interrupt-driven).
Jan 23 23:31:42 dimitri-desktop kernel: [   47.576571] Adding 538136k swap on /dev/sda10.  Priority:-1 extents:1 across:538136k
Jan 23 23:31:42 dimitri-desktop kernel: [   47.979009] EXT3 FS on sda9, internal journal
Jan 23 23:31:42 dimitri-desktop kernel: [   49.702103] No dock devices found.
Jan 23 23:31:42 dimitri-desktop kernel: [   49.757411] input: Power Button (FF) as /class/input/input4
Jan 23 23:31:42 dimitri-desktop kernel: [   49.761782] ACPI: Power Button (FF) [PWRF]
Jan 23 23:31:42 dimitri-desktop kernel: [   49.785544] input: Power Button (CM) as /class/input/input5
Jan 23 23:31:42 dimitri-desktop kernel: [   49.789862] ACPI: Power Button (CM) [PWRB]
Jan 23 23:31:42 dimitri-desktop kernel: [   50.053362] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
Jan 23 23:31:42 dimitri-desktop kernel: [   50.053415] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2
Jan 23 23:31:42 dimitri-desktop kernel: [   50.053417] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
Jan 23 23:31:42 dimitri-desktop kernel: [   50.053420] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
Jan 23 23:31:42 dimitri-desktop kernel: [   51.162411] ppdev: user-space parallel port driver
Jan 23 23:31:42 dimitri-desktop kernel: [   51.359525] audit(1201127502.965:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4693 profile="/usr/sbin/cupsd"
Jan 23 23:31:44 dimitri-desktop kernel: [   52.482871] Failure registering capabilities with primary security module.
Jan 23 23:31:44 dimitri-desktop kernel: [   52.645031] Bluetooth: Core ver 2.11
Jan 23 23:31:44 dimitri-desktop kernel: [   52.645121] NET: Registered protocol family 31
Jan 23 23:31:44 dimitri-desktop kernel: [   52.645124] Bluetooth: HCI device and connection manager initialized
Jan 23 23:31:44 dimitri-desktop kernel: [   52.645127] Bluetooth: HCI socket layer initialized
Jan 23 23:31:44 dimitri-desktop kernel: [   52.654642] Bluetooth: L2CAP ver 2.8
Jan 23 23:31:44 dimitri-desktop kernel: [   52.654647] Bluetooth: L2CAP socket layer initialized
Jan 23 23:31:44 dimitri-desktop kernel: [   52.715291] Bluetooth: RFCOMM socket layer initialized
Jan 23 23:31:44 dimitri-desktop kernel: [   52.715370] Bluetooth: RFCOMM TTY layer initialized
Jan 23 23:31:44 dimitri-desktop kernel: [   52.715373] Bluetooth: RFCOMM ver 1.8
Jan 23 23:31:44 dimitri-desktop kernel: [   52.727285] Marking TSC unstable due to cpufreq changes
Jan 23 23:31:44 dimitri-desktop kernel: [   52.728346] Time: acpi_pm clocksource has been installed.
Jan 23 23:31:46 dimitri-desktop kernel: [   54.075834] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jan 23 23:31:46 dimitri-desktop kernel: [   54.075843] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jan 23 23:31:46 dimitri-desktop kernel: [   54.075869] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jan 23 23:31:46 dimitri-desktop kernel: [   54.389640] eth0: no IPv6 routers present

---

### Post by dverhoeven on 2008-01-26
Hi,

just wanted to answer on my own thread, as it seems to be a bios/mobo problem. Either my bios is messed up, or my mobo gave up on me. Reason being is that all of a sudden Windows is also hanging. Why this happened while installing Ubuntu is a mystery, but then again, tech stuff always either works or breaks down just out of warranty. 

Thanks to all who read it. Can't blame anyone not answering such a vague issue :confused:

---

### Post by crjackson on 2008-01-26
It happened when installing Ubuntu most likely because you are moving to a 64-bit system that take FULL advantage of every nook / cranny of your hardware (cpu, processor, & memory mostly).  If there is the SLIGHTEST fault in your hardware, Ubuntu will ferret it out.

Often times things will run on windows and not on Linux due to hardware problems.  This is because windows does not fully exploit every last vestige of processing and memory power.

It's likely that when you did the BIOS update you made matters worse.  I would run memtest on the system and start trouble shotting there.  Faulty memory is the most common problem, and can be responsible for file system corruption.  In fact it's common.  It can also mess up your BIOS flash making matters worse.

---

### Post by steveneddy on 2008-01-26
I would imagine that the issue is memory (RAM) and not a mobo prob.

moving to a 64 bit OS shouldn't make the system run hotter or any other way that would damage the hardware in any way.

---

