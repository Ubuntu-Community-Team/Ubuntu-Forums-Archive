---
title: "Creative X-Fi XtremeMusic (No sound)"
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by Solaris3k1 on 2009-04-30
Hi all, I recently installed Ubuntu 9.04 on my desktop and I don't have any sound coming from it whatsoever.  I have a Creative X-Fi XtremeMusic on a PCI slot in my desktop so I went through the instructions on this page...

[http://ubuntuforums.org/showthread.php?t=870001&highlight=xtrememusic](http://ubuntuforums.org/showthread.php?t=870001&highlight=xtrememusic)

When I ran it it seemed it all installed properly and I even had sound working on the test button of my sound panel when I set it to OSS.  After the reset however, it says the media is disconnected and the test button doesn't even work anymore.  I know the sound card is good as it works on Windows still but I can't figure out what happened.

Note:  I do have onboard audio through my mobo, but I'd rather not have to unattach everything and then reattach it all every time I boot from Windows to Linux/Vice versa.

Thanks!

Here's the output of my lspci -v

```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 2f00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 2900 [size=64]
	I/O ports at 2d00 [size=64]
	I/O ports at 2e00 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at f3f80000 (32-bit, non-prefetchable) [size=512K]

00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f3f7f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f3f7ec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f3f7d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f3f7e800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f462:7508
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f3f78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f4000000-fbffffff
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Device 7508
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2300
	I/O ports at c480 [size=8]
	I/O ports at c400 [size=4]
	I/O ports at c080 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at bc00 [size=16]
	Memory at f3f76000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 508c
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2299
	Memory at f3f7c000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at b880 [size=8]
	Memory at f3f7e400 (32-bit, non-prefetchable) [size=256]
	Memory at f3f7e000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fc000000-feafffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

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
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:08.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0021
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at dc00 [size=32]
	Memory at fbe00000 (64-bit, non-prefetchable) [size=2M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel modules: ctxfi

02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GT/GTO] (rev a1)
	Subsystem: XFX Pine Group Inc. Device 2213
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at feae0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 Multimedia controller: ATI Technologies Inc Theater 550 PRO PCIe
	Subsystem: ATI Technologies Inc Device a347
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at feb00000 (32-bit, non-prefetchable) [size=1M]
	Memory at f0000000 (32-bit, prefetchable) [size=32M]
	Capabilities: <access denied>

```

---

### Post by Antioch on 2009-04-30
This isn't the answer you're looking for, but the last time I inquired about X-Fi and Linux I learned that the X-Fi drivers that Creative *finally* released are terrible and there's not really much you can do about it. Get a more friendly sound card, because I don't think Creative will be making any improvements for a long time - if ever.

My Xonar works just fine out-of-the-box, much better than my X-Fi which has long since been e-bayed off.

Sorry =\

---

### Post by Yellow Pasque on 2009-04-30
You could always give OSS4 a try for your X-fi:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
I think that guide's a bit out of date, but it will give you the general idea.

---

### Post by Francewhoa on 2009-05-22
If your sound card isn't automatically detected by Ubuntu 8.04.2 the below installation script is the easiest way that I know of to install & configure any sound card. It's a script made by *soundcheck*. It does all the hard manual setup process for you. ** [Click here to open the post]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810"), then find the latest installation script attached at the bottom. **Current installation script is title *AlsaUpgrade-1.0.x-rev-1.17.tar*.


If the script works for you please add your results here:

[LIST]
[*][https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)
[*][http://www.ubuntuhcl.org/browse/search+sound-cards?category=27](http://www.ubuntuhcl.org/browse/search+sound-cards?category=27)
[/LIST]

---

