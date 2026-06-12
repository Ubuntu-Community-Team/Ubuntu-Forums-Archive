---
title: "Forsaken World Not Working Still"
date: 2012-04-02
forum: Wine
---

### Post by TurtleKing on 2012-04-02
For some reason, wine will not even run the .exe file to download the entire game. I got this error from terminal:

```
username@computer:~/Downloads$ wine ForsakenWorld_EN_v187_Pando.exe 
Log file is being written to C:\users\username\Temp\ForsakenWorld_EN_v187_Pando.exe.log
Exception in thread "LibgcjInternalFinalizerThread" Exception in thread "main" err:seh:setup_exception_record stack overflow 920 bytes in thread 0009 eip f760cd17 esp 00a90f98 stack 0xa90000-0xa91000-0xc90000

```

I'm gonna try the steam version next. If anyone has a faster Internet connection (I have 1MBps), please test it and report back the results.

---

### Post by schtufbox on 2012-04-02
Downloading it now to try, I have a 10mbit connection, so slightly faster to download here.  Will update with the result when it's done.

---

### Post by tut3point0 on 2012-04-02
I would be interested in this as well. im not to sure how to get it up and running. if anyone could help or send me link to forum, on how to install i would really appreciate it. Thanks

---

### Post by schtufbox on 2012-04-02
Gave it a try via steam, tried most suggestions from WineHQ but still no joy I am afraid..

---

### Post by TurtleKing on 2012-04-05
> **schtufbox said:**
> Gave it a try via steam, tried most suggestions from WineHQ but still no joy I am afraid..

Thanks will save me the hassle of doing an over-night download.:)

I wonder if it would help WINE developers, if we reported to them the feedback from terminal?

Maybe it will help them narrow down the problem.:-k

---

### Post by cogadh on 2012-04-05
These are all [known issues with the game in Wine]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=12391"). The only known way to run the game in Wine is to install the game in Windows, update it, then copy the installed files over to your Wine prefix. Even then, the game still does not fully work.

---

### Post by synaptix on 2012-04-06
Forsaken World has anti-hack (last time I checked it did) stuff which Wine can't run, hence why most of the AppDB stuff is rated Garbage.

---

### Post by TurtleKing on 2012-04-07
> **synaptix said:**
> Forsaken World has anti-hack (last time I checked it did) stuff which Wine can't run, hence why most of the AppDB stuff is rated Garbage.

Yeah I recall Game Guard being installed on Windows. Sadly Perfect World Entertainment has no interest in Linux. Despite having a lot of fans (myself included) back when Perfect World worked on Wine (not sure if it does anymore).

Heck, I would even pay the standard game price ($40-$60) to have a native Linux client.

---

### Post by synaptix on 2012-04-09
> **TurtleKing said:**
> Yeah I recall Game Guard being installed on Windows. Sadly Perfect World Entertainment has no interest in Linux. Despite having a lot of fans (myself included) back when Perfect World worked on Wine (not sure if it does anymore).

Heck, I would even pay the standard game price ($40-$60) to have a native Linux client.

Last I recalled the company produced it's own integrated anti-hack system into Forsaken World, as to not have it showing to end users or something like that.

PWI still does work on Wine, just have to do some workarounds to actually get it working right:

[http://ubuntuforums.org/showthread.php?t=1943114](http://ubuntuforums.org/showthread.php?t=1943114)

---

### Post by tut3point0 on 2012-04-09
i was finally apple to get it up and running connected and did a few quest.
bugs: icons are messed up but i think there is work around. (working on it)
most mobs are blacked out and NPC's are invisable (still there but hard to find someone you have never seen before)
im running ubuntu 11.04 with wine 1.4 ATI graphics card(forget which one)
i installed on a laptop running widows 7 and copied to wine dir.
installing a later version of wine tonight( supposed to fix NPC's and icon issues)

---

### Post by cogadh on 2012-04-09
> **TurtleKing said:**
> Yeah I recall Game Guard being installed on Windows. Sadly Perfect World Entertainment has no interest in Linux. Despite having a lot of fans (myself included) back when Perfect World worked on Wine (not sure if it does anymore).

Heck, I would even pay the standard game price ($40-$60) to have a native Linux client.
> **synaptix said:**
> Last I recalled the company produced it's own integrated anti-hack system into Forsaken World, as to not have it showing to end users or something like that.

PWI still does work on Wine, just have to do some workarounds to actually get it working right:

[http://ubuntuforums.org/showthread.php?t=1943114](http://ubuntuforums.org/showthread.php?t=1943114)
It does indeed use its own "home grown" anti-cheat application and not Game Guard, however, given that almost no anti-cheat application will work in Wine due to how they accomplish their anti-cheat functions, it is reasonable to suspect that whatever PWE does do may be a factor in why these games don't work fully.

---

### Post by shirlay on 2012-04-12
Although some problems and glitches cannot be solved over time, it still qualifies the best free MMO.  [http://www.dotmmo.com/forsaken-world-272.html](http://www.dotmmo.com/forsaken-world-272.html)

---

### Post by TurtleKing on 2012-04-30
> **shirlay said:**
> Although some problems and glitches cannot be solved over time, it still qualifies the best free MMO.  [http://www.dotmmo.com/forsaken-world-272.html](http://www.dotmmo.com/forsaken-world-272.html)

Yup.
I loved the game, but I rather only have FPS Games in Windows (too distracting to play MMORPG).

---

