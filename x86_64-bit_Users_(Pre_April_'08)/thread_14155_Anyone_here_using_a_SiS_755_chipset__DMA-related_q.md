---
title: "Anyone here using a SiS 755 chipset?  DMA-related question..."
date: 2005-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by cuoog on 2005-02-05
Hi,

I'm using a SiS 755 chipset (ECS 755-A2 motherboard), and I've been trying like crazy to get DMA enabled on my DVD burner.  I've been using the i686 kernel.  I tried hdparm and it just fails.  I tried the k7 kernel, no help.  I even tried recompiling the kernel to enable generic pci-dma, but it seems to already be enabled (though I'm new at this and could just be reading it wrong, I admit).  Anyway, my question for any fellow users out there is this: does the 64-bit kernel enable DMA for IDE on this chipset?

Also, is there an easy way to just install the 64-bit kernel on top of my 32-bit installation?  I really dont want to have to reinstall everything, as I've finally gotten it where I like it except for the DMA.  I'd like to watch DVDs and burn CDs, so I'd just try and install the amd64 kernel if it were trivial.

Finally, if anyone out there knows, I'm using Warty, is this something that could be fixed in Hoary with its 2.6.10 kernel?

thanks everyone for the help.  other than this issue, ubuntu is the BEST!

dan

---

### Post by K6-III on 2005-02-05
SIS755 support for AGP was only added in 2.6.7 RC3.

2.6.10 may help...but not sure.

As for 64 bit, from what I garner, no choice but to reinstall.

64bit flash is all that is holding me back...

---

