---
title: "Getting cursor to show in C&amp;C3"
date: 2008-03-27
forum: Wine
---

### Post by DanielJackins on 2008-03-27
Hi all,

I recently installed Command and Conquer 3: Tiberium Wars following the guide on the WineHQ website. Everything worked perfectly (actually the best any game has for me, graphics-wise at least) except the cursor in the game doesn't show up (which they said would happen). They tell you how to update the cursors so it shows in the game, but I can't make heads nor tails of what they're telling me to do, and I can't figure it out.

Any help would really be appreciated, thanks :)

---

### Post by mnnn on 2008-04-17
you have to use patched wine to get cursor/network play in C&C3.

---

### Post by Homunculi on 2008-04-17
of you goto winehq.org they have all the link to get the patches 
and a how to to get you started for the mouse curser and the network patch 

also a precompiled wine 9.5.0 
says it is unstable but i gave it a shot after my hdd failed .. it worked 

go to [www.winehq.org](www.winehq.org) ... look in the apps database for cnc3 and they have a how to there 
pretty simple 

good luck ... the game is great

---

### Post by DanielJackins on 2008-04-20
I wish i could say it is simple to me but I have no idea what to do with it all

---

### Post by funguy on 2008-04-20
Ya I got the same issue. Tried all night to get it to install "needed vb6runtimes" A new uncompiled version of wine is out. I hope it fixes it.](*,)

---

### Post by Homunculi on 2008-05-05
sorry you all are having trouble ... i should have just posted the links b4 

here is a bit off the web page from winehq.org ..... 
the second page is where you can get a pre-compiled copy of wine that will work and have the cursors 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7440](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7440)
[http://oliverdeisenroth.de/index.php?option=com_remository&Itemid=85&func=fileinfo&id=15](http://oliverdeisenroth.de/index.php?option=com_remository&Itemid=85&func=fileinfo&id=15)



How to compile the custom Wine version (you don't have to; you can also use the RPM or DEB packages above)

    * Download Wine 0.9.58, the cursor patch and network(bind) patch to the same directory
    * Unpack the Wine archive through the file manager or with 'tar -xvjf wine-0.9.58.tar.bz2'
    * Enter the Wine directory with 'cd wine-0.9.58'
    * Apply the cursor patch with 'patch -p1 < ../cursor-patches-0.9.58.patch'
    * Apply the network patch with 'patch -p1 < ../cnc3net-0.9.58.patch'
    * Update wineserver with 'tools/make_requests'
    * Update the configure script with 'autoconf'
    * Configure Wine with './configure --prefix=$HOME/wine-cnc3', where you can choose another install path if you want to. If it displays
      any errors and you are unable to fix them yourself, post the error message here, without the full console output
    * Build Wine with 'make depend && make'
    * Install with 'make install'
    * Delete the Wine source with 'cd ..; rm -rf wine-0.9.58'
    * Now you can run the game by substituting the 'wine' commandd with '$HOME/wine-cnc3/bin/wine'


:guitar:
rock on

---

