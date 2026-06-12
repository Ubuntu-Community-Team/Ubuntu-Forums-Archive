---
title: "yea..just wondering"
date: 2005-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by sunrex on 2005-11-16
on my ubuntu64bit desktop i couldent change res..it works fine with x86 kubuntu breezy, and ubuntu hoary...so... will it work on kubuntu breezy 64bit? please dont lie or make up tales...since i really dont want to do a reinstall just to find out it doesnt work

---

### Post by tokyovigilante on 2005-11-16
You need to be much more specific both in your post title and in your description of your problem (i.e. what hardware and drivers you have, and the specifics of what resolutions work, don't work, and what measures you have tried) before anyone can help you. 

I would suggest that you check your /etc/xorg.conf under AMD64, and run ```
dpkg-reconfigure xserver-xorg
``` as a first port of call.

---

### Post by sunrex on 2005-11-16
i did. i also tried manualy editing it..hmm ill look it up on the kubuntu desktop..

---

### Post by nikodell on 2005-11-17
I did too and I just had to fix my sync rates in xorg.conf now I can chanse settings from KDE desktop

---

