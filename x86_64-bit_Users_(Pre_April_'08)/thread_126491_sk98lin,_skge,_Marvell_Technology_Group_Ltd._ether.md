---
title: "sk98lin, skge, Marvell Technology Group Ltd. ethernet"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by coredump25 on 2006-02-06
Hi,

I compiled a vanilla kernel 2.6.15.2 using the configuration
from 2.6.12-10-amd64-k8-smp with one change, namely
I compiled usbcore as a module.

Now sk98lin is not detecting my ethernet card.  The module
is loaded, but not ethernet is showing up in /sys/class/net.

I also tried the new module, skge, with no luck.

Here is my lspci output:

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4362 (rev 19)
        Subsystem: Giga-byte Technology: Unknown device e000
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR-
        Latency: 0, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at f3000000 (64-bit, non-prefetchable) [size=16K]
        Region 2: I/O ports at a000 [size=256]
        Expansion ROM at f4200000 [disabled] [size=128K]
        Capabilities: <available only to root>

Any help is appreciated.

Thanks.

---

### Post by Clefferson on 2006-03-28
Well, I think You should recompile the Kernel with a little change on the .config file under this section:

#
# Ethernet (1000 Mbit)
#
...
CONFIG_SKGE=y
# CONFIG_SKY2_EC_A1 is not set
CONFIG_SK98LIN=y
# CONFIG_SK98LIN_NAPI is not set
...

Anyway... You'll pehaps have a skge bogus sensor interrupt during boot time....
So I Suggest You to patch the skge module before recompiling, using this Diff file: [http://bugs.gentoo.org/attachment.cgi?bugid=87182&action=viewall]("http://bugs.gentoo.org/attachment.cgi?bugid=87182&action=viewall")

---

