---
title: "How to get nvidia 6600GT cards to work"
date: 2005-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Compwiz on 2005-02-10
I just read the greatest news in the history of me : 

from another linux/6600GT forum: The nvidia drivers did not work neither did the nv driver so to get a picture in X windows i am nor running vesa driver...

i just changed this and it damn well worked!!!! i am soo damn happy!!!! 2 linux distros in 1 day! i am having a good day!! this is awsome!!! xcept no 3d support, but who cares! i have UBUNTU!!!!  the damn VESA driver works and not the friggin nv one!!! anyone who wants to know, this is where its at!!!!!!  \\:D/  \\:D/  \\:D/

---

### Post by Psy on 2005-02-10
The nvidia drivers do work, but you need the latest version from [www.nvidia.com](www.nvidia.com)

---

### Post by Compwiz on 2005-02-12
well since i dont have acces to the inernet on thet copmuter, it would be rather difficult to download the drivers, eh there psy?

---

### Post by Tichondrius on 2005-02-12
[QUOTE=Compwiz]well since i dont have acces to the inernet on thet copmuter, it would be rather difficult to download the drivers, eh there psy?[/QUOTE]
 The vesa driver didn't work in hoary (which uses Xorg), so I think it only works in warty (XFree86).  Please post your specs - hoary/warty, i386/amd64 ?  But I do agree that the nv driver doesn't work at all on 6600GT, nor does the older nvidia drivers (v1.0-6111). But the new nvidia drivers (v1.0-6629) is only available from hoary repository. So on Warty, you can use the vesa driver, but on Hoary you can install the new nvidia drivers. In both cases, you will need to do it from text mode, as X will fail to start after the installation, because as I said the default 'nv' driver doesn't work with  the 6600GT.

---

### Post by Compwiz on 2005-02-13
i have te amd64 version of warty

---

### Post by Tichondrius on 2005-02-13
[QUOTE=Compwiz]i have te amd64 version of warty[/QUOTE]
 And is your graphics card pci-express ?

---

### Post by Compwiz on 2005-02-16
[quote=Tichondrius]And is your graphics card pci-express ?[/quote]
it is not

---

### Post by Tichondrius on 2005-02-16
[QUOTE=Compwiz]it is not[/QUOTE]
 great, but next time you might want to mention that when you start a thread like this, because your vesa driver solution doesn't work for pci-express cards. because otherwise you're just confusing readers, and wasting their time.

---

### Post by MaX on 2005-02-17
The Nvidia 6600 GT is an AGP version of the PCI-Express Nvidia 6600.

So if you knew that you wouldn't need the specification.


So, from the commandline how do I get my dad's computer upgraded to hoary?
```
apt-get dist-upgrade hoary
```?

---

### Post by ember on 2005-02-17
[QUOTE=MaX]The Nvidia 6600 GT is an AGP version of the PCI-Express Nvidia 6600.

So if you knew that you wouldn't need the specification.
[/QUOTE]

It actually is not ... there is an 6600GT and an 6600-Version of Nvidias chip, the first one has GDDR-3 RAM and I think some more pixel pipelines activated.
Of both chips there are AGP versions, yet most of them are 6600 GT.

Just my 2 cent,
Ember

---

### Post by Tichondrius on 2005-02-17
[QUOTE=MaX]The Nvidia 6600 GT is an AGP version of the PCI-Express Nvidia 6600.

So if you knew that you wouldn't need the specification.


So, from the commandline how do I get my dad's computer upgraded to hoary?
```
apt-get dist-upgrade hoary
```?[/QUOTE]
 funny that you say that as if you know, because I actually have 6600GT pci-express card, and went thru hell trying to get it to work. As the previous poster said, most 6600GT are pci-express cards, as initially 6600GT was only available in pci-express version. Only later, AGP versions of the card started to appear. Secondly, there is well known bug in Xorg/Xfree86 which affects pci-express video cards running in 64-bit mode.  So neither the vesa nor the nvidia drivers work correctly for 6600GT pci-e on AMD64. And the "nv" driver doesn't supprt 6600/GT at all (both pci-e and agp). See [this thread](http://www.ubuntuforums.org/showthread.php?t=15311) for more details on the bug, and solutions/workarounds.

---

