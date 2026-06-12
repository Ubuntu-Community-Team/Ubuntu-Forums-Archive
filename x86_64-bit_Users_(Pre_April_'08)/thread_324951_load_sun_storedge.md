---
title: "load sun storedge"
date: 2006-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by ahissi on 2006-12-24
Hello,

I've installed ubuntu 6.10 on a sunfire X4100 which is connected to a sun storedge 320 (configured in raid 5 -- logical disk 2,8 TO).

I need to configure the storedge in lvm
during the installation ubuntu list only the diks on the X4100 but not the storedge disk.

after the installation,  fdisk -l did not display the logical drive

$sudo fdisk -l


Disk /dev/sda: 73.4 GB, 73407865856 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13        1957    15623212+  82  Linux swap / Solaris
/dev/sda3            1958        8924    55962427+   5  Extended
/dev/sda5            1958        8924    55962396   83  Linux

Disk /dev/sdb: 73.4 GB, 73407865856 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8924    71681998+  83  Linux



but lspci display the logical drive

$ sudo lspci -v


06:01.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 08)
        Subsystem: LSI Logic / Symbios Logic Unknown device 5110
        Flags: bus master, 66MHz, medium devsel, latency 72, IRQ 177
        I/O ports at c800 [size=256]
        Memory at fe8e0000 (64-bit, non-prefetchable) [size=128K]
        Memory at fe8c0000 (64-bit, non-prefetchable) [size=128K]
        Expansion ROM at fe400000 [disabled] [size=4M]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [68] PCI-X non-bridge device


thinks for any help!

---

### Post by gtoo-dtux on 2007-11-05
Hi - may I ask you how you installed 6.10 on the Sunfire x4100? I am very keen on installing the new Gutsy (either the x86 or AMD version of the server software).  I know that there is a problem booting a Linux install disk from the CD drive.

Also did you sort out the issue regarding the Storedge drives?

Thanks

---

