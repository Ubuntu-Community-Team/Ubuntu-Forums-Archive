---
title: "Should I be installing 64 bit"
date: 2006-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sir_Sid on 2006-09-15
I have a 64 bit processor but a friend has told me alot of apps are not available on 64 bit versions of linux. Is this still true? What major apps dont have a build? All I plan on doing in linux is listing to music, browsing the web, messing with kismet and some other stuff like that. Also want to be able to watch movies and stuff like that. So what would I have to watch out for if I went ahead and installed the 64 bit version of Ubuntu?

---

### Post by Kilz on 2006-09-16
> **Sir_Sid said:**
> I have a 64 bit processor but a friend has told me alot of apps are not available on 64 bit versions of linux. Is this still true? What major apps dont have a build? All I plan on doing in linux is listing to music, browsing the web, messing with kismet and some other stuff like that. Also want to be able to watch movies and stuff like that. So what would I have to watch out for if I went ahead and installed the 64 bit version of Ubuntu?

You shouldnt have that hard of a time. All the major applications are avilable. You might have to follow a howto, or run a auto setup script for some things. I wont lie to you, there may be some older application, or oddball thing that may not be avilable. But there is only a 2% diffrence in the avilable packages between i386 and amd64. 
We have a constant FUD battle with the "things are not avilabe" line. While that may have been true of Breezy, Dapper is another story. One of the nice things about Dapper is that it will run 32bit applications if one is needed. A lot of people run a 32bit firefox for example. The link is in my signature for that one.

---

### Post by jono.carnie on 2006-09-16
Just on the question of should I run 64 bit Dapper... what major advantage is there, apart from the bleeding obvious 64 bit...
I mean is there a increase in speed at which apps run?

There certainly seems to be a lot more tweaking needed to get things like codec's working.
so what's the advantage?

JC

---

### Post by Kilz on 2006-09-16
> **jono.carnie said:**
> Just on the question of should I run 64 bit Dapper... what major advantage is there, apart from the bleeding obvious 64 bit...
I mean is there a increase in speed at which apps run?

There certainly seems to be a lot more tweaking needed to get things like codec's working.
so what's the advantage?

JC
There is a performance improvement, it can be as much as 30% for some applications like encoders/rippers, 3d modeling programs, or anything that dose a lot of number crunching. But ymmv depending on what applications you use. Most users that have tried both say the 64bit os is more responsive.
True some people just want things to work as quickly as they can and don't care about performance, so they install the 32 bit version. It will work, most of the time. Some people report that the 32bit version had problems that went away when they switched like odd crashes and sluggishness. Its like buying a corvette and taking the plugs out of 4 of the cylinders to save gas imho.
For the most part the setup isn't that hard. All the codecs except wma and wmv can be installed with a few clicks in synaptic. The wmv and wma can be set up in 10 15 minutes with a howto. If you run my firefox with flash and mplayer script you dont even have to do it as the script sets that up so the mplayer plugin works. The setup isn't that much and once its done, its done.

---

### Post by samssf on 2006-09-19
Heh, I wouldn't install ubuntu 64 bit if I were you. I've had horrible problems and spent 30 hours over the weekend trying to get things running. (and I'm a pretty experienced user)

things I can't get running:

xgl + compiz + amd64 is hell. I've tried every single how-to there is, and been very careful to keep track of what I am doing. Still, nothing.

My wireless card (linksys) which users the broadcom chipset isn't working, and like above, I have tried the walkthroughs without success.

Amarok (great media player) will not work on my system. Other people with 64bit chipsets have had the same problems, and I have not been able to get it to work.

I've had tons of other problems with software like KeePass, Wine, etc. Installing Wine on amd64 sucks, and using force architecture I still have problems.

Maybe it's just me, but it's been a living nightmare. And I've tried everything... and 32bit users never seem to have my problems.

---

### Post by city-17 on 2006-09-19
> **samssf said:**
> Heh, I wouldn't install ubuntu 64 bit if I were you. I've had horrible problems and spent 30 hours over the weekend trying to get things running. (and I'm a pretty experienced user)

things I can't get running:

xgl + compiz + amd64 is hell. I've tried every single how-to there is, and been very careful to keep track of what I am doing. Still, nothing.

My wireless card (linksys) which users the broadcom chipset isn't working, and like above, I have tried the walkthroughs without success.

Amarok (great media player) will not work on my system. Other people with 64bit chipsets have had the same problems, and I have not been able to get it to work.

I've had tons of other problems with software like KeePass, Wine, etc. Installing Wine on amd64 sucks, and using force architecture I still have problems.

Maybe it's just me, but it's been a living nightmare. And I've tried everything... and 32bit users never seem to have my problems.

Installing Xgl/Compiz wasn't that hard for me, take a look at this post:[http://ubuntuforums.org/showthread.php?t=260452]("http://ubuntuforums.org/showthread.php?t=260452")
Hope it helps.

---

### Post by patrickfromspain on 2006-09-19
XGL + compiz is just as easy as in 32 bit. Maybe, the updates take longer to hit the repos.

Amarok.. no problems at all here.

Wine.. haven't tried, but crossover office works just as fine as in 32bit mode.

---

### Post by samssf on 2006-09-21
Yeah, I've tried every single walkthrough / how-to for getting xgl and compiz up and running.. and followed every step perfectly. I've installed several times and made sure to always clean up after a how-to doesnt work correctly. I'm guessing my hardware config just must not work with it. AMD64 + XFX Nvidia 6600GT AGP card

---

### Post by RAOF on 2006-09-21
**My** 6600GT works just fine with XGL/compiz.

---

### Post by tymek666 on 2006-09-21
I've tried xgl/compiz on my system in june and it worked fine.
Amarok - no problem
Wine - thx to Kilz HowTo runnig fine.

---

### Post by kick6 on 2006-09-21
> **Kilz said:**
>  Its like buying a corvette and taking the plugs out of 4 of the cylinders to save gas imho.



This is off-topic, but I had to comment:  Its funny you used that analogy as the new vettes will shut off 4 injectors and plugs on the freeway to do just that :-P

---

### Post by Kilz on 2006-09-21
> **kick6 said:**
> This is off-topic, but I had to comment:  Its funny you used that analogy as the new vettes will shut off 4 injectors and plugs on the freeway to do just that :-P

Kind of like the adm64chip lets you run 32bit applications. Thats why we can setup some 32bit things. But it would be stupid imho if it was setup to only run on 4 all the time.

But isnt that an old technology, I seem to remember cadalic's used to do that.

---

