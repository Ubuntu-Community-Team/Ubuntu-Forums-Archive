---
title: "iTunes on Lubntu"
date: 2013-06-04
forum: Wine
---

### Post by philpense on 2013-06-04
Followed the community guidance found at: [SIZE=3][http://ubuntuforums.org/showthread.php?t=1688221](http://ubuntuforums.org/showthread.php?t=1688221)[/SIZE]

Navigated to winehq.org/download.  The 'download ubuntu packages' link is seen and clicked. The instructions are: "open the software sources menu by launching the Ubuntu Software Center"  This is a lubuntu machine and clicking the link leads to nothing but an image of what one should see... but no download.  [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu) is the URL.   

Not sure about how to proceed.

---

### Post by MidnightGrey on 2013-06-04
At the very bottom of the page you linked are instructions on how to install wine by command line.
You can follow those instructions; or just type out these commands:
```

*$ *sudo add-apt-repository ppa:ubuntu-wine/ppa[I]
$ [/I]sudo apt-get  update
$ sudo apt-get  install wine1.5 
```

---

### Post by Baldrick_NZ on 2013-06-05
It depends on what you want iTunes to do for you. You can get the player to work with some older versions, but forget about buying music from the store - that part just wont work.

If you're looking for an online store, try Google Music. They leave iTunes for dead in terms of features, and the music costs about the same. Best part is, because it's web-based, it works across all platforms (Linux, iOS & the other one...)

Also, I wouldn't use wine1.5, as it's in development. Best to use the stable wine1.4, imho.

Best of luck!

---

### Post by s.fox on 2013-06-05
Thread moved to [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313") :)

---

### Post by philpense on 2013-06-05
Much thanks  for the reply.  I already installed wine 1.4  weeks ago.  It is the iTunes install that I thought I was following.

---

### Post by philpense on 2013-06-05
Much thanks for the reply.  I actually have 1.4 installed.  I seek minimal itunes features...  app downloads, upload my own cd music, and download a few video news shows.

AppDB is supposed to be downloaded from the winehq.org site.  Found the site and the download link but no download is forthcoming.  any guidance is welcome

---

### Post by Mark Phelps on 2013-06-05
As you will see from the linked WineHQ web page, every version of iTunes has a different success (or lack thereof) in Wine.  You need to read the details for the version you're attempting to use and see what folks did to get it working:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")

---

