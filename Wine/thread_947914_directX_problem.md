---
title: "directX problem"
date: 2008-10-14
forum: Wine
---

### Post by turtleface78 on 2008-10-14
Hey, I run 8.04 ubuntu and wine used to work fine, ive played lots of games without any problems.  recently it has stopped working and whenever i try to play warcraft 3 i get the message "Warcraft 3 was unable to initialize directX...".  It worked fine like 2 days ago and the only things that has changed since then is i have udpated to wine 1.1.6 ( not sure what i was running before udpate but probly most recent before 1.1.6) and i have been messing aroudn with compiz settings.  Does anyoen know how i can get wc3 back up and running?  All help appreciated

---

### Post by Thelasko on 2008-10-15
> **turtleface78 said:**
> ...the only things that has changed since then is i have udpated to wine 1.1.6

There's your problem.  Wine Updates are supposed to fix bugs, but sometimes they create a few.  Check the [appdb]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922"), but I'm willing to bet the solution is to reinstall Warcraft.

---

### Post by hikaricore on 2008-10-16
Reinstalling warcraft is not quite a reasonable answer. (we're not using windows here) :p

Just downgrade your version of wine to the previous version and see if that fixes your problem.

---

### Post by turtleface78 on 2008-10-20
I downgraded to 1.1.5 but i still get the same direcx error.  I have a feeling that i screwed something up when i was messing around with compiz as I was playing around with alot of the added graphics features but im not sure if that woudl affect wine.  Any others ideas i can try?  I have to restart to windows whenver i want to play a game and its such a hassle knowing that I was playing games in linux less than aweek ago.

---

### Post by turtleface78 on 2008-10-20
Comp specs are Pentium D 805, nvidia geforce 7600gs, 2 gigs ram...This error is driving me crazy i tried reinstalling warcraft but to no avail.  I remember i had the same problem when i first installed wine and wc3 but i can't remember what i did to get it working.  I have spent a lot of time searching for a solution without making any progress.  Also when i try to run wc3 with -opengl it just give me teh same error just with opengl instead of directx.

---

### Post by cogadh on 2008-10-21
Disable Compiz, it doesn't get along with Wine all that well.

---

### Post by david_kt on 2008-10-21
> **turtleface78 said:**
> Hey, I run 8.04 ubuntu and wine used to work fine, ive played lots of games without any problems.  recently it has stopped working and whenever i try to play warcraft 3 i get the message "Warcraft 3 was unable to initialize directX...".  It worked fine like 2 days ago and the only things that has changed since then is i have udpated to wine 1.1.6 ( not sure what i was running before udpate but probly most recent before 1.1.6) and i have been messing aroudn with compiz settings.  Does anyoen know how i can get wc3 back up and running?  All help appreciated

First of all, lock you wine to avoid confusion. Please read below thread for clearer explanation:
[http://ubuntuforums.org/showthread.php?t=944949](http://ubuntuforums.org/showthread.php?t=944949)

Second, disable compiz, it might interfere with wine.

Third,

```
glxinfo | grep render
```

Make sure direct rendering: Yes. If direct rendering: No, try:

```
sudo dpkg-reconfigure xserver-xorg
```

or any other method you ever tried to enable direct rendering.

DK

---

