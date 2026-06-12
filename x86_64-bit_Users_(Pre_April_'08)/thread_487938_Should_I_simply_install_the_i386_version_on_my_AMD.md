---
title: "Should I simply install the i386 version on my AMD X2 64-bit system?"
date: 2007-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by daller on 2007-06-29
Hi there,

I get segmentation faults in UT2004 when playing on my new 64-bit machine...

Can this be due to the 64-bit platform?

What do I gain / loss if I install i386 instead?

---

### Post by Buendia on 2007-06-29
I think for a normal desktop/laptop user the 64 bit distros are big mess. 64 bit is almost only superior for scientific application, see [this]("http://art-blog.no-ip.info/files/amd64vsi386.pdf") for a benchmark.

I have installed feisty 64 for performance, but it is terrible for browsing and multimedia, very disappointing and very time consuming to fix thousands of little problems -- things like these bounce people back to windows.

You will probably find an easy solution for your problem, perhaps running as root will help. However that is not going to be the end of your problems, in a few minutes, something else will not work properly and you will find out that is is yet another 64 bit issue.

---

### Post by John.Michael.Kane on 2007-06-29
> **Buendia said:**
> I think for a normal desktop/laptop user the 64 bit distros are big mess. 64 bit is almost only superior for scientific application, see [this]("http://art-blog.no-ip.info/files/amd64vsi386.pdf") for a benchmark.

I have installed feisty 64 for performance, but it is terrible for browsing and multimedia, very disappointing and very time consuming to fix thousands of little problems -- things like these bounce people back to windows.

You will probably find an easy solution for your problem, perhaps running as root will help. However that is not going to be the end of your problems, in a few minutes, something else will not work properly and you will find out that is is yet another 64 bit issue.

There's numerous guides in this section that allow for the install of codecs flash wine java. So your theory that 64bit is terrible for browsing and multimedia is false.

Also what may not have worked for you has worked many other 64bit users.

> **daller said:**
> Hi there,

I get segmentation faults in UT2004 when playing on my new 64-bit machine...

Can this be due to the 64-bit platform?

What do I gain / loss if I install i386 instead?

We need more info. Is the game the being run through wine cedega or is it a native linux game. Also your system specs may help as well.

As for going back to 32bit yes that is an option,however. make sure your doing it for the right reasons. As any problems you have on 64bit can still manifest themselves on 32bit as well.

---

### Post by Cappy on 2007-06-29
> **daller said:**
> Hi there,

I get segmentation faults in UT2004 when playing on my new 64-bit machine...

Can this be due to the 64-bit platform?

What do I gain / loss if I install i386 instead?

Install the mega patch and THEN install ut2004-lnxpatch3369-2.tar.bz2. It contains a fix for AMD64. Then you must edit the script in the root of whereever you installed the game. I forgot where the default install path is, but say it is /usr/games/ut2004. You would need to edit /usr/games/ut2004/ut2004 and replace the text "ut2004-bin" with "ut2004-bin-linux-amd64" inside of it (search and replace).

Links:
[http://gaming.gwos.org/e107_plugins/content/content.php?content.56](http://gaming.gwos.org/e107_plugins/content/content.php?content.56)
[http://www.gamershell.com/download_11937.shtml](http://www.gamershell.com/download_11937.shtml)
[http://www.gamershell.com/download_11985.shtml](http://www.gamershell.com/download_11985.shtml)

Buendia: 64-bit works easily, if you learn to use the search feature on the forums which you should be doing anyway

---

### Post by Buendia on 2007-06-29
> **SD-Plissken said:**
> 
Also what may not have worked for you has worked many other 64bit users.


See, that is the problem. An ideal OS must be universal, what is the point of something working for some and not working for others? The age of download-the-course compile-to-binary is gone, people want things to work out-of-the-box.

The aim is that the OS serves us, but this forum and all forums like this are full of creatures serving the OS.

---

### Post by stmiller on 2007-06-29
I run ut2004 in Ubuntu 64. There is a 64bit version which is part of the last ut2004 Linux patch release. It contains both 32bit and 64bit binaries.


I also have no problems with any multimedia codecs. There is an easy script from a forum member which installs and sets up all codecs.

---

### Post by Kilz on 2007-06-29
> **Buendia said:**
> See, that is the problem. An ideal OS must be universal, what is the point of something working for some and not working for others? The age of download-the-course compile-to-binary is gone, people want things to work out-of-the-box.

The aim is that the OS serves us, but this forum and all forums like this are full of creatures serving the OS.

OOOOOOOOOOOOOOOOO so if something doesnt work out of the box it isnt ready? Perhaps its skipped your attention, but 64bit is just this small section. The WHOLE ENTIRE REST OF THE FORUM IS FULL OF 32BIT USERS HAVING PROBLEMS. So by your own reasoning 32bit isnt ready. In fact no operating system is ready as someone is going to have things not work out of the box. 
You come off as a customer, someone who expects things to be perfect and when it isnt complains. Expecting something to be ready for you without having to do anything or give anything back. 
If I were you I would demand a full refund!!

---

### Post by cprofitt on 2007-06-30
> **Kilz said:**
> OOOOOOOOOOOOOOOOO so if something doesnt work out of the box it isnt ready? Perhaps its skipped your attention, but 64bit is just this small section. The WHOLE ENTIRE REST OF THE FORUM IS FULL OF 32BIT USERS HAVING PROBLEMS. So by your own reasoning 32bit isnt ready. In fact no operating system is ready as someone is going to have things not work out of the box. 
You come off as a customer, someone who expects things to be perfect and when it isnt complains. Expecting something to be ready for you without having to do anything or give anything back. 
If I were you I would demand a full refund!!

Do you take the same approach to Microsoft products? You must have loved Windows ME and been one of the guys helping Microsoft fix the "problems"

---

### Post by GumbyX on 2007-06-30
> **PrivateVoid said:**
> Do you take the same approach to Microsoft products? You must have loved Windows ME and been one of the guys helping Microsoft fix the "problems"

I hate to add to this soon-to-be flame war, but MS is PAID to put out a decent product. I myself was stuck with ME and it was horrid. There was no reason for MS to put out that horrible OS. Ubuntu, along with all linux distros , are free and willing take input from the community to fix the problems, where as MS just seems to cover it up and make you pay your way out of the whole they dug for you. If MS followed linux (being open to community input and help), I highly doubt that many users, like myself, would be looking for alternatives. Ubuntu has really grown on me and I am starting to see the light of Open-Source. Not ready to give up on Windows yet, but its nice to get some help when the "product" has problems. Esp when it doesn't cost me over $100 to get said help.

But thats just me.

---

### Post by Kilz on 2007-06-30
> **PrivateVoid said:**
> Do you take the same approach to Microsoft products? You must have loved Windows ME and been one of the guys helping Microsoft fix the "problems"

I was one of the few who never installed that Bloat monster from the netherworld. But I did have friends who did. The difference in that case is windows is a commercial product. You pay for it. Its a different situation than FOSS.
With Free and Open Source Software you receive something free. You should do your part to help improve it if you can and give back because you were given it free.
With a commercial product, you paid for it. You have some right to expect it to work and if it doesnt to complain to the person who you bought it from, or to the creator.
The problems start when people who are used to deaing as a consumer and demanding because they paid for something do the same thing with FOSS. You cant, its not the same thing.
Anyone who doesnt understand what I just said [might want to read this]("http://linux.oneandoneis2.org/LNW.htm"), the whole page is good, butsection 3a explains it in more detail.

---

### Post by Kilz on 2007-06-30
> **GumbyX said:**
> I hate to add to this soon-to-be flame war, but MS is PAID to put out a decent product. I myself was stuck with ME and it was horrid. There was no reason for MS to put out that horrible OS. Ubuntu, along with all linux distros , are free and willing take input from the community to fix the problems, where as MS just seems to cover it up and make you pay your way out of the whole they dug for you. If MS followed linux (being open to community input and help), I highly doubt that many users, like myself, would be looking for alternatives. Ubuntu has really grown on me and I am starting to see the light of Open-Source. Not ready to give up on Windows yet, but its nice to get some help when the "product" has problems. Esp when it doesn't cost me over $100 to get said help.

But thats just me.

It takes some people time to adjust and move over to open source. Some people never give up Windows completely. I used a duel boot for about 3 months. You may find yourself using one operating system less and less. 
The freedom to help is a freedom everyone should enjoy.  :D

---

### Post by tetrafuran on 2007-06-30
> **Buendia said:**
> I think for a normal desktop/laptop user the 64 bit distros are big mess. 64 bit is almost only superior for scientific application, see [this]("http://art-blog.no-ip.info/files/amd64vsi386.pdf") for a benchmark.

I have installed feisty 64 for performance, but it is terrible for browsing and multimedia, very disappointing and very time consuming to fix thousands of little problems -- things like these bounce people back to windows.

I can imagine lots of people would uninstall linux because of this and go back to windows. Good thing I started struggling with ubuntu during my summer vacation. I still think ubuntu.com should mention that i386 version is recommended for beginners and AMD64 version is for computer enthusiasts who also happen to be running AMD64 processors. It should be clearly mentioned that i386 is possible to run in 64 processors too and doing so will be much better for newbies.

When I downloaded Ubuntu I noticed there are different versions of it. I knew I had AMD 64 so I figured I should install a 64 bit ubuntu as well. Being new to ubuntu, this decision probably was not the best one to be made at this point. Of course I suffered (and still do) from all sorts of issues with software not working or even being available. In any case the amd64vsi386.pdf was good news for me. I think in my case it's worth the extra effort, since I'm using GIMP a lot. Besides this situation is forcing me to learn new stuff about linux. Perhaps the road is a bit rocky, but so it was in the 90's when I started using DOS and windows. Nothing new there.

I've noticed several issues with software, but somehow I've managed to get the things working. Of course it requires lots of reading an plenty of forum time. I wish I had linux veteran living next door. I help my friends with windows related problems, but I'm pretty alone with my own computer. Thanks to these forums I've managed live past the initial purgatory.

---

### Post by Kilz on 2007-06-30
> **tetrafuran said:**
> I can imagine lots of people would uninstall linux because of this and go back to windows. Good thing I started struggling with ubuntu during my summer vacation. I still think ubuntu.com should mention that i386 version is recommended for beginners and AMD64 version is for computer enthusiasts who also happen to be running AMD64 processors. **It should be clearly mentioned that i386 is possible to run in 64 processors too and doing so will be much better for newbies.**

When I downloaded Ubuntu I noticed there are different versions of it. I knew I had AMD 64 so I figured I should install a 64 bit ubuntu as well. Being new to ubuntu, this decision probably was not the best one to be made at this point. Of course I suffered (and still do) from all sorts of issues with software not working or even being available. In any case the amd64vsi386.pdf was good news for me. I think in my case it's worth the extra effort, since I'm using GIMP a lot. Besides this situation is forcing me to learn new stuff about linux. Perhaps the road is a bit rocky, but so it was in the 90's when I started using DOS and windows. Nothing new there.

I've noticed several issues with software, but somehow I've managed to get the things working. Of course it requires lots of reading an plenty of forum time. I wish I had linux veteran living next door. I help my friends with windows related problems, but I'm pretty alone with my own computer. Thanks to these forums I've managed live past the initial purgatory.

The 32bit being better for newbies is debatable.
1. Each and every other section, including [Absolute Beginners]("http://ubuntuforums.org/forumdisplay.php?f=73"), [General Help]("http://ubuntuforums.org/forumdisplay.php?f=131") , and [Installation&Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=140") is FULL of 32bit users having issues and problems. If 32bit was so sure fire "easy" why are there so many posts in the 32bit sections? This question has never been answered by people spreading FUD.
2. Each and every version of Ubuntu requires some setup. Some new users coming from Windows expect it to "just work". See #1 for proof it doesnt.
3. The first thing someone who is having problems looks for is an easy fix. They think that if they only would have installed version xyz all the problems would disappear. Most of the time the problems follow them to the new version. 
4. It has been proved by me and others that there are very few applications that are not A) Available as 64bit versions, B) Can be compiled as a 64bit or C) the 32bit version can be made to run on the 64bit version. Yet the FUD still pops up its ugly head. 
5. Fear of the terminal. Most new users coming from windows have a fear of the terminal. When it is explained that they need to use it to fix a problem cold sweats start. They start looking for a way to "just install" with clicks. Then someone lies to them and tells them that the 32bit version is "fool proof". There are loads of fools proving them wrong , see #1.
6. There is a search on the forums? Sadly some never use it. Its easier to blame the 64bit.
7. They must have the latest and Greatest. Linux is community developed. Sadly most dont understand this. They dont understand that they are the beta testers. They dont understand that they help make everything better by reporting bugs. But this is a problem for the new user comming from Windows who wants polished Software. New users should not install the newest version but one back that has the bugs worked out. New users should never, ever, not in a million years, not even for a second install a clearly labeled Development version. Sadly some are now "trying" Gutsy

Ubuntu should not recommend the 32bit version, it should clearly and in plain words say "Expect to have to do some work to get this operating system to run, regardless of what version you install".

---

### Post by Viewtifulj on 2007-06-30
I dont really have much to add other than that for me everything went fairly smoothly right from the start. Except, and this one is pretty effing huge, the "fglrx" drivers. I simply cant express to you how frustrating this past week has been. I mean, i went from Vista, down to XP, to dual-booting Ubuntu, and the thing that is stopping me dead in my tracks are the graphic drivers.  And for that i dont blame Ubuntu. I blame ATI for 1. Release &*^#% drivers and 2. (Based on Reports) Not releasing some info/materials for people to build their own source drivers.  Whether i actually stick with Ubuntu, I am definately done with AMD.  I know this didnt really add much to the conversation , but i guess the main point is that its the Companies behind the software that are at fault simply because some have yet to take developing for Linux seriously. Thus the problems you see.

---

### Post by Kilz on 2007-06-30
> **Viewtifulj said:**
> I dont really have much to add other than that for me everything went fairly smoothly right from the start. Except, and this one is pretty effing huge, the "fglrx" drivers. I simply cant express to you how frustrating this past week has been. I mean, i went from Vista, down to XP, to dual-booting Ubuntu, and the thing that is stopping me dead in my tracks are the graphic drivers.  And for that i dont blame Ubuntu. I blame ATI for 1. Release &*^#% drivers and 2. (Based on Reports) Not releasing some info/materials for people to build their own source drivers.  Whether i actually stick with Ubuntu, I am definately done with AMD.  I know this didnt really add much to the conversation , but i guess the main point is that its the Companies behind the software that are at fault simply because some have yet to take developing for Linux seriously. Thus the problems you see.

[In case you havent found this site yet.]("http://wiki.cchtml.com/index.php/Ubuntu") I recommend it , from one ATI user to another.

---

### Post by dogson on 2007-06-30
If im installing linux on a friends computer and i know that he/she wont be doing any video/audio/3d rendering/high load server stuff i just install the i386 version. hell even xp64 and vista64 have problems that you need to workaround.

---

### Post by GumbyX on 2007-06-30
> **Kilz said:**
> It takes some people time to adjust and move over to open source. Some people never give up Windows completely. I used a duel boot for about 3 months. You may find yourself using one operating system less and less. 
The freedom to help is a freedom everyone should enjoy.  :D

I am ready to do the total switch (been using Ubuntu for a year on my laptop), but I have some programs that will only run in windows (stupid Rhapsody.....), and my college has a Windows-based network, which I cannot get to "play nice" with Linux (printing and the like).

Also, as of last night, the stupid ATI driver problems with the 32 and 64bit systems is driving me nuts (if you think you can help, PLEASE do.) But, every time I have a stupid problem with Windows (which is usually daily), I want to do the switch more and more.

---

### Post by Kilz on 2007-06-30
> **dogson said:**
> If im installing linux on a friends computer and i know that he/she wont be doing any video/audio/3d rendering/high load server stuff i just install the i386 version. hell even xp64 and vista64 have problems that you need to workaround.

But as evident by the entire rest of the forums, the 32bit version is far from perfect. What you are doing is lowering the number of 64bit users. Thereby lessening the perceived need for 64bit improvements by the developers.
Exactly what applications do you think will give them problems?

---

### Post by Buendia on 2007-06-30
Actually, reply was not specific to 64-bit, I have extended this discussion to [here]("http://ubuntuforums.org/showthread.php?p=2939980#post2939980").

---

### Post by nss0000 on 2007-06-30
BigB:

I have never heard it stated so well:

" See, that is the problem. An ideal OS must be universal, what is the point of something working for some and not working for others? The age of download-the-course compile-to-binary is gone, people want things to work out-of-the-box.

The aim is that the OS serves us, but this forum and all forums like this are full of creatures serving the OS."
__________________

OTOH my DAPPERx64 zipps-along with minimal effort on my AMD5400+ kit. DAPPERx64 certainly does what I've "hired" it to do. Yep, I focus on scientific apps, but then what's a computer for? U-Tube?? OhmeOHmy ...

nss
******

---

### Post by ashwin_cse on 2007-06-30
There are lot more 32-bit apps than there are 64-bit apps. Hence when till thinks 64-bit as the platform of choice, sticking to 32-bit might be better choice. For instance i am using the same processor as you do & i am pretty happy using 32-bit OS & hence the apps with it. I have never tried UnrealTornament on it, though.

HTH

---

### Post by Viewtifulj on 2007-06-30
> **Kilz said:**
> [In case you havent found this site yet.]("http://wiki.cchtml.com/index.php/Ubuntu") I recommend it , from one ATI user to another.

Thats one of the many i have tried. A few reinstalls as well, and envy. For right now I am partially satisfied simply using the vesa drivers and 1028x780 (?).  I need to learn my way around the OS anyway.

---

### Post by Kilz on 2007-06-30
> **ashwin_cse said:**
> There are lot more 32-bit apps than there are 64-bit apps. Hence when till thinks 64-bit as the platform of choice, sticking to 32-bit might be better choice. For instance i am using the same processor as you do & i am pretty happy using 32-bit OS & hence the apps with it. I have never tried UnrealTornament on it, though.

HTH

FUD, pure FUD

The[ i386 version]("https://launchpad.net/ubuntu/feisty/i386") :
This archive currently contains 21683 software packages.

[The AMD64 version:]("https://launchpad.net/ubuntu/feisty/amd64")
This archive currently contains 21386 software packages.

Taking into the packages that may be combined, obsolete, etc. The difference is negliable. Its less than 1%. Exactly what are you suggesting is missing? Please dont give a general "theres more" give examples of what is in the 32bit version that isnt in the 64bit .

---

### Post by tetrafuran on 2007-06-30
Kliz

Point 1
If there are 100 people using 32 bit OS and 50 people using 64 OS and both are having approximately same number of problems, you could see this in the forum. In this example there would be twice as much 32 bit posts as there would be those of the 64 bit system.

Point 7
Even during the era of windows I learned to avoid alpha and beta versions. Some of my friends did so too, and those who didn't got plagued by errors, random, crashing etc. That's mainly why in chose ubuntu 6.10. Of course  you cannot expect everyone to learn. Besides there are lots of people who didn't start computing in the age of ten.

I agree about other points you mentioned. Good post.

---

### Post by stmiller on 2007-06-30
> **ashwin_cse said:**
> There are lot more 32-bit apps than there are 64-bit apps. Hence when till thinks 64-bit as the platform of choice, sticking to 32-bit might be better choice. For instance i am using the same processor as you do & i am pretty happy using 32-bit OS & hence the apps with it. I have never tried UnrealTornament on it, though.

HTH

UT2004 has a 64bit Linux executable. It runs blazingly fast. And 64bit Ubuntu can execute any 32bit code. So the 32bit skype, flash, everything works in a 64bit install. But then when you need the nice 64bit for encoding, etc. that power is there.

You paid money for a nice 64bit processor. Why not use it?

The same debate was happening several years ago when windows 95 came out. The move from 16bit (windows 3.1) to 32bit computers was a hot topic, but seems like a trivial debate now.

---

### Post by John.Michael.Kane on 2007-06-30
Theres also this sticky [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607) which list almost all the debates on  32bit vs 64bit that took place on this forum.

---

### Post by Kilz on 2007-06-30
> **tetrafuran said:**
> Kliz

Point 1
If there are 100 people using 32 bit OS and 50 people using 64 OS and both are having approximately same number of problems, you could see this in the forum. In this example there would be twice as much 32 bit posts as there would be those of the 64 bit system.

Point 7
Even during the era of windows I learned to avoid alpha and beta versions. Some of my friends did so too, and those who didn't got plagued by errors, random, crashing etc. That's mainly why in chose ubuntu 6.10. Of course  you cannot expect everyone to learn. Besides there are lots of people who didn't start computing in the age of ten.

I agree about other points you mentioned. Good post.

1. But , 32bit is the "cure all" it cant mess up. Thats why people go back. Though most that do experience the same (or other)problems. The whole point it there is no perfect version of linux, or any operating system. People who think so are only fooling themselves. Rationalizing the reason for not installing the operating system that fits their hardware. The reason I point out all the posts in the 32bit section is to prove it isnt perfect. Not that one has more posts, but that it has any. Those rationalizing seem to forget all the problems those using the 32bit version experience. They are looking for the quick fix that doesnt exist.

7. I see it all the time, people on a never ending series of problems. They no sooner get one install working, then they install the next. I just wonder when they will learn.  :D

---

### Post by daller on 2007-07-16
I initially started this thread, to get to know whether or not to got with the 64-bit version...

I went 64-bit, and everything seems to work nicely, but...

Firefox and Sun's java doesn't seems to work together (it works in Konqueror!)

Any idea on how to fix this?

---

### Post by Kilz on 2007-07-16
> **daller said:**
> I initially started this thread, to get to know whether or not to got with the 64-bit version...

I went 64-bit, and everything seems to work nicely, but...

Firefox and Sun's java doesn't seems to work together (it works in Konqueror!)

Any idea on how to fix this?

Install the 32bit version and java. Link to install script in my signature. Someone may suggest using the jgc-compat plugin, it runs without a security manager, so that has risks you may not want to deal with.

---

### Post by tetrafuran on 2007-07-27
Some time ago I found an old computer magazine which was discussing the bit issue in detail. When that magazine came out I concentrated mainly on gaming so I didn't know about the great debate that went on. In any case it seems that history is repeating its self.

P.S. 64 bit ubuntu + 32 bit switfweasel seems to do the trick while we are waiting for 64 bit flash and other stuff like that. As always, there's a way around problems.

---

### Post by asbesto on 2007-09-09
> **SD-Plissken said:**
> There's numerous guides in this section that allow for the install of codecs flash wine java. So your theory that 64bit is terrible for browsing and multimedia is false.


reading howto's, fixing and patching by hand for every problem isn't a "solution", is TERRIBLE. Because thing must work simply installing it - isn't this the Ubuntu philosophy ? 

:confused:

---

### Post by Kilz on 2007-09-09
> **asbesto said:**
> reading howto's, fixing and patching by hand for every problem isn't a "solution", is TERRIBLE. Because thing must work simply installing it - isn't this the Ubuntu philosophy ? 

:confused:

No, its nice when it just works, but if you look at the number of [howto posts]("http://ubuntuforums.org/forumdisplay.php?f=100") most of which are for the i386 version. It proves that there is no version of ubuntu that "just works" for everyone. Making it easy for the beginner is more the Ubuntu philosophy imho. So a cut and paste howto showing exactly what to do is a good thing.
Secondly, one of the advantages of Linux in general is customization. The ability to change the system to whatever you need or want. You dont have to have it stuck as it was installed (a downfall of M$ Windoze).

---

### Post by delquattro on 2007-10-24
[QUOTE=tetrafuran;2938761]I can imagine lots of people would uninstall linux because of this and go back to windows. Good thing I started struggling with ubuntu during my summer vacation. I still think ubuntu.com should mention that i386 version is recommended for beginners and AMD64 version is for computer enthusiasts who also happen to be running AMD64 processors. It should be clearly mentioned that i386 is possible to run in 64 processors too and doing so will be much better for newbies.

Thank you for finally answering THE question!  You are a genius.

---

