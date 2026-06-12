---
title: "Breezy install bombs out on disk errors"
date: 2005-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by jshamlet on 2005-11-14
Hey,
I am (attempting to) install Ubuntu 5.10 PPC on a G3 Minitower, and running into problems. I have managed to get through the first stage install, and apparently at least partway through the second stage install, before I run into problems.

This machine is not overclocked, and has a stock G3 333/66 processor on a Rev.C "Gossamer" board, and 384MB of RAM. I installed an Acard 6280M ATA-133 disk controller, which works great in Mac OS 9. There is a single Maxtor 740DX ATA133 drive on the first port, and a standard Apple/Sony 24X CD-ROM on the second port. The "boot disk" is a 2GB ATA drive on the internal ATA controller. (The Mac will boot from the Maxtor disk, but having a disk on the internal controller seems to make it boot faster - I suppose it doesn't waste time looking for an onboard disk) This machine also has a generic OHCI USB controller, and a Asante' AF686 Fast Ethernet card in it, along with the regular "audio-only" A/V option card. There is no modem installed.

Oddly, the kernel is reporting the Acard 6280M as a 6880R. I can't quite tell, but it looks like the kernel is accessing both the HDD and the CD-ROM in PIO mode, instead of DMA - not sure what the deal is there. The errors seem to imply that DMA is being used, so perhaps I'm just missing something here.

I saw no errors during the first stage install. The installer ran smoothly, and copied over everything with no errors. The first stage install went smooth as glass. Since this is an Oldworld Mac - I mounted a HFS+ partition at the end (on the screen that warns about the lack of a bootloader), and copied the vmlinux and initrd.img files over. Other than that, nothing unusual happened.

The second stage install seemed to go well at first, until it started configuring packages. Then, I started seeing these:

[xxx] hde:dma_intr:status=0x51 {DriveReady SeekComplete Error}
[xxx] hde:dma_intr:status=0x84 {DriveStatusError BadCRC}
[xxx] ide:failed opcode : unknown

It did this several times before finally giving up about 44% of the way in. There was a notice about continuing the install, but there was only one option - OK, which dropped me to a prompt. I was not able to restart the installation ( I couldn't find a command that seemed obvious )

The errors seem to indicate a bad hard disk, but I have not had any problems out of the drive in Mac OS - and the disk was fairly full before I backed it up.

To check it, I had Mac OS zero the entire disk in DriveSetup - and got no errors. This disk has only been used with this Mac - so if anyone knows of any other ways to verify disk integrity, I'd be glad to try - but so far, it has not shown any signs of having problems.

I have another ATA100 disk (A WD1200JB) I can try as well, but I'm still not convinced the problem is the disk.

At this point, I can almost, but not quite, get a working install. At 44%, X was working - but most of the applications were not.

Does this ring a bell? Is there anything I can do to get Ubuntu booting properly on this system?

(and as an aside, does Ubuntu come with a secure shell daemon?)

Thanks!

---

### Post by ssam on 2005-11-15
can you try again. if it fails at the same point then its probably a software problem, it it happens ant another point then its probably hardware.

you could try doing a server install, you can do this with the normal install disk, just type server at the boot prompt. This just installs a fairly basic system, so it make get all the way through. then you could easily install the extra packages you need to get a graphic interface, and some desktop applications.

how big is the disk you are installing to? i think you need 1.2 gb for the default linux install.

the secure shell server needs to be installed. the package is called openssh-server, you can either search for it in synaptic, or install it with the command

```
sudo apt-get install openssh-server
```

---

### Post by jshamlet on 2005-11-15
The Maxtor disk is a 40GB drive. 4.3GB are reserved for MacOS (for Mac on Linux ), 35GB are reserved for Linux, and the rest is swap.

As for the install type, I don't recall being asked what kind of install I wanted when I booted the CD. I've been through the first stage several times - but it's possible I missed something. I'm booting the kernel/RAMdisk image supplied on the Breezy PPC CD with no arguments to run the installer, and "root=/dev/hde7" to boot the installed copy.

At what point are you asked about the install type? I would actually prefer a server-style install anyway.

---

### Post by ssam on 2005-11-15
at the cd boot prompt you can either just press enter for the default install, or add some boot arguments. i think you press f1 to see a list of the available options. one of them is server. (just type 'server' and press enter)

---

### Post by jshamlet on 2005-11-16
I never saw a boot prompt - I have to use bootx, so I am guessing that is why I don't see it. I never actually "boot" from the CD-ROM. I did try passing "server" as an argument when I launched vmlinux from bootx - but I didn't notice any difference in behavior, so I am guessing it missed that bit of info.

That said, I tried again, and saw a bunch of the same errors again. The install crapped out at a different place, but fortunately, late enough that I was able to recover using the package manager.

So, I finally have Ubuntu installed and configured. I'm still having problems with the refresh rate being stuck at 60Hz, when I know the hardware is capable of much higher rates - but that's another story...

---

