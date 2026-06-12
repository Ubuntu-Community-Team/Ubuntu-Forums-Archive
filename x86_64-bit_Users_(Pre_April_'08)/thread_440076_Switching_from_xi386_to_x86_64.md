---
title: "Switching from xi386 to x86_64"
date: 2007-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by LuisGMarine on 2007-05-11
Hello,

Since reading so much about how well 64-bit feisty is now and days, I'm going to give it a try.  The problem is that I don't want to loose 40 GB that I have worth of music and videos, and a few games that are saved on my hdd.

So what I was thinking was creating another 40GB partition on my hdd, and moving all my music and movies to this partition, then installing Ubuntu 64-bit over my regular 32-bit ubuntu, without having to touch the partition set aside for music and videos.  So my question is, can I do this?  If not, then how can I upgrade to 64-bit without loosing all that music that I've collected for the past few months?  Also, once I have my 64-bit system, can I merge those two partitions back together?

The only things that worry me about switching right now are my gaming on the 64-bit machine, although I've read some pretty convincing posts on how to get Cedega running in a 32-bit chroot system, but I'm wondering if it is successful at all.  I mostly use my computer for music, internet browsing, the occasional gaming, somewhat hardcore gamer, but not all that much.

Another thing is, how do apps like Azureus and Frostwire run?  I know they require java, but is it a hard deal to set up java to work with Azureus and Frostwire on a 64-bit system?

I can't say that I'm not exited to give this a go, I'm really hoping to unleash the power of my AMD-64 bit processor.  Also if you can point to any sort of guide that will answer all my questions, something close to the Ubuntu Guide, I will greatly appreciate it.  

Thanks!

---

### Post by Toet on 2007-05-11
By default I have to separate partitions for music, pictures and my home. This way I can reinstall what I want, and just at install of the new ubuntu install can point to these partitions. So I wouldn't merge them into one partition if you have 64bit running.

---

### Post by LuisGMarine on 2007-05-11
I was looking at gparted, but can I resize my partition when I'm using it?  Like when I'm using ubuntu can I use gparted while running my system , or would i have to burn the Live CD version, and go from there?


Also I want to ask you, how much did you set aside for each partition?  I have a 160GB hdd, so let me know what would be a good break down of everything.  I don't want to give too little to the root partition or home and sometime down the line I run out of space.

---

### Post by Cappy on 2007-05-11
Cedega installs with 0 hassle. It's just double click on the .deb they give you and you're good to go. Playing Oblivion with it because I have too many problems with WINE. I'm obsessed with Oblivion atm. Also running UT2004 even though there is only a handful of good players left.

---

### Post by RTrev on 2007-05-11
> **LuisGMarine said:**
> Hello,

Since reading so much about how well 64-bit feisty is now and days, I'm going to give it a try.  The problem is that I don't want to loose 40 GB that I have worth of music and videos, and a few games that are saved on my hdd.

So what I was thinking was creating another 40GB partition on my hdd, and moving all my music and movies to this partition, then installing Ubuntu 64-bit over my regular 32-bit ubuntu, without having to touch the partition set aside for music and videos.  So my question is, can I do this?  If not, then how can I upgrade to 64-bit without loosing all that music that I've collected for the past few months?  Also, once I have my 64-bit system, can I merge those two partitions back together?

The only things that worry me about switching right now are my gaming on the 64-bit machine, although I've read some pretty convincing posts on how to get Cedega running in a 32-bit chroot system, but I'm wondering if it is successful at all.  I mostly use my computer for music, internet browsing, the occasional gaming, somewhat hardcore gamer, but not all that much.

Another thing is, how do apps like Azureus and Frostwire run?  I know they require java, but is it a hard deal to set up java to work with Azureus and Frostwire on a 64-bit system?

I can't say that I'm not exited to give this a go, I'm really hoping to unleash the power of my AMD-64 bit processor.  Also if you can point to any sort of guide that will answer all my questions, something close to the Ubuntu Guide, I will greatly appreciate it.  

Thanks!

May I ask what it is you expect to find that's better running the 64-bit version?  I've been switching back and forth, and I can't honestly say I even *imagine* a difference in performance or in anything else.. except that 64-bit is a pain because things aren't up to 64-bit in the driver and application world quite yet.  It sounds like you are going to considerable lengths to do this, so either I've missed something important, or you're expecting something you may not find.

To my knowledge, the only advantage of a 64-bit OS right now is that it can address more than 4G of RAM.

Regards,
Bob

---

### Post by LuisGMarine on 2007-05-11
Honestly I was expecting a great deal of improvement from regular old 32-bit Ubuntu.  I can't say that I don't like the way things are running here, but I guess I just want to see what 64-bit Ubuntu has to offer.

Like I said, I'm only looking to listen to some Music, play some games, and surf the internet.  It seems like you aren't that convinced about 64-bit, I just keep hearing things from other people that its great.

---

### Post by LuisGMarine on 2007-05-11
I'm curious, is there a Ubuntu Guide for amd64?

I really want to try ubuntu 64-bit, and now you are giving me second thoughts.  I've found all the proper things to install bitorrents and flash and firefox, but nothing as far as video cards or cedega.

---

### Post by RTrev on 2007-05-11
> **LuisGMarine said:**
> Honestly I was expecting a great deal of improvement from regular old 32-bit Ubuntu.  I can't say that I don't like the way things are running here, but I guess I just want to see what 64-bit Ubuntu has to offer.

Like I said, I'm only looking to listen to some Music, play some games, and surf the internet.  It seems like you aren't that convinced about 64-bit, I just keep hearing things from other people that its great.

What do these othert people say they like about it?  It may be that it's really good at doing things that I don't happen to do.  To me, honestly, if you sat me down at a machine I wouldn't be able to tell which it was running without actually looking.

It isn't that I'm not convinced about it.  I think it's wonderful to have that rock-solid 64-bit platform ready for when the world moves en mass to 64-bit.  That should be soon, since you can barely buy a new machine that isn't 64-bit now.

The things that were a pain were having to hack an install of wine, because there is none for 64-bit, having to do without most plugins because of the same thing, and getting nothing at all back in exchange for these issues.  I love that it exists, and I'll use it as soon as it's practical for me to.

But, again, I'm curious what I'm missing?  Why do people love it so much more than the 32-bit?

---

### Post by Kilz on 2007-05-11
> **RTrev said:**
> What do these othert people say they like about it?  It may be that it's really good at doing things that I don't happen to do.  To me, honestly, if you sat me down at a machine I wouldn't be able to tell which it was running without actually looking.

It isn't that I'm not convinced about it.  I think it's wonderful to have that rock-solid 64-bit platform ready for when the world moves en mass to 64-bit.  That should be soon, since you can barely buy a new machine that isn't 64-bit now.

The things that were a pain were having to hack an install of wine, because there is none for 64-bit, having to do without most plugins because of the same thing, and getting nothing at all back in exchange for these issues.  I love that it exists, and I'll use it as soon as it's practical for me to.

But, again, I'm curious what I'm missing?  Why do people love it so much more than the 32-bit?

Why do some people prefer the 64bit version?  I like it because there is a performance increase in applications I use. I like 3d modeling, I like encoding. I also like to have an operating system that matches the hardware I own. I also dont mind having to do a little bit of setup and hack around in my system. Its one of the pleasures of Linux. To be able to make it how I want it. To add things to the os, to change things, and if something doesnt work, to make it work.
Some people just want everything to work out of the box, and thats fine. But I think of them as people running away from Windows, not running to Linux. 
Sadly we get FUDsters in the 64bit section all the time. Most of them want Linux to be Windows.

---

### Post by RTrev on 2007-05-11
> **Kilz said:**
> Why do some people prefer the 64bit version?  I like it because there is a performance increase in applications I use. I like 3d modeling, I like encoding. I also like to have an operating system that matches the hardware I own. I also dont mind having to do a little bit of setup and hack around in my system. Its one of the pleasures of Linux. To be able to make it how I want it. To add things to the os, to change things, and if something doesnt work, to make it work.
Some people just want everything to work out of the box, and thats fine. But I think of them as people running away from Windows, not running to Linux. 
Sadly we get FUDsters in the 64bit section all the time. Most of them want Linux to be Windows.

Well, if there are performance increases, then it's all worth it.  I didn't see any in the simple applications I use.  I'm also a newbie and unable to hack around as well as you seem to be able to.

Believe me when I say the last thing in the world I want is Windows.  I had 64-bit running with the low-latency kernel, but the bottom line was that I wasn't skilled enough to tweak things so that I could use the system normally.  A friend would send me a link to something they wanted me to see, and there was no way I could find to get the Firefox plugins working correctly.  I even tried Automatix and got the 32-bit Swiftfox, but that screwed things up so that my normal Firefox wouldn't launch, and Swiftfox couldn't handle the extensions I use.

Not meaning to put 64-bit down, just not skilled enough yet to use it.. and, as I said, I could see no plus side with the work I do.  Looking forward to trying it again soon.

---

### Post by Kilz on 2007-05-11
> **RTrev said:**
> Well, if there are performance increases, then it's all worth it.  I didn't see any in the simple applications I use.  I'm also a newbie and unable to hack around as well as you seem to be able to.

Believe me when I say the last thing in the world I want is Windows.  I had 64-bit running with the low-latency kernel, but the bottom line was that I wasn't skilled enough to tweak things so that I could use the system normally.  A friend would send me a link to something they wanted me to see, and there was no way I could find to get the Firefox plugins working correctly.  I even tried Automatix and got the 32-bit Swiftfox, but that screwed things up so that my normal Firefox wouldn't launch, and Swiftfox couldn't handle the extensions I use.

Not meaning to put 64-bit down, just not skilled enough yet to use it.. and, as I said, I could see no plus side with the work I do.  Looking forward to trying it again soon.

I have only been using Linux about 2 years. I am not a hacker, I ran Windows XP before. But I bought a 64bit computer, and it came with 32bit windows. After trying Linux, I found I loved it, and the freedom it gives you.
Give yourself some time, learning anything new takes time. Eventualy you will get good if you give it a chance. What extension wouldnt work?

---

### Post by LuisGMarine on 2007-05-12
Well I'm ready to make the move.  I've got all my cd's ready and I think I'm just going to do a clean install.  Stopped at the store and got a sweet deal on some DVD's, so I'm just going to copy my games and music on to them.

Before I install x86_64, can someone be so kind as to point me in the right direction of installing the drivers for nvidia?  I wonder if the xorg.config I have now will work on the 64-bit version?  I installed the nvidia drivers, and gaming was crappy.  Then for some reason I ran some other command the other day, it changed my xorg, and gaming improved like 100% on my Ubuntu Box.  I couldn't believe what the heck this command did.  Too bad I can't remember the command, but it improved my graphics A LOT.  

Now that I think about it, I don't want to loose these setting and loose this ubber gaming.

---

### Post by RTrev on 2007-05-12
> **Kilz said:**
> I have only been using Linux about 2 years. I am not a hacker, I ran Windows XP before. But I bought a 64bit computer, and it came with 32bit windows. After trying Linux, I found I loved it, and the freedom it gives you.
Give yourself some time, learning anything new takes time. Eventualy you will get good if you give it a chance. What extension wouldnt work?

Thanks for the encouragement.  When I got the Switfox, I was surprised that it had picked up the settings and extensions from my Firefox, but the one that didn't work was Google Browser Sync.  I love this extension.  Close some tabs on one machine, go somewhere else, continue what you were doing.

The trouble with Automatix, it seems to me, is that it doesn't talk to Apt.  I'll install Gftp from Automatix, and Apt says it's not installed.

As it is with Ubuntu and me at the moment, I'm learning, slowly, and just about able to do the things I want.. provided no extra hurdles are placed in my path.  :) 

Here are a couple of examples of things I'm wrestling with to give you a sense of my skill level.  It took me a week (!) to figure out how to write a script which would over-clock my Nvidia card when I wanted to watch DVD movies.  Setting the execute bit on the file, setting up a panel applet to overclock or normalclock the board when wanted.  

Another example.. I'm trying to accommodate a friend who is losing his vision and who communicates with everybody via an app called PureVoice by Qualcomm.  Went and got the Linux PVCONV which converts a wav file to a qcp (PureVoice) file, then struggled and struggled with sound recorder to produce a mono wav file with the correct sample rate, etc.  Couldn't do it.  Had to fall back to using arecord at the command line

```

arecord -f S16_LE filename.wav
pvconv filename.wav

```

Oh, and pvconv wouldn't run under the 64-bit, and I know of no way to get it to.

Thanks again for the encouragement.. it helps!

---

### Post by Kilz on 2007-05-12
> **LuisGMarine said:**
>  Then for some reason I ran some other command the other day, it changed my xorg, and gaming improved like 100% on my Ubuntu Box.  I couldn't believe what the heck this command did.  Too bad I can't remember the command, but it improved my graphics A LOT.  

The xorg.conf should work, its just settings.

> **RTrev said:**
> Thanks for the encouragement.  When I got the Switfox, I was surprised that it had picked up the settings and extensions from my Firefox, but the one that didn't work was Google Browser Sync.  I love this extension.  Close some tabs on one machine, go somewhere else, continue what you were doing.

The trouble with Automatix, it seems to me, is that it doesn't talk to Apt.  I'll install Gftp from Automatix, and Apt says it's not installed.

As it is with Ubuntu and me at the moment, I'm learning, slowly, and just about able to do the things I want.. provided no extra hurdles are placed in my path.  :) 

Here are a couple of examples of things I'm wrestling with to give you a sense of my skill level.  It took me a week (!) to figure out how to write a script which would over-clock my Nvidia card when I wanted to watch DVD movies.  Setting the execute bit on the file, setting up a panel applet to overclock or normalclock the board when wanted.  

Another example.. I'm trying to accommodate a friend who is losing his vision and who communicates with everybody via an app called PureVoice by Qualcomm.  Went and got the Linux PVCONV which converts a wav file to a qcp (PureVoice) file, then struggled and struggled with sound recorder to produce a mono wav file with the correct sample rate, etc.  Couldn't do it.  Had to fall back to using arecord at the command line

```

arecord -f S16_LE filename.wav
pvconv filename.wav

```

Oh, and pvconv wouldn't run under the 64-bit, and I know of no way to get it to.

Thanks again for the encouragement.. it helps!

2 things, Swiftfox is a 32bit browser. Its also a proprietary build, with a restrictive license. You can use Firefox32 if you want. I use google browser sysnc myself. If you really need an optimized build of Firefox you can also try [Swiftweasel]("http://sourceforge.net/projects/swiftweasel") Its a new project one of my friends told me about. You can just download the file , extract it, and run it from the folder. 
As for getting a 32bit application to run under 64bit. Its a little complicated for some applications. [Take a look here at how I do it.]("http://tghc.org/32biton64bit.php")

---

### Post by LuisGMarine on 2007-05-12
Kilz what about applications like Azureus?  Or frostwire?  How would I got about installing the nvidia drivers and such?

I'm curious to know if I can use the ubuntu guide for feisty, even thought I'm on a 64-bit system, or if there is an actual Ubuntu Guide for amd64.

I think I'm going to hold the install until tomorrow, I'm starting to contemplate if these things will work or not.  So far gaming is fixed, since I know that cedega supports 64-bit platforms.   Java and Azureus I'm not sure about, I'm still a bit lost on the whole deal with Java and Flash.

---

### Post by Kilz on 2007-05-12
> **LuisGMarine said:**
> Kilz what about applications like Azureus?  Or frostwire?  How would I got about installing the nvidia drivers and such?

I'm curious to know if I can use the ubuntu guide for feisty, even thought I'm on a 64-bit system, or if there is an actual Ubuntu Guide for amd64.

I think I'm going to hold the install until tomorrow, I'm starting to contemplate if these things will work or not.  So far gaming is fixed, since I know that cedega supports 64-bit platforms.   Java and Azureus I'm not sure about, I'm still a bit lost on the whole deal with Java and Flash.

Azureus is in the repos. The frostwire deb from the frostwire site can be --force-architectures installed. Look at this thread for information on how to do it. While the thread title says Dapper, it still usefull to people running Edgy and Feisty.
Flash and java can be used in a browser. But the java plugin will cause you more problems, flash can be run using the nspluginwrapper. [I have a setup script for that.]("http://ubuntuforums.org/showthread.php?t=425672") But not java. There are 64bit versions of the java plugin, but the ones I have tried caused the browser to crash on all pages with applets.  You can install the 32bit firefox from my setup script if you just want it all to work with little problem.
Sorry I cant help you with nvidia drivers. I have ati graphics so I dont know a lot about the nvidia drivers.
Since you plan on installing to another partition and keeping the existing 32bit install for now ( a great idea) just install asap. Then you can slowly work on getting the install as you want it, having a working install to use in case there are any problems.

---

### Post by Cappy on 2007-05-12
nvidia drivers install by themselves, no work required.
Kilz hit 3,000 posts yahhhhhhh

---

### Post by LuisGMarine on 2007-05-12
Ok sounds like a good idea to have a dual boot for now, just until I test things out.

I'm going to go ahead and install when I get back, so wish me luck and I hope to join you guys, on the other side :)

---

### Post by RTrev on 2007-05-12
> **Kilz said:**
> Sorry I cant help you with nvidia drivers. I have ati graphics so I dont know a lot about the nvidia drivers.

Ah, this is something I can perhaps help with.  There were zero issues with the Nvidia drivers when I tried 64-bit.  Just the exact same routine as with the 32-bit.  Everything "just worked."  :)

