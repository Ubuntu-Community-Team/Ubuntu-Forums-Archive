---
title: "I/O Buffer error with MSI K8n Neo4 Platinum/SLI"
date: 2005-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by queuetue on 2005-04-16
I have a brand new K8n Neo4 Platinum/SLI with an Athlon 3500, and a pair of IDE disks.  (This problem occurs with or without the second disk attached)

Install worked fine, and the machine is fine booting from a DSL (32-bit Damn small linux) disk I happen to have around, but if I boot into Ubuntu, I get 

Booting the kernel.
PCI: Cannot allocate resource region 0 of device 0000:02:00.0
PCI: Cannot allocate resource region 0 of device 0000:03:00.0
PCI: Cannot allocate resource region 2 of device 0000:03:00.0
PCI: Cannot allocate resource region 3 of device 0000:05:00.0
Audit(1072984235.238:0): initialized
Starting Ubuntu...
Buffer I/O error on device hda, logical block 0
pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel panic - not syncing: Attemted to kill init!

And there it locks until I hit the reset switch.

I've tried apci=no, I've checked other IDE disks (same behavior), and I have no SATA disks to test with.

---

### Post by FluffyElmo on 2005-04-19
Just a shot in the dark, but have you tried disabling your onboard RAID controller? 

From DSL you should also try to fsck and see if you can mount hda. I had the same kernel panic as you and solved it by chroot into the ubuntu partition and upgrading my kernel. I didn't have the I/O errors though so that is new to me.

---

