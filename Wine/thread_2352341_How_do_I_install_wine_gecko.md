---
title: "How do I install wine gecko?"
date: 2017-02-11
forum: Wine
---

### Post by namisan on 2017-02-11
So whilst trying to install league of legends using wine I was adviced to install Wine Gecko. I accidentally hit cancel and I am now unable to figure out a method to install wine gecko. Any help?

---

### Post by Dennis N on 2017-02-11
Looks like it is in the Ubuntu repository.
For xenial:
```
dmn@Zotac ~ $ sudo apt-get install wine-gecko2.21
```

---

### Post by namisan on 2017-02-11
nami-san@namisan-Latitude-3340:~$ sudo apt-get install wine-gecko2.21
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
nami-san@namisan-Latitude-

---

### Post by namisan on 2017-02-11
Nevermind, that worked fine.

---

### Post by howefield on 2017-02-12
Moved to the "*Wine*" forum.

---

### Post by mrlinn on 2017-05-02
sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock

---

