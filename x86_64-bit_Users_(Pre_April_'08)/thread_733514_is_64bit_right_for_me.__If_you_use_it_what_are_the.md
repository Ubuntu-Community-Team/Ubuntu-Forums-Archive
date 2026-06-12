---
title: "is 64bit right for me.  If you use it what are the pro's/con's?"
date: 2008-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rizla on 2008-03-23
I just finished buying all the parts for a new system.  Intel Q6600 Quad Core, 2 GB DDR2 (800mhz), 2.25 TB (1.5 RAID 5 config to be set up), Geforce 7150 built in video.  The main purpose for this box will be my storage server/DVD backup box for encoding movies.

I'm debating whether to make the 64 bit switch, but was wondering what the main advantages were.  Currently, my board maxes out at 2 slots for DDR2 ram, i think it supports up to 4GB Dual Channel.    Will running a 64 bit OS give me any major improvements over 32 bit.

Also, given the timing of my purchases and the new release of Hordy, should I wait till its out of beta and install then or can I go ahead and set my box up with the beta version then upgrade to the final release when it comes out.  OR should I go with Gusty then update to Hordy when its ready?

64 bit or 32 bit.. whats your take?

---

### Post by Tyler H on 2008-03-23
I've been running Ubuntu(64) 7.10 for about a month now. From all the research on 64 bit systems, if you're going to be doing DVD ripping and other apps that require alot of number crunching, then you might want to consider a 64 bit Ubuntu release. 64 bit systems get their advantage over 32 bit systems in this general area. As for waiting, going for the beta of Hardy, or going with 7.10 is a decision of personal preference and risk management of using a beta OS. 7.10 64 does however have some serious issues with flash.....which is still pestering me.

---

### Post by talsemgeest on 2008-03-23
Take a look here: [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by defenestratos on 2008-03-24
If you're ripping dvds youll see big improvements. Some report a 120 percent increase in speed for some applications. Do it man!

---

### Post by talsemgeest on 2008-03-24
The only downside is quite a lot less compatibility with some apps. If you are willing to work through all of the problems for the extra speed, go for it!

---

### Post by teslarage on 2008-03-24
I installed 64bit Hardy BETA just for the speed (though I am not sure what am I going to use the speed for!).

Still couldn't get Java to work with Firefox (even with IcedTea) but I can live with that :)

---

### Post by hvacr on 2008-03-24
To many programs don't seem to like the 64 version. I will be using the 32 bit one next, as I don't like fighting to make things work. I can honestly say that winxp 64 is far better, everything just works with it.

---

### Post by Sef on 2008-03-24
> To many programs don't seem to like the 64 version. I will be using the 32 bit one next, as I don't like fighting to make things work. I can honestly say that winxp 64 is far better, everything just works with it.

If the programs are not yet ported to 64-bit, then they will not be so easy to get working, if at all.

---

### Post by Kilz on 2008-03-24
> **hvacr said:**
> To many programs don't seem to like the 64 version. I will be using the 32 bit one next, as I don't like fighting to make things work. I can honestly say that winxp 64 is far better, everything just works with it.
64bit Windows has far to many drivers missing. Can you please list some of those applications that are missing or not work?


> **Sef said:**
> If the programs are not yet ported to 64-bit, then they will not be so easy to get working, if at all.

Few things that are in the 32bit repositories are not in the 64bit repo's.

---

### Post by Rizla on 2008-03-24
For the immediate future i just see it as a file server dishing out Xvid's and ISO dvd's to my xbox and a NMT (once it get it).  I'll be ripping dvd's and doing some encoding.  I'll probably setup freenx for remote access and ushare.  Also, a major MAJOR point for me will be mdam.  I'm going to use that to set up my software raid 5.  I'm assuming i could get a boost in performance using a quadcore on 64 bit with it.  I wont really use it for gaming or web browsing.  Pretty much general purpose server use.  Might thrown an apache web server with a mysql db.   Maybe myth, but dont think so.

It seems from the threads i've read, java and flash have the most hiccups.

How easy is it to go from beta to the final release?  I'm going to have a seperate OS drive and my raid set will be its own 'drive'.  Does that make for easier migration?

---

### Post by jhnphm on 2008-03-24
I just run all the 32 bit apps I have in a chroot, no headaches once it's set up, unlike using ia32-libs and having gtk look in the wrong places for themes and whatnot.

Seperate drives for OS and /home make it easier to recover if the OS gets fubared or you want to reinstall cleanly. I'm running Hardy alpha (upgraded to "beta" i guess) and don't have real problems, other than the aforementioned problems w/ the gtk in ia32-libs, which I solved by just using a full-blown chroot install of ubuntu32.

---

### Post by hvacr on 2008-03-24
> **Kilz said:**
> 64bit Windows has far to many drivers missing. Can you please list some of those applications that are missing or not work?


No movie catalogue software, no cd catalogue software. I could not get the software for my APC unit to work properly. There has been a few others, just cannot recall what. As far as xp64 is concerned, no driver issues at all. I have had it on my system for 2 years now, the original install. I actually find in more stable than ubuntu 64. 

Few things that are in the 32bit repositories are not in the 64bit repo's.

Seems to be the few things I want that are not in there. :)

---

### Post by Kilz on 2008-03-24
> **hvacr said:**
> Seems to be the few things I want that are not in there. :)

