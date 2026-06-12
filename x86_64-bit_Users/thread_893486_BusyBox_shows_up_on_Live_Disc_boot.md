---
title: "BusyBox shows up on Live Disc boot"
date: 2008-08-18
forum: x86 64-bit Users
---

### Post by Vega on 2008-08-18
hai guys

Well my recently built machine is having trouble loading Ubuntu, I tried both 64 and 32 bit discs I still can't boot into Live Disc mode or install. Whenever I see the progress bar going back and forth I get taken to this thing called "Busy Box 1.1.3" some sort of ash prompt

I've futher researched this before your answer someone suggested switching SATA mode in BIOS from IDE to RAID would work but I've had no such luck.

My new specs on my machine are:

AMD Athlon X2 [4050e]
Geforce 8300 Chipset w/ Hybrid SLi[function disabled][currently sharing 256MB of physical ram]
2GB DDR2 800

Any idea why is this happening?

thanks

---

### Post by Vega on 2008-08-18
well I found out what happened. Appararently Ubuntu doesn't like my SATA DVD RW drive

I used an ext dvd rw drive to load ubuntu and it worked. but my display and networking on ethernet doesn't seem to work..

I should of never bought an nvidia chipset T_T

---

### Post by lekidos on 2008-08-18
I'm having a similar problem!

I can boot into live 32-bit Sometimes!  But I want to install the 64-bit, and I keep getting stuck at [initframs].   is there a way to install 64-bit without getting into the GUI?

---

### Post by Funkysauce on 2008-10-02
I am having a problem with the Live CD and trying to install. I get as far as language selection but after that I get the BusyBox prompt.

System specs:
E8500 Core 2 Duo 3.16
4GB Dual Channel DDR2 1066
750GB SATA
80GB SATA (I want to install on this drive)
DVD-RW SATA
nVidia Geforce GTX 260 896MB PCI-E
ASUS p5Q-PRO Motherboard

I tried installing both Ubuntu 8.04.1 32-bit and 64-bit, but no matter what happens it runs into the Busy Box prompt. I'm an absolute Ubu noob so any advice will be a great help.

For the record I was able to install Ubu 8.04.1 32 bit on an old machine.

OK SOLVED! Here's what I did: some more searching on the forums! Booted to LiveCD, hit F6 then entered: all_generic_ide floppy=off irqpoll pci = nomsi

and hit enter and it booted! Hooray!

---

### Post by jaktar on 2008-10-02
> **Funkysauce said:**
> 
OK SOLVED! Here's what I did: some more searching on the forums! Booted to LiveCD, hit F6 then entered: all_generic_ide floppy=off irqpoll pci = nomsi
and hit enter and it booted! Hooray!

This needs a little clarification...
Are you saying you somehow got the 64bit live CD to boot or the 32bit?

I also have an Asus P5Q mobo and have the same problem with the live CD's not loading.  
*64 bit(both 8.04.1 ubuntu and kubuntu) won't load at all, prompts me to enter a valid boot disk.  I verified the burn after writing, so I'm fairily sure the disk is not the problem.

*32 bit kubuntu 8.04.1 (32 bit) gives the spash screen, but dumps to initramfs.  Ubuntu 7.10 32bit also dumps to initramfs after splash screen.  I've used both of these disks to install on my previous system, so I know they're also good.  

I'm going to try and boot from USB to see if this resolves the invalid boot media problem.  

I've used this DVD drive to install 32bit Ubuntu/Kubuntu previously, but just in case it matters I'm using a TSSTcorp SH-S203N.

---

### Post by jaktar on 2008-10-02
On my mobo (Asus P5Q) I had to change my SATA mode to AHCI.  This allowed me to boot Kubuntu 8.04.1.  I was not, however, able to boot to Ubuntu 7.10.

I believe I also may have identified a problem with the 64bit versions via direct download (vs bittorrent).  Both versions I downloaded directly only produced approximately 10mb of files if extracted/burned even though the image is ~670mb.  I attempted to check the file via bittorrent, only to have bittorrent attempt to re-download the entire image.  In short, use the bittorrent option if you have a choice.

**Update**
After setting SATA mode to AHCI I successfully installed Ubuntu 32bit.  If you're dual booting with XP/Vista you may run into problems switching from enhanced IDE to AHCI due to not having AHCI drivers installed.  There is an easy fix with either your Windows recovery disk or simply follow these instructions: [http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976)

I now have longer boot times in Vista due to the extra time to load the AHCI drivers, but Kubuntu loads fine.

---

