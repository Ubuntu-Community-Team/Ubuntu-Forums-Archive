---
title: "QUAKE 2 in AMD64 - YES ITS TRUE AND YOU CAN TOO!!"
date: 2005-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by hammett111 on 2005-08-14
As of 7.38pm tonight I am now running Quake2 IN native 64bit!!!! It took alot of compiling of source and a few binary edits here and there but now I have got it. Once I learn how to create a .deb file I will try and post it somewhere for everyone to DOWNLOAD!!! HAIL 64bit its F$@&* awesome when you get the biatch goin!!

Quake is back and with AVENGENCE!!!
And if you have quake 3 download the tremulous full conversion mod, its a whole new game and frags a plenty!!! :grin:  :grin:

---

### Post by fistfullofroses on 2005-08-15
[QUOTE=hammett111]As of 7.38pm tonight I am now running Quake2 IN native 64bit!!!! It took alot of compiling of source and a few binary edits here and there but now I have got it. Once I learn how to create a .deb file I will try and post it somewhere for everyone to DOWNLOAD!!! HAIL 64bit its F$@&* awesome when you get the biatch goin!!

Quake is back and with AVENGENCE!!!
And if you have quake 3 download the tremulous full conversion mod, its a whole new game and frags a plenty!!! :grin:  :grin:[/QUOTE]
 I am sure that if you just ask on another thread such as the packages thread people can tell you how to make a deb

---

### Post by Sam on 2005-08-16
[QUOTE=fistfullofroses]I am sure that if you just ask on another thread such as the packages thread people can tell you how to make a deb[/QUOTE]
[Howto make debian standards debs from scratch](http://ubuntuforums.org/showthread.php?t=51003)
[How to package a simple application](http://ubuntuforums.org/showthread.php?t=49216)
[Debian New Maintainers' Guide](http://www.debian.org/doc/maint-guide/)
[Debian for Developers Tutorial](http://www.wiggy.net/presentations/2001/DebianWalkThrough/handouts/handouts.html)
[debhelper](http://nixdoc.net/man-pages/Linux/man1/debhelper.1.html)

---

### Post by hammett111 on 2005-08-16
I have actually gone a different route. I have tar'd the bugger with the demo and am now trying to get my server back online for people to test it. I have had one person test it and it runs fantastically on their machine so no hiccups so far.

Once I have uploaded it I will point everyone in the direction.

Cheers for your .deb help guys

---

### Post by Jet2k5 on 2005-08-16
Is it possible for you to mail the stuff to Tamir?  I mean if Tamir is cool with it he can make a .deb for it.  Tar.gz sounds great but it would be easier for some to just do an apt-get quake2 or something : :smile: .  Although I don't really care I can install both :) , just for new users.

---

### Post by DancingSun on 2005-08-16
[QUOTE=Jet2k5]Tar.gz sounds great but it would be easier for some to just do an apt-get quake2 or something : :smile: .  Although I don't really care I can install both :) , just for new users.[/QUOTE]
Are you kidding?  It can be a pain in the butt sometimes when you don't have any installers/uninstallers. :grin:

---

### Post by hammett111 on 2005-08-17
Its a single folder with everything you need to run it, in it. If you want to remove it you can just delete the folder. But okay I will ask Tamir if I can give it to him to turn into a .deb package.

We have almost finished a 64bit version of the original quake too.

---

### Post by jamesrw on 2005-08-22
I am not much of a gamer but quake on my amd64 notebook would be pretty cool!! keep me posted!

---

### Post by hammett111 on 2005-08-22
[QUOTE=jamesrw]I am not much of a gamer but quake on my amd64 notebook would be pretty cool!! keep me posted![/QUOTE]


Indeed. I will have my servers up and running soon. The addy for my website is [www.al-cunta.com](www.al-cunta.com). We are a programming unit from my old group q-works. We also now dabble in taking the piss out of al-qaeda and other testical-orrists, hence the name parody. Give us about a week we are having probs creating the flash intro......hehehe!! You'll love it!! I know I do....

Projects in the pipeline are:

Memorial pages for all those killed by terrorists "RIP Nick berg, you remind me daily of the depths of human depravity"

A native linux starcraft port/broodwar naturally too (this is an updated project from an old one we had at Q-works) Blame Blizzard for that baby being shutdown.

Quake AMD64 World, Quake1, 2, 3 native linux 64bit "the way it should be played"

and the good ol' bash the terrorists blogs......

---

### Post by Tamir on 2005-08-23
[QUOTE=hammett111]Indeed. I will have my servers up and running soon. The addy for my website is [www.al-cunta.com](www.al-cunta.com). We are a programming unit from my old group q-works. We also now dabble in taking the piss out of al-qaeda and other testical-orrists, hence the name parody. Give us about a week we are having probs creating the flash intro......hehehe!! You'll love it!! I know I do....

Projects in the pipeline are:

Memorial pages for all those killed by terrorists "RIP Nick berg, you remind me daily of the depths of human depravity"

A native linux starcraft port/broodwar naturally too (this is an updated project from an old one we had at Q-works) Blame Blizzard for that baby being shutdown.

Quake AMD64 World, Quake1, 2, 3 native linux 64bit "the way it should be played"

and the good ol' bash the terrorists blogs......[/QUOTE]
 Guys, I can build this package from debian's source! I just found this:
[http://debian-amd64.alioth.debian.org/debian-amd64/pool/contrib/q/quake2/](http://debian-amd64.alioth.debian.org/debian-amd64/pool/contrib/q/quake2/)

---

### Post by hammett111 on 2005-08-23
[QUOTE=Tamir]Guys, I can build this package from debian's source! I just found this:
[http://debian-amd64.alioth.debian.org/debian-amd64/pool/contrib/q/quake2/](http://debian-amd64.alioth.debian.org/debian-amd64/pool/contrib/q/quake2/)[/QUOTE]
 Well there you go peeps, Tamir is gonna make a .deb for Ubuntu 64bit Quake 2, think you can do a Quake 1 as well? We are having a little trouble..!!

---

### Post by d0nk on 2005-08-25
As far as quake1 goes, It seems that the best q1 engine for linux is DarkPlaces.  QuakeForge is good (official continuation of quakeworld), but it lacks menu's, has a wierd binding system, etc. It does, however have the debian/ directory for .deb building.

Darkplaces compiles and runs great under amd64.  Nexuiz (free gpl fps) uses the darkplaces engine too.  A nexuiz .deb would be pretty cool.  

[Darkplaces page](http://icculus.org/twilight/darkplaces/download.html)
[Nexuiz page](http://nexuiz.com)

---

### Post by Kuolio on 2005-08-25
Hmm, i heard and red from different forums, that quake 3 engine was released under GPL today...

---

### Post by nwillis on 2005-08-25
[QUOTE=Kuolio]Hmm, i heard and red from different forums, that quake 3 engine was released under GPL today...[/QUOTE]

The truth you speak.  Which means already there are two-dozen GPL'ed forks each trying to "improve" on it.  Most will die, few (if any) will actually bring any rendering improvements.

---

### Post by d0nk on 2005-08-25
What i want is a configure/makefile based q3 build, with SDL/GL (not just GL), for native amd64.  Since I am not good with 3d related programming (best work is a 2D sdl pong game), I'll leave it to other people :p

Q3 Won't compile for me on amd64.  It works fine on my 32bit 1800+ though :x  It also claims it needs gcc-2.95 to compile  (i have both 2.95 and 3.3 on my other box)

---

