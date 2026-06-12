---
title: "Ubuntu 64bit and more than 4GB of RAM"
date: 2008-06-02
forum: x86 64-bit Users
---

### Post by padcom on 2008-06-02
Hi there,

I'm having some strange issues with Ubuntu 8.04 (amd64 version) with GA-MA69VM-S2 motherboard and more than 4 GB of RAM. Here's what happens: 

Right after booting everything works just fine for some time, all the memory is recognized properly - basically everything works. 
I also have 3 hard-drives attached to that motherboard: one is a small, 40Gigs old IBM drive on IDE channel 0 Master, second is a 200Gigs drive on IDE channel 0 Slave and the 3rd one is a 500Gigs SATA drive that I use as a Samba-shared storage for the rest of the workstations in my network.
Now here's the problem: when up to 4GB of memory is installed there are no problems whatsoever with the stability of the system. However when I expand the memory (by adding additional 2 DDR2 modules that are exactly the same as the ones that are already there) then strange things happen. First of all when copying data between the 200Gigs HDD and the 500Gigs one a series of errors occurs and after that Ubuntu just freezes for good. When Ubuntu is booted into safe mode then almost the same behavior can be seen just that prior to being frozen for good I'm dropped out of Midinight Commander back to shell with a lot of strange messages.

Again, for the sake of proper testing I've removed the extra memory leaving only 4GB of RAM and everything went back to normal.

I've tested the pairs of RAM modules separately and they both check out ok. I've also tested the 8GB setup using a different motherboard and the same version of Ubuntu (same software installed too) and all seems to be working ok. The memtest available on Ubuntu install CD passes without errors as well.

Did anyone experience the same problem? Is there a workaround I could use to make it work?


Best regards,
Matthias.

---

### Post by shakabra on 2008-06-02
What size PSU are you using?  With all that hardware it sounds like it could be a power problem.

---

### Post by padcom on 2008-06-02
400 Watt. Same MB and all other equipment (exactly the same physical one) runs ok with WinXP 64bit.

---

### Post by felker2 on 2008-06-03
> **padcom said:**
> 
Now here's the problem: when up to 4GB of memory is installed there are no problems whatsoever with the stability of the system. However when I expand the memory (by adding additional 2 DDR2 modules that are exactly the same as the ones that are already there) then strange things happen. 

My first guess: faulty RAM. To check that, run the memtest from the boot option on harddisk and/or live CD.

---

### Post by Sef on 2008-06-03
> My first guess: faulty RAM. To check that, run the memtest from the boot option on harddisk and/or live CD.

It's called a [mem86test]("http://www.memtest86.com/").  Boot into GRUB or use the live cd.

---

### Post by fjgaude on 2008-06-03
Do you have the latest **BIOS** upgrade for your motherboard? Many companies, only until recently, didn't have 2GB memory modules to test their boards out with, and just used common sense thinking 8GB would work, but it doesn't.

---

### Post by padcom on 2008-06-05
Well, I thought so too that it could be a faulty RAM module. Memtest showed no problems on both MBs that I have available but Ubuntu has problems with the one I mentioned above.
On the second MB all runs smoothly since 3 days so I guess it must be some kind of compatibility problem with MB drivers in Ubuntu (V690 chipset).

---

