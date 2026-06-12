---
title: "When I compile wine, windows buttons and fonts get trashed"
date: 2008-03-24
forum: Wine
---

### Post by Mr.Johnny on 2008-03-24
I have done apt-get build-dep wine and get no compile errors, but I notice that when I compile wine myself, fonts and window's maximize, minimize and restore buttons get trashed.

When I install the repository version that comes a few days after, everything is working.

Is there any extra setting I should be aware of when compiling wine myself?

thanks

---

### Post by Mr.Johnny on 2008-03-25
bump

---

### Post by h4mx0r on 2008-03-26
try installing fontforge and icotool. At winehq site they have a gutsy.sh file for installing what you need to compile wine but they leave out a lot and don't consider wine might be only thing you compile. Attached is my special gutsy.sh you can open it with any text editor and review it, its all the dependencies you will need for compiling and running. You might want to consider getting a hex editor such as "bless" (getdeb.net) or cabextract for extracting things.

---

### Post by Mr.Johnny on 2008-03-26
Thanks! :D I'll add it to my notes.

I had noticed that besides apt-get install build-dep wine I also had to do 
apt-get install libxi-dev
apt-get install libxinerama-dev

but after that it would not complain about anything else.

Also (althought not related to this) in x64 ubuntu, following the official guide doesn't stop it from complaining about a lot of stuff missing.

---

### Post by h4mx0r on 2008-04-08
Yeah wine didn't complain about anything to me either but then I did winecfg and noticed it had no sound!?:confused: anyway I got the alsa -dev and it worked fine.

---

