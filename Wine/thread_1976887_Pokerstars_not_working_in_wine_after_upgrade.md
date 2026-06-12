---
title: "Pokerstars not working in wine after upgrade"
date: 2012-05-09
forum: Wine
---

### Post by iclestu on 2012-05-09
Title says it all really...

PS client just hangs as if it cant connect (same symptoms as if ps server was down) but i know server is ok because i can get it in an xp virtualbox.

anyone else having issues?

reinsatalling wine didnt help neither did reinstalling the pokerstars client itself.

---

### Post by CrispyC on 2012-05-12
Exact same problem for me.

Just upgraded my ubuntu to 12.04, and now its not connecting. 


Have you found any solution?  


UPDATE: Ok if you load from a terminal it connects fine, check the post here -
[http://ubuntuforums.org/showthread.php?p=11820303](http://ubuntuforums.org/showthread.php?p=11820303)

or just use the command 
wine ~/.wine/drive_c/Program\ Files/PokerStars/PokerStars.exe 

And this is French discussion page on the same problem, but google translate works pretty well on it
[http://forum.ubuntu-fr.org/viewtopic.php?id=907611](http://forum.ubuntu-fr.org/viewtopic.php?id=907611).


Im still interested in a proper quik launch button though

---

### Post by iclestu on 2012-05-14
> **CrispyC said:**
> Exact same problem for me.

Just upgraded my ubuntu to 12.04, and now its not connecting. 


Have you found any solution?  


UPDATE: Ok if you load from a terminal it connects fine, check the post here -
[http://ubuntuforums.org/showthread.php?p=11820303](http://ubuntuforums.org/showthread.php?p=11820303)

or just use the command 
wine ~/.wine/drive_c/Program\ Files/PokerStars/PokerStars.exe 

And this is French discussion page on the same problem, but google translate works pretty well on it
[http://forum.ubuntu-fr.org/viewtopic.php?id=907611](http://forum.ubuntu-fr.org/viewtopic.php?id=907611).


Im still interested in a proper quik launch button though

ah - thanks for these.  Tend to use it through an xp virtualbox anyways (in order to use pokertracker) so was no biggie for me really but glad there is a solution if i wanna just play around for a bit

---

### Post by lucacerone on 2012-07-08
Hi guys, I've solved the issue installing wine1.5 using the
ppa from this site [http://www.unixmen.com/201204-wine-1-5-2-has-been-released-ppa-ubuntu/](http://www.unixmen.com/201204-wine-1-5-2-has-been-released-ppa-ubuntu/) . It seems to work just fine...

---

### Post by oldos2er on 2012-07-08
Moved to Wine.

---

