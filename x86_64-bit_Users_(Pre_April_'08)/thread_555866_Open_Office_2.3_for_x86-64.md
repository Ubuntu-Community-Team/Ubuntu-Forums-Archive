---
title: "Open Office 2.3 for x86-64??"
date: 2007-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ericindie on 2007-09-20
Any clue when a 64 bit version of the new, improved Open Office 2.3 might become available?  With so many people having 64-bit hardware now I'm surprised it didn't come out the same time as the 32 bit version.

Eric

---

### Post by ryno519 on 2007-09-20
It comes with Gutsy. So you should get it in about a month.

---

### Post by sawjew on 2007-09-21
I just installed the 32 bit version from the openoffice web site on 64 bit feisty with no problems at all.  They now (finally) have deb packages as well as rpms so I just downloaded them, extracted them to a folder and then entered ```
sudo dpkg -i --force-architecture *.deb
``` in the folder I extracted them to.  Works perfectly and now has the mozilla plugin which has been missing since Dapper.  Unfortunately the mozilla plugin only works in 32bit swiftweasel not in 64bit firefox but it's a start.

You will need the 32 bit libs though which I already had installed for Crossover and I also had 32 bit java for the browser plugin.  Oh for the time when I can have a pure 64 system or seamless integration of 32 bit apps.

---

### Post by stmiller on 2007-09-21
You could try installing the [64bit Gutsy debs]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=openoffice&searchon=names&subword=1&version=gutsy&release=all"), though that might possibly make dependency conflicts.

---

