---
title: "no sound 9.10 64amd studio"
date: 2009-11-08
forum: x86 64-bit Users
---

### Post by ken78724 on 2009-11-08
tickled to see Ubuntu Studio 9.10 Karmic Koala but am with no sound. 

have toggled and followed Markbuntu's guide for Ubuntu Studio, including guide for updating. Says "You have the latest sudo get required" Cannot figure out next step. 

Am open to any guidance put forth. Any help would be appreciated. 
 
kenneth


Am finally back here tonight 12-13-09 at 12:45 AM with the same problem and found your help below but I cannot do a reply to your wonderful message Thanks Sin@Sin-Sacrifice! Below here is my response:
k78724@Kproductions:~$ aplay -l

aplay: device_list:223: no soundcards found...

k78724@Kproductions:~$ lspci -v

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)

	Subsystem: ASUSTeK Computer Inc. Device 817a

	Flags: bus master, fast devsel, latency 0

	Capabilities: <access denied>

	Kernel driver in use: agpgart-intel

	Kernel modules: intel-agp



00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

	Subsystem: ASUSTeK Computer Inc. Device 817a

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at dfe00000 (32-bit, non-prefetchable) [size=512K]

	I/O ports at 8800 [size=8]

	Memory at e0000000 (32-bit, prefetchable) [size=256M]

	Memory at dfe80000 (32-bit, non-prefetchable) [size=256K]

	Capabilities: <access denied>

	Kernel driver in use: i915

	Kernel modules: i915



00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

	Subsystem: ASUSTeK Computer Inc. Device 8249

	Flags: bus master, fast devsel, latency 0, IRQ 19

	Memory at dfef8000 (64-bit, non-prefetchable) [size=16K]

	Capabilities: <access denied>

	Kernel driver in use: oss_hdaudio

	Kernel modules: snd-hda-intel



00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0

	I/O behind bridge: 0000e000-0000efff

	Capabilities: <access denied>

	Kernel driver in use: pcieport-driver

	Kernel modules: shpchp



00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0

	I/O behind bridge: 0000d000-0000dfff

	Memory behind bridge: dff00000-dfffffff

	Capabilities: <access denied>

	Kernel driver in use: pcieport-driver

	Kernel modules: shpchp



00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)

	Subsystem: ASUSTeK Computer Inc. Device 8179

	Flags: bus master, medium devsel, latency 0, IRQ 20

	I/O ports at 9000 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)

	Subsystem: ASUSTeK Computer Inc. Device 8179

	Flags: bus master, medium devsel, latency 0, IRQ 17

	I/O ports at 9400 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)

	Subsystem: ASUSTeK Computer Inc. Device 8179

	Flags: bus master, medium devsel, latency 0, IRQ 18

	I/O ports at 9800 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)

	Subsystem: ASUSTeK Computer Inc. Device 8179

	Flags: bus master, medium devsel, latency 0, IRQ 19

	I/O ports at a000 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)

	Subsystem: ASUSTeK Computer Inc. Device 8179

	Flags: bus master, medium devsel, latency 0, IRQ 20

	Memory at dfeffc00 (32-bit, non-prefetchable) [size=1K]

	Capabilities: <access denied>

	Kernel driver in use: ehci_hcd



00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32

	I/O behind bridge: 0000c000-0000cfff

	Capabilities: <access denied>



00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)

	Subsystem: ASUSTeK Computer Inc. Device 8179

	Flags: bus master, medium devsel, latency 0

	Capabilities: <access denied>

	Kernel modules: iTCO_wdt, intel-rng



00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])

	Subsystem: ASUSTeK Computer Inc. Device 8179

	Flags: bus master, medium devsel, latency 0, IRQ 22

	I/O ports at 01f0 [size=8]

	I/O ports at 03f4 [size=1]

	I/O ports at 0170 [size=8]

	I/O ports at 0374 [size=1]

	I/O ports at ffa0 [size=16]

	Kernel driver in use: ata_piix



00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])

	Subsystem: ASUSTeK Computer Inc. Device 2601

	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 23

	I/O ports at b800 [size=8]

	I/O ports at b400 [size=4]

	I/O ports at b000 [size=8]

	I/O ports at a800 [size=4]

	I/O ports at a400 [size=16]

	Capabilities: <access denied>

	Kernel driver in use: ata_piix



00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)

	Subsystem: ASUSTeK Computer Inc. Device 8179

	Flags: medium devsel, IRQ 10

	I/O ports at 0400 [size=32]

	Kernel modules: i2c-i801



01:00.0 Communication controller: Agere Systems Lucent V.92 Data/Fax Modem

	Subsystem: Agere Systems Lucent V.92 Data/Fax Modem

	Flags: bus master, medium devsel, latency 64, IRQ 10

	I/O ports at c800 [size=256]

	Capabilities: <access denied>



02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

	Subsystem: ASUSTeK Computer Inc. Device 8233

	Flags: bus master, fast devsel, latency 0, IRQ 26

	Memory at dffc0000 (64-bit, non-prefetchable) [size=256K]

	Expansion ROM at dffa0000 [disabled] [size=128K]

	Capabilities: <access denied>

	Kernel driver in use: atl2

	Kernel modules: atl2

k78724@Kproductions:~$
Many thanks Sin@Sin-Sacrifice. So far I have not learned how to proceed to Step 3 found in the guide you built. The response to step 2 is more than I can decipher at the moment.Will rest and see what it says and try to get back to this once the Forum Administrator decides we are big kids and allowed to work together as such.

---

### Post by Sin@Sin-Sacrifice on 2009-11-09
This [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) might help. As might this [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683). Hope it does.

---

