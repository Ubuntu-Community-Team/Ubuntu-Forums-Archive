---
title: "[SOLVED] Firefox 3 bloating?"
date: 2008-11-23
forum: x86 64-bit Users
---

### Post by unknown03 on 2008-11-23
I did have the opportunity to install the 180.06 driver but I'm not yet sure if its nVidia related. 
I disabled IPV6 in firefox and web browsing is the same, but that really wasnt the problem.

It seems that the more I use firefox, the slower it seems to get when switching between tabs, scrolling, browsing, etc.

A fresh install of Ubuntu and firefox is lightning fast. But now it seems like its bloated and takes a while to load ANYTHING.

Anyone else notice this?

My specs:

AMD Athlon X2 5000+ 2.6Ghz Dual-Core processor
Gigabyte Ga-m57-sli-s4 Motherboard
2x 320GB HDD
4GB RAM
nVidia Geforce 9800GTX
Gigabyte 800W PSU

---

### Post by unknown03 on 2008-11-24
Really? No one?

---

### Post by CholericKoala on 2008-11-24
> **unknown03 said:**
> Really? No one?

I went to opera for awhile, then switched back.  FF3 for me works pretty well comparatively.

---

### Post by unknown03 on 2008-11-24
I used to be an Opera user for a long time. I especially love the mouse gestures. Problem was it kept crashing and flash didnt work very well

---

### Post by Cracauer on 2008-11-24
So it's getting slower over time?

What's

du -a ~/.mozilla/firefox/<yourprofile>/. | sort -n | tail -20

?

---

### Post by unknown03 on 2008-11-24
Yeah its getting slower over time. When opening up a new tab or switching between them it takes up to 10 seconds when it used to be instant.

```
unknown@unknown-desktop:~$ du -a ~/.mozilla/firefox/mj758oqs.default/. | sort -n | tail -20
76	/home/unknown/.mozilla/firefox/mj758oqs.default/./Cache/6584183Bd01
84	/home/unknown/.mozilla/firefox/mj758oqs.default/./Cache/03C42E2Ad01
92	/home/unknown/.mozilla/firefox/mj758oqs.default/./Cache/170A49A5d01
108	/home/unknown/.mozilla/firefox/mj758oqs.default/./xpti.dat
112	/home/unknown/.mozilla/firefox/mj758oqs.default/./Cache/746D2D7Fd01
116	/home/unknown/.mozilla/firefox/mj758oqs.default/./Cache/C746D2F1d01
152	/home/unknown/.mozilla/firefox/mj758oqs.default/./compreg.dat
160	/home/unknown/.mozilla/firefox/mj758oqs.default/./cookies.sqlite
228	/home/unknown/.mozilla/firefox/mj758oqs.default/./sessionstore.js
1008	/home/unknown/.mozilla/firefox/mj758oqs.default/./XUL.mfasl
1760	/home/unknown/.mozilla/firefox/mj758oqs.default/./Cache/_CACHE_001_
2032	/home/unknown/.mozilla/firefox/mj758oqs.default/./XPC.mfasl
2584	/home/unknown/.mozilla/firefox/mj758oqs.default/./Cache/_CACHE_002_
5984	/home/unknown/.mozilla/firefox/mj758oqs.default/./Cache/_CACHE_003_
6896	/home/unknown/.mozilla/firefox/mj758oqs.default/./places.sqlite-journal
8616	/home/unknown/.mozilla/firefox/mj758oqs.default/./places.sqlite
23200	/home/unknown/.mozilla/firefox/mj758oqs.default/./Cache/0820AF34d01
34432	/home/unknown/.mozilla/firefox/mj758oqs.default/./urlclassifier3.sqlite
35036	/home/unknown/.mozilla/firefox/mj758oqs.default/./Cache
89352	/home/unknown/.mozilla/firefox/mj758oqs.default/.

```

---

### Post by Cracauer on 2008-11-24
The urlclassifier is at fault. We have seen cases like this before. I think it belongs to some phishing preventing extensions that goes amok does some braindead search over way too much data way too often.

Nuke it and you'll be fine.

Myself I don't use a disk cache, BTW. But I don't think your problem is caused by it.

---

### Post by unknown03 on 2008-11-24
ok..so just type in sudo rm -rf / ? :popcorn:
heheh.

so exactly how should i do that? just delete urlclassifier, delete the entire profile, or change some settings in about:config?

---

### Post by Cracauer on 2008-11-24
It's some crazy extension that either FF or Ubuntu decided to include by default. I'm still on FF2, so I can't point you directly to it. A search for it will bring up the other threads where people noticed this slowdown.

A formal bug report to Ubuntu seems in order.

---

### Post by unknown03 on 2008-11-25
> **Cracauer said:**
> It's some crazy extension that either FF or Ubuntu decided to include by default. I'm still on FF2, so I can't point you directly to it. A search for it will bring up the other threads where people noticed this slowdown.

A formal bug report to Ubuntu seems in order.

well i did a search for urlclassified. It seemed to work by going into preferences -> security -> and disabling "Tell me if the site I'm visiting is a suspected attack site" and "Tell me ... is a suspected forgery". Closing firefox and deleting the urlclassified*.* and restarting

---

### Post by kevmitch on 2008-11-25
Just delete the file directly 

```

rm /home/unknown/.mozilla/firefox/mj758oqs.default/./urlclassifier3.sqlite

```

will do it.

---

### Post by Arup on 2008-11-25
> **unknown03 said:**
> I used to be an Opera user for a long time. I especially love the mouse gestures. Problem was it kept crashing and flash didnt work very well


Use the x64 flash, it works fine. I use Opera exclusively and use it for hours with no issues of bloat etc. In fact x64 Opera is the fastest browser I have ever used and it beats their own x32 Opera.

---

### Post by pingpongboss on 2008-11-25
This is a problem with the nvidia 180.xx drivers. I had the exact same problem when I updated to the 180.06 and .08 drivers. When I reboot and log in, firefox would be quick, but after a few hours of usage, X would slow down and switching tabs in firefox would be very slow.

Just revert back to the 177.xx drivers and it is fixed.

---

