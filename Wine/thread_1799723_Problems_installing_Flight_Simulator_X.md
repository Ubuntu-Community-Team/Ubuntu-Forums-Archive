---
title: "Problems installing Flight Simulator X"
date: 2011-07-08
forum: Wine
---

### Post by xavi787 on 2011-07-08
Hello,

I have installed DirectX9, corefonts but I was unable to install vcrun2005 for some unknown reason.

Anyways I tried to install Flight Simulator X (FSX) by copying both disks to a directory. 
I ran the installer and everything went well.  
During the installation it asked me to insert disk 2 but when I inserted it the installer doesn't recognize it. 
I cancelled the installation but the archives are still on the C: drive. 
My FSX folder is 13 GB. 
I opened FSX by going to that folder and I see the splashscreen followed by the activation dialog. 
I put my product key and activated it but then Wine says that it encountered an error and needs to close the application. 
When I press the activate later button the screen goes black and I have to force the computer to shutdown by holding the power button.

I hope to find a solution to this :(

Thanks

---

### Post by bobwyajnr on 2011-07-08
Hey,

No problem there dude! :popcorn:

What are your hardware specs ? **lspci -v** console output (as a .txt attachment would do) if you are not sure - would be a start! Have you installed a proprietary Linux driver for your graphics card?

What Wine version are you using?

Have you checked out the [Wine AppDB for Flight Simulator X]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7775")?

Also I would recommend reading the [Wine FAQ]("http://wiki.winehq.org/FAQ") and [Wine User Guide]("http://www.winehq.org/documentation"). These are clear and concise (if a bit dated in places)...

Bob

---

### Post by xavi787 on 2011-07-08
> **bobwyajnr said:**
> Hey,

No problem there dude! :popcorn:

What are your hardware specs ? **lspci -v** console output (as a .txt attachment would do) if you are not sure - would be a start! Have you installed a proprietary Linux driver for your graphics card?

What Wine version are you using?

Have you checked out the [Wine AppDB for Flight Simulator X]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7775")?

Also I would recommend reading the [Wine FAQ]("http://wiki.winehq.org/FAQ") and [Wine User Guide]("http://www.winehq.org/documentation"). These are clear and concise (if a bit dated in places)...

Bob

My computer specs:

lspci -v:
```

xavi@xavi-laptop:~$ lspci -v 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d2200000-d23fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: d1200000-d21fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: d1100000-d11fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2500000-d25fffff
	Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 6038 [size=8]
	I/O ports at 604c [size=4]
	I/O ports at 6030 [size=8]
	I/O ports at 6048 [size=4]
	I/O ports at 6010 [size=16]
	Memory at d2409000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2408000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2407000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d2409500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2406000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2405000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d2409400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 80 [Master])
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 6000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
	I/O behind bridge: 00001000-00001fff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2404000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=256]
	Memory at d2300000 (32-bit, non-prefetchable) [size=64K]
	Memory at d2200000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 137f
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 3045
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at 2000 [size=256]
	Memory at d1010000 (64-bit, prefetchable) [size=4K]
	Memory at d1000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1020000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

xavi@xavi-laptop:~$ 


```

I am unable to install the proprietary drivers so I am currently using the open-source drivers. See my other post: [http://ubuntuforums.org/showthread.php?t=1785242]("http://ubuntuforums.org/showthread.php?t=1785242")

I am using Wine 1.3.21

And yes I checked the appDB for FSX

---

### Post by bobwyajnr on 2011-07-08
Hi

Hmmm come back to this thread in 2-5 years time - when the ATI FOSS drivers have fully matured OpenGL support! :popcorn:

Bob

PS I am not joking - it will come :D

---

### Post by xavi787 on 2011-07-11
Hello,

Now I have the proprietary drivers working but Fsx still doesn't work. 
Also, What is vcrun2005 and how can I install it because wine gives me the following error while trying to install:

```

sha1sum mismatch! Rename /home/xavi/.cache/winetricks/vcrun2005/vcredist_X86.exe and try again

```

---

### Post by xavi787 on 2011-07-23
bump... still no answer

---

### Post by Jamesi on 2011-07-24
I think that, you should always have windows and ubuntu or whatever you use. Just keep windows to play games. ubuntu/linux is not really good at Windows games, its a shame really because its a really good OS. in my eyes.

---

### Post by ubudog on 2011-08-01
Have you tried FlightGear?  It's free and open-source, and the graphics are pretty good.

In-game image:
[http://images.pbidir.com/screenshots/flightgear5.jpg](http://images.pbidir.com/screenshots/flightgear5.jpg)

You can get it using apt, or building from source.

Project homepage is here:
[http://flightgear.org](http://flightgear.org)

---------------------------
FSX: Have you tried using PlayOnLinux to install FSX?

---

### Post by CivilizationII on 2012-02-20
FlightGear native Linux is covered by Ubuntu repositories, i recommend this over wine, especially if the wine release is buggy.

---

