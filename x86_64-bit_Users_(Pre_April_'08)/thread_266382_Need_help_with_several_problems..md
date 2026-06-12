---
title: "Need help with several problems."
date: 2006-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by El Lance-O on 2006-09-27
First off, I must admit I should have further investigated the logistics of Linux before making the switch from Windoze XP, but I was just too excited, and VERY much done with Windoze to keep myself from doing something obviously rational.

But these are my problems:

1. DSL connection. I have set up using 'sudo pppoeconf' so that it automatically connects on start-up, but it rarely ever does this (has happened once). I usually find myself with an unresponsive connection for a period of time, or it just doesn't work whatsoever. Using 'pon dsl-provider' and checking with 'plog', it says I have a connection, but is still unresponsive for usually a good 10 minutes. Sometimes I have to just reset the config by using 'sudo pppoeconf' once or twice to finally get it to respond. This is TOO MUCH of a hassle to just get on the internet(s).
[SIZE="1"]Sen. Ted Stevens nor President Bush endorse the previous parody of the word 'internets'[/SIZE]

2. FireFox, works great as always, I just need help using my previous profile from XP seeing as it won't let me just copy it into the folder because of not having owner privledges. I understand this is just a precaution so any ol' program can't just modify any system file. But it's just irritating in the end. Also, I need flash files to work as well.

3. WINE. Where shall I begin. For one, it took me FOREVER to find out how to install WINE on an AMD system, let alone realize that some of the errors in the installation were normal, and only had to do with icons. Great. It is usually unresponsive, and when it is responsive, it doesn't work and ends the program for a variety of reasons. But hell, notepad works and that's all that matters right? Several programs say there is missing file when it is usually in the same folder everytime.

4. CounterStrike:Source. I just copied the entire Valve folder from my XP partition because I do not have the CD as it came with the harddrive that was handed down to me. I would like to know if just running that would still work seeing as it is not a fresh install on the fake C: drive I created with WINE. And would CS work just as well in WINE as it would in Cedega? Because I really don't want to fork over $15 and $5 each month to play a game. I don't like subscriptions, evil, evil things.

5. General clutter. I like having a very upkept and organized system, and Linux seems to really pushing me with that. To me, the system is very confusing and overall irritating to the perfectionist. Another cause of this alarm to be noticeable, is that I used Automatix to install the needed files to do everyday things (such as play .mp3 files) and now I find myself with 2 of some programs. I don't like that, not one bit. Especially seeing as I don't know what to do and am worried I'm just going to f*ck something up.

6. .WMA, I have a lot of these. And I need to play them, plain and simple.

I'm really just asking for someone to help me in setting up my new Linux system so I can do everything I want with ease (download/play music, videos, CounterStrike, DOS games, emulators, iPod management, WINE/Cedega) and hopefully at the same time give me a good crash course on Linux in general. I've been ghosting on this forum for weeks now, and I haven't been able to find someone EXACTALLY with the same problems, so I'm really hoping I can get something positive out of this cry for help.

I've been using Windows for 10 years now, and am quite computer illiterate, so don't assume me to be new on the scene and overall slow. I just need some serious help.

Thamks a million in advance, especially as the responses will probably take a large portion out of someone's time, not to mention reading this painfully long post.

-El Lance-O

---

### Post by El Lance-O on 2006-09-27
Oh, and I'm having problems with my screensavers, they all don't render correctly (or nothing at all) and they used to crash my system just previewing them before I used Automatix.

---

### Post by FluffyElmo on 2006-09-27
I can't help you with everything, but...

2. In your home folder hit *Ctrl-H* to show hidden files. Your profiles should be in *.mozilla/firefox/*. You should be able to put your old profile there without special permissions.

3. & 6. Check this thread which has links to getting 32bit programs installed on 64bit. [http://www.ubuntuforums.org/showthread.php?t=191205]("http://www.ubuntuforums.org/showthread.php?t=191205")

5. From the top menu *Applications->System Tools->Applications Menu Editor* will let you remove menu items. Synaptic (*System->Administration->Synaptic Package Manager*) will let you add/remove programs.

---

### Post by FluffyElmo on 2006-09-27
Oh, and for the screensavers I'd suspect your video drivers. Search the forum for what card do you have (Nvidia or ATI) and you should find instructions for installing the latest drivers.

---

### Post by FluffyElmo on 2006-09-27
Also, your conection problems aren't 64bit specific. You'd probably have the same problem with 32bit so you may want to try the networking forum with that question. [http://www.ubuntuforums.org/forumdisplay.php?f=136]("http://www.ubuntuforums.org/forumdisplay.php?f=136")

Good Luck!

---

### Post by saphil on 2006-09-27
About win to Lin profile moving.
You might just add your bookmark folder to the new linux profile in /home/youracct/.mozilla/firefox/profilealphabetsoup.default

This will not save all of your passwords etc, but it is close to failsafe.  A bookmark file is just an html file and is readable on any platform.

On the clutter/perfectionism.
This is a hard one, consider it a bit like moving from New York to LA.  None of the streets are going to be in the same relation to each other but since it is a different town, you don't keep looking for Central Park as your landmark.  It is just different, so don't stress out on it.  :-)

What is the same is you have a Desktop where you can put all your personal files if you want.  You can make a My_Documents folder there if you want, and save everything there.  You have to get used to the idea that "address of your home is no longer c:\Documents and Settings\YourUsername\...   and that it is now /home/YourUsername/...
Out here, we use forward slashes as directory path markers.  Back wrere you came from they used backwards slashes for that.

---

### Post by fabertawe on 2006-09-27
> **El Lance-O said:**
> 4. CounterStrike:Source. I just copied the entire Valve folder from my XP partition because I do not have the CD as it came with the harddrive that was handed down to me. I would like to know if just running that would still work seeing as it is not a fresh install on the fake C: drive I created with WINE. And would CS work just as well in WINE as it would in Cedega? Because I really don't want to fork over $15 and $5 each month to play a game. I don't like subscriptions, evil, evil things.

You will need to install Steam (search the forums if you have problems installing it) but once that's done you can just copy over any games as long as you maintain the same directory structure/hierarchy as Windows. I have no idea how well the source games play under Wine though!

Welcome to Ubuntu, it's definitely worth sticking with :) 

Paul

---

### Post by El Lance-O on 2006-09-27
Well I copied my FireFox profile over, but there seems to be MANY problems, and it's being quite glitchy. I guess I'm just going to have to reinstall all of my old extentions and re-bookmark all of my sites.

But thanks VERY much for the responses, it's definately putting me on the right track.

I guess I will just keep trying, but expect to hear much more from me in the future, as I'm sure I will be needing the help.

Thanks again!

---

### Post by mips on 2006-09-28
It would have been better to post individual posts for each problem in the appropriate forums.

---