Bob

---

### Post by LuisGMarine on 2007-05-12
Would you guys recommend using Automix2 to get some of those applications installed, also is there  a UBUNTU GUIDE for amd64?  I remember back in the hoary days there was one for 32-bit and one for 64-bit, I'm just curious to know so I can look at how easy it is to install things!

I'm worried that when I installed 64-bit I'm not going to have any idea on how to install anything.  Not even cedega, which is my main concern right now, for bittorents I think ktorrent has built up a rock solid reputation so I'm going to use it and give it a try.

But I deff like to know what commands to run to get stuff running,  I have everything ready to go, but I'm getting those last minute jitters about installing or not installing.

Thanks a lot for all the help, everyone in #irc says that ubuntu 64 is deff not worth all the hassle it is to get it to work!  But I make my own choices!

---

### Post by phidia on 2007-05-12
Hey LuisGMarine, You might also want to do a search here for simple64 which some have praised as useful for installing some popular apps. I will be joing the 64 club myself soon-still waiting for a few parts to complete the build of my new critter :) let us know how the install goes and good luck.

---

### Post by RTrev on 2007-05-12
> **LuisGMarine said:**
> Would you guys recommend using Automix2 to get some of those applications installed, also is there  a UBUNTU GUIDE for amd64?  I remember back in the hoary days there was one for 32-bit and one for 64-bit, I'm just curious to know so I can look at how easy it is to install things!