No cd catalog software? I know I have at least one, CDcat installed. Please tell me specific applications, not just generic categories. The number of packages in the 64bit and 32bit repositories is exactly the same. So if anything is missing that was in 32bit, I wonder why you cant find it.

---

### Post by hvacr on 2008-03-24
> **Kilz said:**
> No cd catalog software? I know I have at least one, CDcat installed. Please tell me specific applications, not just generic categories. The number of packages in the 64bit and 32bit repositories is exactly the same. So if anything is missing that was in 32bit, I wonder why you cant find it.

I will look into it when I get home, there are many software I can find on my laptop, that I cannot find on my desktop. I also need java, does not work on 64. This is very important to me, so I need to boot back into xp. 

I am not saying ubuntu 64 is bad, but for me it is to much work to get things going. I would rather run the 32 bit version, lose out on my 4 gigs of ram, that fight the battle I have been fighting. This is why I will always dual boot, simply because xp 64 works great for me. 


Griffith will not work under ubuntu 64. I use it on my laptop, was hoping to use it on the desktop. See my post about movie catalogue software.

---

### Post by jhnphm on 2008-03-24
> **hvacr said:**
> I will look into it when I get home, there are many software I can find on my laptop, that I cannot find on my desktop. I also need java, does not work on 64. This is very important to me, so I need to boot back into xp. 

I am not saying ubuntu 64 is bad, but for me it is to much work to get things going. I would rather run the 32 bit version, lose out on my 4 gigs of ram, that fight the battle I have been fighting. This is why I will always dual boot, simply because xp 64 works great for me. 


Griffith will not work under ubuntu 64. I use it on my laptop, was hoping to use it on the desktop. See my post about movie catalogue software.

What exactly doesn't work about it? Also, if it's a server, use the server kernel, which will also allow use of all 4 gigs of RAM under Ubuntu32. Last I checked, the server kernel did not have precompiled nVidia drivers, but you don't need that for a server.

---

### Post by hvacr on 2008-03-24
> **jhnphm said:**
> What exactly doesn't work about it? Also, if it's a server, use the server kernel, which will also allow use of all 4 gigs of RAM under Ubuntu32. Last I checked, the server kernel did not have precompiled nVidia drivers, but you don't need that for a server.

Griffith will not install, period. It's not a server, just a desktop system.

---

### Post by saru411 on 2008-03-24
> **hvacr said:**
> Griffith will not install, period. It's not a server, just a desktop system.

I just successfully installed Griffith on my 7.04 AMD64 build. I have also had Java/Flash fixed for a very long time.  If your hardware supports 64bit thats what you should install. All O/S require setup 64bit and 32bit.

As for the installation, I would install 7.10 and then upgrade. Using a Beta can very easily break your system. I recommend making 2 /root partitions and 1 /home partition then installing 7.10 on one of the /root partitions. When 8.04 comes out you can upgrade. If the upgrade doesnt work out so well you can always install 8.04 on the other partition and use the existing /home folder.

