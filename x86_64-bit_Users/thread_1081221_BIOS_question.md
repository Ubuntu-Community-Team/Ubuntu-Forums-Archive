---
title: "BIOS question"
date: 2009-02-26
forum: x86 64-bit Users
---

### Post by TedHale on 2009-02-26
Has anyone had any particular issues with AMD-64bit processors and getting segfaults on fresh installs that were cleared up by BIOS updates/reconfiguring?

I have another thread in the server section asking about segfaults, however, the three machines (all identical hardware), all give me segfaults after a fresh install of 8.04.2 lts 64bit server edition.

I've ruled out memory issues and HD issues and am left with low level infrastructure (CPU/Bus/etc). 

They are Rackable 2U thin clients that are 4 years old.

Thanks in advance.

---

### Post by OLFP on 2009-02-26
I was getting random lock ups- no error messages, but I reflashed yesterday, and so far so good.

I'm fairly certain it was a ethernet interface issue. I never get any error messages, but there were a couple times when my desktop freezing would screw up my whole home LAN.

---

### Post by Yellow Pasque on 2009-02-26
I'd suggest looking at the release notes/changelogs for the BIOS updates offered for your system/motherboard.

Another possibility could be a faulty driver (since the machines are physically identical).

---

### Post by TedHale on 2009-02-26
I updated the BIOS from 

TYAN Thunder K8SR 2.04 to 2.07

During the install, after this upgrade, I got an error with trying to install GRUB, which I had not seen up to this point. On a google search, I've seen that there was an issue with GRUB and RAID1 at times, so I reinstalled again using LVM. After the install, I did a apt-get update and an apt-get upgrade (which I'm using as my test to see if I'm going to get segfaults or not). As soon as the packages began configurations, bam segfault.

I also read that having swap space issues could cause this. So I did another reinstall with no swap space configured. 6GB or RAM, I figured it was safe for the test. Again, apt-get upgrade gave me a segfault.

I'm down to scouring my BIOS or trying to figure out what driver in my kernel is just not happy. Incidently, what would be the best way to go about doing this?

Thanks for your comments and future advice.
I'll get a more complete picture of my system up in a little while as far as hardware components I'm using.

T

---

### Post by TedHale on 2009-02-26
Here is the output of lspci -nnv

There are a few 'unknown devices' that show up. Thanks in advance.



00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] AMD-8111 PCI [1022:7460] (rev 07) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000a000-0000bfff
	Memory behind bridge: fc900000-feafffff
	Capabilities: [c0] HyperTransport: Slave or Primary Interface
	Capabilities: [f0] HyperTransport: Interrupt Discovery and Configuration

00:07.0 ISA bridge [0601]: Advanced Micro Devices [AMD] AMD-8111 LPC [1022:7468] (rev 05)
	Subsystem: Advanced Micro Devices [AMD] AMD-8111 LPC [1022:7468]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:07.1 IDE interface [0101]: Advanced Micro Devices [AMD] AMD-8111 IDE [1022:7469] (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Advanced Micro Devices [AMD] AMD-8111 IDE [1022:7469]
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]

00:07.2 SMBus [0c05]: Advanced Micro Devices [AMD] AMD-8111 SMBus 2.0 [1022:746a] (rev 02)
	Subsystem: Advanced Micro Devices [AMD] AMD-8111 SMBus 2.0 [1022:746a]
	Flags: medium devsel, IRQ 9
	I/O ports at cc00 [size=32]

00:07.3 Bridge [0680]: Advanced Micro Devices [AMD] AMD-8111 ACPI [1022:746b] (rev 05)
	Subsystem: Advanced Micro Devices [AMD] AMD-8111 ACPI [1022:746b]
	Flags: medium devsel

00:0a.0 PCI bridge [0604]: Advanced Micro Devices [AMD] AMD-8131 PCI-X Bridge [1022:7450] (rev 12) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	Memory behind bridge: fc800000-fc8fffff
	Prefetchable memory behind bridge: 00000000ff500000-00000000ff5fffff
	Capabilities: [a0] PCI-X bridge device
	Capabilities: [b8] HyperTransport: Interrupt Discovery and Configuration
	Capabilities: [c0] HyperTransport: Slave or Primary Interface

00:0a.1 PIC [0800]: Advanced Micro Devices [AMD] AMD-8131 PCI-X IOAPIC [1022:7451] (rev 01) (prog-if 10 [IO-APIC])
	Subsystem: Advanced Micro Devices [AMD] Unknown device [1022:36c0]
	Flags: bus master, medium devsel, latency 0
	Memory at febff000 (64-bit, non-prefetchable) [size=4K]