I'm worried that when I installed 64-bit I'm not going to have any idea on how to install anything.  Not even cedega, which is my main concern right now, for bittorents I think ktorrent has built up a rock solid reputation so I'm going to use it and give it a try.

But I deff like to know what commands to run to get stuff running,  I have everything ready to go, but I'm getting those last minute jitters about installing or not installing.

Thanks a lot for all the help, everyone in #irc says that ubuntu 64 is deff not worth all the hassle it is to get it to work!  But I make my own choices!

As do we all, young Skywalker.  :) :) :) :) :) 

As for Automatix, I don't care for it.  It doesn't communicate with Apt and so you may have something installed but Apt doesn't know it.. and never notifies you that's there's a new version, etc.  Apt will think it's leftover crap from something, or part of a broken package, or whatever.

 Instead, I'd suggest that you add to your /etc/apt/sources.list
```

 deb http://medibuntu.sos-sts.com/repo/ feisty free non-free

```

And then go here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

That should tell you most of what you need to know to get common things up and running.

HTH,
Bob

---

### Post by Kilz on 2007-05-12
> **LuisGMarine said:**
> Would you guys recommend using Automix2 to get some of those applications installed, also is there  a UBUNTU GUIDE for amd64?  I remember back in the hoary days there was one for 32-bit and one for 64-bit, I'm just curious to know so I can look at how easy it is to install things!

