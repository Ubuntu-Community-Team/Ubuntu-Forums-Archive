---
title: "[SOLVED] Ubuntu install-cd not working"
date: 2008-09-10
forum: x86 64-bit Users
---

### Post by aupo on 2008-09-10
Hi! I'm mostly new to Linux, and just got a new laptop with an Intel Core2Duo P9500 CPU (it's 64bit ofc) and nVidia GeForce 9800M GT video card (heard it could be a problem.)

I downloaded the 64bit Ubuntu installer, burned it on a DVD (and cd-rw too, but that complained about i/o error) and tried to run, but I ended up in a situation where the "main menu" of the install disk doesn't respond to some keys, for instance e and i (if I remember correct), but the most annoying one was the fact that it didn't respond to Enter in any other place except "Boot from first hard disk". Tried to press Enter on the "Install Ubuntu" choice, no avail. Any other place except hard disk booting, no avail, but it gladly left the installer and booted from hard disk.
There is a Win Vista installed on the computer, but I don't think that should be much of a problem?


More about the computers specifications can be found here:
[http://kobaltcomputers.co.uk/nexus_specifications.php](http://kobaltcomputers.co.uk/nexus_specifications.php)

Anyone have any idea how to get the damn Ubuntu installed? :)

UPDATE: gotten through the problem with _starting_ the install, but new problems arise. Read lower to find the full log of the error.

---

### Post by aupo on 2008-09-10
Hmm, small update. I just tried the acpi=off installing, and when pressing enter (should start install, right?) it says: "Loading. / Invalid or corrupt kernel image."

---

### Post by aupo on 2008-09-10
Oh, and I actually even burned a 32bit installer, and when trying that, after pressing Enter on "Install Ubuntu", the whole thing just freezes. It seems to be doing something in the background (DVD spins, cpu fan humms etc) but nothing changes on-screen. Could it be because of the 32bit/64bit not liking each other, or from video card or?

---

### Post by jespdj on 2008-09-10
In the boot menu, you can select a disc check to see if the CD you burned contains errors. Try running that and see if it reports any errors.

You say that when you burned it on a CD-RW and got an I/O error. That sounds like there might be something wrong with the disc that was burned. Did you download a CD image? I didn't even know you could burn that onto a DVD. Try using a normal CD-R and burn at a lower speed, to make sure that the disc is OK.

---

### Post by aupo on 2008-09-10
jespdj: Careful reading reveals that only the "Boot from first hard disk" option works, all other either (on 64bit) do nothing or (on 32bit) freeze the screen (at least).

The CD-RW is indeed rather old and might be damaged, though you never know. Mmm, and about burning on a DVD, I'm not that sure myself either, it seemed to work fine for the start-up part at least, but there indeed might be some friction... Well, I'll have to get my hands on a regular CD-R to test that out too, problem is that there are none nearby *laugh*

Thanks anyways *smile*

---

### Post by Sef on 2008-09-10
> and cd-rw too, but that complained about i/o error

You can use a CD-RW to burn the iso to and install from it.  Could be you have a bad cd-rw or the burn was bad, or the md5sum.

---

### Post by aupo on 2008-09-11
Yah, tried reburning the CD-RW with slow speed (and also fully cleared it first) but it still complains about i/o-error: "Error reading boot disk" or something.

There are few _minor_ scratches in the disk, so they might affect, you never know, but I'm off to school now and will go buy myself new CD's etc. Hope this'll work out...

---

### Post by aupo on 2008-09-11
Okay, now I got the installer working, at first. The installer started up and started installing ("Loading kernel"), but after that it ends up in built-in shell and says:
"[   129.114368] ata2.00: revalidation failed (errno=-5)
[   129.149872] ata2: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
[   129.149923] ata2: irq_stat 0x40000008"

---

### Post by aupo on 2008-09-11
Well, problem "solved", just installed Debian and left Ubuntu alone.

---

