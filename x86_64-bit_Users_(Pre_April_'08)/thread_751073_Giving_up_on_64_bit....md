---
title: "Giving up on 64 bit..."
date: 2008-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by JemW on 2008-04-10
I'm going back to 32 bit Ubuntu, even though I have an Athlon 64 4400+  X2. It's just too damn hard to get things working. Can someone point me at the right download please - I'm really confused...

---

### Post by misfitpierce on 2008-04-10
Download any disc that says i386. [http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

 What was so hard to set up on 64 bit... curiously..

---

### Post by JemW on 2008-04-10
> **misfitpierce said:**
> Download any disc that says i386. [http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

 What was so hard to set up on 64 bit... curiously..

The browser. No matter what instructions I follow I cannot get any flavour of Java or Flash running in Firefox, and I want both. So, it's a choice of following even harder instructions to get 32 bit FF installed on 64 bit Ubuntu, or just installing 32 bit Ubuntu and making my life easier. Unless I've missed a trick here, I'm voting for the latter until the 64 bit software world gets itself sorted...

---

### Post by OoooMatron on 2008-04-10
> **JemW said:**
> I'm going back to 32 bit Ubuntu, even though I have an Athlon 64 4400+  X2. It's just too damn hard to get things working. Can someone point me at the right download please - I'm really confused...

I gave up on 64bit months ago for that reason and others.

The performance difference that I noticed was totally zero.

---

### Post by felker2 on 2008-04-10
I've been using Ubuntu AMD64 on my 4GB system for quite some time now: first 7.10, now 8.04 Hardy. 
Both Flash and Java work without any problem on 8.04 (can't remember anymore about Java plugin on 7.10). Both installed via Add/Remove. I've installed the "Ubuntu restricted extras" to get the Java plugin.

But: if you like 32-bit more, that's OK.

---

### Post by employeeno5 on 2008-04-10
I've got a new core duo 2 system that has 4 gigs of RAM. I've got the Hardy beta for 32 bit running on it now, but I think I've broken it so badly that I'm going to have to reinstall. 
If I do I was thinking about trying out the 64 bit system.

Now, I know very little about this, and I'm confused about why it's difficult to get things working.

As far as I understood, you can run any 32 bit piece of software on a 64 bit system. So if something doesn't have 64 bit support, you can just install the 32 bit version.

Does that turn out to not be so simple in practice, or do I misunderstand/simplify the whole issue? I've read all the threads warning of difficulties yet I still don't understand why the difficulties are present. 

I'm told I shouldn't expect to see much of any noticeable performance increase (I'm not building large data bases or anything) but it would be nice to know that I'm getting access to all 4GB of my RAM and it just seems that 64 bit processing has been so common for so long in hardware now that it's about time users got around to using and supporting it more. 

So I guess while we're on the subject of it just being not worth the hassle sometimes, what exactly is difficult about getting 32 bit firefox, for example, to run? 
What more is there to it than a good old apt-get?

Regardless, I hope your 32bit experience goes well. If I can't get [this broken package]("http://ubuntuforums.org/showthread.php?t=750633") removed in the next few days, I'm going to use it as an excuse to try out 64bits for myself.

---

### Post by felker2 on 2008-04-10
> As far as I understood, you can run any 32 bit piece of software on a 64 bit system. 
Yes, you can.
Well: *any*? I believe you can't run 32-bit kernel modules and other stuff close to the hardware.

> So if something doesn't have 64 bit support, you can just install the 32 bit version.
Ouch: "just" install? I'm no expert at all, but all kinds of library dependencies are involved there. I hate library dependencies. I therefore only install via Add/Remove Programs and let Ubuntu take care of the all those dependencies. That works perfect.

> Does that turn out to not be so simple in practice, 
Correct. Therefore: Keep it simple, and only install via Add/Remove Programs (or "sudo apt-get install"). In other words: via the Ubuntu 64bit repositories. That way, the Ubuntu will take care of it.

> or do I misunderstand/simplify the whole issue?
Make it even more simple and limit yourself to the Add/Remove Programs.

---

### Post by Linder on 2008-04-10
> **JemW said:**
> The browser. No matter what instructions I follow I cannot get any flavour of Java or Flash running in Firefox, and I want both. So, it's a choice of following even harder instructions to get 32 bit FF installed on 64 bit Ubuntu, or just installing 32 bit Ubuntu and making my life easier. Unless I've missed a trick here, I'm voting for the latter until the 64 bit software worls gets itself sorted...

Flash is dead easy. Open Synaptic, search for "Flash" and install the flash-nonfree package. Restart firefox: DONE!

And yes, I run 64 Bit Hardy Heron.

---

### Post by Jouke74 on 2008-04-10
The choice of 32 bit or 64 bit is not so much based on whether people think it is the right "bit" for their computer. It's more on how they are able to deal with the problems that come along the way..... unfortunately.

If you are using your computer mostly for internet surfing with flash and java then a 32 bit OS on a 64 bit computer will suffice fine as well. There is no obligatory reason to switch to 64 bit. I am afraid the OS switch to 64 bit for companies, programs, drivers and OSes is still going to be a few years away. As soon as most people will have +4 GB of memory it will probably come quickly.

---

### Post by employeeno5 on 2008-04-10
Felker2, 
Thanks for the taking the time for the in depth input. I think I'll be giving it a go. I rarely tread far from Ubuntu's official packages.

---

### Post by Thelasko on 2008-04-10
What happened?  I had Flash and Java working in Feisty.  I upgraded to Gusty because they were supposed to be better supported.  Flash was, when I installed it, but Java never worked under Gusty for me.  Now I'm hearing reports that Flash support has issues.  I had better luck hacking 64-bit Feisty than with Gusty's supposed fixes.  It also makes me wonder if Hardy will be worth the effort.  I must say that 64-bit Gusty has been a disappointment over Feisty.

---

### Post by JemW on 2008-04-10
> **Linder said:**
> Flash is dead easy. Open Synaptic, search for "Flash" and install the flash-nonfree package. Restart firefox: DONE!

And yes, I run 64 Bit Hardy Heron.

I tried that - it never worked. Bear with me, I'm new to Linux and Ubuntu - I don't 'get' all the 'Herons' and other Ubuntu flavours. I'm just installing the main Ubuntu packages from the Home page. The 64 bit version didn't work, the 32 bit version does. I'd rather have 64 bit with plug-ins working, because I do stuff with digital media processing where 64 bit would be useful, but I cannot understand what Ubuntu 'flavour' to install to achieve all this with minimum pain.

---

### Post by Half-Left on 2008-04-10
Unfortunately Adobe dont support 64bit flash on any platform so if you want pure 64bit you'll have to give some things up. If Windows and others where not so far behind in the 64bit era then we may well have alot proprietary companies supporting 64bit, even Apple dont support full x86_64.

---

### Post by JemW on 2008-04-10
> **Half-Left said:**
> Unfortunately Adobe dont support 64bit flash on any platform so if you want pure 64bit you'll have to give some things up. If Windows and others where not so far behind in the 64bit era then we may well have alot proprietary companies supporting 64bit, even Apple dont support full x86_64.

As I'm now running Ubuntu 32 bit, I shouldn't even be in this thread I guess, but as you're all knowledgeable on this subject I'd like to ask here. On visiting the Verify Java page I was prompted to choose from the options which included:

1) GCH something or other plug-in
2) Java SE 6
3) Java SE 5
4) Iced Tea something or other plug-in

I chose 2) and the test shows that I'm running Java 6 Update 3, although the 'latest' is Update 5. How do I update that? Or do I just leave alone until Ubuntu tells me there's an update available?

