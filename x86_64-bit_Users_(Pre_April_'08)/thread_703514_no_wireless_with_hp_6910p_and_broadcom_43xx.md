---
title: "no wireless with hp 6910p and broadcom 43xx"
date: 2008-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by brunoscunha on 2008-02-21
I have a hp-compaq laptop 6910p, a Core 2 duo. Their are a couple things not working properly after install.
The wireless driver does not work, it's a Broadcom 43xx chipset family. Whenever i try to scan for wireless networks the gnome network manager crashes with or without the restricted driver installed.
If I go to manual configuration no wireless network shows up. How can solve this?

```
bruno@bruno-laptop:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at e4400000 (64-bit, non-prefetchable) [size=1M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 4000 [size=8]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, fast devsel, latency 0
        Memory at e4500000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: [d0] Power Management version 3

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at e4600000 (32-bit, non-prefetchable) [size=128K]
        Memory at e4620000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 4020 [size=32]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 4040 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 4060 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at e4621000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at e4624000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
        Capabilities: [40] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30be
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
        Memory behind bridge: e4000000-e40fffff
        Capabilities: [40] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30be
        Capabilities: [a0] Power Management version 2

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=28, subordinate=28, sec-latency=0
        I/O behind bridge: 00002000-00003fff
        Memory behind bridge: e0000000-e3ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30be
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 4080 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 40a0 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 40c0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at e4628000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=07, sec-latency=32
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: e4100000-e43fffff
        Prefetchable memory behind bridge: 0000000070000000-0000000077ffffff
        Capabilities: [50] Subsystem: Hewlett-Packard Company Unknown device 30be

00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 40e0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
        I/O ports at 13f0 [size=8]
        I/O ports at 15f4 [size=4]
        I/O ports at 1370 [size=8]
        I/O ports at 1574 [size=4]
        I/O ports at 4120 [size=32]
        Memory at e4629000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable-
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] #12 [0010]

02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at e4100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=03, sec-latency=176
        Memory window 0: 70000000-73fff000 (prefetchable)
        Memory window 1: 78000000-7bfff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 168, IRQ 19
        Memory at e4101000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=04, subordinate=07, sec-latency=176
        Memory window 0: 74000000-77fff000 (prefetchable)
        Memory window 1: 7c000000-7ffff000
        I/O window 0: 00005800-000058ff
        I/O window 1: 00005c00-00005cff
        16-bit legacy interface ports at 0001

02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at e4102000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

02:06.3 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at e4103000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 30be
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at e4104000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

10:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1371
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at e4000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0

bruno@bruno-laptop:~$ 
```

thanks

---

### Post by brunoscunha on 2008-02-22
Please anyone. I tried several tips in this forum and none have worked so far. I also don't want to mess up my wired connection, it's the only way I have to connect to lan/internet.

Thanks in advanced

---

### Post by ferdostar on 2008-02-22
Check this:[http://ohioloco.ubuntuforums.org/showthread.php?t=600097](http://ohioloco.ubuntuforums.org/showthread.php?t=600097) than this
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)
and this [https://answers.launchpad.net/ubuntu/+question/16646](https://answers.launchpad.net/ubuntu/+question/16646)
Post if you have your issue, hope will help you ;)

---

### Post by brunoscunha on 2008-02-22
Well something has changed. When i'll get home i'll try to connect to my wireless router. Thanks so much for your help

---

### Post by brunoscunha on 2008-02-22
Do i have to enable the restrited driver ?

---

### Post by ferdostar on 2008-02-22
> **brunoscunha said:**
> Do i have to enable the restrited driver ?

Normally it isn't necessary if you have you connection working. You can check it by ```
iwconfig
```

---

### Post by brunoscunha on 2008-02-22
the output of was this iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I find this strange because at first it said i had a 4312 now it says its a 4311. LOL I'm getting confused

---

### Post by ferdostar on 2008-02-22
> **brunoscunha said:**
> the output of was this iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I find this strange because at first it said i had a 4312 now it says its a 4311. LOL I'm getting confused

4311  	PCI-E  	Supported for kernel 2.6.20.6 and later
4312 	PCI-E 	802.11b/g supported for kernel 2.6.20 and later (802.11a unsupported, work in progress) ;)

---

### Post by brunoscunha on 2008-02-22
So in theory it should work because the kernel I have is the 2.6.22-14-generic x86_64.
And now when I try to connect to other wireless networks, the gnome network manager crashes (the network icon on the top bar disapears, I presume it has crashed)
:(

---

### Post by ferdostar on 2008-02-22
> **brunoscunha said:**
> So in theory it should work because the kernel I have is the 2.6.22-14-generic x86_64.
And now when I try to connect to other wireless networks, the gnome network manager crashes (the network icon on the top bar disapears, I presume it has crashed)
:(

In fact you need to install patches for 2.6.24 [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by brunoscunha on 2008-02-22
Do you mean this?

```
 Driver
	

              Kernel                                              Firmware                                                                                             Firmware extractor                          Instructions
	
  
b43                                      Linux-2.6.24, including 2.6.24-rcX and 2.6.24.Y                                                                  4.80.53.0                             b43-fwcutter v. 011

	 
b43                                    Bleeding edge, i.e. compat-wireless-2.6 package, linus-2.6 or wireless-2.6 trees                   4.150.10.5                            b43-fwcutter v. 011  

	
b43legacy                                            Any                                                                                                                3.130.20.0                             b43-fwcutter v. 011 


bcm43xx (deprecated)                          Any                                                                                                                 3.130.20.0                             bcm43xx-fwcutter v. 6
```

---

### Post by brunoscunha on 2008-02-25
I just need to know that, because i'm not sure what to download and don't want to mess things up in my laptop.

---

