---
title: "Wine 0.9.57 Released"
date: 2008-03-07
forum: Wine
---

### Post by mad_max0204 on 2008-03-07
I just checked wines site and they released next version.

---

### Post by b0rka7a on 2008-03-07
Yep... And maybe in April they will make a .deb package :D
Before, the .deb package was released in the same day (or the other day in the worst case), and now we must wait 2-3 weeks to get it... why ?

---

### Post by IanW on 2008-03-07
Because the deb version is maintained by ONE guy. If he's on vacation or out sick, it doesn't get done.

---

### Post by Mr.Johnny on 2008-03-07
quick test:

- messenger 8.1 still doesn't work.
- maple story (for my sister, not me, lol) still doesn't work.

for all of you who want to test it and don't want to wait for the package, do this (in case you don't know how to do it, personally I would have been happy if I had a found a post like this a few months ago, lol):

open a terminal and type ( 1), 2), 3), etc, not included, of course):

1) sudo su (enter your password):
2) apt-get build-dep wine
3) apt-get install libxi-dev
4) apt-get install libxinerama-dev

then dl the new *.tar or *.bz2 from winehq, extract it, go to the dir where you extracted it to  and do (this is in the terminal, of course) :

1) ./configure --prefix=/usr
2) make depend && make
3) sudo make install

If all goes well you should have your new wine version working. :guitar:

---

### Post by b0rka7a on 2008-03-07
Okay, I've just made a .deb package of Wine 0.9.57 so you don't have to compile it yourself :) Have fun!
[http://rapidshare.com/files/97803569/wine_0.9.57-1_i386.deb.html](http://rapidshare.com/files/97803569/wine_0.9.57-1_i386.deb.html)

---

### Post by DarkSim on 2008-03-07
Here is the announcement detailing what was fixed:

[http://www.winehq.org/?announce=0.9.57](http://www.winehq.org/?announce=0.9.57)

Seems like they got a good bit done. Great job.

I'm off to check it out.

---

### Post by Vadi on 2008-03-07
> **b0rka7a said:**
> Okay, I've just made a .deb package of Wine 0.9.57 so you don't have to compile it yourself :) Have fun!
[http://rapidshare.com/files/97803569/wine_0.9.57-1_i386.deb.html](http://rapidshare.com/files/97803569/wine_0.9.57-1_i386.deb.html)

Can you make a 64bit one?

And yeah, looks like the one guy who was doing the .debs isn't anymore. Real pity, because he was doing an excellent job on them.

---

### Post by YokoZar on 2008-03-07
> **Vadi said:**
> Can you make a 64bit one?

And yeah, looks like the one guy who was doing the .debs isn't anymore. Real pity, because he was doing an excellent job on them.I've been working all today on this new release.

Hardy is a priority now, not backporting to Gutsy.  See this thread:

[http://ubuntuforums.org/showthread.php?t=714740](http://ubuntuforums.org/showthread.php?t=714740)

---

### Post by b0rka7a on 2008-03-07
> **Vadi said:**
> Can you make a 64bit one?

And yeah, looks like the one guy who was doing the .debs isn't anymore. Real pity, because he was doing an excellent job on them.

Sorry, I'm a newbie and I don't know how :D
I used `checkinstall' instead of `make install' and that's it :) I don't have a clue about making a 64-bit version. Maybe I must compile it under 64-bit Ubutnu, but... I don't have one :)

PS: Btw, that's nice - "duubuntutu?" :lolflag:

---

### Post by YokoZar on 2008-03-07
> **b0rka7a said:**
> Sorry, I'm a newbie and I don't know how :D
I used `checkinstall' instead of `make install' and that's it :) I don't have a clue about making a 64-bit version. Maybe I must compile it under 64-bit Ubutnu, but... I don't have one :)

PS: Btw, that's nice - "duubuntutu?" :lolflag:Don't bother, I'll have both a proper i386 one and a 64 bit one up at budgetdedicated by tonight.

---

### Post by Twitch6000 on 2008-03-07
Hey can someone make a .deb for gusty because I tried compling the source and each time I do I never get it in the app menu :/.It works but I never get a wine thing in the app menu like you get with a .deb.

---

### Post by SBFC on 2008-03-07
> I never get a wine thing in the app menu

Why not just edit your menu then?

---

### Post by Vadi on 2008-03-07
> **YokoZar said:**
> I've been working all today on this new release.

Hardy is a priority now, not backporting to Gutsy.  See this thread:

[http://ubuntuforums.org/showthread.php?t=714740](http://ubuntuforums.org/showthread.php?t=714740)

Holy crap, you're like my favourite ubuntonian now. Packaging wine AND spring = :popcorn:.

---

### Post by YokoZar on 2008-03-07
> **Twitch6000 said:**
> Hey can someone make a .deb for gusty because I tried compling the source and each time I do I never get it in the app menu :/.It works but I never get a wine thing in the app menu like you get with a .deb.That's because when you compile from source (or make a deb with checkinstall) you're missing all the changes to the package I made, such as the .desktop files.

---

### Post by cysco24 on 2008-03-09
update manager tells me there is an upgrade.  0.9.57.   Awesome....then I install and wine doesn't work anymore.  I uninstalled wine completely and tried it again.  Still no go.

I went back to 0.9.56 and everything is working again.

---

### Post by Melcar on 2008-03-09
This release broke support for my Infinity Engine games (Baldur's Gate mostly), which was the main reason I still use Wine.

---

### Post by YokoZar on 2008-03-09
> **cysco24 said:**
> update manager tells me there is an upgrade.  0.9.57.   Awesome....then I install and wine doesn't work anymore.  I uninstalled wine completely and tried it again.  Still no go.

I went back to 0.9.56 and everything is working again.
Could you please explain what you mean by "it doesn't work" ?

Are you using Gutsy?  32 or 64 bit?  Do you get an error message?  Is it segfaulting?  When you "uninstalled completely" did you remove ~/.wine?

---

### Post by dandixon on 2008-03-09
hey YokoZar

I know you were working on a 64 version . Did you finish it?
I'm new to lunix and interested in using wine.

Thanks 
Dan

---

### Post by Vadi on 2008-03-09
Yep, he finished the 64bit one:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by cysco24 on 2008-03-10
> **YokoZar said:**
> Could you please explain what you mean by "it doesn't work" ?

Are you using Gutsy?  32 or 64 bit?  Do you get an error message?  Is it segfaulting?  When you "uninstalled completely" did you remove ~/.wine?

Thanks for your reply.  I uninstalled through synaptic, complete removal. and deleted the .wine folder and installed 0.9.57 and it works now.

Only thing i did different this time was delete the .wine folder.

thx

---

### Post by dementic on 2008-03-14
Hello!

I have the same problem as you, but I can't find any wine folder remaining after deleting the app. 

Where is that .wine folder you mention?

THX

---

### Post by Vadi on 2008-03-14
A folder that begins with a dot is usually hidden. Try doing Ctrl+H in the file browser - that'll toggle the display of hidden folders. Doing that in your home folder will show up the .wine one.

---

### Post by dementic on 2008-03-15
Ok, it works now!

Thanks for the help

PS: The problem was that I defined ADVAPI32.DLL as a bultin/native in ressources, although Wine said me that is wasn't recommended with that DLL

---

