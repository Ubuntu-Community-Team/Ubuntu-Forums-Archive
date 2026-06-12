---
title: "Offline codec install?"
date: 2007-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by idumych on 2007-06-13
Last night I ressurected a virus-clogged pentium 3 machine for my friend. Ubuntu runs so well on it I'm almost jealus, I suppose that's the difference between a desktop-class p3 and a Pentum 4 M.

Anyway, here's the deal. I need to make sure that this computer is useful for him, and he is has little if any computer knowledge. He needs to be able to play mp3s and videos, and he needs Wine. There is no way I'm going to be able to hook up his box to an internet connection since I'm in a dorm, but I have a GPRS connection on my laptop. Now, getting GPRS to work was real black magic and achemy, so I really don't want to have to do that on his box. So, how can I get a basic set of codecs and wine installed? I may be able to burn a dvd with debs at the library, but that's about it.

---

### Post by tgoose on 2007-06-13
If you put all the neccessary debs, and dependencies, in one directory, then in Ubuntu go to that directory in terminal and type ```
dpkg -i *.deb
```, they should all install.

---

