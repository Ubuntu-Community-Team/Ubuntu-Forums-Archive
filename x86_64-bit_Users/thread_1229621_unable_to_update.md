---
title: "unable to update"
date: 2009-08-02
forum: x86 64-bit Users
---

### Post by alaukik.kot on 2009-08-02
i had ubuntu 8.1 last month, jst a week back i upgraded it to ubuntu 9.01, i have AMD processor, newer version is working very fine, but when i ask for update it fails, message i'm getting is

could not download all repository index-

Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)/dists/intrepid/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages)  503 Service Unavailable
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  503 Service Unavailable
Some index files failed to download, they have been ignored, or old ones used instead.


this message promts on my screen and update terminates, kindly seeking for help,

---

### Post by Clancy_s on 2009-08-02
It looks as though the update didn't change your source list to ibex, at least for the CD.

Change your sources list (under System > admin > software sources) to remove the CD from the list, your sources will update, then try the update again.

---

### Post by thuleni on 2009-10-19
Hmm - looks like the URL has changed:
[http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/)

but how would you change the URL in the System > admin > Software Sources

---

### Post by thuleni on 2009-10-19
Does anyone have a working version of source.list for Jaunty AMD 64 bit OS.

Cheers
:biggrin:

---

