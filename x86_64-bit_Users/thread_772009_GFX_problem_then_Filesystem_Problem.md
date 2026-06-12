---
title: "GFX problem then Filesystem Problem"
date: 2008-04-28
forum: x86 64-bit Users
---

### Post by IsotropicSpin on 2008-04-28
:confused::confused::confused:](*,)](*,)

ok... heres what happened (right in the middle of writing a college essay!). (from the very beginning)

1.Installed Hardy Heron 64bit.
2. Cool AWESOME! Fun for a week.
3. One day: in the middle of essay using TomNotes: BLACK computer turns off
4. Check it out. Seems to be power supply. Cool! Replace it. Windows starts up fine. Ubuntu on the other hand gives me "Could not start the X server (your graphical interface) etc blue screen of death right after the login screen.
5. Restart, this time I cant even get to the login screen because i get Automatic File System check failed.

I am writing this in windows on the same machine.
I don't know how to pastebin stuff because I don't know how to get into terminal.
I have an NVIDIA graphics card, 64bit AMD Dual Core 3600 processor. 

Please help! My precious essay notes are on there!

(Also if anyone could tell me how to get into the linux file system from Windows and where tomboy notes are stored so i can back those up first that would be a pleasure!)

THANKS!
Bit of a n00b who decided to be adventurous and get the 64bit so spell things out a little!
Everything worked fine on Gutsy Gibbon

---

### Post by madjr on 2008-04-28
use the live-cd to get your stuff.

thats why we make them for emergency situations like this.

Not only if something happens to Ubuntu, but if something goes wrong with windows too.

didn't you burn it ?

---

### Post by IsotropicSpin on 2008-04-28
> **madjr said:**
> use the live-cd to get your stuff.

thats why we make them for emergency situations like this.

didn't you burn it ?

Ok thanks! As I said: please state the obvious.

Will do! But how to fix this problem with the X server (I think thats GNOME) failing with NVIDIA card and also the file system thingy.

Thanks

---

### Post by Julius on 2008-04-28
Maybe the new power supply is not giving enough power to the graphics card?

---

### Post by IsotropicSpin on 2008-04-28
that wouldn't be the case since it works with windows fine

---

### Post by Yellow Pasque on 2008-04-28
It sounds like your filesystem got corrupted because your computer shut down improperly. Use the LiveCD to run fsck on it. Also, mount the filesystem and look for /etc/X11/xorg.conf on it (i.e. not the LiveCD's /etc dir, but something like /media/disk/etc..). Make sure the file is present and open it to make sure it's not corrupt.

---

### Post by Falcorian on 2008-04-28
> **Temüjin said:**
> It sounds like your filesystem got corrupted because your computer shut down improperly. Use the LiveCD to run fsck on it. Also, mount the filesystem and look for /etc/X11/xorg.conf on it (i.e. not the LiveCD's /etc dir, but something like /media/disk/etc..). Make sure the file is present and open it to make sure it's not corrupt.
And just to state the obvious... I'd recover and backup your files BEFORE running fsck. ;)

---

### Post by Yellow Pasque on 2008-04-28
> **Falcorian said:**
> And just to state the obvious... I'd recover and backup your files BEFORE running fsck. ;)
And how do you propose that be done?

---

