---
title: "Installing iTunes in Wine, How do you do it?"
date: 2007-12-04
forum: Wine
---

### Post by mattfatrat on 2007-12-04
So I went on Apple.com and downloaded the "exe" installer file for iTunes I want to install it with wine and run it with wine, what do I do next?
If you need to know I am running Ubuntu Linux 7.10 Gutsy Gibbon and I installed Wine using Add/Remove Programmes.

---

### Post by anachreon_ on 2007-12-04
At least since the last time I checked, iTunes does not work under Wine.  This may have changed since I last looked into it, but I wouldn't hold out too much hope.

---

### Post by mattfatrat on 2007-12-04
Well can anyone tell me how to install anything on wine coz I'm a n00b!

---

### Post by pedro_orange on 2007-12-04
I don't think iTunes works under Wine.

What functionality of iTunes are you after specifically? 
RhythmBox (Sp!) is a good mp3 player and displays your music library in the same sort of way iTunes can.
If you're looking for iPod sync'ing and so on I use gtkpod, although I have heard there are many more alternatives.

Although if you're looking for the iTunes store to buy music you might be out of luck. 

Could try VM'ing

Installing anything in Wine...well it's just like Windows! :lolflag:

I just associated the *.exe file types with WINE & it usually runs the installer / app
You should check WineHQ/AppDB before pulling your hair out as to why a piece of software won't install/run :)

---

### Post by cogadh on 2007-12-04
iTunes uses a proprietary DRM system which does not work in Linux or Wine. You may be able to get iTunes to run in Wine, but the store and any previously purchased music won't work. If you have any non-DRM'ed music, it should probably work fine for managing that music, but why use iTunes when Amarok or RhythmBox work just as well and are native apps.
[http://appdb.winehq.org/appview.php?iAppId=1347](http://appdb.winehq.org/appview.php?iAppId=1347)

---

### Post by Clarke on 2007-12-04
How can I access the podcast database of iTunes from Amarok?
Even if I I'll have to download podcasts manualy, is it possible to upload them the to the "Podcasts" section of the iPod? Or it will be stored as an ordinary music?

---

### Post by cogadh on 2007-12-04
This thread and forum are not for Amarok support. You should post your question over in the [Multimedia & Video](http://ubuntuforums.org/forumdisplay.php?f=138) forums.

---

### Post by Promaster91 on 2007-12-04
itunes won't save any preferences however it will run in wine.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8535](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8535)

---

### Post by Sunflower1970 on 2007-12-05
> **Promaster91 said:**
> itunes won't save any preferences however it will run in wine.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8535](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8535)

Yep. I've gotten it to run. But it's so slow it's pretty much not even worth it. Not only that, it blacks out my screen for a moment or two (on my laptop--specs in siggy) until I begin to move the cursor around and the desktop comes back. (Weird). I've played around in the store, listening to the snippets of songs. Haven't tried purchasing anything though

I have been able to get 7.2 to run, but I see 7.3, according to Winehq works..? I wasn't able to get it d/l and install. Might have to test that again

---

### Post by edwardgel on 2008-01-07
> **mattfatrat said:**
> Well can anyone tell me how to install anything on wine coz I'm a n00b!

(1)   Find the EXE file that installs the Windows application.  This could be the "installer" EXE if you downloaded the Windows appliation, or it could the the AUTORUN.EXE contained in the AUTORUN folder on the Windows installation disk.

(2)    Right-click on that EXE file and select OPEN WITH....  "Wine Windows Emulator"....

Everything else should go as in Windows!

:popcorn:

---

### Post by DarinB on 2008-01-23
i can't get that to work.
i think if apple just announced that they haev sold less ipods maybe if they make itunes for linux they can sell about 4 million more overnight.

---

### Post by chrisgsmith on 2008-01-31
I was able to get it to work following the guide on the following site:

[http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html)

---

### Post by asuastrophysics on 2009-04-14
> **cogadh said:**
> iTunes uses a proprietary DRM system which does not work in Linux or Wine. You may be able to get iTunes to run in Wine, but the store and any previously purchased music won't work. If you have any non-DRM'ed music, it should probably work fine for managing that music, but why use iTunes when Amarok or RhythmBox work just as well and are native apps.
[http://appdb.winehq.org/appview.php?iAppId=1347](http://appdb.winehq.org/appview.php?iAppId=1347)

ummm...except no native apps on linux can restore an ipod. 
that bit has been missing,
which is why installing itunes in wine is a good idea;)

---

