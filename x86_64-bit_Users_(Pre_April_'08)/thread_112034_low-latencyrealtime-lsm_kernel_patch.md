---
title: "low-latency/realtime-lsm kernel patch?"
date: 2006-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ughhhh on 2006-01-03
Hi all, 

I'm pretty much a newbie with Linux

I've put Ubuntu on an old G3 iMac/600 with the goal of installing SuperCollider (sound synthesis server and language). The thing that's been holding me up is trying to install the low-latency kernel patch, there just doesn't seem to be an easy way to do it through Ubuntu. 

I'm comfortable with "apt-get install *" but everything I find on the internet seems to be for non-ppc machines. I've also found pre-compiled kernel patches for PowerPC, but I have no idea how to install them. 

Anybody have any ideas? 

Here is a page that details all that goes into installing SC on a linux machine: 
[http://swiki.hfbk-hamburg.de:8888/MusicTechnology/478](http://swiki.hfbk-hamburg.de:8888/MusicTechnology/478)

---

### Post by 23meg on 2006-01-03
realtime-lsm was obsoleted by rtlimits, which it seems is already built into the Breezy kernel. You can also use DeMuDi's patched multimedia kernel; for info on both, see [this thread]("http://www.ubuntuforums.org/showthread.php?t=97453").

---

