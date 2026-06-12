---
title: "Flock x64 can't find Flash x64"
date: 2009-02-04
forum: x86 64-bit Users
---

### Post by joey-elijah on 2009-02-04
I've gone through the how to above, but still no joy.

Flash x64 works (pretty much) flawlessly in Firefox x64 and in a youtube screenlet and elsewhere bar Flock x64.

I've installed the .so file into a created /opt/flock/plugins as well as in usr/share/flock/plugins and extensions. Bit i still get the "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest flash player." yarn. 

I've also downloaded and install the 'Get64Flash' script thingy from the how to, but alsa, no comprendez!

---

### Post by redhed on 2009-02-05
I had the same problem, so I ran flock from the command line and I saw errors about the plugins I had linked from the mozilla directory being the wrong version. It seems that the flock debs and tar files available on the web are actually 32bit even though they say they are for amd64. I installed the 32bit flash plugin for flock and now it works.

I wish I could actually find a 64bit version of flock somewhere it would make my life easier.

---

### Post by empty_spaces on 2009-06-23
Thanks Redhed, that did the trick for me.

---

