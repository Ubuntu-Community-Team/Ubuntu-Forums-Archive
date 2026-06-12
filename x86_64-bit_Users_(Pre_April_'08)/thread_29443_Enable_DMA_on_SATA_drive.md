---
title: "Enable DMA on SATA drive?"
date: 2005-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by merc on 2005-04-24
I just installed Hoary64 on my AMD64 machine. Here are the specs:

AMD Athlon64 3000+
K8T800 Motherboard with 8237 southbridge (native SATA)

My drives are setup as follows:

IDE Channel 0: DVD
IDE Channel 1: 10gb Seagate PATA drive
SATA Channel 0: 80gb Seagate SATA drive

The problem is that I can't enable DMA on the SATA drive. It mounts under /dev/sda, and here's where the weirdness begins:

```

merc@blackbox:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=ST380013AS      3.18, FwRev=3.18, SerialNo=
 Config={ }
 RawCHS=9729/255/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=9729/255/63, CurSects=0, LBA=no
 IORDY=no
 PIO modes:  pio0
 AdvancedPM=no

 * signifies the current active mode

```

And by contrast, this is what I get for the IDE drive:
```
/dev/hda:

 Model=ST310014A, FwRev=3.09, SerialNo=5JREKJA7
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=20005650
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: device does not report version:

 * signifies the current active mode

```

When I try to enable DMA on the SATA drive, this happens:

```

merc@blackbox:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device                                  

```

Here's an "lsmod | grep via":

```
merc@blackbox:~$ lsmod | grep via
via_rhine              22788  0
mii                     5504  1 via_rhine
i2c_viapro              8716  0
i2c_core               23960  1 i2c_viapro
sata_via                9476  0
libata                 52488  1 sata_via
via82cxxx              14128  1
ide_core              143748  4 ide_cd,ide_generic,via82cxxx,ide_disk


```

I have tried removing the via82cxxx modules (I read somewhere that it conflicts with the sata_via module), but even if i deleted the module (the .ko file), it would still showup in the lsmod output.

The weird thing is that I think the SATA drive worked fine with DMA before I added the PATA drive to the computer.

 :-(

Any help would be greatly appretiated.

---

### Post by merc on 2005-04-25
ANyone?

---

### Post by devil28 on 2005-04-25
cant really help you other then that I got the same board with 2 pata and one sata and dma worked from the start for me

---

### Post by FluffyElmo on 2005-04-25
I have the same hardware and the exactly same problem. From looking at posts, it appears that hdparm doesn't work with SATA drives but there isn't an alternative tool yet?

Devil28, could you post your /etc/modules file? I've tried various combinations but mostly succeeded only in disabling DMA altogether  :???: 

Any help appreciated...

---

### Post by floogy on 2005-04-26
[QUOTE=FluffyElmo] From looking at posts, it appears that hdparm doesn't work with SATA drives but there isn't an alternative tool yet? [...] Any help appreciated...[/QUOTE]

Hello,

I postet Yesterday some lines about that. [Ubuntu Forums - Other Application Support:  Default  hdparm and s-ata  ](http://ubuntuforums.org/showthread.php?t=29635) 
There is a Tool blktool from the gkernel projekt. It's written by the author of libata [[LKML]From: Jeff Garzik - Subject: new tool: blktool](http://lkml.org/lkml/2004/8/15/157) .



Maybe you can find some useful Information about SATA and DMA in Jeff Garzik's [posts](http://www.kerneltraffic.org/kernel-traffic/quotes/Jeff_Garzik.html)  on kernelorg. For example [New ADMA Driver](http://www.kerneltraffic.org/kernel-traffic/kt20041130_286.html#6)  .

I hope that helps a little.

Further Info's:
[Wikipedia about Serial ATA](http://en.wikipedia.org/wiki/Serial_ATA) 
[Serial ATA (SATA) chipsets — Linux support status](http://linuxmafia.com/faq/Hardware/sata.html) 

A google search for dma on serialata.org gives poor results:
[Google Search: dma site:serialata.org](http://www.google.de/search?hl=de&q=dma+site%3Aserialata.org&btnG=Google-Suche&meta=) 

For example:

> Future enhancements
• Serial ATA includes a transport protocol for first
party DMA transfers as well as second party DMA
transfers
– The device can set up a host adapter DMA engine to
execute DMA transfers
• With the appropriate drivers a device could:
– Execute commands out of a queue located in host
memory
– Report command results into a table/list in host memory
– Execute commands out of order to optimize
performance
– Deliver data out of order to optimize performance
– Scatter/gather data in host memory

Here You can read the details about DMA and SATA:
[Serial-ATA - Native Command Queuing Final [pdf]](http://www.serialata.org/docs/Native%20Command%20Queuing%20Final.pdf) 

I don't know exactly if that means, that dma could already be performed on SATA drives under windows or linux?

Kind regards

Gerhard

---

### Post by etitor on 2005-05-13
I thought I had managed to get DMA on my SATA drive by first enabling DMA for SATA in my BIOS. But now I see it doesnt get there.

---

