---
title: "Still having trouble with powerpoint 2007 under wine excel and word are working"
date: 2013-09-28
forum: Wine
---

### Post by W7yt8kc on 2013-09-28
I recently installed Ubuntu (after several years of not using it). I for work I need to use some of the MS office apps. I have word and excel working under wine; however, I can not get powerpoint working (all are in office 2007). 

I looked that this thread [http://ubuntuforums.org/showthread.php?t=1632527](http://ubuntuforums.org/showthread.php?t=1632527) it says> you must set riched20.dll to (native) in winecfg

Quite simply, I can not find it in Wine config, or anywhere else. I ran a search and I can not find the file anywhere on the computer. 

In Wine Configurator the only thing there is a single entry under Appplications that says "default settings"

Where is this file to be found and what am I to do to it?



Thanks,
Robert

---

### Post by Gyokuro on 2013-09-28
It get installed with wine and from a terminal you have to enter:

winecfg

and here it is documented: [http://wiki.winehq.org/winecfg](http://wiki.winehq.org/winecfg)

- HTH

---

### Post by Toz on 2013-09-28
*Moved to the **Wine** subforum.*

---

### Post by W7yt8kc on 2013-09-28
You will notice that I unmarked it. The reason is that I discovered that Canno open a powerpoint file. I amso can not save a file. 

When I try to open a file it goes into th econfiguration screen and stays ther. Unfortunuatly, I seems to also be that in excel also.

> I found it (Thread Tools) and marked it.

[QUOTE]Mark SOLVED (I don't see how to do that in this forum)

The file I needed was in the Windows > System32 folder

> Thanks, this is usefull; but, I am still having a problem. In wine cfg I need to browse to the powerpoint applicatoin; but, wine is a hidden file and wine cfg does not seem to be able to see hidden files..

Here is where I need to go to:
[QUOTE]env WINEPREFIX="/home/robert/.wine" wine C:\\windows\\command\\start.exe /Unix /home/robert/.wine/dosdevices/c:/users/robert/Start\ Menu/Programs/Microsoft\ Office/Microsoft\ Office\ PowerPoint\ 2007.lnk

. . . yes, I know, go to / > home > robert . . . but once I get there I can not go any further

In the terminal I can get to this point:> robert@robert-Lenovo:~/.wine/dosdevices/c:/users/robert$ ls
Application Data  Favorites       My Music     NetHood    SendTo      Templates
Cookies           Local Settings  My Pictures  PrintHood  Start Menu
Desktop           My Documents    My Videos    Recent     Temp



Start\ isn't even there[/QUOTE][/QUOTE]

---

### Post by Mark Phelps on 2013-09-29
The linked page from the WineHQ website provides some details:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813")

But ... be advised that a Silver rating is quite poor, and you should not be surprised if quite a few of the features do not work.

---

### Post by W7yt8kc on 2013-09-29
> **Mark Phelps said:**
> The linked page from the WineHQ website provides some details:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813)

But ... be advised that a Silver rating is quite poor, and you should not be surprised if quite a few of the features do not work.

The feature that does not work is "save." For all intents and purposes this leaves the program non functoinal. 

I have been doing some reading. It looks like I need to remove the instalatoin of 2007 that I currently have and reinstall it. Unfortunantly, it looks like the only way to do that is to completly remove WINE. So, what it really comes down to is that I need to completly reinstall Ubuntu because it looks like WINE leaves stuff all over the machine.

As mentioned, I tried Linux several years ago (red hat in 95, Mandrake in 99, Ubuntu around 06 or 07, some odd distros in 09 and 10, Ubuntu in about 11), at that time the answer to any problem was "you need to write your own app" or "you just ned to edit a config file" (I became convinced that "you need to edit a config file" is linux for "I have no idea but don't want to admitt it. . . the thing that convinced me of this was that no matter what the problem, this was the naswer and no one knew which config file).

Here is the real trouble, I work over 50 (and closer to 60) hours a week. . . then I work at least one day on the weekend to catch up. I just don't have time to play with stuff. I am willing to follow a real step by step; but, when there are a dozen conflicting ones, all of them are suspect.

Is there a way to make office work?
If not, is there a way to remove the broken install?
after removing the broken install, can office 2003 work?

Please don't point me at Lebre office. I tried it, I tried it 3 years ago too. I just don't have the time to work with something that has so little functionality and so many compatability problems.

I would like to use somethig that works better than Windows; but. . . BUT. . . I also have to get work done.

---

### Post by Mark Phelps on 2013-09-30
There is no general way to make "Office" work.  The different components, and indeed, the different versions of each have different degrees of success.  Word and Excel tend to work well, everything else has problems, and some components don't work at all.  The WineHQ site I linked has pages for each of the components and each version -- so you can see what works and what does not.

Unfotunately, Office is one of the MS products that has the worst experience in Wine.  If you need it regularly, you really have no choice other than to retain Windows to run it, either in dual-boot or running in a virtual machine.

---

