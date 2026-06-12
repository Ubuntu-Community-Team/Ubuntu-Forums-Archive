---
title: "S3 suspend state, corrupted disk"
date: 2008-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by captaintrav on 2008-04-16
Running Gutsy AMD64.   Trying unsuccessfully to get S3 suspend to work, twice it corrupted the root file system when trying to resume from suspend.  Upon a cold boot,  I get 'GRUB error 17'.  Subsequent booting from a live CD and running fsck said that the superblock was invalid, tossed the journal, reverting it to fsck2 and found 1000's of errors.  I'm assuming I should file some sort of bug, the system is 100% stable otherwise.  The system is suspending file once I changed /etc/default/acpi-support to 'ACPI_SLEEP_MODE=standby'   I've seen plenty of suspend problems, but usuaully it's just a matter of it working or not working, I've lost many hours rebuilding the system (twice).

Here's some questions:  

1) does Linux care what BIOS options are set to?  I believe the corruption only happened when I set the ACPI suspend mode to S3 in the bios, otherwise the system just would just hard lock.

2) what info do I need to include in a bug report?  Google tells me I'm not the first one to have this happen.

3) what is the "proper" setting to use for Nvidia video cards as far as reposting the video bios on resume from suspend.  there is an option regarding that both in /etc/default/acpi-support, and in the bios.

4) when the system was (unsucessfully) trying to resume from suspend, the hard disk activity light was on, sounded like disk activity, probably what caused the corruption.  Any ideas WHY the disk would be going bananas on resume?

results of **lspci -v**

```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
        Subsystem: ASRock Incorporation 939NF6G-VSTA Board
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
        Subsystem: ASRock Incorporation 939NF6G-VSTA Board
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
        Subsystem: ASRock Incorporation 939NF6G-VSTA Board
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at ec00 [size=64]
        I/O ports at 5000 [size=64]
        I/O ports at 6000 [size=64]
        Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
        Subsystem: ASRock Incorporation 939NF6G-VSTA Board
        Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation 939NF6G-VSTA Board
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at dffff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation 939NF6G-VSTA Board
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at dfffec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: ASRock Incorporation Unknown device 0888
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at dfff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: ASRock Incorporation Unknown device 03ec
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
        Subsystem: ASRock Incorporation Unknown device 03ef
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at dfffd000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e480 [size=8]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: ASRock Incorporation 939NF6G-VSTA Board
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at 0e00 [size=8]
        I/O ports at 0e20 [size=4]
        I/O ports at 0e40 [size=8]
        I/O ports at 0e60 [size=4]
        I/O ports at d880 [size=16]
        Memory at dfffc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: ASRock Incorporation 939NF6G-VSTA Board
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at 0e80 [size=8]
        I/O ports at 0ea0 [size=4]
        I/O ports at 0ec0 [size=8]
        I/O ports at 0ee0 [size=4]
        I/O ports at d000 [size=16]
        Memory at dfff7000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2) (prog-if 00 [VGA])
        Subsystem: ASRock Incorporation Unknown device 03d0
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dd000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at dffc0000 [disabled] [size=128K]
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
        Capabilities: <access denied>

```

Some other info:

```
travis@tbird:/etc/default$ linuxinfo
Linux tbird 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008
Two AMD Unknown 1000MHz processors, 4022.44 total bogomips, 5120M RAM
System library 2.6.1

```

The system has 4 GB of ram installed (thus the reason for AMD64)

---

### Post by pmn03 on 2008-05-02
I also had this happen to me. Amazingly this is a known bug and hasn't been fixed in the released version of Hardy. 
[https://bugs.launchpad.net/bugs/203537]("https://bugs.launchpad.net/bugs/203537")

I would recommend to everyone, don't try suspend. There is a small possibility it will completely wipe out your hard drives. Like it did to me.

---

### Post by arqueware on 2008-05-05
i had this happen on a virgin install of Hardy x86_64; i hadn't changed any acpi settings.  My XP-64 partition was unharmed, so i was able to revert to it for function, but have had to reinstall Ubuntu 3 times of late.

this bug is also referenced at:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537)

---

