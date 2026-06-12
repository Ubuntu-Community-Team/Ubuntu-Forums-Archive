---
title: "Linksys Gigabit Etherfast + r8169 (8.04.1 Server)"
date: 2009-01-14
forum: x86 64-bit Users
---

### Post by Treth on 2009-01-14
Ok, so, this has me rather stumped.  I gave the gift of open source to a friend of mine who wanted a good home network.  So now, we have 3.5TB of storage in a dual-core Opteron setup with Hardy server.

We just got done wiring the house for Gigabit, so I picked up a Linksys Etherfast Gigabit card, figuring they're all the same, since it's just a board with a Realtek chip on it.  I installed the board, and booted up the machine.

But alas, the gigabit card does not work!  I can query it, bring the link up, and run dhclient on it, but it never receives an IP address.  Manual configuration likewise reports success, but no packets ever reach their destination.  I'm SSHing into the server over its 10/100 link, and both cards are connected into the gigabit switch, because I'm not onsite.

Here's all the relevant information . . .

Kernel Parameters:  pci=nomsi
uname -r:  2.6.24-22-server

lspci output:
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 SATA controller: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 70)
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)
02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
05:0b.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)
```

Any ideas, or further requests for information, guys?  Thanks in advance!

~Treth

---