I'm worried that when I installed 64-bit I'm not going to have any idea on how to install anything.  Not even cedega, which is my main concern right now, for bittorents I think ktorrent has built up a rock solid reputation so I'm going to use it and give it a try.

But I deff like to know what commands to run to get stuff running,  I have everything ready to go, but I'm getting those last minute jitters about installing or not installing.

Thanks a lot for all the help, everyone in #irc says that ubuntu 64 is deff not worth all the hassle it is to get it to work!  But I make my own choices!

I will second the dont use automatix vote. It isnt that hard to install things. You really dont need it. You will be a much better at running linux if you dont use it. with synaptic, apt, and gdebi there isnt much you cant install on your own.
As for people on irc, well there is always someone who is full of fud and seems to want to spread it around. I will let you be the judge of how hard everything is once you have your install setup.

---

### Post by RTrev on 2007-05-13
> **LuisGMarine said:**
> 
I'm worried that when I installed 64-bit I'm not going to have any idea on how to install anything.  

Just a p.s. to this part, but what's to worry about?  At the absolute worst, you'll just re-install the 32-bit and wait a while for the 64-bit stuff to catch up.  At the best, you'll find that you really like digging into the guts and making things work, and you'll have a blast.

It isn't like you are making an irrevocable decision here.  And, as my dad always told me, worrying is just wasted energy.

