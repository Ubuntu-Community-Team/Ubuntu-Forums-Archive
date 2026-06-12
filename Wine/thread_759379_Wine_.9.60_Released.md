---
title: "Wine .9.60 Released"
date: 2008-04-19
forum: Wine
---

### Post by ekravche on 2008-04-19
Wine .9.60 is released but it's not in the repositories yet. [http://www.winehq.org/?announce=0.9.60](http://www.winehq.org/?announce=0.9.60)

---

### Post by atomkarinca on 2008-04-19
> # Option for Windows-style window decorations.

I wonder if this means themes will not hog the cpu now.

---

### Post by stinger30au on 2008-04-19
> **ekravche said:**
> Wine .9.60 is released but it's not in the repositories yet. [http://www.winehq.org/?announce=0.9.60](http://www.winehq.org/?announce=0.9.60)


patience grasshopper

---

### Post by Liolikas on 2008-04-19
[http://sourceforge.net/project/downloading.php?groupname=wine&filename=wine-0.9.60.tar.bz2&use_mirror=osdn](http://sourceforge.net/project/downloading.php?groupname=wine&filename=wine-0.9.60.tar.bz2&use_mirror=osdn)

Preparing Installation and Installing from Source

Get the development packages you need and install them properly. Get the source
package and install it into a directory of your choice. This directory may be a
directory in your home directory as root access is not necessary for compiling
the program. If you want to get any CVS version of the Wine source tree,
install CVS and follow the instructions on [http://www.winehq.org](http://www.winehq.org). After
installing the source tree, you may make some changes to the configure script
and in the root of the tree do:

         
$ ./configure
$ make depend
$ make
         

If there are errors, ensure that you got all the packages you need, and ensure
that the changes you made to the configure script work. For some errors you
have to delete config.cache (or just do a make distclean) in the directory with
the Wine source tree and try again with the steps above. If there were no
errors in each step and you want to install Wine system wide, change to root or
use "sudo" or "su -c" to install Wine:

$ sudo make install
         
or
$ su -c make install
         

Now Wine should be installed on your system. Before trying to run it, complete
the configuration as described below.

---

### Post by schtufbox on 2008-04-19
I have it installed now, but now Counterstrike Source no longer works.
Steam loads, but the game itself won't. Pity, as everything else works fine. I think I'll drop back to 0.9.58 for now :D

---

### Post by cookies on 2008-04-19
> **atomkarinca said:**
> I wonder if this means themes will not hog the cpu now.

Theming is quite fast for me on .9.59 if I use this style (on MOST programs I have, I cannot vouch for all):
[http://wingnome-xp.deviantart.com/art/Clearlooks-Gummy-72460126](http://wingnome-xp.deviantart.com/art/Clearlooks-Gummy-72460126)

So, I'm guessing it should be.

---

### Post by schtufbox on 2008-04-20
> **schtufbox said:**
> I have it installed now, but now Counterstrike Source no longer works.
Steam loads, but the game itself won't. Pity, as everything else works fine. I think I'll drop back to 0.9.58 for now :D

I have the proper ubuntu 0.9.60 from winehq.org now, and CS source now works..I guess I forgot something when i compiled it myself.

---

### Post by funguy on 2008-04-21
CANT WAIT for this to hit the repo's:guitar:

---

### Post by funguy on 2008-04-21
Oh I almost forgot, does anyone know if this will fix the SHIFT LEFT-CLICK issue found in WOW and some other programs?

---

### Post by YokoZar on 2008-04-22
> **funguy said:**
> CANT WAIT for this to hit the repo's:guitar:
It's already there, for the Hardy repo.

I have intentionally *not* made a Wine 0.9.60 package for Gutsy to avoid conflicts when upgrading to Hardy.  Hardy fixes other bugs with the Wine package due to missing libraries, so it's really best if Wine users migrate to Hardy.  It's only a few days until release now :)

---

### Post by cogadh on 2008-04-22
Will there eventually be a 0.9.60 package for those who choose not to upgrade to Hardy or will 0.9.59 be the last avaialble official package for Gutsy?

---

### Post by paxmark1 on 2008-04-22
And if you were like me, wondering why your beta or release candidate kept listing your wine sources as gutsy and everything else as hardy when running apt-get or aptitude update there is info at

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

and voila 

wine 0.9.60

Possibly hand editing /etc/apt/sources.list.d/winehq.list would have accomplished the same, but I am satisfied with the results.  

peace,  mark

---

### Post by andrebrait on 2008-04-23
Hmm..

Well..
It seems that in x86-64 Hardy, Wine can Install gecko engine but it won't work...
Tried Win98, Win2k and WinXP (Default) and got no progress... steam is also affected by this, since it uses gecko engine to browse pages
I tried removing and reinstalling Wine 0.9.59 from official repositories and 0.9.60 from WineHQ's ones.

With IEs4Linux, if I change Wine to WinXP mode, IE won't work. Win2k is OK.

With the 0.9.60 the "Start" menu Icons are gone, and they won't return if I reinstall 0.9.59 :(
Anyway, I can live without them...

Am I the only one with this "bug"? :confused:

---

### Post by vexorian on 2008-04-28
> **YokoZar said:**
> It's already there, for the Hardy repo.

I have intentionally *not* made a Wine 0.9.60 package for Gutsy to avoid conflicts when upgrading to Hardy.  Hardy fixes other bugs with the Wine package due to missing libraries, so it's really best if Wine users migrate to Hardy.  It's only a few days until release now :)
Thanks, I guess -.- Now I'll have to install from source [yay?] Hardy upgrade is quite hard when you are a feisty user not wanting to break a heck load of things you did for one year, will upgrade to hardy but I will wait a month or something, before that I would like to upgrade WINE to 0.9.60 since the devs asked me to test worldeditor on it, so I'll have to compile from source.

Edit. nah it wasn'tso bad, although compiling from source does take ages...

---

### Post by kochecc2 on 2008-04-30
Can someone please verify whether or not shift-clicking works in World of Warcraft now? I've been staying back at .9.58 because of this issue.

---

