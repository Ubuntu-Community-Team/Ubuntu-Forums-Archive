---
title: "switch discs problem"
date: 2008-10-24
forum: Wine
---

### Post by odedkarp on 2008-10-24
hey every body.
I tried to install Sims 2 with wine and when i should to switch the disc the computer do not let me to eject the disc. the error message was that it cant unmounted the volume.
what can i do? 

Oded.

---

### Post by hikaricore on 2008-10-24
Try this:

[http://wiki.winehq.org/eject](http://wiki.winehq.org/eject)

decided to quote it also:
> eject is a function of Wine. It is used to free, unlock, and eject an optical device when Wine is using it.

Note: in order to eject, the drive must be correctly set up in winecfg and must be invoked with wine preceding it.

[QUOTE]Usage

 wine eject [-u] [-a] [-h] [x:]...
    -a  Eject all the CD drives we find
    -h  Display this help message
    -u  Unmount only, don't eject the CD
    x:  Eject drive x:

useful when trying to install mutidisk installs

1. wine /media/cdrom/setup.exe (or whatever it's called)

2. when the installer prompts for the 2nd disc, go to another window and run "wine eject" if just pressing the button doesn't let go of the disc[/QUOTE]

---

### Post by scragar on 2008-10-24
Using umount with the -l option will work, but there's a chance of wine crashing then, so be warned:
```
sudo umount -l /media/cdrom0
```

---

### Post by odedkarp on 2008-10-24
it eject the disc to me but when i insert disc number 2 the installion it no accept this disc and i saw that the first disc is still mounted.

---

