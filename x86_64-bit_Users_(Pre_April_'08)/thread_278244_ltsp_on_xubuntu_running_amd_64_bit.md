---
title: "ltsp on xubuntu running amd_64 bit"
date: 2006-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by snoop-e on 2006-10-16
HI 
I am running xubuntu on an amd_64 server and want to run i386 clients is this possible ? if so has anyone tried this ?

---

### Post by DonVla on 2006-10-16
> **snoop-e said:**
> HI 
... want to run i386 clients ...

what kind of clients?

---

### Post by Jimmypainter on 2007-03-07
I also would like to know how to install an i386 chroot folder or folders nessacary to boot my NON-amd64 clients. I also would like to know how to mix PXE boots with etherboot. I am running Edubuntu with pc's that I want to convert to thin clients and also buy some more thin clients for my network. I would just about Explode with joy :biggrin: to talk to a real human about this over an old device known as a "Telephone" I think is what they called em. (205) 856-2544 ex. 313

---

### Post by clarknova on 2007-06-20
> **snoop-e said:**
> HI 
I am running xubuntu on an amd_64 server and want to run i386 clients is this possible ? if so has anyone tried this ?

This appears to be possible. From the Edubuntu Handbook, included in the Help and Support Application on my Edubuntu Feisty Server install:

> [this] is called a **chroot environment**. You can have several of them, based upon several different CPU architectures. They'll normally live under /opt/ltsp on the server, with subdirectories for each of the architectures. For instance, if you have a lab full of old Power PC Macs, and older PC's, you'll have an /opt/ltsp/ppc and an /opt/ltsp/i386 directory on the server.

eHow this is accomplished has thus far escaped me. I have only an /opt/ltsp/amd64 directory on my server and no amd64 machine to try booting off it. Doesn't seem to be much Ubuntu-specific documentation on the subject, I'm going to search the ltsp sites for a bit and let you know what I find.

db

---

### Post by clarknova on 2007-06-20
Ok, I found a pretty thorough guide to setting up ltsp on Ubuntu posted by a user named manway:

[http://ubuntuforums.org/showthread.php?t=465021&highlight=ltsp+i386](http://ubuntuforums.org/showthread.php?t=465021&highlight=ltsp+i386)

If you already have Edubuntu x86-64 Feisty server installed and you just want to add i386 client support, then a single command will do it:

> sudo ltsp-build-client --arch i386

After running this single command I was able to PXE boot an x86 client with no further configuration. I assume you would just change the arch to ppc or whatever you want to add support for other architectures.

Although there must be some lines you would have to add to /etc/ltsp/dhcpd.conf, as that particular file appears only to support i386 clients out of the box.

db

---

