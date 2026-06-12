---
title: "No Sound / Static"
date: 2009-04-01
forum: x86 64-bit Users
---

### Post by kehon on 2009-04-01
i just installed wine the other day since then i have installed a few apps like eclipse,vuze, etc but now wine wont load at all and besides that(in another topic) my sound stopped working on my compaq presario c700 i've never had a problem with the sound before but i'm new to linux altogether can someone help me with the sound because i got wine fixed while fixing another error

this is from another post and i was told to seperate it and run lspci -v

```
lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91000000 (64-bit, non-prefetchable) [size=1M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 30d0 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, fast devsel, latency 0
	Memory at 91100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Conexant Systems, Inc. Device 5051
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 92400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 91300000-923fffff
	Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 3080 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 3060 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 3040 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 92404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 91200000-912fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 30a0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: pata_acpi, ata_piix, ata_generic

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2302
	I/O ports at 30b8 [size=8]
	I/O ports at 30dc [size=4]
	I/O ports at 30b0 [size=8]
	I/O ports at 30d8 [size=4]
	I/O ports at 3020 [size=32]
	Memory at 92404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: medium devsel, IRQ 11
	Memory at 92404c00 (32-bit, non-prefetchable) [size=256]
	I/O ports at 3000 [size=32]
	Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k, ath_pci

02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at 1000 [size=256]
	Memory at 91200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too

```

---

### Post by Korcia on 2009-04-01
I met the same problem and after trying several configurations I selected ALSA in Sound Capture (Preferences -> Sound) and in Wine (Applications -> Wine -> Configure Wine and select Audio tab) I selected just OSS Driver. Now everything works fine.

---

### Post by Lunx on 2009-04-01
Not sure this will help, but I had problems with sound and static myself. Using HDA Intel (Asla mixer) and it turns out it was the PCM setting being turned down to nothing (but still activated, not muted). If you are using same, you can right click on your volume button in top panel and open volume control and then check what the PCM setting is. 

As I said, no idea if this will solve it, but it's something to investigate anyway

---

### Post by kehon on 2009-04-01
cool thanks so much that fixed it the preferences thing by right clicking on my volume control button and it turns out that PCM was muted i put it on max and now my sound works thanks so much man that was simple just right click volume control

---

### Post by Lunx on 2009-04-01
> **kehon said:**
> cool thanks so much that fixed it the preferences thing by right clicking on my volume control button and it turns out that PCM was muted i put it on max and now my sound works thanks so much man that was simple just right click volume control

Glad that was it, took me a bit to figure it out myself when the problem happened here

---

### Post by dowell_p on 2009-04-13
Thanks! My PCM was all the way down but not muted. Dont know how it happened, but the fix worked.

---

### Post by Clancy_s on 2009-04-14
The sound down / muted on reboot is a know intrepid (intermittent) bug, apparently fixed in jaunty.

---

### Post by radostyle on 2009-07-29
I also had this problem on Jaunty.

---

### Post by go_beep_yourself on 2009-08-05
> **Lunx said:**
> Not sure this will help, but I had problems with sound and static myself. Using HDA Intel (Asla mixer) and it turns out it was the PCM setting being turned down to nothing (but still activated, not muted). If you are using same, you can right click on your volume button in top panel and open volume control and then check what the PCM setting is. 

As I said, no idea if this will solve it, but it's something to investigate anyway

YOU SAVED MY LIFE AND MY SOUND IN LINUX!!!!!!!!!! TIME TO PARTY! :popcorn:

THANKS ALOT!

---

### Post by Zenguy on 2009-09-07
Thanks for the PCM level tip. My sound's been messed up for quite a while and this fixed it in an instant!

---

### Post by pablolie on 2009-09-14
all i have is a PCM switch under preferences - no level setting.

i am also stuck with no sound on a 9.04 64 bith install (standard asus p5q em mobo)...

---

