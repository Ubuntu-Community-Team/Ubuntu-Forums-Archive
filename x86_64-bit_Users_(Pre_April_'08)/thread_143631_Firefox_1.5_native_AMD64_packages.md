---
title: "Firefox 1.5 native AMD64 packages"
date: 2006-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by oopsz on 2006-03-12
Okay, If you're as sick as I am of having to install software outside the package manager to stay current..  well..  you're in luck.

I'm building AMD64 packages of firefox 1.5.0.1, basically backported to breezy from dapper.  They should install (fairly) cleanly on any up to date breezy system.

download all the packages, then dpkg -i them.  You might have to apt-get remove firefox first, because apt has issues upgrading all the required libs.

[http://www.plur.ca/ubuntu/](http://www.plur.ca/ubuntu/)

The current version uploaded is -ubuntu7.

---

### Post by Bandit on 2006-03-13
How well is Flash working? Or is it still a no go with 64bit firefox?

---

### Post by RAOF on 2006-03-13
Still no-go.  Although the GNU flash player (gnash) is getting close - it can play Strongbad emails ;)

---

### Post by oopsz on 2006-03-16
Flash still doesn't work, but I find that's not so bad a thing.  If I want to watch flash movies, i can load my 32 bit chrooted opera.  For regular browsing, it gets rid of a lot of ads..  The only annoying thing is the pop-up saying "additional plugins required to view this page" whenever there's flash on a page.

version -ubuntu9 is up.  This fixes some display problems with the Thai codepage and has some .deb cleanups.  No real changes from -ubuntu7 if you don't read or write Thai.

[http://www.plur.ca/ubuntu/breezy-backports/firefox-1.5.0.1-ubuntu9/](http://www.plur.ca/ubuntu/breezy-backports/firefox-1.5.0.1-ubuntu9/)

---

### Post by herk on 2006-03-18
Very handy packages oopsz, thanks.

---

### Post by oopsz on 2006-03-30
Uploading -ubuntu10.  This release adds a package with debugging symbols (firefox-dbg, 50 megs and not required to actually use firefox), fixes norweigan translation and fixes the .desktop link.  No other changes.

I guess I didn't mention it before, but you don't need the -dev packages or the -dbg package to use firefox.  So grab what you need.

[http://www.plur.ca/ubuntu/breezy-backports/firefox-1.5.0.1-ubuntu10/](http://www.plur.ca/ubuntu/breezy-backports/firefox-1.5.0.1-ubuntu10/)

---

### Post by oopsz on 2006-04-25
updated to -ubuntu12.  I haven't looked at this changelog, sorry.  Been travelling a lot and my AMD64 box is my home desktop.  Laptop's an ibook :P

[http://www.plur.ca/ubuntu/breezy-backports/firefox-1.5.0.1-ubuntu12/](http://www.plur.ca/ubuntu/breezy-backports/firefox-1.5.0.1-ubuntu12/)

---

