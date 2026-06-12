---
title: "atom 230 kernel panic on 8.04.1 x86_64"
date: 2008-12-17
forum: x86 64-bit Users
---

### Post by Robstarusa on 2008-12-17
Anyone seen this?

I get a nasty kernel panic after installing from the x86_64 dvd.  The install goes fine, but first boot kernel panics.  Box is an "msi wind pc" nettpo with an 8G sdhc & 8GB compactflash card in raid1.

8.10 x86_64 is not able to even check the cd before I get a kernel panic

---

### Post by PatrickVogeli on 2008-12-18
I'd try without the raid array..

---

### Post by Robstarusa on 2008-12-18
> **PatrickVogeli said:**
> I'd try without the raid array..

I was thinking of trying that, but why would it work on i386 and not x86_64?  The raid works ok on 32-bit.

---

### Post by Mange_S on 2008-12-21
Atom is a 32 bit processor and you are trying to run a 64 bit kernel on it. Use the 32 bit version of Ubuntu and all will be fine.

To be perfectly clear use i386.

---

### Post by Yellow Pasque on 2008-12-22
> **Mange_S said:**
> Atom is a 32 bit processor and you are trying to run a 64 bit kernel on it. Use the 32 bit version of Ubuntu and all will be fine.

To be perfectly clear use i386.
The Atom 230 (and 330) has x86_64 extensions according to Intel.

---

### Post by Mange_S on 2008-12-22
As I understand it not all ATOM:s have the 64 bit instructions activated eventhough they could. 

> **Temüjin said:**
> The Atom 230 (and 330) has x86_64 extensions according to Intel.

---

### Post by jespdj on 2008-12-23
If the Atom processor that Robstarusa is using would not have 64-bit instructions, then he couldn't have installed 64-bit Ubuntu at all - he would have gotten a message immediately when trying to boot from the CD (or DVD), telling him that his processor doesn't support 64-bit. So this is certainly not the cause of his problem.

---

### Post by stchman on 2008-12-23
I would recommend running 32 bit on an Atom processor.  I recently bought a Aspire One with an Atom processor.  It has only 1GB RAM.  Frankly Intrepid 32 bit is a touch taxing on it so I could imagine that if I ran a 64 bit OS.

I personally recommend that if you run 64 bit that you run at least 4GB RAM.

---

### Post by Mange_S on 2008-12-23
> **jespdj said:**
> If the Atom processor that Robstarusa is using would not have 64-bit instructions, then he couldn't have installed 64-bit Ubuntu at all - he would have gotten a message immediately when trying to boot from the CD (or DVD), telling him that his processor doesn't support 64-bit. So this is certainly not the cause of his problem.

Sorry i read the line "8.10 x86_64 is not able to even check the cd before I get a kernel panic" and misinterpret that line.

---

### Post by phil02 on 2008-12-23
According to wikipedia, Atoms intended for desktop/nettop systems have 64 bit support enabled and Atoms intended for netbooks (N and Z series Atoms) do not have 64 bit support.

When I tried to boot a x86_64 live cd on my MSI Wind netbook, it gives a message saying the kernel needs 64 bit support but the processor does not support it.

---

### Post by Lord Alexander on 2009-01-01
By the way, I'm still seeing this same panic, with the Intel LF2 (Atom 330) board, and the current (as of 12/30/2008) Intel BIOS.  Has anyone regenerated the live CD, lately, with a newer kernel?  I checked [http://cdimage.ubuntu.com/daily-live](http://cdimage.ubuntu.com/daily-live), and I only see Ubuntu 9.04 alpha images there.

Any other installation advice would be appreciated, as well.  I have verified that several other distros (Knoppix -current, for one) boot and run just fine, with the same BIOS, and I've run memtest86, to make sure that I don't have RAM issues.

After I first posted this, I went ahead and re-generated the live CD, myself, with the most up-to-date packages, and 2.6.27-7 kernel, and the install still panics.  I'm really at a loss as to what to do.  Any help would be appreciated.

OK, so it turns out that the issue was that BIOS 0137 didn't flash correctly, though it said that it did.  I went and flashed 0122, to match what was posted here, and in a matching bug, and the system now boots.  I'm not sure if my burn of the Intel BIOS cd was bad, or what.

Anyway, I'm on to my next problem, having to do with why the onboard NIC doesn't work.

Thanks!

---

### Post by Mopper on 2009-01-07
I also ran into the same problem and I can confirm that flashing the bios has solved the problem. I used the bootable cd that can be downloaded from [the Intel site.]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2926&DwnldID=17249&strOSs=38&OSFullName=OS%20Independent&lang=eng")

My setup:

Ubuntu Server 8.10 x86_64
Intel D945GCLF2 with Atom 330
2GB Kingston DDR2 @ 667MHz.

---

### Post by cariboo on 2009-01-07
I just got my  [945GCLF]("http://www.intel.com/Products/Desktop/Motherboards/D945GCLF/D945GCLF-overview.htm") yesterday, I installed the 32bit version and everything just works. Compiz works, I get 1600X1200 resolution, I thought I might have a problem with the network card, but it turned out to be a bad cable. I'm going to wait until Jaunty comes out before installing a 64bit distribution.

Jim

---

### Post by davidlm on 2009-03-14
I confirm the update bios for intel 945gclf solve the problem and install ubuntu amd64 ...but i have another problem the network card don't work....

---

