---
title: "Firewire issues"
date: 2005-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by X5-655 on 2005-11-17
I am having a problem with the Firewire port on my Mac mini, when booted into Ubuntu Linux.

if my iPod is connected, it shows on the desktop, along with the Firewire HD I have connected.  However, if I go to Places, and click Computer, it shows like 20 iPods, and 50 of my Firewire HD, and only one of them actually loads either the iPod or my Firewire HD..

What's causing this?  both the iPod and my Firewire HD are formatted as HFS+.  but if I hook the iPod to a PC with Ubuntu Linux and use a USB cable, it works just fine...

---

### Post by ssam on 2005-11-17
sounds odd.

have you played around with stuff, edit config files or anything? does it happen if you boot from the live cd?

what does the folder /media/ look like? does that have the multiple entries?

---

### Post by X5-655 on 2005-11-17
[QUOTE=ssam]sounds odd.

have you played around with stuff, edit config files or anything? does it happen if you boot from the live cd?

what does the folder /media/ look like? does that have the multiple entries?[/QUOTE]
im only booting off the Live CD, as I haven't partitioned a spot on my HD just yet to dual boot..

configuration files would be useless, as it's a CD, rebooting and changes are gone...

ill check what that folder looks like when i boot back to linux (im under OS X on iChat right now)

---

### Post by X5-655 on 2005-11-17
[QUOTE=ssam]sounds odd.

have you played around with stuff, edit config files or anything? does it happen if you boot from the live cd?

what does the folder /media/ look like? does that have the multiple entries?[/QUOTE]
here's what i'm talking about..  and /media looks just fine and clean...

btw, i also noticed i can't access my Mac minis internal HD, where OS X is..

---

### Post by ssam on 2005-11-17
ok, i can explain those :-)

on a mac formated disk there are a whole load of hidden partitions a few kb in size. in mac os they are always hidden. in linux sometimes they are visable.

i think they hold things like disk drivers and stuff that mac os needs to boot. i dont think they are in any normal filesystem format so you can't mount them.

best not to worry about them. (or if you are able, write a patch to nautilus to stop them being shown.) (or fire a bug, and hope that someone fixes it)

---

### Post by X5-655 on 2005-11-17
[QUOTE=ssam]ok, i can explain those :-)

on a mac formated disk there are a whole load of hidden partitions a few kb in size. in mac os they are always hidden. in linux sometimes they are visable.

i think they hold things like disk drivers and stuff that mac os needs to boot. i dont think they are in any normal filesystem format so you can't mount them.

best not to worry about them. (or if you are able, write a patch to nautilus to stop them being shown.) (or fire a bug, and hope that someone fixes it)[/QUOTE]
thanks!  :)

just one more question if you don't mind....  how can I access my Mac minis internal HD, the one with OS X on it?  It doesn't show at all, and under adminstration, "Disks", it shows, and I find the large partition, the one that has to be it, and trying to mount it goes no where, just a little pause and then just nothing...

---

### Post by kingler on 2005-11-17
the answer is here:
[http://ubuntuforums.org/showthread.php?t=88590&highlight=hfs](http://ubuntuforums.org/showthread.php?t=88590&highlight=hfs)

[QUOTE=X5-655]thanks!  :)

just one more question if you don't mind....  how can I access my Mac minis internal HD, the one with OS X on it?  It doesn't show at all, and under adminstration, "Disks", it shows, and I find the large partition, the one that has to be it, and trying to mount it goes no where, just a little pause and then just nothing...[/QUOTE]

---

