---
title: "no sound"
date: 2007-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ecurb on 2007-10-08
hi i have a gigabyte GA-K8N Ultra-Sli motherboard and i have no sound at all.
I have tried several things but no good. could someone please help as i am new at this!

ecurb@Slowbro:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ecurb@Slowbro:~$ lspci -v
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at e400 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at f4001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: Giga-byte Technology Unknown device ae01
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        I/O ports at b400 [size=256]
        I/O ports at b800 [size=256]
        Memory at f4004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at cc00 [size=16]
        Memory at f4005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at e000 [size=16]
        Memory at f4000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: f0000000-f1ffffff
        Prefetchable memory behind bridge: 88000000-880fffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at f4002000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e800 [size=8]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f2000000-f3ffffff
        Prefetchable memory behind bridge: 0000000088100000-00000000881fffff
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: e8000000-efffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000e7ffffff
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:09.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device b004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        I/O ports at 8000 [size=8]
        I/O ports at 8400 [size=4]
        I/O ports at 8800 [size=8]
        I/O ports at 8c00 [size=4]
        I/O ports at 9000 [size=16]
        Memory at f1005000 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at 88000000 [disabled] [size=512K]
        Capabilities: <access denied>

01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at f1004000 (32-bit, non-prefetchable) [size=2K]
        Memory at f1000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
        Subsystem: Giga-byte Technology Marvell 88E8053 Gigabit Ethernet Controller (Gigabyte)
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f3000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        [virtual] Expansion ROM at 88100000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2) (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Memory at e0000000 (64-bit, prefetchable) [size=128M]
        Memory at ec000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at ed000000 [disabled] [size=128K]
        Capabilities: <access denied>


ecurb@Slowbro:~$ sudo modprobe snd-
FATAL: Module snd_ not found.

---

### Post by Yellow Pasque on 2007-10-09
Did you try the suggestions in this guide?

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+solutions+guide)

---

