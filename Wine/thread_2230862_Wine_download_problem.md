---
title: "Wine download problem"
date: 2014-06-21
forum: Wine
---

### Post by gordon99 on 2014-06-21
I am trying to install WINE and winetricks for a second time, having had to re-install Ubuntu14.04. This time, after about half an hour or maybe longer, I ended up getting these messages:

E: connection failed to fetch some archives.
E: could not open lock file /var/lib/apt/lists/lock-open (13:permission denied).
E: unable to open lock directory /var/lib/apt/lists/
E: unable to lock the adminisration directory (/var/lib/dpkg/) are you root?

Does anybody, please , know what the problem is and how I get around it?

---

### Post by gordon99 on 2014-06-21
P.S I don't know if I am 'root' but I do know that, had I sat there much longer during the installation, I would have taken root.

---

### Post by aramil248 on 2014-06-21
did you you use sudo?

---

### Post by aramil248 on 2014-06-21
since for some reason i cant edit my post i will make anothoranyway use sudo -s to switch to root

---

### Post by gordon99 on 2014-06-22
Yes, I did use sudo i.e
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install  winw1.7 winetricks

I read later that WINE 1.7 may be unstable and 1.6 is ok. Maybe that's part of the problem or perhaps I have to use sudo -s as suggested.

---

### Post by aramil248 on 2014-06-22
have you tried sudo apt-get install wine1.6 ?

---

### Post by adec2 on 2014-06-23
[COLOR=#000000]sudo apt-get install winw1.7 winetricks

shouldnt that be

[/COLOR][COLOR=#000000]sudo apt-get install wine1.7 winetricks

?[/COLOR]

---

