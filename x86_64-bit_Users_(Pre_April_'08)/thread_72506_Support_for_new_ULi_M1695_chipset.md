---
title: "Support for new ULi M1695 chipset?"
date: 2005-10-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonny on 2005-10-06
Considering getting the ASRock 939Dual-SATA2 motherboard basd on the new ULi M1695 chipset.  Big benefit is that it offers both AGP and PCIe support.

Does anyone have experience of getting this board to work with ubuntu?  I'd like to install Breezy.  Googling produces few relevant results - not surprising, really, as it's all so new.

---

### Post by jonny on 2005-11-01
Well, I bought an ASRock board with this chipset.  Everything seems to work fine out of the box.

I haven't yet tested the onboard network card (I'm using wireless), but it looks like it's there and waiting to be configured.  I'm using an Athlon 64 3800+, an old nVidia GeForce 256 AGP graphics card, a SATA hard drive and an IDE DVD writer; all these work perfectly.  The USB ports, onboard sound and PCI expansion slots all work perfectly.

I wish I could say the same thing for the nForce4 card I bought at the same time :(

---

### Post by jjukka on 2005-11-01
[QUOTE=jonny]Well, I bought an ASRock board with this chipset.  Everything seems to work fine out of the box.[/QUOTE]

Hi,

I have the same board, and no success so far. Biggest difficulties are with SATA disk. Ubuntu does not see it at all, even though it can be seen at BIOS.

Please tell me:
Is there any traditional IDE disks in your system (and if there is, from which you are booting from)?
Did you made a new fresh install, or just swapped the mobo to a working system?
Are you running ubuntu's stock kernel?

Thanks in advance!

---

### Post by jjukka on 2005-11-02
I found a workaround:

My mobo is ASRock 939Dual-SATA2 and the disk is Seagate 7200.9, which is a SATA-II disk.

The disk, when connected to mobo's SATA-II connector is recognized by the BIOS (1.30), but is not recognized by linux (Breezy).

BUT, when the disk is connected to mobo's SATA-I connector, it is also seen by linux :-o

Okay, the disk channel is now only half-speed (1.5 Gbps), but I can live with it for a while, as I believe that one day there will be a nice kernel which gets the SATA-II working.

Keywords: 939Dual-SATA2 SATA-II SATA2 SATA asrock JMicron JMB360 ULi 1695

---

### Post by Erwin123 on 2005-11-07
You may note that there is another thread with a similar topic: the network interface of that MB: [http://ubuntuforums.org/showthread.php?t=83710](http://ubuntuforums.org/showthread.php?t=83710)

One solution that is offered works by compiling some vendor supplied kernel modules
[http://www.uli.com.tw/eng/support/drivers.php](http://www.uli.com.tw/eng/support/drivers.php)

There is also a module for the SATA issue, maybe it solves the SATAII thing.

Greets,
Erwin

---

