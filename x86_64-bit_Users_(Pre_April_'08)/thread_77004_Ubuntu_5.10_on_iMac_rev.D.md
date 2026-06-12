---
title: "Ubuntu 5.10 on iMac rev.D"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by tuzzer on 2005-10-16
I am trying to install 5.10 on an iMac rev.D (333Mhz PowerPC 705, 160Mb RAM, 6Mb Video RAM).
Everything goes fine until the end of the guided standard installation (i just press enter at boot from CD, without typing any special command).

When the installation process ends and the the first startup from HD begins, everything stops with the message "Please wait, loading kernel", i've waited 10-20 minutes but nothing else happens.

I tried to boot with rescue powerpc option, but i don't know what to do with  the filesystem i mount to change boot options

I tried to type ' help ' at boot and two options appear: 'Linux' and 'old', I don't see ' * ' indicating default image

(before installing Ubuntu i tried to install Fedora 4 PPC, but I formatted the HD during the guided Ubuntu installation)

I selected Italian as system language, at the last step of installation a message said that some localization was missing and asked if I want to download from web, (I answered yes expecting an Internet connection during first boot) can this be the reason of the strange behavior at boot?

What can I try to make it work?

Thanks

---

### Post by tuzzer on 2005-10-17
[QUOTE=tuzzer]
I tried to boot with rescue powerpc option, but i don't know what to do with  the filesystem i mount to change boot options
[/QUOTE]

I found /etc/yaboot.conf

here is what it says (I wasn't able to redirect it to another PC so I wrote it down and then wrote it here, I tried to report it exactly, hope I made no typing errors)

> 

boot=/dev/hda2
device=/pci@80000000/mac-io@10/ide@20000/disk@0:
partition=3
root=/dev/hda3
timeout=50
install=/usr/lib/yaboot/ofboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"



Does anyone know what to change to make my iMac load the kernel?

---

### Post by ChantalC on 2005-11-06
Just installed Ubuntu 5.10 on an iMac 233/B. I have got the same problem. Any solution?

---

### Post by tuzzer on 2005-11-09
I gave up and installed Fedora4

---

### Post by at_a_loss on 2005-11-09
We just installed ubuntu on 3 different imacs (all g3s).  We had all sorts of problems installing it on two of them - the third went off without a hitch.  On the two that were causing us problems, we installed debian instead and upgraded to breezy.  That seemed to work.  We still haven't gotten sound working on any of them, though.

---

### Post by MySchizoBuddy on 2005-11-11
even the Live CD doesn't work on G3 iMAC
It boots up asks for setting etc, then resolution and then i see the loading bar and then it goes blank and nothing happens.

---

### Post by neoplasticity on 2005-11-22
so no one has figured out why it installs on some g3 imacs and not on others?

i am buying a imac 333/rev D to install ubuntu on and am worried now :???:

---

### Post by gconn77 on 2005-12-11
I wanted to bumb this up, because I am attempting to install on this computer as well. At the moment I am in the process of burning ths iso image...

---

### Post by Lockranore on 2006-03-05
A friend just bestowed three iMac 333's on me; I was able to install Ubuntu on one, but not the other two.

I found that only one of the three had extra memory installed; the base 32 megs is built in, and my working model had a 64 meg SO-DIMM installed.

So I tried moving the SO-DIMM two one of the other two units, and had no trouble installing.

Hope this helps!

By the way, has anyone else found decent ways to get Gnome running bearably on the iMac D?  I've tried using x4ce, and it's fair, but I'd much rather use Gnome.

---

### Post by jdp on 2006-03-05
To get Gnome running more bearably, make sure you've got X configured to have accellerated ATI video, and certainly make sure you installl 128MB+ RAM.  It makes as much of a difference for Gnome as it does for OS X.

---

### Post by littlewing0906 on 2006-03-15
I have a iMac 64 Rev A ... I have the same problem, 'loading kernel....' and nothing. BUMP!

---

