---
title: "Hardy Heron amd64 install in VirtualBox problem"
date: 2009-03-30
forum: x86 64-bit Users
---

### Post by corkscrew on 2009-03-30
I am running Hardy Heron 8.4.2 amd 64

VirtualBox version 2.1.4 for amd64 cpu ( installed by downloading deb from vb web site and double clicking file)

I am trying to in install Hardy Heron 8.4.2 amd 64 on a virtual machine. Every time I try and install I get the following message

> This kernel requires an x86-64 CPU, but only detected an i1586 CPU. Unable to boot - please use kernel appropriate for your CPU.

I have virtulization enabled in the bios. I have enabled in advanced settings, ACPI, IO APIC, VT-x/AMD-V.

my machine is
Asus M3N78 M/B
AMD AM2 7750 Athlon 64 x2 Duel Core Socket AM2+
4 GB Crucial DDR2 (PC2-6400 CL 6) ram 

2 x Serial ATA hdd

Asus 8800GS 384MB PCI-E Graphics card

---

### Post by sebastianabate on 2009-03-30
Have you selected the "Ubuntu (64 bits)" option in the Basic Tab of the General Settings? Because the other day I had the same problem with a Windows 2008 64 bits guest, and until I especifically select the "(64 bits)" option on that tab, the VM can not boot. After setting this option everything goes well.

PD: Sorry for my english.

---

### Post by corkscrew on 2009-03-31
yes made that selection any other ideas?

---

