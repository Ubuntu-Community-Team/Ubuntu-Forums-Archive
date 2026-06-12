---
title: "More noob probs"
date: 2008-08-02
forum: x86 64-bit Users
---

### Post by alt3rn1ty on 2008-08-02
Okay More problems:...

1. One problem with workspaces is Thunderbird, seems if it downloads an email when not on the active workspace it locks up. (Edit your settings to auto download emails every two minutes, add another account, then send an email to yourself. Go to a different workspace and wait, you will get a ghosted out thunderbird email downloaded message, on switching back to the relevant workspace thunderbird is also ghosted out and all you can do is close it. The email successfully downloads so when you re-run thunderbird it is safe, just cant access it initially after download)

2. Deleting files in the bin which I dont have permissions to do (tried Warzone 2100 again going through [http://gaming.gwos.org/doku.php/guides:64bit](http://gaming.gwos.org/doku.php/guides:64bit) procedures) and ended up with a duff install (probably out of date procedures/links to downloaded files broke? (and not meaning to offend artificial intelligence obviously a lot of work went into those guides - more likely noobish mistakes on my behalf))... anyway not important it was more another experiment in compiling... so I ended up with orphaned packages (now removed)(lol check me out with the linux terminology) and a few folders on the desktop, these I dragged into the bin and a few of those will not delete. So I guesse its a case of sudo some-permission-command to operate on the files/folders recursively?

3. My laptop has a multi card reader, which through windows automatically picks up on the fact that I have inserted a sony magic gate memorystickpro, under Ubuntu I havent got that working yet. I think I remember seeing the built in card reader being recognised on ubuntu install, but havent had any joy being able to access it (it doesnt show as a device in places/computer, nor does it pop up with any action requests when a card is inserted)

---

### Post by alt3rn1ty on 2008-08-02
Scratch question 2, just found out how, I needed to change ownership of the files in the wastebasket to my user name then just empty trash as normal...

sudo chown -R yourusernamehere ~/.local/share/Trash/*

Edit: And I did manage to get the 64 bit compatible warzone 2100 running eventually, its quite good too. 


So the Thunderbird and Memory Card Reader probs are still bugging if anyone has any ideas?

---

### Post by Yellow Pasque on 2008-08-02
For thunderbird, it sounds like your video driver is having trouble with the notification. Either turn the pop-up notification off, or maybe your video driver needs tweaked (what kind of card/driver do you have?).

For the card reader, does this show it?:
```
sudo update-pciids
lspci
```

---

### Post by alt3rn1ty on 2008-08-02
Edit: <Bows deeply, after realising I am in the presence of a 'chocolate covered ubuntu beans'>

Hi the laptop is a compaq presario r3000 with NVidia GeForce4 440 Go 64 DDR, I think Ubuntu decided to use the legacy driver for my installation.

after those commands
sudo update-pciids
lspci

I get amongst others the following, but still dont seem to be able to access the card reader in any way obvious. I list the following because the card reader is listed also in windows device drivers as Texas instruments....

02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

---

### Post by cariboo on 2008-08-03
Insert your memory card and then have a look a dmesg. Either go to System-->Administration-->System Log-->File-->Open and select dmesg, or in a terminal type:

```
dmesg
```

and see if it recognizes your memory card and if it created a mountable device. 

Jim

---

### Post by alt3rn1ty on 2008-08-03
Well I have had a good browse through the results of dmesg, I cant make out what I need to be looking for amongst it so posting results here, also no devices popped up in places/computer, is there somewhere else I should be looking?

Edit: I did insert the memory card first, which usually has a little read light when it detects a card inserted, no read light yet.

dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 21:01:46 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] Command line: root=UUID=***********************19a ro quiet splash vga=773
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ff70000 (usable)
[    0.000000]  BIOS-e820: 000000002ff70000 - 000000002ff7f000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002ff7f000 - 000000002ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002ff80000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 196464) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7240 checksum 0
[    0.000000] ACPI: RSDP 000F7240, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 2FF7A87E, 0034 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 2FF7EE13, 0074 (r1 NVIDIA CK8       6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 2FF7A8B2, 4561 (r1 NVIDIA      CK8  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 2FF7FFC0, 0040
[    0.000000] ACPI: APIC 2FF7EE87, 005A (r1 NVIDIA NV_APIC_  6040000  LTP        0)
[    0.000000] ACPI: BOOT 2FF7EEE1, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 2FF7EF09, 00F7 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 1 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000002ff70000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 196464) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000002ff70000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   196464
[    0.000000] On node 0 totalpages: 196367
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1217 pages reserved
[    0.000000]   DMA zone: 2726 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 2630 pages used for memmap
[    0.000000]   DMA32 zone: 189738 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cff80000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 192464
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=*********************19a ro quiet splash vga=773
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   17.601071] time.c: Detected 797.938 MHz processor.
[   17.601140] Console: colour dummy device 80x25
[   17.601147] console [tty0] enabled
[   17.601183] Checking aperture...
[   17.601189] CPU 0: aperture @ e8000000 size 128 MB
[   17.617230] Memory: 762152k/785856k available (2489k kernel code, 23316k reserved, 1318k data, 320k init)
[   17.617305] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   17.695036] Calibrating delay using timer specific routine.. 1597.26 BogoMIPS (lpj=3194530)
[   17.695101] Security Framework initialized
[   17.695117] SELinux:  Disabled at boot.
[   17.695144] AppArmor: AppArmor initialized
[   17.695152] Failure registering capabilities with primary security module.
[   17.695372] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.696590] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   17.697252] Mount-cache hash table entries: 256
[   17.697501] Initializing cgroup subsys ns
[   17.697508] Initializing cgroup subsys cpuacct
[   17.697529] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.697534] CPU: L2 Cache: 1024K (64 bytes/line)
[   17.697539] CPU 0/0 -> Node 0
[   17.697582] SMP alternatives: switching to UP code
[   17.698815] Freeing SMP alternatives: 24k freed
[   17.699846] Early unpacking initramfs... done
[   18.476725] ACPI: Core revision 20070126
[   18.476844] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.542098] Using local APIC timer interrupts.
[   18.667400] APIC timer calibration result 12467787
[   18.667404] Detected 12.467 MHz APIC timer.
[   18.667500] Brought up 1 CPUs
[   18.667631] CPU0 attaching sched-domain:
[   18.667636]  domain 0: span 01
[   18.667639]   groups: 01
[   18.667935] net_namespace: 120 bytes
[   18.668786] Time: 23:44:18  Date: 08/02/08
[   18.668836] NET: Registered protocol family 16
[   18.669196] ACPI: bus type pci registered
[   18.669341] PCI: Using configuration type 1
[   18.671279] ACPI: EC: Look up EC in DSDT
[   18.673535] ACPI: Interpreter enabled
[   18.673540] ACPI: (supports S0 S3 S4 S5)
[   18.673565] ACPI: Using IOAPIC for interrupt routing
[   18.677775] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   18.724027] ACPI: EC: GPE = 0x21, I/O: command/status = 0x66, data = 0x62
[   18.724033] ACPI: EC: driver started in interrupt mode
[   18.724115] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.725220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.725360] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   18.725432] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP0._PRT]
[   18.749308] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 18 19) *0
[   18.749637] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 18 19) *0
[   18.749959] ACPI: PCI Interrupt Link [LNK3] (IRQs 17) *0, disabled.
[   18.750280] ACPI: PCI Interrupt Link [LNK4] (IRQs 16 18 19) *0, disabled.
[   18.750602] ACPI: PCI Interrupt Link [LNK5] (IRQs 16 18 19) *0
[   18.750916] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22) *0
[   18.751230] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *0
[   18.751552] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *0
[   18.751866] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *0
[   18.752180] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22) *0, disabled.
[   18.752494] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22) *0
[   18.752813] ACPI: PCI Interrupt Link [LMCI] (IRQs 20 21 22) *0
[   18.753131] ACPI: PCI Interrupt Link [LPID] (IRQs 20 21 22) *0, disabled.
[   18.753457] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *0, disabled.
[   18.753682] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.753739] pnp: PnP ACPI init
[   18.753752] ACPI: bus type pnp registered
[   18.780602] pnp: PnP ACPI: found 12 devices
[   18.780607] ACPI: ACPI bus type pnp unregistered
[   18.781056] PCI: Using ACPI for IRQ routing
[   18.781062] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.781076] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   18.795425] NET: Registered protocol family 8
[   18.795429] NET: Registered protocol family 20
[   18.795559] agpgart: Detected AGP bridge 0
[   18.795568] agpgart: Setting up Nforce3 AGP.
[   18.803067] agpgart: AGP aperture is 128M @ 0xe8000000
[   18.803187] AppArmor: AppArmor Filesystem Enabled
[   18.803394] Time: tsc clocksource has been installed.
[   18.815471] system 00:01: ioport range 0x8000-0x807f has been reserved
[   18.815478] system 00:01: ioport range 0x8080-0x80ff has been reserved
[   18.815484] system 00:01: ioport range 0x8400-0x847f has been reserved
[   18.815490] system 00:01: ioport range 0x8480-0x84ff has been reserved
[   18.815496] system 00:01: ioport range 0x8800-0x887f has been reserved
[   18.815501] system 00:01: ioport range 0x8880-0x88ff has been reserved
[   18.815507] system 00:01: ioport range 0x2040-0x207f has been reserved
[   18.815521] system 00:01: ioport range 0x2000-0x203f has been reserved
[   18.815538] system 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[   18.815544] system 00:02: iomem range 0xfec00000-0xfec00fff has been reserved
[   18.815551] system 00:02: iomem range 0xfee00000-0xfeefffff could not be reserved
[   18.815557] system 00:02: iomem range 0xfed00000-0xfed00fff has been reserved
[   18.815568] system 00:03: ioport range 0x200-0x20f has been reserved
[   18.815574] system 00:03: ioport range 0x680-0x6ff has been reserved
[   18.815580] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   18.815586] system 00:03: ioport range 0xfe00-0xfe01 has been reserved
[   18.816383] PCI: Failed to allocate mem resource #10:4000000@e4000000 for 0000:02:04.0
[   18.816391] PCI: Failed to allocate mem resource #10:4000000@e4000000 for 0000:02:04.1
[   18.816399] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   18.816403]   IO window: 00003000-000030ff
[   18.816409]   IO window: 00003400-000034ff
[   18.816414]   PREFETCH window: 40000000-43ffffff
[   18.816420] PCI: Bus 7, cardbus bridge: 0000:02:04.1
[   18.816423]   IO window: 00003800-000038ff
[   18.816428]   IO window: 00003c00-00003cff
[   18.816433]   PREFETCH window: 44000000-47ffffff
[   18.816438] PCI: Bridge: 0000:00:0a.0
[   18.816442]   IO window: 3000-7fff
[   18.816447]   MEM window: e0100000-e17fffff
[   18.816452]   PREFETCH window: 40000000-47ffffff
[   18.816458] PCI: Bridge: 0000:00:0b.0
[   18.816461]   IO window: disabled.
[   18.816467]   MEM window: e2000000-e2ffffff
[   18.816472]   PREFETCH window: f0000000-f80fffff
[   18.816485] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   18.817026] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[   18.817040] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNK1] -> GSI 19 (level, low) -> IRQ 19
[   18.817495] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[   18.817503] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [LNK2] -> GSI 18 (level, low) -> IRQ 18
[   18.817615] NET: Registered protocol family 2
[   18.851546] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   18.852436] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   18.855050] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   18.856405] TCP: Hash tables configured (established 131072 bind 65536)
[   18.856410] TCP reno registered
[   18.867639] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   19.605291]  it is
[   20.385093] Freeing initrd memory: 7556k freed
[   20.394593] Simple Boot Flag at 0x37 set to 0x1
[   20.395755] audit: initializing netlink socket (disabled)
[   20.395775] audit(1217720659.664:1): initialized
[   20.399684] VFS: Disk quotas dquot_6.5.1
[   20.399825] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   20.400074] io scheduler noop registered
[   20.400080] io scheduler anticipatory registered
[   20.400085] io scheduler deadline registered
[   20.400283] io scheduler cfq registered (default)
[   20.401355] Boot video device is 0000:01:00.0
[   20.457532] Real Time Clock Driver v1.12ac
[   20.457698] Linux agpgart interface v0.102
[   20.457703] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.459172] ACPI: PCI Interrupt Link [LMCI] enabled at IRQ 22
[   20.459186] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [LMCI] -> GSI 22 (level, low) -> IRQ 22
[   20.459200] ACPI: PCI interrupt for device 0000:00:06.1 disabled
[   20.460442] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.460568] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.460733] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.470558] i8042.c: Detected active multiplexing controller, rev 1.1.
[   20.476013] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.476021] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   20.476026] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   20.476031] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   20.476036] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   20.486989] mice: PS/2 mouse device common for all mice
[   20.487057] cpuidle: using governor ladder
[   20.487061] cpuidle: using governor menu
[   20.487319] NET: Registered protocol family 1
[   20.487498] registered taskstats version 1
[   20.487699]   Magic number: 4:287:756
[   20.487909] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   20.487915] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.487919] EDD information not available.
[   20.487932] Freeing unused kernel memory: 320k freed
[   20.522869] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.700132] vesafb: framebuffer at 0xf0000000, mapped to 0xffffc20000580000, using 1536k, total 65536k
[   20.700142] vesafb: mode is 1024x768x8, linelength=1024, pages=3
[   20.700147] vesafb: scrolling: redraw
[   20.700154] vesafb: Pseudocolor: size=8:8:8:8, shift=0:0:0:0
[   20.700370] Console: switching to colour frame buffer device 128x48
[   20.710390] fb0: VESA VGA frame buffer device
[   21.940627] fuse init (API version 7.9)
[   21.975178] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   21.978255] Marking TSC unstable due to TSC halts in idle
[   21.978434] Time: acpi_pm clocksource has been installed.
[   21.983319] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   21.987765] ACPI: Thermal Zone [THRM] (50 C)
[   23.286201] usbcore: registered new interface driver usbfs
[   23.286243] usbcore: registered new interface driver hub
[   23.314135] usbcore: registered new device driver usb
[   23.332075] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   23.332155] PCI: Enabling device 0000:00:02.0 (0004 -> 0006)
[   23.332785] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[   23.332801] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 21 (level, low) -> IRQ 21
[   23.333104] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   23.333116] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   23.333453] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   23.550022] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe0000000
[   23.608218] usb usb1: configuration #1 chosen from 1 choice
[   23.608273] hub 1-0:1.0: USB hub found
[   23.608286] hub 1-0:1.0: 3 ports detected
[   23.665698] SCSI subsystem initialized
[   23.710147] PCI: Enabling device 0000:00:02.1 (0004 -> 0006)
[   23.710674] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 20
[   23.710689] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS1] -> GSI 20 (level, low) -> IRQ 20
[   23.711008] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   23.711019] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   23.711110] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   23.925911] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe0001000
[   23.984081] usb usb2: configuration #1 chosen from 1 choice
[   23.984134] hub 2-0:1.0: USB hub found
[   23.984147] hub 2-0:1.0: 3 ports detected
[   24.026343] libata version 3.00 loaded.
[   24.082668] 8139too Fast Ethernet driver 0.9.28
[   24.086560] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   24.086567] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [LUS2] -> GSI 22 (level, low) -> IRQ 22
[   24.086855] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   24.086866] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   24.086964] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   24.087021] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   24.087040] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe0004000
[   24.213824] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   24.225829] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.226034] usb usb3: configuration #1 chosen from 1 choice
[   24.226081] hub 3-0:1.0: USB hub found
[   24.226094] hub 3-0:1.0: 6 ports detected
[   24.330133] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNK2] -> GSI 18 (level, low) -> IRQ 18
[   24.330907] eth0: RealTek RTL8139 at 0x7000, 00:16:d4:05:18:e2, IRQ 18
[   24.330912] eth0:  Identified 8139 chip type 'RTL-8101'
[   24.336144] pata_amd 0000:00:08.0: version 0.3.10
[   24.336220] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   24.351344] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   24.374420] scsi0 : pata_amd
[   24.389791] scsi1 : pata_amd
[   24.391012] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[   24.391018] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[   24.441869] Floppy drive(s): fd0 is 1.44M
[   24.465422] FDC 0 is a post-1991 82077
[   24.554237] ata1.00: ATA-6: IC25N080ATMR04-0, MO4OAD5A, max UDMA/100
[   24.554246] ata1.00: 156301488 sectors, multi 16: LBA48 
[   24.570228] ata1.00: configured for UDMA/100
[   24.897644] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   24.905933] ata2.00: ATAPI: _NEC DVD+/-RW ND-6450A, 2.36, max MWDMA2
[   25.109806] ata2.00: configured for MWDMA2
[   25.110000] scsi 0:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
[   25.111813] usb 1-1: configuration #1 chosen from 1 choice
[   25.145390] scsi 1:0:0:0: CD-ROM            _NEC     DVD+-RW ND-6450A 2.36 PQ: 0 ANSI: 5
[   25.149022] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNK1] -> GSI 19 (level, low) -> IRQ 19
[   25.199283] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[e0106000-e01067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   25.410357] Driver 'sd' needs updating - please use bus_type methods
[   25.410501] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   25.410525] sd 0:0:0:0: [sda] Write Protect is off
[   25.410531] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.410561] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.410636] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   25.410654] sd 0:0:0:0: [sda] Write Protect is off
[   25.410659] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.410686] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.410694]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   25.459954] usbcore: registered new interface driver hiddev
[   25.465920] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.0/input/input2
[   25.477555] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.0-1
[   25.477584] usbcore: registered new interface driver usbhid
[   25.477592] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   25.778830]  sda1 sda2 < sda5 sda6 sda7 >
[   25.831558] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.842926] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.842964] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   25.946969] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   25.946979] Uniform CD-ROM driver Revision: 3.20
[   25.947078] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   26.328922] Attempting manual resume
[   26.328930] swsusp: Resume From Partition 8:7
[   26.328934] PM: Checking swsusp image.
[   26.329109] PM: Resume from disk failed.
[   26.380369] kjournald starting.  Commit interval 5 seconds
[   26.380393] EXT3-fs: mounted filesystem with ordered data mode.
[   26.477328] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[643f0200643f0200]
[   41.603981] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2040
[   41.604046] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
[   41.706219] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.770120] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.048867] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   42.844651] input: Power Button (FF) as /devices/virtual/input/input4
[   42.860345] ACPI: Power Button (FF) [PWRF]
[   42.860473] input: Power Button (CM) as /devices/virtual/input/input5
[   42.872351] ACPI: Power Button (CM) [PWRB]
[   42.872529] input: Lid Switch as /devices/virtual/input/input6
[   42.880922] ACPI: Lid Switch [LID]
[   43.240460] ACPI: WMI-Acer: Mapper loaded
[   45.747706] ACPI: AC Adapter [ACAD] (on-line)
[   47.039343] ACPI: Battery Slot [BAT1] (battery present)
[   47.116054] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/LNXVIDEO:00/input/input7
[   47.131120] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   48.149988] Yenta: CardBus bridge found at 0000:02:04.0 [103c:006d]
[   48.150013] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   48.150017]   IO window: 00003000-000030ff
[   48.150023]   IO window: 00003400-000034ff
[   48.150028]   PREFETCH window: 40000000-43ffffff
[   48.150034]   MEM window: e0400000-e07fffff
[   48.150041] Yenta: Enabling burst memory read transactions
[   48.150047] Yenta: Using CSCINT to route CSC interrupts to PCI
[   48.150051] Yenta: Routing CardBus interrupts to PCI
[   48.150058] Yenta TI: socket 0000:02:04.0, mfunc 0x01111d22, devctl 0x64
[   48.319987] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 21
[   48.319997] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LACI] -> GSI 21 (level, low) -> IRQ 21
[   48.320296] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   48.379461] Yenta: ISA IRQ mask 0x0cb8, PCI irq 19
[   48.379469] Socket status: 30000086
[   48.379475] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   48.379485] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   48.379491] pcmcia: parent PCI bridge Memory window: 0xe0100000 - 0xe17fffff
[   48.379497] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x47ffffff
[   48.423314] Yenta: CardBus bridge found at 0000:02:04.1 [103c:006d]
[   48.423338] Yenta: Using CSCINT to route CSC interrupts to PCI
[   48.423342] Yenta: Routing CardBus interrupts to PCI
[   48.423349] Yenta TI: socket 0000:02:04.1, mfunc 0x01111d22, devctl 0x64
[   48.434722] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2128: AC'97 0 analog subsections not ready
[   48.595716] input: PS/2 Mouse as /devices/virtual/input/input8
[   48.627005] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   48.655361] Yenta: ISA IRQ mask 0x0cb8, PCI irq 18
[   48.655369] Socket status: 30000006
[   48.655374] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   48.655383] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   48.655389] pcmcia: parent PCI bridge Memory window: 0xe0100000 - 0xe17fffff
[   48.655395] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x47ffffff
[   49.002559] intel8x0_measure_ac97_clock: measured 55295 usecs
[   49.002568] intel8x0: clocking to 48000
[   49.032739] nvidia: module license 'NVIDIA' taints kernel.
[   49.524654] parport_pc 00:0b: reported by Plug and Play ACPI
[   49.524715] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   49.843000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 16
[   49.843018] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNK5] -> GSI 16 (level, low) -> IRQ 16
[   49.843291] NVRM: loading NVIDIA Linux x86_64 Kernel Module  96.43.05  Tue Jan 22 17:37:40 PST 2008
[   54.150751] lp0: using parport0 (interrupt-driven).
[   54.363244] Adding 746980k swap on /dev/sda7.  Priority:-1 extents:1 across:746980k
[  173.921501] EXT3 FS on sda6, internal journal
[  175.210971] ip_tables: (C) 2000-2006 Netfilter Core Team
[  175.917530] No dock devices found.
[  176.370519] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3400+ processors (1 cpu cores) (version 2.20.00)
[  176.370587] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x2
[  176.370592] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[  176.370597] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x12
[  177.457673] Clocksource tsc unstable (delta = 688740197 ns)
[  180.841069] ppdev: user-space parallel port driver
[  182.169589] audit(1217717218.562:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6311 profile="/usr/sbin/cupsd" namespace="default"
[  189.400053] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  190.874284] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  190.874313] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  190.874372] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  192.296675] NET: Registered protocol family 17
[  198.844455] NET: Registered protocol family 10
[  198.845233] lo: Disabled Privacy Extensions
[  211.525955] eth0: no IPv6 routers present

---

### Post by alt3rn1ty on 2008-08-03
Update: I have in-advertently solved the in-active workspace/thunderbird problem. While going through CompizConfig advanced desktop settings, cutting away bits I dont want/need, I de-selected the ability of off-screen fading of windows. Then went back having more of a browse, then realised this may affect my thunderbird problem.. sure enough the problem is now gone, and no need to disable the incoming message pop-up either. :)

Trouble is, for the last 20 minutes I have been trying to find where I de-selected it for the purpose of posting my findings.... sorry I cant find it again just now. :oops:


:confused: I still have not had any joy with my card reader as yet.

---

### Post by Ptero-4 on 2008-08-04
Have you tried with SD and XD cards. My older laptop's card reader (a Ricoh one) could only see SD cards under ubuntu. Under windoze it could see all the four formats it supported (SD, XD, memorystick, memorystick pro).

---

### Post by alt3rn1ty on 2008-08-04
Thats certainly a possibility but I dont have any other kind of memory cards to try, we have two digital cameras, the newest was chosen to utilise the same 2gb memorystickpro cards we were already using (regular scrooge here lol).
But the thing which makes me doubt the whole card reader unit in the laptop failing to be mounted properly is that when windows boots,the read light on the side of the laptop flashes once as the system checks all devices, aswell as when a card is inserted, in linux I havent seen that happen once. Which is a shame its the only fly in my ubuntu ointment now, this OS is fantastic (Well it is when I am not screwing it up that is, but I am pretty sure I havent done anything to affect the card reader, and I havent plowed on ahead with this one in any random noobish 'lets see if this works' fashion, mainly because I have got past the dont care if I have to reformat stage and am now looking at a more valuable 'lot of work since installation and everythings sweet' stage).

---

### Post by alt3rn1ty on 2008-08-07
Well thanks for helping to try and resolve this one, but I think I can assume I have a weird card reader configuration in my laptop that x64 cant interface with for now, maybe the next distro.

Its no biggy anyway, dual booting I can still access the card reader through windows, I was just hoping to completely do away with windows on the laptop though.

My installation on the desktop has now gone well and the card reader on there was recognised no problem. Have to stick with dual boot on that one though for the rest of the family users and games on xp. :rolleyes:

---