---

### Post by ericson578 on 2008-04-10
JemW, that doesn't sound correct the way you were installing java to me.  Take that with a grain of salt since I'm fairly new to ubuntu/linux (about 4 months now), but all I had to do to install java on my 32bit copy of 7.10 was go to the package manager, search for java6 and select the jre.  Everything worked fine.

I only install packages that can be done through the package manager, or on rare occassion if it comes in a .deb file, but only because I think it gets handled by the same program (example, skype)?

---

### Post by ericson578 on 2008-04-10
oh I almost forgot what I originally wanted to post!

I've been thinking about upgrading my hardware to a 64bit cpu, and I think I'm going to try out 64 bit 8.04 when it comes out.  It sounds like most of the really technical issues have been worked out, plus when I figure out a problem it means that my level of understanding in linux has gone up dramatically :)

Now I just have to decide if I should shoot for 8gb or 4gb of ram.  DDR2 PC-800 is so cheap! :)

---

### Post by Thelasko on 2008-04-10
> I don't 'get' all the 'Herons' and other Ubuntu flavours.
They're not flavors they're nicknames for version numbers.  You may be familiar with software companies that number their software revisions (version 1.0, 2.0, 3.0, 3.11, etc). Ubuntu does too but they also give it a nickname.  6.06 is Dapper Drake, 6.10 is Edgy Eft, 7.04 is Feisty Fawn, 7.10 is Gusty Gibbon, and 8.04 will be Hardy Heron.  Each version is supposed to be an improvement over the previous one.  They are all intended to serve the same purpose

