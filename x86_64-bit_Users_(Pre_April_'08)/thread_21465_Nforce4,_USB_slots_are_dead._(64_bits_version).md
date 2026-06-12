---
title: "Nforce4, USB slots are dead. (64 bits version)"
date: 2005-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kell on 2005-03-22
I got hoary-preview-live amd64 hardware detection looks good, but i cant use my USB devices (including mouse). I think USB slots are not on becouse mouse led is off.
I have this PC.
Gigabyte GA-K8NXP-SLI.
AMD64 NEWCASTLE.
GF-6600-GT.
Any idea?
Thnx.

---

### Post by IdoMcFly on 2005-03-22
[QUOTE=Kell]I got hoary-preview-live amd64 hardware detection looks good, but i cant use my USB devices (including mouse). I think USB slots are not on becouse mouse led is off.
I have this PC.
Gigabyte GA-K8NXP-SLI.
AMD64 NEWCASTLE.
GF-6600-GT.
Any idea?
Thnx.[/QUOTE]
 there is a bug in kernel 2.6.10-x with x < 5 as you run a live CD the kernel is not the current one. 

USB2 is not supported : workaround with the liveCD : disable USB2 in the BIOS.

current kernel fixed the bug though.

---

### Post by Cannon on 2005-03-24
[QUOTE=Kell]I got hoary-preview-live amd64 hardware detection looks good, but i cant use my USB devices (including mouse). I think USB slots are not on becouse mouse led is off.
I have this PC.
Gigabyte GA-K8NXP-SLI.
AMD64 NEWCASTLE.
GF-6600-GT.
Any idea?
Thnx.[/QUOTE]
Another workaround, remove the ehci_hcd module and you will get your mouse work.

---

