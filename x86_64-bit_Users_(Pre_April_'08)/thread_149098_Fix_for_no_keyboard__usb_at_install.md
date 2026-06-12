---
title: "Fix for no keyboard / usb at install"
date: 2006-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by stmiller on 2006-03-23
I saw several posts of people having problems with this. This should perhaps be in the installation notes for PPC.

At the boot, press TAB to get specific arch options. You have to pick what is specific to your machine. 

Ex:

install-powerppc64

Then install should go okay.

---

### Post by glennric on 2006-03-23
[QUOTE=stmiller]I saw several posts of people having problems with this. This should perhaps be in the installation notes for PPC.

At the boot, press TAB to get specific arch options. You have to pick what is specific to your machine. 

Ex:

install-powerppc64

Then install should go okay.[/QUOTE]

This doesn't work.  The keyboard and mouse still lock up as soon as anything tries to play a sound.

---

### Post by linear on 2006-03-23
Is this a G5? There was a fix posted here some time ago - it involves (surprise!) disabling sound.

---

### Post by ssam on 2006-03-23
seems like bug [https://launchpad.net/distros/ubuntu/+source/gdm/+bug/29368](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/29368)

i marked the bug as being in esd, so hopefully the right people will have a look at it.

---

### Post by glennric on 2006-03-23
[QUOTE=linear]Is this a G5? There was a fix posted here some time ago - it involves (surprise!) disabling sound.[/QUOTE]

Yeah, do you really call that a fix?  A work around perhaps, but not a fix.

---

### Post by linear on 2006-03-23
My bad! I concede that it's a workaround. :-#

---

### Post by mufapu on 2006-03-26
Had the same problem on my PC, so it's not Mac/Sound driver related.

The solution for me was simple. There's a bios option "enable USB keyboard" (as well as one for a USB mouse). When enabled the keyboard kept working after initial boot and during Ubuntu install.

Embarrasingly simple really. What threw me off was the fact that the first few seconds at boot up my keyboard does work (I can skip memory check and go into the bios setup). 

Try it out!

---

### Post by jdp on 2006-03-26
Macs don't have that option, let alone a BIOS.  If a Mac has factory USB, it can use USB peripherals normally.  There is no "emulation" needed.  It is sound related, as disabling sound stops the lockups... ;)

---

