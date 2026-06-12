---
title: "[corrected] Slow internet speed in Sony Vaio using Intel Pro 5100"
date: 2008-12-31
forum: x86 64-bit Users
---

### Post by pravlm on 2008-12-31
Hi Everybody,

Just came out of graphics problem in Sony Vaio FW.

Now itw wireless card turn -

Its able to connect to my Wireless Modem but the speed is too slow and I am trying to find the MTU of TCP/IP but I am unable to find it, the speed is terribly slow just around 3 Kbps.

As suggested here,
[ Optimize the internet speed ]("http://ubuntuforums.org/showthread.php?t=872346")

It command throws the following error but I can ping like ping google.com, 
```

$ ping -s 1474 -cl google.com
Error: bad number of packets.

```

The Wireless hardware I have is Inter PRO Wireless 5100 
here is the output of lspci 
```

$ lspci -v


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 6140 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, fast devsel, latency 0
	Memory at d0400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 60e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 60c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at d5604c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d5600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d4100000-d54fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d2d00000-d40fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d1900000-d2cfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=08, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0500000-d18fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 60a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 6080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 6060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 6040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d5604800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
	Memory behind bridge: d5500000-d55fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2299
	I/O ports at 6130 [size=8]
	I/O ports at 6120 [size=4]
	I/O ports at 6110 [size=8]
	I/O ports at 6100 [size=4]
	I/O ports at 6020 [size=32]
	Memory at d5604000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Sony Corporation Device 9035
	Flags: medium devsel, IRQ 5
	Memory at d5605000 (64-bit, non-prefetchable) [disabled] [size=256]
	I/O ports at 6000 [size=32]
	Kernel modules: i2c-i801

05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Subsystem: Intel Corporation Device 1301
	Flags: bus master, fast devsel, latency 0, IRQ 2297
	Memory at d1900000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	Memory at d0520000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Expansion ROM at d0500000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

09:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at d5500000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

09:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at d5500900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

09:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Sony Corporation Device 9035
	Flags: bus master, medium devsel, latency 32, IRQ 4
	Memory at d5500800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>


```

Do I need to upgrade my driver , any suggestion is appreciated please help.

---

### Post by dcstar on 2009-01-01
> **pravlm said:**
> 
........
As suggested here,
[ Optimize the internet speed ]("http://ubuntuforums.org/showthread.php?t=872346")

It command throws the following error but I can ping like ping google.com, 
```

$ ping -s 1474 **-cl** google.com
Error: bad number of packets.

```

........

It is not "-cl" it is "-c1", as it shows in the link.

The command **ifconfig** will show you the Linux MTU, but other network equipment in your system may have a different MTU and fragment packets anyway.

As an example, the maximum packet size I can send with that command is 1468 bytes and my MTUs are set to 1500.

---

