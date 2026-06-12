---
title: "Greetings,Salutations &amp; ?'s"
date: 2006-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by butchca on 2006-04-11
Hello All.
Been lurking about a week now, time to jump in.

Running a eMac 800, 512 ram, G4, Tiger & a G5 1.8 dual processor
I recently became interested in  a new potential hobby, namely the construction
and operation of home built CNC (computer controlled machinery), Unfortunately
Mac is weak in the CAD/CAM/CNC area. Research revealed Linux offered a viable
alternative to machine control via real time architecture and emc (enhanced machine control) Created a dual boot setup on the eMac with Ubuntu 5.10.
Jumped through 3 days worth of hoops almost resolving nVidia driver problem,
which brings me to my first question.

When I first got program loaded it would boot fine, and I could even hear the drum intro, but...no video...searched the forum....did the edit xorg.conf then xvidtune
trick, but in xvidtune it would get the screen position very close to the correct position, then show an error. If I accepted the closest I could get without error,
then re-edit xorg.conf & re-boot, I would now have a screen, but I'm still missing a little bit of the left side of the screen ie:I can see the whole word "Applications" in the top menu.

Any ideas?

Way more questions, but getting too verbose.

More to follow

Very intriguing OS & concept!!

Thx.
Butchca

---

### Post by tidris on 2006-04-11
I don't have an answer to your problem, but I would like to know how you plan to control the CNC hardware from a Mac. Most people seem to use the parallel port in a PC, but Macs don't have parallel ports.

---

### Post by butchca on 2006-04-12
Haven't addressed that issue yet, it's on the list, was hoping I can find
some kind of USB>parallel adapter. 

Thx. for the reply!

---

### Post by jdp on 2006-04-12
The problem with USB->Parallel adapters is that you can't usually bit-bang the lines, thus many of the high speed or custom uses for a parallel port don't work.  Most USB adapters only work for generic printer connections.

---

