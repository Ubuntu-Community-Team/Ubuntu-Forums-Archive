---
title: "Wine 1.5 on Ubuntu 12.04Lts how to"
date: 2013-02-12
forum: Wine
---

### Post by zouthe on 2013-02-12
Just wanted to post a good guide on putting together a decent wine for gaming.. seems to appear that there are no good guides out there, so here's a short one i threw together.
--------------------------------------------------------------------------------------------------------------------------------
1. Get whatever Wine version you want... id advice getting 1.5:

sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update && sudo apt-get install wine1.5



2.  Build deb:

sudo apt-get build-dep wine




3. Make sure that git is installed:

sudo apt-get install git



4. Find a copy of the wine source:
[CENTER][LEFT] 
git clone git://source.winehq.org/git/wine.git wine-git cd wine-git


5. Get patch:

wget -O KUSER_SHARED_DATA [http://bugs.winehq.org/attachment.cgi?id=40435](http://bugs.winehq.org/attachment.cgi?id=40435)


6.Install patch:

cat KUSER_SHARED_DATA | patch -p1


7. Build Wine (this may take 5-20 minutes):

./configure make




8. Get Winetricks:

sudo apt-get install winetricks




9. Install prerequisites:

winetricks d3dx9 winetricks vcrun2008 winecfg

---------------------------------------------------------------


Hopefully this helped, good luck!
:D
[/LEFT]
[/CENTER]

---

### Post by Nemesis2012 on 2013-02-12
you know the **KUSER_SHARED_DATA** is broken in newer wine's?  :(

---

