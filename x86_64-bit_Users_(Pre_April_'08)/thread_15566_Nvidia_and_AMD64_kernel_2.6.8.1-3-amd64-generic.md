---
title: "Nvidia and AMD64 kernel: 2.6.8.1-3-amd64-generic"
date: 2005-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nebula10111 on 2005-02-15
MOBO: MSI K8N Neo2 Platinum
CPU: AMD 3500
AGP CARD: NVIDIA 6800 GT

Allrighty, I used the prepackaged Nvidia drivers to get my system working and while it worke it doesnt recognize my card as 6800 GT and I'm pretty sure its not up to full capability. And for whatever reason "nvidia-settings" gives me a segmentation fault. So basically it half works. So I wanted to install the latest 6629 driver for amd64. 

Now I tried... Tried pretty hard to get the driver installed. My kernel version is 2.6.8.1-3-amd64-generic. I got the right driver and all but somthing is up with the kernel source. Where can I get the source and headers for my version? On a side note is there an nvidia-kernel-source for amd64? There are all kinds of posts about how nvidia drivers and such. Any help or reference as it pertains to gettin those drivers to work on amd64 would be appreciated.

Thanks

---

### Post by Dylanby on 2005-02-16
I have the same card & mobo. I used the [BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) 

When you ```
sudo dpkg-reconfigure xserver-xfree86
```  you can fill in some details for your card.

The 6629 driver is in Hoary. You can use the [PinningHowto](http://www.ubuntulinux.org/wiki/PinningHowto) 

Another [example of apt-pinning](http://www.ubuntulinux.org/wiki/InstallingMplayerFromHoaryInWarty) 

I also think you'd be better off with the amd64-k8 kernel instead of the generic one.

---

### Post by Nebula10111 on 2005-02-16
Thanks for the info.

> I also think you'd be better off with the amd64-k8 kernel instead of the generic one. 
I wanted to use that kernel. I just installed Ubuntu off the CD. How would I go about getting and implementing the K8 kernel?

---

### Post by Dylanby on 2005-02-16
Fire up Synaptic. Edit => Search. Type "linux-image" & you'll see it listed.

Make sure to install the corresponding "linux-restricted-modules" package (not in the standard repo's).

Refer to the [Unofficial Ubuntu Starter Guide](http://ubuntuguide.org/index.html) for enabling the universe/multiverse repositories.

---

### Post by Dylanby on 2005-02-16
Forgot to mention that Warty's nvidia-settings package segfaults for me too.

Under 32bit it works fine.

---

### Post by henla464 on 2005-03-05
nvidia-settings seg faults here too. Anyone know how to fix that?



/Henrik Larsson
Amd64

---

### Post by my64 on 2005-03-06
[QUOTE=henla464]nvidia-settings seg faults here too. Anyone know how to fix that?



/Henrik Larsson
Amd64[/QUOTE]


I had this problem under hoary also. It has been fixed recently when I installed last Hoary packages. I think, but not 100% sure, that installing the xorg 6.8.2 fixed it.
Anyway, if you have a PCI-express video board, you should install this version at it fixes a nasty bug with PCI-e and 64 bits.

---

