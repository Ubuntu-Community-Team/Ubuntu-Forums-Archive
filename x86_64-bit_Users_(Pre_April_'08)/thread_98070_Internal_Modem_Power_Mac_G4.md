---
title: "Internal Modem Power Mac G4"
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by alfred on 2005-12-02
I will keep searching the forum on this but I installed ppc ubuntu on a power mac g4 and dialing out seems to be not working.
I used the gnome /ubuntu network settup program it seems to fine the modem and the tries to dial out.
Is the hardware supported.
Thanks
Al

---

### Post by ssam on 2005-12-03
its hard to tell whether this era of machine would have a hardware or software modem. software modems are smaller and cheaper, but need special drivers. hardware modems have very simple interfaces and are easily supported by linux.

my g3 imac had hardware my g4 powerbook has software modem.

opening a teminal, and running
```
wvdialconf /dev/null
```
should let you know if you have a supported modem.

---

### Post by autocrosser on 2005-12-04
Alfred--I'm afraid that if you have a "newer" G4--it is a software modem--I cruised eBay & bought a Zoom 2986L USB Modem that was reconized/configured with ease by GnomePPP--With a slight amount of tweeking, I'm getting about 44k down--cost was $15 + shipping

That worked for me-----

---

### Post by alfred on 2005-12-16
Thanks for the replies guys.
That /dev/null worked out. 
I've been swamped with a learning curve here that same user who I was setting the G4 up with also wanted their iBook set up and above that trying to train on Ubuntu.  
Anyways the modem started working ie I got lucky with pppconfig and it was go, same with the older iBook.
I will keep the /dev/null handy for later.
I posted a question on Bonobo error else where on the site if you have any more thoughts as I try and get this laptop to them.
Thanks again,
Al

---

