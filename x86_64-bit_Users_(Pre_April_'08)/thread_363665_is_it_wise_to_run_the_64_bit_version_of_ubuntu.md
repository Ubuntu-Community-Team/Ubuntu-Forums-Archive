---
title: "is it wise to run the 64 bit version of ubuntu ?"
date: 2007-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by simonsphotos on 2007-02-17
ok not wanting to be funny but I am new to the issues that can arise when you have a 64 bit OS and some programs are not written for 64 but 32 bit, my issue mainly regards wine but I would like to ask if I am better off running 64 or 32 bit version on my computer that has an intel core 2 duo processor, I would like to reap all the performance possible from my computer as I work in photography and some mighty sized photos too, can I upgrade from 32 to 64 bit later without loosing everything I have installed etc. ?

---

### Post by rai4shu2 on 2007-02-17
The main issue with 64-bit IMO is the lack of decent Flash support, but there are ways to work around all the issues. If you don't mind the trade off of having to work around things, you do get a little extra speed using native 64-bit programs as much as possible.

On the other hand, Wine is basically a 32-bit only program so if you're mainly going to be using Wine, there's no particular reason I can think of to prefer 64-bit except the slightly faster kernel and such.

---

### Post by simonsphotos on 2007-02-17
well I will run all the native linux programs I can but there will be some I will have to run under wine and that too will become 64 bit.

---

### Post by Kilz on 2007-02-17
> **simonsphotos said:**
> well I will run all the native linux programs I can but there will be some I will have to run under wine and that too will become 64 bit.

No, wine is a 32bit windows application layer. Even those packages compiled to be installed on the 64bit version are all 32bit. Work on a 64bit wine is in early alpha from what I have read, the reason is there are few if any 64bit windows applications out there.
Being 32bit they take a hit on performance vs native 64bit Linux applications. There are few if any windows applications that dont have a linux application with the same functionality.

---

### Post by NilsJeppe on 2007-02-17
> **rai4shu2 said:**
> 
On the other hand, Wine is basically a 32-bit only program so if you're mainly going to be using Wine, there's no particular reason I can think of to prefer 64-bit except the slightly faster kernel and such.

How much of a hit are we talking here? Noticeable on any modern PC? Even noticeable for non-game apps?

---

### Post by simonsphotos on 2007-02-17
well my main worry at the moment is possible complications

---

### Post by Kilz on 2007-02-17
> **NilsJeppe said:**
> How much of a hit are we talking here? Noticeable on any modern PC? Even noticeable for non-game apps?

Some applications outside of wine that crunch numbers like ripping(encoding) and 3d design/rendering can see a 30% or more improvement. Its very noticeable.

---

### Post by simonsphotos on 2007-02-18
good so I'll stay on 64 bit then

---

### Post by penvzila on 2007-02-20
I haven't had a single 64bit-related problem so far.  I was expecting a lot worse from some of the things I've read.

---

### Post by simonsphotos on 2007-02-20
well wine plain won't run end of story i don't know if it is a 64 bit issue or that i am just a bit dense (50/50 chance of either)

---

### Post by B. W. on 2007-02-20
> **simonsphotos said:**
> well wine plain won't run end of story i don't know if it is a 64 bit issue or that i am just a bit dense (50/50 chance of either)
You have to compile it yourself. [This](http://www.ilfilosofo.com/blog/2007/01/12/installing-wine-on-ubuntu-edgy-610-64-bit/) might help.

---

### Post by Kilz on 2007-02-20
> **B. W. said:**
> You have to compile it yourself. [This](http://www.ilfilosofo.com/blog/2007/01/12/installing-wine-on-ubuntu-edgy-610-64-bit/) might help.

No you dont have to compile it yourself. There are 64bit packages and the 32bit one works for most people.

---

### Post by TimJBart on 2007-02-22
I am going to install ubunutu this week on my 64 bit mahcine.

From what you guys are saying, you recommend 64bit ubuntu and there is very little that I can't do in the 64bit version that works in 32bit?  The graphics and sound drivers all work the same way do they?

I know very little and so want as few complications as normal so don't know which version to install.  Gonna use XP64 for games so hopefully won't need WINE.

So, ubuntu 64 yay or nay? :confused:

---

### Post by Kilz on 2007-02-22
> **TimJBart said:**
> I am going to install ubunutu this week on my 64 bit mahcine.

From what you guys are saying, you recommend 64bit ubuntu and there is very little that I can't do in the 64bit version that works in 32bit?  The graphics and sound drivers all work the same way do they?

I know very little and so want as few complications as normal so don't know which version to install.  Gonna use XP64 for games so hopefully won't need WINE.

So, ubuntu 64 yay or nay? :confused:

Give it a try, I have cedega on my 64bit install. I am addicted to a few games. Mostly older ones like sim city 4, warcraft 3, and diablo 2. The drivers for video and sound are not a problem.

---

### Post by simonsphotos on 2007-02-22
well I'll be getting a 320 GB HDD tomorow so this weekend some major reorganising and resinstalling is going to go on, I'm considering having my 80 GB HDD for my OSes like 20 GB pertitions each, can multiple compies of Linux (any distro) use the same swap partitions ? can most distros (preferably Ubuntu) use more than one swap disk, I'll have a total of 3 HDDs so a swap disk on each should yeild 3 times the virtual memory speed

---

### Post by John Jason Jordan on 2007-02-22
> **simonsphotos said:**
> well I'll be getting a 320 GB HDD tomorow so this weekend some major reorganising and resinstalling is going to go on, I'm considering having my 80 GB HDD for my OSes like 20 GB pertitions each, can multiple compies of Linux (any distro) use the same swap partitions ? can most distros (preferably Ubuntu) use more than one swap disk, I'll have a total of 3 HDDs so a swap disk on each should yeild 3 times the virtual memory speed
Yes, they can all use the same swap partition. During installation of the first distro just create the swap partition for it and under filesystem type choose "swap." They will all understand that the partition is a swap partition and be able to use it, regardless of the distribution. Note that each distro has its own setup utility and some of them are smarter than others. When installing subsequent distros be sure to choose the "manual" partition option so you can tell the distro where to install itself and what to use for the swap partition. 

Regarding using more than one swap partition, I'm not sure, but I don't think so. But since they can all use the same swap partition, I don't see the need to do so. My understanding is that your swap doesn't need to be more than the same size as the installed memory, and some people say less. (There are lots of discussions and differences of opinion on this if you google.)

---

### Post by Jovec on 2007-04-02
[QUOTE=simonsphotos]I'll have a total of 3 HDDs so a swap disk on each should yeild 3 times the virtual memory speed[/QUOTE]

You'll want to add the same option pri=1 for each swap partition in /etc/fstab if you are going to use multiple swap partitions located on multiple hard drives, which will effectively split your swap partition usage between them. Otherwise, you'll just fill them up in linear order. But then again I've never seen concrete evidence this will improve performance much either, and if you are trying to maximize swap performance the best way is to add more RAM.

---

### Post by simonsphotos on 2007-04-02
well theoretically speed should increase it would be like a raid setup but appling only to the virtual memory,

On a side note how does windows handle multiple swap partitions ? does more than one increase speed ? or are they used consecutively

---

### Post by trepidprism on 2007-05-26
if memory serves, windows does not use a 'partition' for virtual memory it uses a page file. this file must be present in the c:\windows dir so I would assume it cant be on multiple hdd or have more then one file.

please correct me if I am wrong about this

---

### Post by Case_f on 2007-05-26
> **trepidprism said:**
> if memory serves, windows does not use a 'partition' for virtual memory it uses a page file. this file must be present in the c:\windows dir so I would assume it cant be on multiple hdd or have more then one file.

please correct me if I am wrong about this

The pagefile in Windows is located in root directory of the drive and it can be spread across multiple drives/partitions (talking about NT-based Windows, of course).

---

### Post by simonsphotos on 2007-05-26
I prefer to use a seperate 2-8 GB partition for swap memory

---

### Post by Kilz on 2007-05-26
> **simonsphotos said:**
> I prefer to use a seperate 2-8 GB partition for swap memory

You use that much swap? I know with 2gb ram I rarely use swap.

---

### Post by bigtom2 on 2007-07-07
> **Kilz said:**
> Some applications outside of wine that crunch numbers like ripping(encoding) and 3d design/rendering can see a 30% or more improvement. Its very noticeable.

I DO A LOT OF VIDEO 64 BIT DOES IT MUCH FASTER. THIS IS THE WAY ALL COMPUTERS ARE GOING.
ITS WORTH IT.:p

---

### Post by funkwurm on 2007-07-07
> **bigtom2 said:**
> I DO A LOT OF VIDEO 64 BIT DOES IT MUCH FASTER. THIS IS THE WAY ALL COMPUTERS ARE GOING.
ITS WORTH IT.:p

As far as I know, a big advantage is that a 64-bits kernel is able to address way more internal memory. So if your photo is so big that it would need more than 2 GB only to display, a 32 bit kernel is unable to do that, even if you do have 8 GB of RAM in your machine.

---

### Post by jespdj on 2007-07-08
> **funkwurm said:**
> As far as I know, a big advantage is that a 64-bits kernel is able to address way more internal memory. So if your photo is so big that it would need more than 2 GB only to display, a 32 bit kernel is unable to do that, even if you do have 8 GB of RAM in your machine.

Yes, but it is not only that. A 64-bit Intel or AMD processor also runs 64-bit programs faster.

To go into the technical details: In 64-bit mode, the processor has more internal registers available and the registers are also larger (64 instead of 32 bits). There are also more floating point and SSE registers (which are used for multimedia applications such as video editing).

Software that has been compiled for 64 bit is able to use those extra registers and so can make more efficient use of the processor. With some number crunching applications it can be as much as 20%-30% faster.

---

### Post by hendoc on 2007-07-08
I run Feisty on AMD64 and on Celeron D 32bit. I used the same install CD on both machines. The 32 bit machine has a 3.2 Gh processor, while the 64 bit is onlt 2.19. The 64 bit AMD machine is still WAY, WAY faster. The ram is the same. Draw your own conclusions.

---

### Post by rsambuca on 2007-07-09
> **hendoc said:**
> I run Feisty on AMD64 and on Celeron D 32bit. I used the same install CD on both machines. The 32 bit machine has a 3.2 Gh processor, while the 64 bit is onlt 2.19. The 64 bit AMD machine is still WAY, WAY faster. The ram is the same. Draw your own conclusions.

hendoc, I hate to break it to you,but your comparison of cpu speeds in this fashion is completely irrelevant.  AMD and Intel chip designs are quite different, and thus they can complete a different amount of tasks per cycle from one another.  Then, to top it all off, you are trying to compare 32 bit vs 64 bit on different designed chips.  Basically, your statement has to meaning.

The real test would be to run Feisty 64 bit and Feisty 32 bit on the same rig and then test your speeds.

---

### Post by blakjak on 2007-07-14
I've run Feisty 32bit and 64bit each for a couple of weeks on an AMD64 (3.0Ghz, Single Core, 1.5GBRam). I've have no issues with running anything from the ubuntu repository and the 64Bit version seems to run every much quicker and more consistently (IE no crunchy slowdowns when mutlitasking)

I'm having trouble getting a couple things to run under wine, but that's because of my video card/drivers, all my 32bit apps seem to run fine until they need openGL. Otherwise no issues to report and the 64bit build is quick.

---

### Post by stmiller on 2007-07-15
I've noticed a difference with encoding using programs like Handbrake and LAME. 64bit seems to be able to crunch quite a bit faster.

Almost all recent CPUs sold today are 64bit, and probably by the end of the year there will not be any more 32bit CPUs sold by computer retailers. PC motherboards are available which can hold 4GB of ram (or more) for powerful 64bit goodness. This is the direction computers are going, so the larger user base the better. 
Even if you have an AMD64 cpu from the past several years you are already ready for 64bit!

There was a similar debate when we went from 16bit (Windows 3.1) to 32bit (Windows 95) computers. Lots of people thought 32bit was crazy/risky. Windows 95 had a compatibility mode to run 16bit apps. Linux has a similar setup where we can execute and run 32bit code just fine in a 64bit install.

---

### Post by jespdj on 2007-07-15
Indeed, (almost?) all current Intel and AMD processors are 64 bit and 2 GB RAM is nowadays the standard amount of RAM for a new PC. Next year 4 GB is probably going to be the standard amount of RAM.

32-bit operating systems have a limit of 4 GB memory, although there are some tricks such as [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension) which in principle makes it possible to use up to 64 GB memory on a 32-bit system; in practice, only the advanced business / server versions of Windows support this. I don't know if 32-bit Linux supports it.

Anyway, to really go beyond the 4 GB limit, we'll need 64-bit operating systems. I expect that in about 2 or 3 years 64-bit OS'es will become more and more the default, for Windows as well as Linux.

One thing that holds 64-bit Windows back is the fact that many hardware manufacturers are unwilling to invest time and money into writing drivers (drivers for 32-bit Windows don't work on 64-bit Windows). This isn't such a problem for Linux, where most drivers are open source.

In principle you can run any 32-bit Linux program on 64-bit Linux too. If you want to run a specific 32-bit program on your 64-bit Linux computer then there is most likely someone, somewhere who has figured out how to do it, and by searching on Internet you can most likely find instructions on how to run it.

---

### Post by Kilz on 2007-07-15
It is indeed a shame IMHO that linux is wasting time on the 32bit version, thereby giving Windows more time to fix the problems with 64bit Windows. When Windows gets 64bit working better we will lose the advantage of being one of the few working 64bit operating systems.

---

### Post by dptxp on 2007-07-16
> **Kilz said:**
> It is indeed a shame IMHO that linux is wasting time on the 32bit version, thereby giving Windows more time to fix the problems with 64bit Windows. When Windows gets 64bit working better we will lose the advantage of being one of the few working 64bit operating systems.

Agreed. New processors from both AMD and INTEL are now 64 bit though they may still be selling some of the 32 bit ones.

Ubuntu should only support the LTS version of 32 bit (maybe upto 7.04) and move to 64 bit in their 6 month releases. So the 32 bit machine owners will not suffer and we shall keep pace.

---

### Post by rsambuca on 2007-07-16
You guys realize that there are still hundreds of thousands of 32 bit computers being used around the world, right?  Yes, 64-bit is the way of the future, but what about all of these others?  Too bad, so sad?  I feel that both architectures should be supported for the next while.

Just because many people living in the industrialized nations have cheap and easy access to 64-bit computers does not mean that everyone in the world does.

---

### Post by Kilz on 2007-07-16
> **rsambuca said:**
> You guys realize that there are still hundreds of thousands of 32 bit computers being used around the world, right?  Yes, 64-bit is the way of the future, but what about all of these others?  Too bad, so sad?  I feel that both architectures should be supported for the next while.

Just because many people living in the industrialized nations have cheap and easy access to 64-bit computers does not mean that everyone in the world does.

I dont think 32bit computers should not be supported. But that the focus of development should be changed to 64bit. The 32bit version should still be produced. 
But the view of having 64bit users use the 32bit version to get things to "just work" if they dont like something not working should be changed. Work should be done to make sure that the 64bit version "just works" as well as the 32bit one without any additional setup over that witch is done on the 32bit version. Even if this means that some eye candy features get put on hold.
Both amd and intel no longer produce 32bit processors, what is out there will die off , even in the developing areas of the world. Should the focus of whats being worked on be on hardware that is no longer being produced? If you say yes, then why is the Ubuntu version designed to run on Apple computers focused on intel processors?

---

### Post by jespdj on 2007-07-16
Apple's next version of OS X, version 10.5 (codenamed Leopard) which is going to be out in a few months is completely 64-bit. It will run 32-bit as well as 64-bit Mac OS X applications. So Apple is making the jump to 64-bit soon.

I agree with Kilz that it is time that 64-bit is going to be the default for Linux. (And ofcourse 32-bit should be continued to be supported for a number of years).

---

### Post by rsambuca on 2007-07-16
> **Kilz said:**
> I dont think 32bit computers should not be supported. But that the focus of development should be changed to 64bit. The 32bit version should still be produced. 
But the view of having 64bit users use the 32bit version to get things to "just work" if they dont like something not working should be changed. Work should be done to make sure that the 64bit version "just works" as well as the 32bit one without any additional setup over that witch is done on the 32bit version. Even if this means that some eye candy features get put on hold.
Both amd and intel no longer produce 32bit processors, what is out there will die off , even in the developing areas of the world. Should the focus of whats being worked on be on hardware that is no longer being produced? If you say yes, then why is the Ubuntu version designed to run on Apple computers focused on intel processors?

I agree that 64 bit should definitely be the focus, it's just that dptxp indicated that 32 bit support should be dropped, which I completely disagree with.

---

### Post by dptxp on 2007-07-17
> **rsambuca said:**
> I agree that 64 bit should definitely be the focus, it's just that dptxp indicated that 32 bit support should be dropped, which I completely disagree with.

Never said that 32 bit support should be dropped. Please read again. 32 bit needs support for a few more years.
Said that further development should be on 64 bit.

---

### Post by kiv on 2007-07-17
I have just bought a intel core 2 duo laptop. 

i'm going to rip vista out and install ubuntu... is it worth me installing the 64bit version? is there a 64 bit version of ubuntu studio? & what advantages will i gain?

regards.

---

### Post by punky on 2007-07-17
My advice is don't! I really regret installing the 64bit so much that i'm considering going down to 32bit. I've come across numerous bugs and probs with Flash, VNC amongst others. XP and Vista 64bit also have their problems. 

I've not really noticed a great improvement over XP32 and XP64. Can't make the comparison with Ubuntu though, but i'd suspect its about the same.

I'd leave it another while until 64bit development improves.

---

### Post by dptxp on 2007-07-17
> **kiv said:**
> I have just bought a intel core 2 duo laptop. 

i'm going to rip vista out and install ubuntu... is it worth me installing the 64bit version? is there a 64 bit version of ubuntu studio? & what advantages will i gain?

regards.

If you have 6 GB disk space to spare then why not try out both and find out for yourself.

---

### Post by Kilz on 2007-07-17
> **punky said:**
> My advice is don't! I really regret installing the 64bit so much that i'm considering going down to 32bit. I've come across numerous bugs and probs with Flash, VNC amongst others. XP and Vista 64bit also have their problems. 

I've not really noticed a great improvement over XP32 and XP64. Can't make the comparison with Ubuntu though, but i'd suspect its about the same.

I'd leave it another while until 64bit development improves.

While you say you have had problems with the 64bit version. Looking at your post history, this is the first post in the 64bit section. Why have you not posted problems here? Even if you have not posted, there are sticky's , and numerous posts on how to get flash to work. Yet by your post history you have posted in none of them. Are you perhaps waiting for the answer to bite you on the rear end?
You say you have found bugs, have you made bug reports on them on launchpad? If not how do you expect them to be noticed so they can be fixed? If you have filed the reports please provide a link to them on launchpad so we can see if we can be any help.
Taking a look at that poost history of yours. You posted you have problems with beryl , while using an ATI card. Expect the problem to follow you to 32bit, its because you have an ATI card. That and compiz\beryl are still in BETA. While they work for some, its not always easy to get them to work.

---

### Post by kiv on 2007-07-17
> **Kilz said:**
> While you say you have had problems with the 64bit version. Looking at your post history, this is the first post in the 64bit section. Why have you not posted problems here? Even if you have not posted, there are sticky's , and numerous posts on how to get flash to work. Yet by your post history you have posted in none of them. Are you perhaps waiting for the answer to bite you on the rear end?
You say you have found bugs, have you made bug reports on them on launchpad? If not how do you expect them to be noticed so they can be fixed? If you have filed the reports please provide a link to them on launchpad so we can see if we can be any help.
Taking a look at that poost history of yours. You posted you have problems with beryl , while using an ATI card. Expect the problem to follow you to 32bit, its because you have an ATI card. That and compiz\beryl are still in BETA. While they work for some, its not always easy to get them to work.

I think I'll stick with 32bit but what would your recommendation be kilz?

---

### Post by odiseo77 on 2007-07-17
I have both, Feisty 32 bits and Feisty 64 bits installed on my machine (a hyperthreaded, 64 bits P4) mainly to test its performance and other stuff. After reading some tutorials here on how to get flash to work on firefox the 64 bits version is working fine (not sure about wine because I rarely use it) but I don't notice a considerable performance boost Ubuntu 64 bits, so I mostly use the 32 bits version... just my thoughts.

---

### Post by John.Michael.Kane on 2007-07-17
> **kiv said:**
> I have just bought a intel core 2 duo laptop. 

i'm going to rip vista out and install ubuntu... is it worth me installing the 64bit version? is there a 64 bit version of ubuntu studio? & what advantages will i gain?

regards.

This may help you [Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

IMHO anything that can be done on 32bit ubuntu can be  accomplished using 64bit ubuntu, and It's not about is it worth installing 64bit or 32bit as neither one is perfect, and they both come with their bag of issues.

What I would sugest you or any other user wanting to try 64bit ubuntu is to use it for thirty days without rebooting into 32bit ubuntu, and make use of the guide made for 64bit.  This will allow you to see for your self if it's worth it or not.  

In the end it's about the end user being willing to solve whatever issue they come across be it on 32bit ubuntu or 64bit ubuntu or any other distro for that matter.

---

### Post by jespdj on 2007-07-17
> **punky said:**
> My advice is don't! I really regret installing the 64bit so much that i'm considering going down to 32bit. I've come across numerous bugs and probs with Flash, VNC amongst others. XP and Vista 64bit also have their problems. 

I've not really noticed a great improvement over XP32 and XP64. Can't make the comparison with Ubuntu though, but i'd suspect its about the same.

I'd leave it another while until 64bit development improves.
Here we go all over again! Really, for how long did you try 64-bit Ubuntu? What where those numerous bugs and problems you encountered? Installing Flash in 64-bit Firefox is easy with [nspluginwrapper](http://gwenole.beauchesne.info/projects/nspluginwrapper/). I've been running 64-bit Ubuntu for about a year now and never encountered "numerous bugs and problems".

Problems with 64-bit Windows XP or Vista do not have anything to do with 64-bit Ubuntu. Ubuntu and Windows are two completely different operating systems, you are comparing apples to oranges. The fact that you didn't see any improvement between 32-bit and 64-bit Windows XP does not mean anything for 32-bit or 64-bit Ubuntu. So there is no reason to suspect anything.

Running 64-bit Ubuntu is not that hard. You can run any 32-bit Ubuntu program on 64-bit Ubuntu too. 64-bit Ubuntu is not a "beta" or "test" version. It works just as well as 32-bit Ubuntu, or even better because it knows how to use the 64-bit capabilities of your hardware.

---

### Post by Kilz on 2007-07-17
> **kiv said:**
> I think I'll stick with 32bit but what would your recommendation be kilz?

I would recommend you try the 64bit version. If you already have the 32bit version installed and have spare room on your hard drive, install both. This way you can at your own pace move over while still having the 32bit install to get things you need done.
The post below is quoted for the pure truth it gives.

> **SD-Plissken said:**
> This may help you [Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

**IMHO anything that can be done on 32bit ubuntu can be  accomplished using 64bit ubuntu, and It's not about is it worth installing 64bit or 32bit as neither one is perfect, and they both come with their bag of issues.**

What I would sugest you or any other user wanting to try 64bit ubuntu is to use it for thirty days without rebooting into 32bit ubuntu, and make use of the guide made for 64bit.  This will allow you to see for your self if it's worth it or not.  

In the end it's about the end user being willing to solve whatever issue they come across be it on 32bit ubuntu or 64bit ubuntu or any other distro for that matter.

Great post. The highlighted section is pure truth. The only thing I would add to that section is that the issues of either are equally hard. Simply moving from one bit to another is not going to make solving the issues you will face any easier.

---

