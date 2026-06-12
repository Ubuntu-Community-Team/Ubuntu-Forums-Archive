---
title: "Star trek online in wine"
date: 2011-08-20
forum: Wine
---

### Post by Nevyn04 on 2011-08-20
I've been trying for about a week now to get Star Trek Online working in wine and so far no luck. I got the Login screen to load but once i sign in it won't go beyond the load screen. 

I'm using Wine 1.3.26 and Ubuntu 10.10. 

I've followed several guides and so far none have gotten any better results than another. 

I've added a Direct 3D key, installed winetricks, installed IE7. Can anyone help?

---

### Post by Nevyn04 on 2011-08-22
No one has any ideas or experience with this?

---

### Post by Nevyn04 on 2011-08-26
Still no luck getting it to run. Does anyone on the forums have experience with running this game in wine? Would really appreciate some assistance in getting it to run.

---

### Post by hazelnut on 2011-08-27
I run this game.  As I recall, I installed IE6 as instructed, but it still didn't work, I needed to install IE8 as well. Never tried IE7. But it sounds like your problem is related to that, because I had the exact same problem, and only after install IE8 did it start working.

Also, I have to use wine 1.3.24 because of a change in the way sound is handled in 1.3.25 and above.  I'm still trying find a solution to the sound in later the versions of wine.

---

### Post by Nevyn04 on 2011-08-30
Thanks. I'll try that ASAP. I'll post the results as soon as I do. Other than the sound problem does everything else function well? No other bugs I should know about?

---

### Post by Nevyn04 on 2011-08-31
No luck, IE8 keeps crashing on install.

---

### Post by hazelnut on 2011-08-31
Yes, everything works.  I used Playonlinux [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

And this helpful article: [http://www.redshirtlinux.com/?p=122](http://www.redshirtlinux.com/?p=122)

Watch the video.  

Also, you can try deleting the original preferences detected on setup:

...../Program\ Files/Cryptic\ Studios/localdata/GamePrefs.pref

and

...../Program\ Files/Cryptic\ Studios/Star\ Trek\ Online/Live/localdata/Gameprefs.Pref

Then re-run the game.  It will detect everything again.

---

### Post by hazelnut on 2011-09-01
Another note, make sure you can access the internet with the IE you installed in wine.  Because, if that's failing, you have some other problem.

---

### Post by Nevyn04 on 2011-09-04
For some reason I cannot get IE8 to install. It say "This program has encountered an error and needs to close." I can't get it to fully install.

---

### Post by hazelnut on 2011-09-05
Did you try from a fresh prefix in playonlinux? And even so, maybe that's all that's needed. if it installed some files, then install IE6 and go from there.  The game only needs the mshtml libs from IE to run.

---

### Post by hazelnut on 2011-09-18
More information, I found this thread at the STO forums.  Very succinct and it describes pretty much what I did, except I used Playonlinux and, as I said before, the latest version of wine causes no sound, so I have to use 1.3.24

[http://forums.startrekonline.com/showthread.php?t=229720&highlight=Linux]("http://forums.startrekonline.com/showthread.php?t=229720&highlight=Linux")

Good luck!

---

