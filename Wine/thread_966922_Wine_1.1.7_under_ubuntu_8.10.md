---
title: "Wine 1.1.7 under ubuntu 8.10"
date: 2008-11-01
forum: Wine
---

### Post by sk8ordie97 on 2008-11-01
so i jsut updated ubuntu and now whenever i try to launch something under wine nothing happens. what do i do????

---

### Post by Dark9204 on 2008-11-01
Try to completely remove wine.
In Synaptic package manager select "complete uninstall" then go to your home dir and select "show hidden folders" and delete your .wine folder.

Also, make sure that you are using ubuntus 8.10 software source/repository when you reinstall it.

---

### Post by ajgreeny on 2008-11-01
Wine 1.1.7 certainly works in hardy, so I would expect it to be OK in intrepid as well.  Have you got the wine.hq repos enabled?  If not go to [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and you can enable the repos and get the .deb which should work.  Perhaps just needs reinstalling as non-ubuntu apps can cause problems if you do a distro update from 8.04 to 8.10.

---

### Post by stinger30au on 2008-11-01
wine is working for me on 8.10 no drama with updates from winehq


i suggest you run the windows program from the command line and see what errors your getting

you may need to install wine tricks to make the program run correctly

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by deathpulse on 2008-11-01
I just downgraded to wine 1.1.5 - 1.1.7 does NOT work - sound locks up (ALSA in wine cfg) or during game running.  1.1.7 and AMD64 ubuntu 8.10 = no go for me.  1.1.5 seems to work.

---

### Post by sk8ordie97 on 2008-11-01
i got it working tahnks guyss

---

