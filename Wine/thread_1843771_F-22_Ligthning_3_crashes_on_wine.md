---
title: "F-22 Ligthning 3 crashes on wine"
date: 2011-09-14
forum: Wine
---

### Post by OrangeVixen on 2011-09-14
This is the only program that I have come across that crashes with wine, for those of you who have played it on real Windows, it will crash in wine if you click on "Accept" in the Options menu or play a mission.

_SYSDUMP.TXT says l3.map is missing, and I have no idea what that file is for and it does not seem to exist on the real Windows and it runs fine there.

I know this is an old game but if anyone knows I'd appreciate it, I can't find anything googling or searching through the posts here.

Running wine 1.3 on Lucid, btw.

---

### Post by Toz on 2011-09-14
Looks like a known bug. According to: [http://bugs.winehq.org/show_bug.cgi?id=25231]("http://bugs.winehq.org/show_bug.cgi?id=25231"), it appears to have been fixed in 1.3.11. 

But, [http://bugs.winehq.org/show_bug.cgi?id=28333]("http://bugs.winehq.org/show_bug.cgi?id=28333") seems to indicate it still exists in 1.3.28.

Which subversion of wine 1.3 are you running?

---

### Post by OrangeVixen on 2011-09-16
I'm using the one from the repositories:

user@zareason-limbo:~$ wine --version
wine-1.3.26

I recall coming across this problem with wine 1.2 (but I can not confirm as it was a while ago).

---

### Post by drs305 on 2011-09-16
Thread moved to the Wine forum.

---

