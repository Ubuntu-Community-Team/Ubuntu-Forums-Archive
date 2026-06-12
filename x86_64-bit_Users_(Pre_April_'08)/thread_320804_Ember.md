---
title: "Ember"
date: 2006-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by WhiteHorse on 2006-12-17
Any luck getting Ember to run on 64 bit Ubuntu? I have 6.10 Dapper Drake LTS and am trying to get it to compile from source. It seems like all of the libs in the repository are too old so I have to download/compile all the recent dependencies. I can get the latest Ogre to compile with the Synaptic package for CEGUI. Ember is compiling right now...

---

### Post by zingo on 2006-12-20
> **WhiteHorse said:**
> Any luck getting Ember to run on 64 bit Ubuntu? I have 6.10 Dapper Drake LTS and am trying to get it to compile from source. It seems like all of the libs in the repository are too old so I have to download/compile all the recent dependencies. I can get the latest Ogre to compile with the Synaptic package for CEGUI. Ember is compiling right now...

I manage to compile it 
I had to compile (in no perticular order)
Atlas-C++ 0.6.0 rc2
eris 1.3.11
Nvidia cg 1.5 beta2
ogre
skstream 0.3.6
wfmath 0.3.5
ember 0.4.1


I just got it starting then i have not played with it so much, my plan was to chip in on some simple coding work, I wanted to learn some orge programing and I have followed the progress of worldforge from a distance in a while (since about 1999) so my idea was to combine my interests... But as usual live got in the way...


I don't remember exactly what I did to get it to compile, ogre had some problems. If I remember correctly the configure script for ember was very help full. It basicly told me what it missed and what version, it needed of it.

Good luck 
/Zingo

---

