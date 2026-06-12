---
title: "Can't find map file on boot (with kernel errors)"
date: 2009-06-16
forum: x86 64-bit Users
---

### Post by Ashocka on 2009-06-16
I'm loosing initialization of home directory and mapping on boot.
> 
Jun 16 10:44:58 my-desktop syslogd 1.5.0#5ubuntu3: restart.
Jun 16 10:44:58 my-desktop kernel: Inspecting /boot/System.map-2.6.28-11-generic
Jun 16 10:44:59 my-desktop kernel: Cannot find map file.
Jun 16 10:44:59 my-desktop chat[3271]: timeout set to 60 seconds

Computer is crashing a few times a day now.

More complete log here
[http://pastebin.com/d662e4bbe]("http://pastebin.com/d662e4bbe") (until it expires)

Appreciate some advice on where I need to start to repair the installation... which has been running for a month. (Ubuntu 9.04/AMD64 upgraded from 8.04/8.10)

---

### Post by pixel :-) on 2009-06-16
It started out of the blue?

Do a memory test, 3° option in grub

Are you using ext4? don't. Reinstall

You upgraded the kernel? Boot with the previous kernel (in grub)

As a last resort reinstall

---

### Post by Ashocka on 2009-06-16
> **pixel :-) said:**
> It started out of the blue?
I can't think exactly what I was doing that might have triggered this.
> **pixel :-) said:**
> 
Do a memory test, 3° option in grub OK
> **pixel :-) said:**
> 
Are you using ext4? don't. Reinstall
Don't think so but will check
> **pixel :-) said:**
> 
You upgraded the kernel? Boot with the previous kernel (in grub)Yes, when I upgraded versions, but it was running fine except for sound, which I fixed
> **pixel :-) said:**
> 
As a last resort reinstall
Yeap... may come to this.  Any advice on backing up /apt/cache or anything to aid the reinstall?

Thanks for feedback
Geoff

---

### Post by pixel :-) on 2009-06-16
maybe if you reinstalled the kernel?

There isn't a tool for some repair on the live cd?

reinstalling grub, grub-install something, but theres a million ways the system can become unbootable, research this option seriously.

what do you mean initializing of home directory? Its read only?

About reinstalation

I recomend to have a /home and / on separate  partitions.

good idea to save

/var/cache/apt

/etc

---

