---
title: "Help required after reinstallation - sort of noob"
date: 2006-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by walkerx on 2006-06-30
I had to reinstall Ubuntu 6.06 (64bit) because it wouldn't boot when I replaced my other drives, and didn't know how to modify grub etc to make it work.

I now have the following issues, but everything was fine before I had to reinstall.

Nvidia 6800GT
I've reinstalled the nvidia-glx and enabled it, I get 3d graphics now without any problems, but when checking dmesg it reports that the nvidia taints the kernel. What does this actually mean.

Freecom DVB-T
I had this previously working as well, and managed to get it to work once since the re-install but now not loading the firmware. I've placed the firmware file in both kernel directories (the old one and the updated one I got after Ubuntu updated itself). I have installed all w32 codecs and also used Automatix, and then Automatix doesn't remember what it's installed

Grub
On the new install I need to edit the boot descriptions for my drives, as I have multiple drives and it is giving the wrong description for some of them so I want to change so shows correct details. How do I do this

Install DVD
The synaptic software and also apt-get update keeps reporting that the installation dvd is not correct, but I can go back in and re-add it and its then ok, but getting multiple entries in my sources list.

Printer
I have a hp-693c printer attached to a netgear printserver. If I set this up using cups and point it to the ip address I can print a single test sheet, but then nothing else. None of the other options work.

Any help on this is appreciated - and simple instructions on how to fix as not that brilliant with linux

regards
walkerx

---

### Post by Kilz on 2006-06-30
[QUOTE=walkerx]I had to reinstall Ubuntu 6.06 (64bit) because it wouldn't boot when I replaced my other drives, and didn't know how to modify grub etc to make it work.

I now have the following issues, but everything was fine before I had to reinstall.

Nvidia 6800GT
I've reinstalled the nvidia-glx and enabled it, I get 3d graphics now without any problems, but when checking dmesg it reports that the nvidia taints the kernel. What does this actually mean.

Freecom DVB-T
I had this previously working as well, and managed to get it to work once since the re-install but now not loading the firmware. I've placed the firmware file in both kernel directories (the old one and the updated one I got after Ubuntu updated itself). I have installed all w32 codecs and also used Automatix, and then Automatix doesn't remember what it's installed

Grub
On the new install I need to edit the boot descriptions for my drives, as I have multiple drives and it is giving the wrong description for some of them so I want to change so shows correct details. How do I do this

Install DVD
The synaptic software and also apt-get update keeps reporting that the installation dvd is not correct, but I can go back in and re-add it and its then ok, but getting multiple entries in my sources list.

Printer
I have a hp-693c printer attached to a netgear printserver. If I set this up using cups and point it to the ip address I can print a single test sheet, but then nothing else. None of the other options work.

Any help on this is appreciated - and simple instructions on how to fix as not that brilliant with linux

regards
walkerx[/QUOTE]

Freecom DVB-T
I dont know what it is, but it looks like you have it running, you mentioned win32codecs, [you might want to take a look at the first post of the sticky]("http://www.ubuntuforums.org/showthread.php?t=191205"). It has a work around for installing them.

Grub
The grub file is located in /boot/grub/menu.lst to edit it
```
gksudo gedit /boot/grub/menu.lst
```
Maybe someone else can help withthe others.

---

### Post by Lil_Eagle on 2006-06-30
Kilz:  Interesting you mention to sudo gedit something.  There's a nice [discussion ]("http://www.ubuntuforums.org/showthread.php?t=165957&highlight=gksudo+sudo") about how sudo and graphical apps don't get along, and how experienced users are telling newbie's to use sudo improperly.  Discussion belongs in another thread...
> Install DVD
The synaptic software and also apt-get update keeps reporting that the installation dvd is not correct, but I can go back in and re-add it and its then ok, but getting multiple entries in my sources list.
I would suggest commenting out the line in etc/apt/sources.list that refers to the cdrom.

To do that, type in a terminal:

gksudo gedit /etc/apt/sources.list

Place a '#' in front of the line (or just delete the whole line) that refers to the cdrom.  And yes, I do mean cdrom.  To Linux a DVD and a CD are the same thing.  They both use the /dev/cdrom symlink to /dev/cdrom0

You might also be interested in [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by Kilz on 2006-06-30
[QUOTE=Lil_Eagle]Kilz:  Interesting you mention to sudo gedit something.  There's a nice [discussion ]("http://www.ubuntuforums.org/showthread.php?t=165957&highlight=gksudo+sudo") about how sudo and graphical apps don't get along, and how experienced users are telling newbie's to use sudo improperly.  Discussion belongs in another thread...
[/QUOTE]
Thanks, I have to keep reminding myself to use gksudo for graphical applications.

---

### Post by tseliot on 2006-06-30
[QUOTE=walkerx]Nvidia 6800GT
I've reinstalled the nvidia-glx and enabled it, I get 3d graphics now without any problems, but when checking dmesg it reports that the nvidia taints the kernel. What does this actually mean.[/QUOTE]
It's not a problem

---

### Post by walkerx on 2006-06-30
thanks people

I've managed to get most of my system operational now

still only the bug with the dvb - i'll check the thread mentioned above to see if can get it to work

the 2nd is the printer
do i need to install anything else other than cups seeing its attached to a printserver

---

