---
title: "Wine Question"
date: 2007-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by blackstealth007 on 2007-03-06
I installed the wine for 64 bit, but have a question. How would i go about installing exe's on cd's? I also downloaded steam and was able to get it update the client, but when it brings up the login part, there is no letters, just tables and borders. It wont even let me click in the box to type something in.

---

### Post by Gerard Barberi on 2007-03-06
Try using winetools.  It's a gui installer for wine.  Plus it will install the windows fonts which seems to be what you are missing when you mention that the install box had no type in it.

---

### Post by blackstealth007 on 2007-03-07
I have the x86_64 version of ubuntu edgy. Is that going to be a problem as it says its for x86 architecture?

---

### Post by Mongoose on 2007-03-07
Read this HowTo to setup Wine for x86_64 for ubuntu:

   [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

It'll guide you step by step -- you don't have to install Oblivion.   =)

Edit:
You can just run > wine setup.exe after that.

---

### Post by dfreer on 2007-03-07
The reason why steam looks so bad is because you do not have the tahoma.ttf file. You can google it or grab it from a windows box, it would be located in C:\windows\fonts\ I believe. Once you have the tahoma.ttf file, simply put it in ~/.wine/drive_c/windows/fonts/ and Steam should install/run fine. 

Note: I would grab the newest version of Wine 9.32 if you don't have it installed, it has fixed the flashbang bug in CS:S and handles the windows correctly.

---

### Post by Moordrik on 2007-03-13
> **dfreer said:**
>  
Note: I would grab the newest version of Wine 9.32 if you don't have it installed, it has fixed the flashbang bug in CS:S and handles the windows correctly.

Be careful if you use Wine 9.32 it fixes some issues, but it comes with some all it's own.  I had a heck of a time getting WoW to work, ended up going back to 9.31, installing the msttcore fonts, and all was well.

---

### Post by konungursvia on 2007-03-13
I can't seem to install anything on wine, just a little secure ftp client. I can't even remember how that went. How do I install downloaded exe's? Also, why can' wine look on my ntfs partition and let me run the exe's from there, like my favourite game, Kyodai Mahjong? :(

---

### Post by dfreer on 2007-03-13
> How would i go about installing exe's on cd's?
It depends on your installation. Use winecfg in terminal, go to the "Drives" tab, and hit the autodetect button. It should map a bunch of your drives to different drive letters, in particular notice which drive letter is mapped to /media/cdrom0. In mine I have it mapped to D:\ You can then use in terminal:
```
wine d:setup.exe
```
(Note of course this totally depends on your game. Maybe it uses Setup.exe, Install.exe, or whatever you should be able to figure stuff out from there :) )

> I also downloaded steam and was able to get it update the client, but when it brings up the login part, there is no letters, just tables and borders. It wont even let me click in the box to type something in.
tahoma.ttf is ABSOLUTELY the problem with messed up text in steam.exe, no question about it. You may have to right-click in the login window the first time in order to type, I dunno why this is. Check winehq applications database for steam and counter-strike, as most of this stuff is already covered.  


> Be careful if you use Wine 9.32 it fixes some issues, but it comes with some all it's own. I had a heck of a time getting WoW to work, ended up going back to 9.31, installing the msttcore fonts, and all was well.
That was exactly my problem with Wine 9.31, it no longer let my window manager "manage" my wine windows... so the main steam window would be on top of everything and mess up my steam games. Wine 9.30 had worked fine, and now Wine 9.32 works great as well. I dunno why wine seems to fix some things and break others on each release, but at least it's getting better and better every day.

> I can't seem to install anything on wine, How do I install downloaded exe's?
Instead of saying "Nothing works", why don't you post which program you are trying to run specifically, and the terminal output when you try to install it? The typical command to install a program saved to your desktop (after you have set wine up using winecfg) is:
```
wine ~/Desktop/myniftyprogram.exe
```

> Also, why can' wine look on my ntfs partition and let me run the exe's from there, like my favourite game, Kyodai Mahjong?

Linux can read (and write, but AFAIK this isn't very reliable yet) to NTFS, do you have your NTFS partition mounted in /etc/fstab? Also, have you setup winecfg so that your NTFS partition is mapped to a drive letter? It would be easier if you just copied those *.exe's to your linux partition and run it from there. Not all windows programs work, however, check winehq's application database to see if anyone has gotten your particular program running.

---

### Post by zorkerz on 2007-03-23
> **dfreer said:**
> Linux can read (and write, but AFAIK this isn't very reliable yet) to NTFS, do you have your NTFS partition mounted in /etc/fstab? Also, have you setup winecfg so that your NTFS partition is mapped to a drive letter? It would be easier if you just copied those *.exe's to your linux partition and run it from there. Not all windows programs work, however, check winehq's application database to see if anyone has gotten your particular program running.

Does anyone know the real status of this?
-ntfs-3g i believe has recently gotten read/write support
-is it some communication thing between wine and ntfs-3g?

Does anybody know about this in anyway?

---