There are different flavors of Ubuntu that are designed for different purposes, For example: Xubuntu (lightweight), Kubuntu (KDE desktop), Edubuntu (for educational work), Ubuntu Studio (for multimedia work).

---

### Post by JemW on 2008-04-10
> **Thelasko said:**
> They're not flavors they're nicknames for version numbers.  You may be familiar with software companies that number their software revisions (version 1.0, 2.0, 3.0, 3.11, etc). Ubuntu does too but they also give it a nickname.  6.06 is Dapper Drake, 6.10 is Edgy Eft, 7.04 is Feisty Fawn, 7.10 is Gusty Gibbon, and 8.04 will be Hardy Heron.  Each version is supposed to be an improvement over the previous one.  They are all intended to serve the same purpose

There are different flavors of Ubuntu that are designed for different purposes, For example: Xubuntu (lightweight), Kubuntu (KDE desktop), Edubuntu (for educational work), Ubuntu Studio (for multimedia work).

Thanks!

---

### Post by Thelasko on 2008-04-10
@ericson578 > but all I had to do to install java on my 32bit copy of 7.10 was go to the package manager, search for java6 and select the jre. Everything worked fine.
Unfortunately, that doesn't work in 64-bit:(

---

### Post by JemW on 2008-04-10
> **ericson578 said:**
> JemW, that doesn't sound correct the way you were installing java to me.  Take that with a grain of salt since I'm fairly new to ubuntu/linux (about 4 months now), but all I had to do to install java on my 32bit copy of 7.10 was go to the package manager, search for java6 and select the jre.  Everything worked fine.

I only install packages that can be done through the package manager, or on rare occassion if it comes in a .deb file, but only because I think it gets handled by the same program (example, skype)?

I can't find anything in Package Manager or anywhere else relating to the latest JRE.

---

### Post by Kilz on 2008-04-10
> **Half-Left said:**
> Unfortunately Adobe dont support 64bit flash on any platform so if you want pure 64bit you'll have to give some things up. If Windows and others where not so far behind in the 64bit era then we may well have alot proprietary companies supporting 64bit, even Apple dont support full x86_64.

Adobe may not support it, but that does not mean that flash cant be ran on a 64bit browser. Anyone who looks at the sticky posts can get flash running in under a minute.

---

### Post by Kilz on 2008-04-10
> **JemW said:**
> As I'm now running Ubuntu 32 bit, I shouldn't even be in this thread I guess, but as you're all knowledgeable on this subject I'd like to ask here. On visiting the Verify Java page I was prompted to choose from the options which included:

1) GCH something or other plug-in
2) Java SE 6
3) Java SE 5
4) Iced Tea something or other plug-in

I chose 2) and the test shows that I'm running Java 6 Update 3, although the 'latest' is Update 5. How do I update that? Or do I just leave alone until Ubuntu tells me there's an update available?

Java 6 does not have a 64bit plugin. You should have chosen 4, icedtea has a 64bit java plugin. Java 6 package is there for those that have installed a 32bit browser.

---

### Post by Half-Left on 2008-04-10
Search for ```
sun java
```

---

### Post by ericson578 on 2008-04-10
You might have to enable other repositories (I can't remember the names, but basically because java is not free and opensource it's not in the main repos that come enabled by default with ubuntu).

Once you enable all repositories (package manager->settings->repositories) then you'll be able to see it.  The package I installed is called: sun-java6-jre
Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
Version 6-03-0ubuntu2

-Eric

---

### Post by ericson578 on 2008-04-10
> **Thelasko said:**
> @ericson578 
Unfortunately, that doesn't work in 64-bit:(

Oh my, I'll have to do a little more research into seeing how difficult it will be to get flash and java working in 64 bit then.  At best it'll be a quick learning experience, at worst it'll be agony that causes me to give the 64 bit version another 6  month wait :P

I'm just glad to not be stuck with vista.  Thank god I'm not a pc gamer, those poor souls

-Eric

---

