---
title: "can't mount/install IDE HD"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by huckleberrymopo3 on 2008-10-06
My BIOS can recognize the hard drive, but I can't find it in Hardy. 

sudo fdisk -l

output:
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0464cbb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3106

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       59322   476503933+  83  Linux
/dev/sdb2           59323       60801    11880067+   5  Extended
/dev/sdb5           59323       60801    11880036   82  Linux swap / Solaris


It sees my sata drives 500GB and 320GB, however my IDE is 300GB

any ideas are appreciated.

---

### Post by Ocxic on 2008-10-06
make sure that your IDE bus is enable in your bios, If it's disabled you BIOS will still detect the drive but not allow any access to it.

---

### Post by Yellow Pasque on 2008-10-06
perhaps a little more info would be helpful. Do you know what kind of motherboard you have? What kind of PATA controller? Use lshw to make sure a driver is loaded.
```
sudo lshw -C storage
```

---

### Post by huckleberrymopo3 on 2008-10-07
sudo lshw -C storage
Output: 
*-ide                   
       description: IDE interface
       product: JMB368 IDE controller
       vendor: JMicron Technologies, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm pciexpress bus_master cap_list
       configuration: driver=pata_jmicron latency=0 module=pata_jmicron
  *-ide:0
       description: IDE interface
       product: 82801IB (ICH9) 2 port SATA IDE Controller
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       logical name: scsi2
       logical name: scsi3
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=ata_piix latency=0 module=ata_piix
  *-ide:1
       description: IDE interface
       product: 82801I (ICH9 Family) 2 port SATA IDE Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list
       configuration: driver=ata_piix latency=0 module=ata_piix

---

### Post by huckleberrymopo3 on 2008-10-09
The jumper on my CD-Rom was set to master. I had a power supply problem not to long ago and I took it to Frys to replace it, they must have set the jumper to master, only god would know why?

Thanks for everyones help.

---

