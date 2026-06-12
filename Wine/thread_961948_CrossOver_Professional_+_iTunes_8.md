---
title: "CrossOver Professional + iTunes 8"
date: 2008-10-28
forum: Wine
---

### Post by OZFive on 2008-10-28
Hello,

I as well as most of you ran out today and downloaded the free CrossOver Professional and Gaming.  Thanks Codeweavers!

Well the only real thing I really wanted to put on it right away was iTunes 8.  I know some here do not like iTunes but that is another thread.

Well I cannot get it to install and it is not on the list of supported applications.  I did some research and found that back in 2004 CodeWeavers got iTunes support built into CrossOver Office.

> Aug. 04, 2004

CodeWeavers has announced the release of an evaluation preview of CrossOver Office 3.1 with support for Apple's iTunes digital jukebox and download store.

Jeremy White, CEO of CodeWeavers said that “iTunes has been our number one, most requested application. We remain confident that by the end of 2005, the majority of Windows applications will be supported by CrossOver Office.”

....

CrossOver Office Version 3.1 with iTunes support will be available later this year in both the standard and professional editions. 
Source:
[http://www.desktoplinux.com/news/NS8798890163.html](http://www.desktoplinux.com/news/NS8798890163.html)

So I am wondering, is there still a CrossOver OFFICE?  Or is iTunes 8 not supported?  Has anyone got it to work with CrossOver?

---

### Post by clamboat on 2008-10-29
I don't know if I am seeing the same problem you are, but I also could not install itunes with the crossover product.  I used the 
"unsupported software" installation, and everything seemed to go well.  At least there were no obvious error messages.  But when I go to run iTunes from the "Run Windows command" dialog, it is nowhere to be found.  

It seems that the installation was at least partially sucessful, in that I can see what looks like a quicktime installation and the Apple software update tool is installed.  Running the apple software update just hangs while "checking for new software..."

---

### Post by Kinst on 2008-10-29
iTunes 8 won't work yet. One person managed to get it to work with his own custom patches at winehq: [http://http://appdb.winehq.org/objectManager.php?sClass=version&iId=13739]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13739")

A way better option is to try iTunes 7.something:
[http://www.oldapps.com/itunes.htm]("http://www.oldapps.com/itunes.htm")

I got 7.3 to work...ish...

---

### Post by YokoZar on 2008-10-29
> **OZFive said:**
> 
So I am wondering, is there still a CrossOver OFFICE?  Or is iTunes 8 not supported?  Has anyone got it to work with CrossOver?

What used to be Crossover Office is now just Crossover, mainly because it supports more than just office apps.

---

### Post by clamboat on 2008-10-29
> **Kinst said:**
> 
A way better option is to try iTunes 7.something:
[http://www.oldapps.com/itunes.htm]("http://www.oldapps.com/itunes.htm")

I got 7.3 to work...ish...

Thanks, Kinst.  I tried iTunes 7.3 and knew I was in trouble as soon as I got the EULA - it was gibberish.  I agreed anyway and after a warning about registry entries, iTunes came up and found my MP3s.  Unfortunately it would quickly crash if I hit the 'Play' button.

I found another helpful post about running iTunes under Crossover - [http://ubuntuforums.org/showpost.php?p=5699360&postcount=45]("http://ubuntuforums.org/showpost.php?p=5699360&postcount=45")


> **Kenzy said:**
> Well first I downloaded iTunes version 6.01 from [http://www.oldapps.com/itunes.htm](http://www.oldapps.com/itunes.htm) - site. I have the Crossover Office ver. 6 and I installed iTunes+Quicktime via the Crossover, and it works. Don't download the 7-version or above, because they won't work. The 6.01 works perfectly and finds the Airport nicely, although I have to put the terminal to ping the Airport before I start the iTunes.

EDIT: In fact, the easiest and the best way to do that is just install the Crossover Office Pro ver. 6, beause the iTunes+Quicktime-option is available in the supported software-list. It isn't there anymore in the 7-version of Crossover, and the iTunes version in CO 6 is 4. Works like a charm.

I'm going to reinstall crossover (I wiped it out in frustration) and try the earlier 6.01 version of iTunes.

---

### Post by huanix on 2008-11-16
iTunes 8 is significantly different than the last version that would run in wine (7.6). There are several possibilities for getting this to work but I'm taking a break - there was less interest than I anticipated. 

Here's my final screenshot of iTunes 8 seeing (but not recognizing) an iPhone under [highly modified] wine:

[http://www.huanix.com/2008/11/12/itunes-8-running-in-wine-recognizes-ipod/](http://www.huanix.com/2008/11/12/itunes-8-running-in-wine-recognizes-ipod/)

---