### Post by Half-Left on 2008-04-10
> **Kilz said:**
> Adobe may not support it, but that does not mean that flash cant be ran on a 64bit browser. Anyone who looks at the sticky posts can get flash running in under a minute.

I know this but I dont see why people should support it if it's not supporting their platform, sometimes you need to make sacrifices just as we sometimes have to do in Linux.

Sun were the x86_64 pioneers and yet dont have proper 64bit support in their plugin.

---

### Post by Kilz on 2008-04-10
> **Half-Left said:**
> I know this but I dont see why people should support it if it's not supporting their platform, sometimes you need to make sacrifices just as we sometimes have to do in Linux.

Sun were the x86_64 pioneers and yet dont have proper 64bit support in their plugin.

You are giving misleading information. If you suggest that it isn't  supported and don't give links to the stickies you may give the impression to new users that its not available.

---

### Post by Kilz on 2008-04-10
> **ericson578 said:**
> Oh my, I'll have to do a little more research into seeing how difficult it will be to get flash and java working in 64 bit then.  At best it'll be a quick learning experience, at worst it'll be agony that causes me to give the 64 bit version another 6  month wait :P

I'm just glad to not be stuck with vista.  Thank god I'm not a pc gamer, those poor souls

-Eric

No need to wait on 64bit Ubuntu, just read the stickies and you will do ok.

---

### Post by Half-Left on 2008-04-10
I didn't say you can't run flash in a 64bit OS, I said they dont do a 64bit flash plugin which is factually correct. Clearly the sticky is there on this forum which I knew.

---

### Post by Thelasko on 2008-04-10
@ericson578
Flash was easy for me under Gusty, I just went to a Flash site and followed the prompts under Firefox.  I installed Gusty the first week it came out.  Apparently, from what I read on these boards, that method stopped working.  I guess people have been able to get it to work using Kilz's old script for Feisty.

For Java there is an open source version called IcedTea that's supposed to work in 64-bit.  I haven't had any success with it though.

---

### Post by Kilz on 2008-04-10
> **Half-Left said:**
> I didn't say you can't run flash in a 64bit OS, I said they dont do a 64bit flash plugin which is factually correct. Clearly the sticky is there on this forum which I knew.

While factually correct it imho is very misleading to new users who are not able to tell the difference. You may want to give the links so that you do not mislead those that are not aware that you are splitting hairs.

---

### Post by Half-Left on 2008-04-10
> **Kilz said:**
> While factually correct it imho is very misleading to new users who are not able to tell the difference. You may want to give the links so that you do not mislead those that are not aware that you are splitting hairs.

Well, your sticky thread is use at your own risk and dont work for everyone, it's also rather complicated otherwise the thread starter would have done it already, now we have two threads about the same thing.

---

### Post by Kilz on 2008-04-10
> **Half-Left said:**
> Well, your sticky thread is use at your own risk and dont work for everyone, it's also rather complicated otherwise the thread starter would have done it already, now we have two threads about the same thing.

You are asuming things, one is that the flash method didnt work for everyone. It does work for everyone, as long as they are not using a corupted mirror. That is the realm of the Ubuntu package maintainers, and not a script.
Second, IMHO few people tend to read the stickies first. They must think its easier to just ask people. Sadly they get as much misinformation from well meaning but missinformed users who havent got a clue. It would be much easier if they just read the stickies. That there are 2 threads leads me to think that the orignal poster is searching for a magic fix, and doesnt want to wait for the one topic to wind up. Sadly they are now doubeling the chance of missinformation.

---

### Post by Half-Left on 2008-04-10
I had to give him the link to the thread in his over thread so. Still that way of installing a 32bit plugin is putting your 64bit systems security at risk just like any propriatary software but I guess people dont know sometimes(*cough* Adobe flash zero day flaw *cough*)" :-\"

---

### Post by jmore9 on 2008-04-10
I use the 64 bit version of 7.10 and am in the process right now of a complete system / version upgrade to 8.04.  Flash on the 7.10 64 bit was installed using the sticky on the forum.  Oh yea i am using Kubuntu not ubuntu 64bit.  flassh was waorking in about 2 minutes for me [ i am a little slow sometimes !!! ] .  I shall see where my adventure of upgradeing to 8.04 takes me to the reinstall path or to the actual use path i shall see in a couple of hours

---

