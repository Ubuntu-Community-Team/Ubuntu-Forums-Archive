---
title: "help regarding mythtv"
date: 2009-03-16
forum: x86 64-bit Users
---

### Post by gowthamchowdary007 on 2009-03-16
please help me in installing  tv for my ubuntu amd64,
i am using intex pci tv tuner card, on googling i came to know mythtv is the best so tried to installed mythtv but??? an error:
 [COLOR="Blue"]mythtv: Depends: mythtv-backend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1) but it is not going to be installed
          Depends: mythtv-frontend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1) but it is not going to be installed
E: Broken packages[/COLOR]

and also help me out on how to install the drivers for that card


please help me out thank you****

---

### Post by kingtaurus on 2009-03-16
Have you enabled the universe ubuntu repositories? See, [http://www.mythbuntu.org/existing-ubuntu]("http://www.mythbuntu.org/existing-ubuntu")

I've never used the cards, but can you please attach ```
sudo lspci -v
``` to your reply.

---

### Post by philinux on 2009-03-16
> **gowthamchowdary007 said:**
> please help me in installing  tv for my ubuntu amd64,
i am using intex pci tv tuner card, on googling i came to know mythtv is the best so tried to installed mythtv but??? an error:
 [COLOR="Blue"]mythtv: Depends: mythtv-backend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1) but it is not going to be installed
          Depends: mythtv-frontend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1) but it is not going to be installed
E: Broken packages[/COLOR]

and also help me out on how to install the drivers for that card


please help me out thank you****

Mythtv is in ubuntu's repos. Multiverse&universe. Should not have dependency problems if you install from synaptic.

---

### Post by gowthamchowdary007 on 2009-03-16
[COLOR="Blue"]code for sudo lspci -v[/COLOR]

 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Giga-byte Technology Device 5000
	Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdffffff
	Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [b0] Subsystem: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
	I/O ports at ff00 [size=8]
	I/O ports at fe00 [size=4]
	I/O ports at fd00 [size=8]
	I/O ports at fc00 [size=4]
	I/O ports at fb00 [size=16]
	Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] SATA HBA <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
	Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
	Subsystem: Giga-byte Technology Device 4385
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Memory at d0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device 5002
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f900 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp, ata_generic, pata_acpi

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Giga-byte Technology Device 5001
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
	Subsystem: Giga-byte Technology Device d000
	Flags: bus master, fast devsel, latency 32, IRQ 18
	Memory at d8000000 (64-bit, prefetchable) [size=128M]
	Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at ee00 [size=256]
	Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 2
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

02:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
	Subsystem: Philips Semiconductors Device 0000
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at fddff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [40] Power Management version 1
	Kernel driver in use: saa7134
	Kernel modules: saa7134

02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
	I/O ports at de00 [size=256]
	Memory at fddfe000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: r8169
	Kernel modules: r8169

---

### Post by kingtaurus on 2009-03-16
> 
02:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
Subsystem: Philips Semiconductors Device 0000
Flags: bus master, medium devsel, latency 32, IRQ 20
Memory at fddff000 (32-bit, non-prefetchable) [size=1K]
Capabilities: [40] Power Management version 1
Kernel driver in use: saa7134
Kernel modules: saa7134

It looks like this is the device. Further, it looks like the kernel driver (saa7134) is enabled. So I think all you need to do, is get mythtv backend up and running (and using mythtv-setup (IIRC) you should be able to configure video capture).

---

### Post by gowthamchowdary007 on 2009-03-16
when i tried  to install mythtv 
[COLOR="Blue"]sudo apt-get install mythtv[/COLOR]
this error showed up

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-backend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1) but it is not going to be installed
          Depends: mythtv-frontend (= 0.21.0+fixes20205-0ubuntu0+mythbuntu1) but it is not going to be installed
E: Broken packages


what should i do now to slove this,
i tried even using synaptic package manager
but this error showed up

[COLOR="Blue"]mythtv:
 Depends: mythtv-backend but it is not going to be installed
 Depends: mythtv-frontend but it is not going to be installed[/COLOR]

please help me out

---

### Post by gowthamchowdary007 on 2009-03-17
Please help me out .. for this prob!! i am looking out for help..

Thank you

---

### Post by GoldenBunip on 2009-03-17
Hi, 
I highly recommend removing all packages relating to MythTV, then go to the very easy guide located here 

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

Follow his instructions step by step, DO NOT BE TEMPTED TO CHANGE ANYTHING ELSE AT ALL ON ANY MENU WHATSOEVER as I did that and have messed it up so many times. 

Just follow each instruction one at a time and you should be ok. If not the guide tells you how to get the logs at the end.

---

### Post by jMon54 on 2009-03-17
Why not just install MythBuntu?  What am I missing?

---

### Post by ameyer on 2009-03-18
> **GoldenBunip said:**
> Hi, 
I highly recommend removing all packages relating to MythTV, then go to the very easy guide located here 

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

That guide won't work since the "apt-get install mythtv" step won't work on Jaunty AMD64 since mythtv-common apparently failed to build on AMD64 due to the transition to python 2.6.

[https://bugs.launchpad.net/mythbuntu/+bug/343672/comments/1](https://bugs.launchpad.net/mythbuntu/+bug/343672/comments/1)

---

