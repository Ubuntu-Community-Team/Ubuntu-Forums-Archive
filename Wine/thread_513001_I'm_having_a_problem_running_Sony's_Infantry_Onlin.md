---
title: "I'm having a problem running Sony's Infantry Online with wine."
date: 2007-07-30
forum: Wine
---

### Post by richardwad1 on 2007-07-30
It installs fine, but when I run it, it get to the zone selection screen and when I select a zone, where it would normally start downloading fiiles, the screen goes black. Any ideas on what might cause this? I looked on the wine website and they say it runs. I am running it in a virtual desktop, but I tried both ways.

---

### Post by SimonPhoto on 2008-01-26
I know this post is old, but I'll answer the question in case anyone else is having this problem.

I play Inf in wine all the time, and there are a few things that must be right.  Color depth must be set to 16-bit, and you must play in windowed mode.  Full-screen doesn't work, at least for me.

Everything else works just fine, as far as I can tell.  I normally play in Archlinux or PCLOS, but this worked when I play in Ubuntu as well on my desktop at work :)

---

### Post by richardwad1 on 2008-01-28
Thanks! I'll try it soon!

---

### Post by Zackie on 2008-02-18
For me it installed fine but when i opened it to login screen is just white but i can see some of the edges... I have it in windowed mode but not sure on how to change it to 16 bit.... any ideas?:guitar:


Had a friend make me an account when in game...  it just blinks over and over.... any ideas?

---

### Post by Cansy on 2008-03-04
I don't think there is any way to tell wine to pretend it is has 16 bit color depth.  I changed the color depth in xorg.conf to 16 and now infantry works fine.

---

