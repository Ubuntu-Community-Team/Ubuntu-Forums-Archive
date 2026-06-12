---
title: "Slow data transfer"
date: 2008-08-10
forum: x86 64-bit Users
---

### Post by underground on 2008-08-10
Hello!!!
My problem is that the data transfer speed is extremely slow...
I copy from dvd to sata hard disk with 10-12mb/sec
From sata to sata (partitions of the same hard disk) the speed is 20-25mb/sec
From sata to ide the speed is 30-35mb/sec

What is going wrong and i have such speeds??
Tell me if you need any hardware info..

---

### Post by underground on 2008-08-12
Can't anyone help me?

---

### Post by lisati on 2008-08-12
I'm not an expert, but I'm wondering if something to do with DMA settings is coming into play. Unfortunately I have no idea of how to check it.

---

### Post by underground on 2008-08-12
Me too..i don't know what to check and how...

---

### Post by underground on 2008-08-12
Problem about low data transfer speed remains...now i am on ubuntu hardy 64 bit
In boot i have the following kernel parametres:
all_generic_ide
floppy=off
irqpoll
pci=nomsi
Without these options i cant boot to ubuntu
Here are the results of various commands

dmesg | grep -i dma
```
hunter@hunter-desktop:~$ dmesg | grep -i dma
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1220 pages reserved
[    0.000000]   DMA zone: 2723 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7110 pages used for memmap
[    0.000000]   DMA32 zone: 513002 pages, LIFO batch:31
[    0.000000] Policy zone: DMA32
[   31.089185] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   31.089187] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   31.414584] ata1.00: ATA-6: WDC WD3200JB-00KFA0, 08.05J08, max UDMA/100
[   31.414600] ata1.01: ATAPI: PIONEER DVD-RW  DVR-112D, 1.24, max UDMA/66
[   31.414608] ata1.00: configured for UDMA/100
[   31.414609] ata1.01: configured for UDMA/66
[   32.827772] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   33.830352] ata3: SATA max UDMA/133 abar m1024@0xfbcffc00 port 0xfbcffd00 irq 21
[   33.830355] ata4: SATA max UDMA/133 abar m1024@0xfbcffc00 port 0xfbcffd80 irq 21
[   33.830358] ata5: SATA max UDMA/133 abar m1024@0xfbcffc00 port 0xfbcffe00 irq 21
[   33.830360] ata6: SATA max UDMA/133 abar m1024@0xfbcffc00 port 0xfbcffe80 irq 21
[   34.328972] ata3.00: ATA-7: WDC WD4000AAKS-00TMA0, 12.01C01, max UDMA/133
[   34.329779] ata3.00: configured for UDMA/133
[   34.973687] ata4.00: ATAPI: Optiarc DVD RW AD-7191S, 1.01, max UDMA/100
[   35.141394] ata4.00: configured for UDMA/100
[   36.766079] ata7: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe100 irq 17
[   45.547140] [fglrx] Maximum main memory to use for locked dma buffers: 1887 MBytes.

```

cat /etc/modules
```

hunter@hunter-desktop:~$ cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
hunter@hunter-desktop:~$ 

```

cat /boot/grub/menu.lst | grep -i generic_ide

hunter@hunter-desktop:~$ cat /boot/grub/menu.lst | grep -i generic_ide
# defoptions=quiet splash all_generic_ide floppy=off irqpoll pci=nomsi
kernel          /boot/vmlinuz-2.6.24-20-generic root=UUID=a0aca0d8-6a97-4aad-acd4-f16e51e48018 ro quiet splash all_generic_ide floppy=off irqpoll pci=nomsi
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=a0aca0d8-6a97-4aad-acd4-f16e51e48018 ro quiet splash all_generic_ide floppy=off irqpoll pci=nomsi
hunter@hunter-desktop:~$ 


sudo hdparm -Tt /dev/sda
```

/dev/sda:
 Timing cached reads:   1400 MB in  2.00 seconds = 699.88 MB/sec
 Timing buffered disk reads:  188 MB in  3.02 seconds =  62.18 MB/sec

```

sudo hdparm -Tt /dev/sdb
```

/dev/sdb:
 Timing cached reads:   2088 MB in  2.00 seconds = 1044.24 MB/sec
 Timing buffered disk reads:  230 MB in  3.02 seconds =  76.28 MB/sec

```

---

### Post by Em-Buntu on 2008-08-12
Good question to which I am eagerly awaiting any feedback.
My system shows what I consider unusually low  IDE &S ATA transfer rates also. 
In fact, the rates you posted are making me really believe my system has a configuration issue. From IDE to SATA transfers, Ubuntu usually reports anywhere from 2 to 8 MB/Sec rates. These are relatively new and fast drives.

---

