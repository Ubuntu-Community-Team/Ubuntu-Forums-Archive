---
title: "Yet Another Halo Thread"
date: 2007-12-10
forum: Wine
---

### Post by soluphobe on 2007-12-10
Sorry, I am a reluctant thred-necro, so I commit the sin of making my own thread.  

I am trying to run Halo: Combat Evolved on Ubuntu 7.10 under wine 0.9.46.  The machine in question has 32 MB graphics and 2.2 Ghz CPU (The game runs fine under the windows partition, so no graphics issues).  Intel processor and some SiS graphics.  Wine directory is pretty clean - has nothing but FilZip (an archive manager to get the .rar no-cd) and some ancient game that doesn't run.

What I did:

I followed all the instructions on the How-To for 0.9.39, full knowing that my version of wine was beyond the safe zone for H:CE.  I ran it a couple of times and it crashed about two minutes into the loading screen each time.  I examined terminal output and found a line requesting a process from faultrep.dll.  I searched my .wine/.../system32 and didn't find faultrep, so I copied it over from my windows partition.  faultrep wanted winsta.dll, so I brought that over too.  

I then ran it and got some sort of error about '... flags 2 not supported.'  I've reached the end of my rope - is there something I can do?

---

### Post by cogadh on 2007-12-10
The SiS driver in Linux is not capable of 3D hardware accelerated graphics, that game will never run on your system, regardless of the Wine version used.

---

### Post by soluphobe on 2007-12-11
Aww...

Thanks, though.  I guess I won't waste any more time on it.

---

### Post by Sockerdrickan on 2007-12-11
I think halo is a pretty cool guy. Eh kills aliens and doesnt afraid of anything

---

