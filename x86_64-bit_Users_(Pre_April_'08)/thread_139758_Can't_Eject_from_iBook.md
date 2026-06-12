---
title: "Can't Eject from iBook"
date: 2006-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by llanitedave on 2006-03-04
I'm using a g4 iBook that I bought in August of 2005.  I tried burning a CD using K3B, got the existing disk read, and got the message to eject the disk to insert a new one.  Then, it didn't eject!  I got an error instead.  There seems to be nothing I can do to make a disk eject -- event the F12 key on the keyboard doesn't work.

I had to boot back into the Mac side to get the cd to eject.

Anyone else have these problems?  Is there a fix?
I'm using Breezy Badger in Kubuntu.

Thanks, all.

---

### Post by pestilence4hr on 2006-03-04
Odds are if k3b thinks the disk has something on it, ubuntu has automounted it.  Look on your desktop, see if a cd icon appeared there.  If so, right click and unmount it, then eject should work.

---

### Post by llanitedave on 2006-03-05
Part of the problem is that at the time there was no right click.  I was using the laptop remotely, and I didn't have the mouse along -- using the keypad only.

I was copying a cd for a friend, and K3b had already read the contents of the disk, and was trying to eject it so that I could insert the blank disk for writing.  But nothing would cause the disk to eject, not automatically through K3b, and not manually either.

I had to reboot to the Mac side, and do the copying from that.

How embarrasing!

---

### Post by ssam on 2006-03-05
F12 and F11 should be mapped to right and middle click. you may need to hold 'fn' down aswell to get the eject.

you can always eject a disk from a mac by holding down the mouse button at boot time.

opening a terminal (Applications -> Acessories -> terminal) and typing 'eject' may eject some disks.

places -> computer and right clicking (F12) on the cd drive may let you eject.

hope one of these helps

---