---

### Post by Kilz on 2008-03-24
> **hvacr said:**
> Griffith will not install, period. It's not a server, just a desktop system.

[Its in the repositories,]("http://packages.ubuntu.com/gutsy/griffith") listed in the Universe and available for ALL versions of Ubuntu. That includes the AMD64 version.

---

### Post by hvacr on 2008-03-24
> **Kilz said:**
> [Its in the repositories,]("http://packages.ubuntu.com/gutsy/griffith") listed in the Universe and available for ALL versions of Ubuntu. That includes the AMD64 version.


I will have a look

---

### Post by utUtu on 2008-03-24
> **Rizla said:**
> I just finished buying all the parts for a new system.  Intel Q6600 Quad Core, 2 GB DDR2 (800mhz), 2.25 TB (1.5 RAID 5 config to be set up), Geforce 7150 built in video.  The main purpose for this box will be my storage server/DVD backup box for encoding movies.

I'm debating whether to make the 64 bit switch, but was wondering what the main advantages were.  Currently, my board maxes out at 2 slots for DDR2 ram, i think it supports up to 4GB Dual Channel.    Will running a 64 bit OS give me any major improvements over 32 bit.

Also, given the timing of my purchases and the new release of Hordy, should I wait till its out of beta and install then or can I go ahead and set my box up with the beta version then upgrade to the final release when it comes out.  OR should I go with Gusty then update to Hordy when its ready?

64 bit or 32 bit.. whats your take?

Looks like you got the Ferrari but you wanted to have an inline 4 instead of the V12 Bi-Turbo.

---