Have fun, and please keep us posted!  You might be an inspiration to me to try it again.  My problem is that I don't really dig operating systems all that much.  They are there to let me run applications, write code, communicate, and be productive.  So I'd much rather be working on learning PHP, for example, than tinkering with the engine.  One older guy I know says he went through the "Linux from Scratch" phase, and now he's in the phase of just using it to be productive.  I'd like to know more about it, but only in my spare time when I'm not doing actual work with the system.

Bob

---

### Post by LuisGMarine on 2007-05-13
Ok, I think I'm going to do it.  For testing purposes I'm just going to split my current partition down and give 64-bit about 40GB.

I'm going to test a bunch of things, that include, and not limited to:

Cedega
Frostwire
Ktorrent ( I guess I'm going to install KDE for that )
Firefox ( with a working flash sound ( on my 32-bit system only root runs firefox and flash like a sweet melody, everything else just sucks , but I think it has to do in great part with my current ~/.asoundrc )


I might fiddle here and there with beryl since its soo cool, but since I'm taking this Cedega and gaming thing serious I don't think 1GB is enough to run KDE and game happily.

I'm just waiting for a couple of things to finish downloading and then I"m going to go ahead and do it.  I think I just adopted your fathers moto, bob,  " Worrying is a waste of energy."  

I'll keep you guys posted :)  Thanks for the help, and hope to work with you guys in the near future to get more people that are afraid of Ubuntu-AMD64 to come and try it out, and hopefully stay.  After all, I wish I would have had the balls to install this a year ago when Hoary was first coming out.  There would have not been anything better in the world then helped test and get Ubuntu to what it has become today!

-LuisGMarine

---

### Post by markusf21 on 2007-07-16
I have been using ubuntu for about 6 months or better. This is my second computer running it. The first one was an older than dirt Dell XPS. Then its HDD died. Rather than replacing it i got this Emachines W3619 I'm using now. Anyway I have been using 32 bit on this one for probably 3 months now. So it's set up just the way I want it. (thanks to the community for all the help, could not have done it alone) I was looking at the specs of the system today, because I want to do some upgrading. I didn't know it when i bought it but it is a 64 bit computer.
I am running 32 bit ubuntu. Is there a way to switch to 64 bit without having to start from scratch? I am running Feisty by the way Thanks

---

