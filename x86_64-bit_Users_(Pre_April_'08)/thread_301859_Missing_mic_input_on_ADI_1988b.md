---
title: "Missing mic input on ADI 1988b"
date: 2006-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jonas84 on 2006-11-17
I have a problem getting the mic of the sound card (integrated) to work. The output is working, at least the front channel (with Mplayer or xmms etc). There are two possibilities on the volume control window. 
Either:
-Hda Nvidia(Alsa)
-Analog Devices AD1988B (OSS mixer)

The volume levels have no affect and neither the muting. 
Is it that the hardware is to new and the "driver" doesn't understand what its trying to tell it?
I have also a couple of unknown devices, but the rest of the computer is working fine. Got the graphics card working properly after installing the new nvidia beta driver.

this is what i get if i run sudo lspci -v in a terminal

00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] #00 [fee0]

00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at fc00 [size=64]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: [44] Power Management version 2

00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: [44] Power Management version 2

00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at dc00 [size=16]
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at c800 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        I/O ports at c400 [size=8]
        I/O ports at c000 [size=4]
        I/O ports at bc00 [size=8]
        I/O ports at b800 [size=4]
        I/O ports at b400 [size=16]
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:06.0 PCI bridge: nVidia Corporation Unknown device 0370 (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Capabilities: [b8] #0d [0000]
        Capabilities: [8c] HyperTransport: MSI Mapping

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81f6
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b000 [size=8]
        Memory at fe029000 (32-bit, non-prefetchable) [size=256]
        Memory at fe028000 (32-bit, non-prefetchable) [size=16]
        Capabilities: [44] Power Management version 2
        Capabilities: [70] MSI-X: Enable+ Mask- TabSize=8
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/3 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:0a.0 PCI bridge: nVidia Corporation Unknown device 0376 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:0b.0 PCI bridge: nVidia Corporation Unknown device 0374 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:0c.0 PCI bridge: nVidia Corporation Unknown device 0374 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:0d.0 PCI bridge: nVidia Corporation Unknown device 0378 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:0e.0 PCI bridge: nVidia Corporation Unknown device 0375 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:0f.0 PCI bridge: nVidia Corporation Unknown device 0377 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fa000000-fcffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000eff00000
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

07:00.0 VGA compatible controller: nVidia Corporation Unknown device 0391 (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81f7
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at ac00 [size=128]
        [virtual] Expansion ROM at fcfe0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [128] Power Budgeting

Any good ideas,I'm out if them anyhow. I'll be happy to provide additional data if required. 

With thanks in advance. Jonas

---

### Post by Jonas84 on 2006-12-05
Duh ](*,) ,I found the fault. A volume named Analog Mix in Alsa (HDA NVidia) was muted and therefore no input from mic. The sound card was probably installed correctly by Edgy all from the start. 

Also flashed the bios, Apic issue fixed :) .

---

### Post by mervmitch on 2008-01-16
Thanks - I have checked again - Microphone (and everything else as well) is not muted.
This was muted in Mandrake2008 One.
NB I now get a very loud white noise when I test for input using AD198Analog - Is this an improvement ? The mike still does not work though

---

### Post by mervmitch on 2008-01-16
An Interim Update
I have enabled Line In and AD198 and changed my Input Source to Line In in the Alsa Control panel- NB my microphone is still in the microphone jack socket which works correctly for other OS - and I now have a usable microphone BUT it does not respond to any microphone controls ONLY to Line in control - This is livable but ....
I will advise if it does NOT work on re-boot or cold boot. Tomorrow Thursday 17th Jan
Also I have to check whether I can record or just kareoke.

---

### Post by Yellow Pasque on 2008-01-16
If your mic input isn't working, try adding "options snd-hda-intel model=3stack"  into the /etc/modprobe.d/alsa-base file.

Also try the same thing with model=laptop.

Source: [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

