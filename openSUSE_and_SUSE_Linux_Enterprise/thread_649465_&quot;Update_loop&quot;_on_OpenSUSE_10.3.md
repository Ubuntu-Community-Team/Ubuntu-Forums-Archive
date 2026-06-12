---
title: "&quot;Update loop&quot; on OpenSUSE 10.3"
date: 2007-12-24
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Moonfrost on 2007-12-24
OpenSUSE 10.3, ever since installation this morning keeps telling me there's an update for Amarok which I installed at least five times already, the problem is every time I reboot the computer or shut it down and turn it back on the exact same update appears all over again...also tried logging is as root and the same thing happens...does anybody know what could this be? it's getting annoying...

---

### Post by igknighted on 2007-12-25
> **Moonfrost said:**
> OpenSUSE 10.3, ever since installation this morning keeps telling me there's an update for Amarok which I installed at least five times already, the problem is every time I reboot the computer or shut it down and turn it back on the exact same update appears all over again...also tried logging is as root and the same thing happens...does anybody know what could this be? it's getting annoying...

Update via the cli instead... it needs your response to something that the update icon can't handle.

---

### Post by Moonfrost on 2007-12-25
> **igknighted said:**
> Update via the cli instead... it needs your response to something that the update icon can't handle.

What's the cli?

---

### Post by RebounD11 on 2007-12-25
CLI = command line interface :D I had a hard time figuring that one out too

for me that didn't work either... I disabled the update repos 1 by 1 until I found which one caused the problem... later on I installed a newer amarok (the one with the 8 at the end :D) and I reenabled my repo... no more problems afterwards.

---

### Post by Moonfrost on 2007-12-25
> **RebounD11 said:**
> CLI = command line interface :D I had a hard time figuring that one out too

for me that didn't work either... I disabled the update repos 1 by 1 until I found which one caused the problem... later on I installed a newer amarok (the one with the 8 at the end :D) and I reenabled my repo... no more problems afterwards.

I also have the latest version of Amarok now but the update thing keeps appearing...I'll have to check which is the repo giving me the problems...and I knew cli had to do with "command" but you don't see a lot of people referring to them like that...most people say a command prompt or shell or console and so on...

---

### Post by Gallius25 on 2007-12-31
I had the same problem (10.3 64bit here). All I did to fix it was run the "Online Update" in YaST and install it from there.

---

### Post by r4ik on 2007-12-31
It worked indeed thanx.

---