00:0b.0 PCI bridge [0604]: Advanced Micro Devices [AMD] AMD-8131 PCI-X Bridge [1022:7450] (rev 12) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fc500000-fc7fffff
	Prefetchable memory behind bridge: 00000000ff400000-00000000ff4fffff
	Capabilities: [a0] PCI-X bridge device
	Capabilities: [b8] HyperTransport: Interrupt Discovery and Configuration

00:0b.1 PIC [0800]: Advanced Micro Devices [AMD] AMD-8131 PCI-X IOAPIC [1022:7451] (rev 01) (prog-if 10 [IO-APIC])
	Subsystem: Advanced Micro Devices [AMD] Unknown device [1022:36c0]
	Flags: bus master, medium devsel, latency 0
	Memory at febfe000 (64-bit, non-prefetchable) [size=4K]

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface
	Capabilities: [a0] HyperTransport: Host or Secondary Interface
	Capabilities: [c0] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Flags: fast devsel

00:19.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface
	Capabilities: [a0] HyperTransport: Host or Secondary Interface
	Capabilities: [c0] HyperTransport: Host or Secondary Interface

00:19.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Flags: fast devsel

00:19.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Flags: fast devsel

00:19.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Flags: fast devsel

01:03.0 SCSI storage controller [0100]: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI [1000:0030] (rev c1)
	Subsystem: Unknown device [5100:1000]
	Flags: bus master, 66MHz, medium devsel, latency 72, IRQ 28
	I/O ports at 9800 [size=256]
	Memory at fc7e0000 (64-bit, non-prefetchable) [size=128K]
	Memory at fc7c0000 (64-bit, non-prefetchable) [size=128K]
	Expansion ROM at fc600000 [disabled] [size=1M]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [68] PCI-X non-bridge device

02:09.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet [14e4:1648] (rev 03)
	Subsystem: Broadcom Corporation Unknown device [14e4:1644]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 24
	Memory at fc8c0000 (64-bit, non-prefetchable) [size=64K]
	Memory at fc8b0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at fc8a0000 [disabled] [size=64K]
	Capabilities: [40] PCI-X non-bridge device
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-

02:09.1 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet [14e4:1648] (rev 03)
	Subsystem: Broadcom Corporation Unknown device [14e4:1644]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 25
	Memory at fc8f0000 (64-bit, non-prefetchable) [size=64K]
	Memory at fc8e0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at fc8d0000 [disabled] [size=64K]
	Capabilities: [40] PCI-X non-bridge device
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-

03:00.0 USB Controller [0c03]: Advanced Micro Devices [AMD] AMD-8111 USB [1022:7464] (rev 0b) (prog-if 10 [OHCI])
	Subsystem: Advanced Micro Devices [AMD] AMD-8111 USB [1022:7464]
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at feafc000 (32-bit, non-prefetchable) [size=4K]

03:00.1 USB Controller [0c03]: Advanced Micro Devices [AMD] AMD-8111 USB [1022:7464] (rev 0b) (prog-if 10 [OHCI])
	Subsystem: Advanced Micro Devices [AMD] AMD-8111 USB [1022:7464]
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at feafd000 (32-bit, non-prefetchable) [size=4K]

03:05.0 Mass storage controller [0180]: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller [1095:3114] (rev 02)
	Subsystem: Silicon Image, Inc. SiI 3114 SATALink Controller [1095:3114]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at bc00 [size=8]
	I/O ports at b400 [size=4]
	I/O ports at b000 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at a800 [size=16]
	Memory at feafec00 (32-bit, non-prefetchable) [size=1K]
	Expansion ROM at fea00000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2

03:06.0 VGA compatible controller [0300]: ATI Technologies Inc Rage XL [1002:4752] (rev 27) (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Rage XL [1002:8008]
	Flags: bus master, stepping, medium devsel, latency 64, IRQ 11
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	I/O ports at b800 [size=256]
	Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at feac0000 [disabled] [size=128K]
	Capabilities: [5c] Power Management version 2

---

### Post by Yellow Pasque on 2009-02-26
If you haven't already, I encourage you to register this bug on Launchpad, since it's reproducible on a fresh install and it sounds like you've methodically eliminated common hardware issues (corrupt storage, bad RAM, etc.).

---

### Post by TedHale on 2009-02-26
Will do, thanks.

---

