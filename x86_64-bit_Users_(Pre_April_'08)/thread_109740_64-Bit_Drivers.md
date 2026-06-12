---
title: "64-Bit Drivers"
date: 2005-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by ATAQ on 2005-12-29
I have just updated my system from 32-bit Ubuntu 5.04 to 64-bit Breezey.
It seems to run okay, but I cant get a proper feel of power for the system as I cant get any drivers. I have an MSI 945p Neo-F Mainboard, Azalla onboard sound, I cant even get the best out of the nvidia drivers because there is no proper PCI-E drivers, does anybody have any info that may help me? Thanks

---

### Post by queenorych on 2005-12-29
What drivers can't you get?  I'm running a pci-express an nvidia 6600-gt.  Didn't have to do anything special here.  Nforce4 sound, nic, usb, ide, firewire all came up.

Do you have any errors?

---

### Post by ryan76 on 2005-12-29
Hi, sorry to hijack the thread... I'm trying to install the realtek driver for ALC655 sound card and I keep getting this error during ./configure:

```
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
```

I got to the realtek page from the AMD64 support page [http://developer.amd.com/drivers.aspx](http://developer.amd.com/drivers.aspx) so I assume it's 64 bit...

---

### Post by ATAQ on 2005-12-30
Well nothing shows up, USB devices, firewire etc. And the pci-e bus isnt showing up right, I think that it is being seen as a standard PCI bus (I dunno if that makes a difference or not)
And I cannot get drivers for my Azalla AC'97 Sound, I havent a clue what to do to be honest!

---

### Post by Suger on 2005-12-30
Azalia ? It worked since the beginning on my laptop. Isn't it just that you need to raise the sound in alsamixer ?

---

### Post by ATAQ on 2005-12-30
haha, I wish it was as simple as that!! I checked that!! There is just no working drivers, It will run under 32-bit, because there are drivers for that plat, but none for x64, well yet anyway. I suppose I will just use 32-bit Ubuntu for a while!!
Thanks for the responses guys

---

### Post by DRF on 2005-12-30
ryan76: Have you installed the kernel source? (or it might be called linux source or there might be some meta package to install all you need, I've not used it in a while, prob easiest to search the forum)

I forget the package name but a search in synaptic might well find the package the driver wants installed. It's better practice and easier to use apt/synaptic to install software (easier to uninstall) so I've not compiled anything more than a game or so from source for a while. But I remember a long time back having to do the same for some nvidia/nforce drivers back when I was using debian, then you have to go and find and install all the stuff the drivers need to work. (build-essential is essential for compiling stuff yourself, after that have to look up the readme for the other software/libarys needed)

Daniel

---

### Post by Suger on 2005-12-31
I am running x86_64 and I can swear you that Azalia is working...

---

