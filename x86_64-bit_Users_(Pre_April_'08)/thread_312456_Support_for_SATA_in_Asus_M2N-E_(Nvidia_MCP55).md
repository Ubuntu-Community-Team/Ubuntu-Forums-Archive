---
title: "Support for SATA in Asus M2N-E (Nvidia MCP55)"
date: 2006-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ispmarin on 2006-12-04
Hello all. I have just discovered that in my new system the DMA on my Barracuda SATA is not active. When I try to put DMA on, I got this message: 
+++++++++
sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

+++++++++
So I am not using or sata_nv or libata correctly, and just ide_generic. I tried then to compile a kernel 2.6.19 from source to see if the problems is resolved, but with no luck - the same error appears (the .config is attached). Anybody had any luck with this configuration? 
Thanks!

Ivan

Conf:
AMD Athlon64 4200 X2 
ASUS M2N-E 
1GB RAM(2x512MB Kingston)
Geforce 6200 512MB TurboCache
Seagate 360GB Barracuda 7200.10
Ubuntu Edgy Eft with kernel 2.6.17-10-generic (SMP)

---

### Post by kuja on 2006-12-05
hdparm doesn't work with SATA drives, only with IDE drives, AFAIK. Chances are if you're using a SATA drive it's already using DMA, per default.

---

### Post by RAOF on 2006-12-05
> **kuja said:**
> hdparm doesn't work with SATA drives, only with IDE drives, AFAIK. Chances are if you're using a SATA drive it's already using DMA, per default.

Indeed.  SATA is newer; it's no longer possible to **disable** DMA.  As far as I'm aware there's no reason to use hdparm with SATA drives (even if it did work).

---

### Post by ispmarin on 2006-12-05
Well, thanks for the response. Did not know that hdparm would not work with SATA drives (the man page says clearly ATA/IDE, so I supposed that SATA would work.). 

Anyway, used the same hdparm to do some benchmarking, and got this results:

/dev/sda:
 Timing cached reads:   3040 MB in  2.00 seconds = 1520.31 MB/sec
 Timing buffered disk reads:  228 MB in  3.02 seconds =  75.42 MB/sec

Not bad, anyway. And as always, why I didnt searched a little before posting? ;-)

[http://freshmeat.net/projects/hdparm/](http://freshmeat.net/projects/hdparm/)

Thank you everybody.

Ivan

---

### Post by kuja on 2006-12-05
Wow, not bad at all, better than mine anyway.

(Both of mine were about: buffered: 62 MB/s, cached: 1780MB/s)

---