### Post by Jouke74 on 2008-04-10
Funny enough today an update on the Adobe Flash plugin came for Gutsy :) It is working here btw. Only the audio starts to unsync with the movie. 
It took me a while to solve that (read install pulse audio en change some settings, and make sure there is some CPU power left, still testing this btw). 

Sun jave JRE does not work with the plugin for Firefox. 
The program itself works fine and you can run JAR files.

---

### Post by JemW on 2008-04-10
> **Kilz said:**
> Java 6 does not have a 64bit plugin. You should have chosen 4, icedtea has a 64bit java plugin. Java 6 package is there for those that have installed a 32bit browser.

Now, I seriously don't understand you. You were suggesting earlier that I started two threads because I want a magic answer. I just want a consistent answer! Your advice above is not correct IMO. I am now running 32 bit, which is why I chose Option 2 on my list (I did state that in that post). When I *was* running 64 bit, I tried the Iced Tea plug-in and it did nothing. You say that Iced Tea has a 64 bit plug-in, but it seems to me that everyone here is saying there is no such thing.

Are you really surprised that I'm confused?

---

### Post by Kilz on 2008-04-10
> **JemW said:**
> Now, I seriously don't understand you. You were suggesting earlier that I started two threads because I want a magic answer. I just want a consistent answer! Your advice above is not correct IMO.** I am now running 32 bit,** which is why I chose Option 2 on my list (I did state that in that post). When I *was* running 64 bit, I tried the Iced Tea plug-in and it did nothing. You say that Iced Tea has a 64 bit plug-in, but it seems to me that everyone here is saying there is no such thing.

Are you really surprised that I'm confused?

Then why are you posting in the 64bit section?

---

### Post by Guilden_NL on 2008-04-11
> **felker2 said:**
> I've been using Ubuntu AMD64 on my 4GB system for quite some time now: first 7.10, now 8.04 Hardy. 
Both Flash and Java work without any problem on 8.04 (can't remember anymore about Java plugin on 7.10). Both installed via Add/Remove. I've installed the "Ubuntu restricted extras" to get the Java plugin..
That's been my experience as well.  I have Hardy running with Flash and Java enabled.  I think I'll have to spend a bit of time to get Wine running, but that's to be expected.  I am going to wait for the official release version just to ensure that I don't have to repeat the process.

I added Flash via Synaptic and Java using Add....... same as you.  No special workarounds. 

The reason I run 64bit on all of my systems is that's the only way vendors will support it - hits on web sites showing 64 bit is out there and being used! =D>

---

### Post by Guilden_NL on 2008-04-11
> **Kilz said:**
> Then why are you posting in the 64bit section?

I wondered the same as you.....it's quite the mystery. :popcorn:

---

### Post by Orion13622 on 2008-04-11
Personally I noticed that when I installed the 64 bit version on my Compaq Presario R3000Z CTO, that the drivers for my Wireless (broadcom), modem, and NVidia graphics card were not accessable by the device drivers item in the administrator panel.  In fact, it would end up having a critical error.  

Now this isn't to say that I'm not going to try the beta of the 32 bit version to see if it's the same, but when I was running 7.10 x86, the restricted drivers came up no problem, and installed without a hitch.  We'll see, and yes I do understand we still have a few days left and this is still in a beta state.  :)  One thing that I am hoping for (and this would totally drag me off of Windows completely) is that with the new kernel update, my onboard 5 in 1 SD card reader works as well.  In Vista, it fails to work, although Vista says it's there, it simply doesn't read the cards when they are inserted.  Unless you get SP1, you're out of luck.  However, even after installing SP1 in Vista, the card reader halfway works.  Card is seen, you are asked to see contents, and then......Please insert card in drive f:   WTF MS????  Thought you fixed this!

Oh well that is for another time.  If I could get my card reader to work, I'd be excstatic (sp?) as the rest of Ubuntu seems to function just fine.  Oh, and one other thing I noticed being a newbie to Linux.  Battery time on my notebook is roughly about 3 hours, with all the bells and whistles in Ubuntu turned on (7.10) as compared to 1.5 hours if you're lucky, in either Vista or XP.  Can MS explain that one?  Or anyone here for that matter???

Orion:lolflag:

---

### Post by crgutierrez on 2008-04-11
Don't give up!!!!!!!!!! Try Quickstart first for many practical applications. To force install 32bit libs make sure you have the latest getlibs. Thenmake sure you have the open source java version called IcedTea7. Believe me: it works!! I will never go back!

---

