---
title: "Problems playing DVD:si"
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by tyr1973 on 2006-02-22
Hello all

I am having trouble with playing DVD:s.  Whether I try Ogle, Xine or Totem-Xine I get choppy pictoure and broken-up sound.  The cpu usage goes through the roof.

I am running all this on a HP HP Pavillion zv6000 
AMD Athlon 3200+  with 512 MB memory.  
ATI Radeon Xpress 200

I followed the instructions [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard)
for getting my graphics card to work.

Does anybody have an idea of what I should do?

Andreas

---

### Post by John Jason Jordan on 2006-02-22
[QUOTE=tyr1973]Hello all

I am having trouble with playing DVD:s.  Whether I try Ogle, Xine or Totem-Xine I get choppy pictoure and broken-up sound.  The cpu usage goes through the roof.

I am running all this on a HP HP Pavillion zv6000 
AMD Athlon 3200+  with 512 MB memory.  
ATI Radeon Xpress 200[/QUOTE]
I have a Compaq Presario R3240 with the same CPU running Ubuntu-64 Breezy. The only significant differences are that I have 1.25 GB of memory and my computer uses the Nvidia video. And I had to switch from the open-source nv video driver to the proprietary one from Nvidia before it would work at all. Still, it works perfectly. My CPU runs at 1600 when playing a DVD.

I'd guess RAM might be the issue. Check your hard drive light. If your RAM is not adequate it will page to disk. On mine the disk like runs off and on, but in synch with the little green light on the DVD drive. In other words, my hard drive light goes on for either the hard disk or the DVD drive, and in this case, it is going on only when the DVD drive is operating. If your hard disk light comes on more than when the DVD drive is working, that might be an indication that it is paging for lack of RAM.

Another possibility is that the ATI driver is the culprit. But I know nothing of the ATI drivers, except that the chip you have is difficult to get working properly.

---

### Post by cat on 2006-02-24
Does your 3D acceleration work? that was the problem with my ati radeon x700

---

### Post by Hygelac on 2006-02-24
I'm having this exact same problem with a zv6000 too (Kubuntu-64), except that mine has 1Gb RAM and still plays a choppy DVD.  However, I am fairly sure that my 3D acceleration does not work (I use the 'ati' driver instead of the 3D 'fglrx').  Is that information useful to anyone?

---

### Post by Hygelac on 2006-02-24
I just got mine to work.  \\:D/  Check out this link: [http://www.ubuntuforums.org/showthread.php?t=126776&highlight=DVD](http://www.ubuntuforums.org/showthread.php?t=126776&highlight=DVD)

It was just that 'DMA' was not on.  Now it runs fine (with the 'ati' driver and no fancy 3D acceleration).  I uncommented three lines from /etc/hdparm.conf so that the section on dev/cdrom (the location of my CD/DVD-ROM drive) would read:

```
/dev/cdrom {
        dma = on
#       interrupt_unmask = on
#       io32_support = 0
}
```

Does that help?

---

### Post by tyr1973 on 2006-02-28
Thanks!

It works now, I uncommented the lines in hdparm.conf.

:)

---

### Post by Hygelac on 2006-03-02
Excellent; glad I could help. :mrgreen:

---

