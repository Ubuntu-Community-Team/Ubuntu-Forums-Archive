---
title: "Debian-marillats are available for the amd64 now"
date: 2005-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Optimal Aurora on 2005-06-17
you can access the debian-marillats from the following

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main

enjoy and now if someone would add it back to the Ubuntuguide.org, we would all be grateful...

---

### Post by joekr on 2005-06-17
I'm getting a GPG key error... any ideas?

---

### Post by Optimal Aurora on 2005-06-17
here after you have modified the apt/sources.list file, open up a terminal and type in 

**sudo gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907** 
**sudo gpg --armor --export 1F41B907 | sudo apt-key add -**

that should help...

---

### Post by Optimal Aurora on 2005-06-18
Sorry but poofyhairguy told me something about as ubuntu ages, debian-marillats are  probably not going to work so well in the future. That is why they made hoary-backports and hoary-extras... Go figure...

---

### Post by mohaham on 2005-06-18
do NOT use marillat repos, to avoid any incompatibility issues..
Use the backports repos...
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Optimal Aurora on 2005-06-18
That's what I meant... But thanks for putting it into english...

---

### Post by Optimal Aurora on 2005-06-28
I just thought about using fedora so I install that over my ubuntu and now I am back to using ubuntu... I decided to get the libdvdcss again, and from what I remember some of the others saying to not use debian-marillat I tried to get them from the backports and extras repos... However, I couldn't because they isn't anything in their for amd64 expect some w-word thing... I tried sudo apt-get install libdvdcss totem-xine which worked in the pass and nothing... So, until ubuntu comes out in breezy I recommend people use the debian-marillats...

Edit= unless any one has anyway to find them in backports or extras repo...

---

### Post by NickB on 2005-06-28
If you're trying to play DVDs, I recommend using xine with the marillat libraries... works great!

Nick

---

### Post by Optimal Aurora on 2005-06-28
Personally I prefer totem-xine... Well, it basicly the same thing...

---

### Post by trinaryouroboros on 2005-11-07
[QUOTE=mohaham]do NOT use marillat repos, to avoid any incompatibility issues..
Use the backports repos...
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)[/QUOTE]

That would be nice, but someone should UPDATE THE GUIDE :

> deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging bleeding main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging bleeding main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras bleeding main universe multiverse restricted

---

