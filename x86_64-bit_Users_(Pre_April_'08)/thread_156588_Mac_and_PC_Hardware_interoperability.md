---
title: "Mac and PC Hardware interoperability"
date: 2006-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ububurns on 2006-04-07
I've been using a PC soundcard in my Mac, and it works perfectly (except for running jack).

Should I also be able to use, say, a GeForce4 card I have lying around from a PC, in my Mac?  Or, do I need to buy Mac-specific hardware?

---

### Post by dpny on 2006-04-07
I know that it's possible to use PC graphics cards under OS X given a little modding, which can include flashing to BIOS on the card. I don't know enough about how Linux handles hardware to know, though.

---

### Post by mjg59 on 2006-04-07
It's possible, but not terribly likely I'm afraid - without a Mac ROM in your video card, the Apple firmware won't be able to initialise video. Without it doing that, I'm not sure whether Linux will be able to bring up a framebuffer. It might be worth a go - the worst that can happen is that the machine will refuse to boot.

However, graphics are a pretty special case. Almost any other PCI card that works in x86 Linux should work fine on PPC Linux.

---

### Post by jdp on 2006-04-07
You might be able to use a PC card as a secondary under Linux without reflashing the ROM, but you won't be able to use it as the boot/main screen.  Be aware that not all cards can be flashed successfully.

---

### Post by 3rdalbum on 2006-04-09
I just want to check whether an optical USB mouse for PCs would work on PPC Breezy, before I shell out $7 :-)

---

### Post by jdp on 2006-04-09
Probably, and it stands a good chance of working in OS X too.  That whole 1-button mouse thing is just a long time Apple supported case of FUD.

---

### Post by 3rdalbum on 2006-04-11
Yeah I bought the mouse and it works perfectly on Ubuntu. It even works as a one-button mouse on OS 9.

---

