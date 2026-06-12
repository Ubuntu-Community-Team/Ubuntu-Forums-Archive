---
title: "Simple Noob Questions i need help with"
date: 2005-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by arnage on 2005-02-26
Hi im a yoper user, and I've just moved to Unbuntu as their is no Yoper 64. :-( 

The install process was really slick, so far im impressed but need a few things to
get it perfect.

Ok im sure this has been asked a few times but i can't find it so here i go.

1. How do I install firefox 1.01 im using 0.93 which is quite old
I wasn't able to find a new version 1.0+ in synaptic.

So I tried
(sudo ./firefox-installer-bin: error while loading shared libraries: libgtk-x11-2.0.so).
and im lost.

2. Ive got openoffice 1.1.2, whats the easiest way to upgrade to 1.1.4

3.I tried to install prelink, but i get message (
Package prelink is not available, but is referred to by another package.)

4. In hdparm i only get 29mb/sec in yoper i got 55mb/sec this seems slow and switching on the usual options e.g. dma , 32-bit mode didn't help.
I think i need the proper nforce 3 chipset drivers but i really need a howto for this.
Drive is ATA-133 not SATA.

5. How do i upgrade my kernel to 2.6.9.10+  a howto here would be great


Thats it, if i get all that done i should have a really fast system and up-to-date, thanks for you help.

---

### Post by kubla on 2005-02-26
If you've just installed, then you're probably tracking Warty. Most of the upgrades you're after can be had by upgrading to Hoary.

Open up /etc/apt/sources and read the instructions in that file. Then, run:

apt-get update

then

apt-get dist-upgrade

This will take you to the less stable but more bleeding edge Hoary.

Re. hdparm, you can turn on dma by running:

hdparm -d1 <device>

ie: hdparm -d1 /dev/hda

I hope that's a help.

Ian

---

### Post by arnage on 2005-02-26
Thanks, will do the dist update to hoary overnight, don't want to upset our
many gamers in the house with high pings.

---

