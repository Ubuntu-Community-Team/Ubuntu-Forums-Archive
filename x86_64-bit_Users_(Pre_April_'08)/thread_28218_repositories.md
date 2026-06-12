---
title: "repositories"
date: 2005-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by tikal26 on 2005-04-19
hey:
I am having tons of problems with my reposistories I don't know if anyone would be willling to post their reposritories file so I can mathch it with mines. I am get all sort of erro messages and whne I use the ones at ubuntuguide.org I guess they are for 32 not 64. if any one has all the nseeesary reposotories for an AMD 64 I would and post it I would aprreaciated. 
Thanks in advance

---

### Post by GrumpySmurf on 2005-04-19
You'll need to comment the following if you used the repository guide from ubuntuguide.org:

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

'stable' and 'testing' do not have amd64 available.  'unstable' does.

My sources.list is the same as the one posted on ubuntuguide, except I commented out those two entries.

---

### Post by tikal26 on 2005-04-19
ok;
It seesm that that was the problem thanks .

---

### Post by Daz_Man on 2005-04-20
im having a few problems with repositories too. i have commented out the ones you said to do above but i still get errors from [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org). i have commented these out and the errors go, i was just wondering if these repositories were important and whether they were for 64bit or 32bit.

---

### Post by Muchacho_Gasolino on 2005-04-20
in fact, I have found(from marillat's website) that the right marillat repository to use is not ftp.nerim.net, but rather 
deb [http://cyberspace.ucla.edu/marillat](http://cyberspace.ucla.edu/marillat) unstable main

---

### Post by GrumpySmurf on 2005-04-26
[QUOTE=Daz_Man]im having a few problems with repositories too. i have commented out the ones you said to do above but i still get errors from [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org). i have commented these out and the errors go, i was just wondering if these repositories were important and whether they were for 64bit or 32bit.[/QUOTE]
The backports repository is an unofficial project to maintain up-to-date packages for released versions of Ubuntu.  This seems to be similar to the Fedora Legacy Project, or of course the Debian backports project.  Unless you know you want this specific repository, it is safe to comment it out and re-run apt-get update.

---

### Post by gomadtroll on 2005-04-29
[QUOTE=Muchacho_Gasolino]in fact, I have found(from marillat's website) that the right marillat repository to use is not ftp.nerim.net, but rather 
deb [http://cyberspace.ucla.edu/marillat](http://cyberspace.ucla.edu/marillat) unstable main[/QUOTE]
 I noticed that mplayer on this site depends on libc6  >= 2.3.2.ds1-21, while hoary ships with 2.3.2.ds1-20ubuntu13, also mplayer is in universe or multiverse.
Just a caution about using different repositories, some may conflict.

greg

---

### Post by c_dog on 2005-04-30
The Backports repositories seem to be alive and kicking now. Firefox 1.0.3-2 is there.

---

### Post by IndieRockSteve on 2005-05-03
[QUOTE=Muchacho_Gasolino]in fact, I have found(from marillat's website) that the right marillat repository to use is not ftp.nerim.net, but rather 
deb [http://cyberspace.ucla.edu/marillat](http://cyberspace.ucla.edu/marillat) unstable main[/QUOTE]

i take it thats for amd64 too?

---