### Post by Rizla on 2008-03-25
**This post could be related to an Ubuntu bug filed at**: rizla [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **utUtu said:**
> Looks like you got the Ferrari but you wanted to have an inline 4 instead of the V12 Bi-Turbo.

I dont get it, in what sense are you talking about?  That Im debating using a beta version of 64 or that i'm considering 32bit?  I think i'll ultimately give the 64 bit a try, but its the whole beta thing or waiting for the official release thats throwing me off.

---

### Post by Kilz on 2008-03-25
> **Rizla said:**
> **This post could be related to an Ubuntu bug filed at**: rizla [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				

I dont get it, in what sense are you talking about?  That Im debating using a beta version of 64 or that i'm considering 32bit?  I think i'll ultimately give the 64 bit a try, but its the whole beta thing or waiting for the official release thats throwing me off.

You bought a Ferrari, a high performance 64bit computer. By asking if you should place a 32bit operating system, you are in fact asking if you should hobble it. Kind of like buying a Ferrari and pulling half of the spark plug wires out thinking you will save money on tune ups. To those of us running the 64bit version it sounds like insanity.
But, regardless, this topic has gone on for 3 pages now on a question you could have easily answered with a search and reading the stickies. Please do so now.

---

### Post by Jouke74 on 2008-03-25
I read it actually this way: 

Ferrari V12 vs inline 4 also in a sense, what % of time it will be encoding movies and what time will it only be used to store and host files, which is basically only disk access and network activity... I would definitively be checking out the use of a large block file system  and disk partitioning (raid or not) as well. A dual core processor would have been fine, although now it is possible to encode 2 to 3 movies at the same time with some speed and still have a responsive system. :)

The 64 bit question is actually a bit uh (trying to find a not ugly word here) given the fact that you want to make it a server and use it for encoding dvd movies (which almost cries 64 bit!). It clearly indicates, what Kilz also points out many times, that users have a clue what to install and what the real difference between a 64bit and 32bit system is. A more annoying issue, they don't want to read about the important differences beforehand but just ask a question at the forum hoping for a quick reply. And to be honest if computers are not your thing and you just want to use one for everyday internet, then this is also very understandable. If you want to install an OS yourself and have it tweaked to optimal performance then it should become your thing, and that requires some study.

As for the Beta, it is not called a "Beta" for nothing, things might break as development to the final version goes on. There are a few options:
1. Wait until the final 8.04 comes out. That gives you some time to read about everything :lolflag:
2. Install Beta Hardy 8.04 and update. Then you take the risk of running into problems these months. The difference between Gutsy and Gutsy Beta was small btw. so I assume this will go fine. 
3. Install Gutsy and do a distro upgrade when Hardy comes out. If you are not tinkering too much with the system this should also not be a problem.
4. Install & keep Gutsy. It's a server... if it works it works.
I don't like this option too much as Hardy will be LTS and therefore a longer supported system.

As with all OSes there always will bugs & (security) updates. With your hardware I cannot imagine much problems.

---

### Post by Rizla on 2008-03-25
**This post could be related to an Ubuntu bug filed at**: rizla [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Kilz said:**
> You bought a Ferrari, a high performance 64bit computer. By asking if you should place a 32bit operating system, you are in fact asking if you should hobble it. Kind of like buying a Ferrari and pulling half of the spark plug wires out thinking you will save money on tune ups. To those of us running the 64bit version it sounds like insanity.
But, regardless, this topic has gone on for 3 pages now on a question you could have easily answered with a search and reading the stickies. Please do so now.

I gotcha.  Honestly, my question is should I build the box with the beta version of Hardy.  If I do, is the migration to the final release seamless or will i have to reinstall everything?

---

### Post by Kilz on 2008-03-25
> **Rizla said:**
> **This post could be related to an Ubuntu bug filed at**: rizla [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				

I gotcha.  Honestly, my question is should I build the box with the beta version of Hardy.  If I do, is the migration to the final release seamless or will i have to reinstall everything?

If you want Hardy, wait till its released. Development versions are not reliable for day to day operation. I also don't recommend upgrading from one version to another, a clean install is always the best practice.

---

### Post by Rizla on 2008-03-25
**This post could be related to an Ubuntu bug filed at**: rizla [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Kilz said:**
> If you want Hardy, wait till its released. Development versions are not reliable for day to day operation. I also don't recommend upgrading from one version to another, a clean install is always the best practice.

So install Gusty and upgrade to final when its released?

---

### Post by Kilz on 2008-03-25
> **Rizla said:**
> **This post could be related to an Ubuntu bug filed at**: rizla [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				

So install Gusty and upgrade to final when its released?

Yes, I still have feisty installed and will do a clean install to Hardy. Gutsy didn't have anything I really needed. If I had Gutsy, Id still do a clean install, about a week after its released. One thing I have learned is that beta's and the latest and greatest are not always a good thing. Stability is better.

---

### Post by Rizla on 2008-03-25
**This post could be related to an Ubuntu bug filed at**: rizla [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Kilz said:**
> Yes, I still have feisty installed and will do a clean install to Hardy. Gutsy didn't have anything I really needed. If I had Gutsy, Id still do a clean install, about a week after its released. One thing I have learned is that beta's and the latest and greatest are not always a good thing. Stability is better.

Alright, we'll i'm going on your experience and will install Feisty 64.  I dont think i really need anything to spectacular since its just going to be a server.  The latest and the greatest might not be necessary at the moment.

---

### Post by lamborghiniwang on 2008-03-27
I switched from the 32bit to 64bit since the release of 7.10, and never looked back. Probably the only draw back you would notice is that the 64bit version tends to use a little bit more memory, the 32bit version never uses any swap on my Thinkpad T61p with 2GB RAM, but occasionally the 64bit version would occupy 100-200MB swap if I run some RAM consuming programs.

The biggest advantage for the 64bit (at least for me) is that some of my numerical computing code is running considerably faster, with the Intel C++ compiler, I see my numerical code is running 20-30% faster than the 32bit version. I am not saying that all program in 64bit is faster than the 32bit version, but it is the case for me at least for some of my numerical computing code. :guitar:

---

### Post by pape on 2008-03-27
Go for 64-bit!

Just installed Kubuntu 7.10 x86-64 on an AMD Athlon 64 (for the 1st time).

Despite lots of reservations expressed regarding the 64 bit systems, I got everything working nicely.

I used Automatix to install flash and codecs. Firefox Java plugin with icedtea. Skype 2.0 using thread 432295. Youtube, all straming video, java and flash stuff works so far.

---

