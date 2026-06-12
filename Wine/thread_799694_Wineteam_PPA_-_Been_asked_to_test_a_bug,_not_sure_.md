---
title: "Wineteam PPA - Been asked to test a bug, not sure what to do."
date: 2008-05-19
forum: Wine
---

### Post by philinux on 2008-05-19
I reported a bug due to this post.
[http://ubuntuforums.org/showthread.php?t=797342](http://ubuntuforums.org/showthread.php?t=797342)

Been asked to do this.

Please test the Hardy package in the Wineteam PPA here: [https://launchpad.net/~ubuntu-wine/+archive](https://launchpad.net/~ubuntu-wine/+archive) and tell me if it fixes your problem. Thank you.

Not a clue what I'm supposed to do. Does he mean install RC1 and test TRA. Or something else.

---

### Post by YokoZar on 2008-05-19
Yes, I mean install the package in that PPA by adding it to your sources.list.

sudo gedit /etc/apt/sources.list.d/wineppa.list

paste
deb [http://ppa.launchpad.net/ubuntu-wine/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ubuntu) hardy main

and then install the newer package (it will be unverified because it's in the PPA and not an official archive)

---

### Post by philinux on 2008-05-19
Ok followed instructions - will test tonight.

What is sources.list.d, I notice medibuntu is in there too, and ppa. Still learning. :)

---

### Post by philinux on 2008-05-19
Tested sooner than I thought.

Orignal tra.exe looks for the dvd tries to start then crashes as before.

The tra.exe nocd version works fine.

---

### Post by _Stevie_ on 2008-05-20
that means TRA works in wine? damn! i just installed it in windows lol

---

