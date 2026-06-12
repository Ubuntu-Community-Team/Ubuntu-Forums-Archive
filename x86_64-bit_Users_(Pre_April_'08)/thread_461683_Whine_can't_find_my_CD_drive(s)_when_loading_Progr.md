---
title: "Whine can't find my CD drive(s) when loading Programs"
date: 2007-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by diddler on 2007-06-01
I just downloaded and installed Wine.  I grabbed the first Windows app I had handy, which was a game.  The install went smoothly (after a dramatic pause where Wine pretended not to notice the WinApp CD).  THEN I went and tried to load the game.  As with most Microcrap apps, this one, assuming I was a filthy bootlegger, looked for the CD.  It could not find it, although it was in the same drive I installed it from,  Game would not play.

Any thoughts?

Oddly, Wine DID find numerous DOS/WIN programs on my disk that SHOULD have been erased when I departitioned my hard drive and reformatted it in preparation for installing Ubuntu.  I even put the link to one of those programs on my desktop where it happily resides and even loads when I tickle the icon, BUT, I can't find the other programs any more.  Wine is freaking me OUT!:confused:

---

### Post by tooCanad on 2007-06-02
I had the same problem.

Call winecfg in a terminal and check to see if your cd /dvd  is mapped as a drive in wine.

TC

---

### Post by diddler on 2007-06-03
> **tooCanad said:**
> I had the same problem.

Call winecfg in a terminal and check to see if your cd /dvd  is mapped as a drive in wine.

TC

Thanks, I will try it as soon as I get to a high-speed connection and download the 16MBs of files needed to install wineconfig on my computer.  This is getting ridiculous.

---

### Post by diddler on 2007-06-16
> **tooCanad said:**
> I had the same problem.

Call winecfg in a terminal and check to see if your cd /dvd  is mapped as a drive in wine.

TC
Finally got wineconfig working and that seems to have done the trick.  Thanks for the assist.

---

### Post by almalaci on 2007-12-08
I still have the same problem, winecfg doesn't solve it. I installed a program that uses a database or something from the cd every time it runs but it doesn't find the disk. The program works fine under windows.
Any other ideas?

---

