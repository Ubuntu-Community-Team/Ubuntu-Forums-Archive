---
title: "64 Bit vs. 32 bit Revisited"
date: 2007-05-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by WhiteHorse on 2007-05-13
**Considering whether to use 64 bit Ubuntu?**

OK I have to revise this post. Things have changed dramatically in the past few months. Now I absolutely, 100%, recommend 64 bit over 32 bit Ubuntu, even for novices. 

One reason I changed my mind is because Automatix is now current in amd64 and allows one to get everything in one click, even Java and Flash. Another reason is that all of the problems I experience now are identical to what x32 users are experiencing, so there's no difference other than huge performance gains in 30% of all apps I run and 90% of all dev or scientific apps. 

Even if you aren't a power user, you will notice a difference. I run WPA2 over my wireless network, to an nfs drive, and play 320kbps mp3s while surfing the net at 3Mbps, and compiling kernels at the same time and watching 1024x768 internetTV on my wall projector(9ftx10ft), and running 1280x800 on my primary display. Now my only limit is my 512MB RAM sometimes caches to disk when I open Eclipse to compile Worldforge(a 3-D game). How sick is that? What will really make you throw up is my system specs:

Processor: Singe AMD Turion MT-34 with scala-rate from 800MHz-1.8GHz(No overclocking)
Memory: 512MB DDR333(No Overclocking)
Video: ATI Radeon Mobile x700 128MB RAM(No Overclocking)
Network: RaLink Rt2500 Wireless G MiniPCI
VGA Port x 1 (D-Sub, 15-pin mini D-Sub)
TV-out (S-Video) Port x 1
AC'97 2.2, SoundBlaster&#8482; Compatible
Weight: 6.39 Lbs :P

---

### Post by Kilz on 2007-05-13
> **WhiteHorse said:**
> **Considering whether to use 64 bit Ubuntu?**

The short answer is no, don't do it.

The long answer is: If you want to compile programs or run a server, then 64 bit is the way to go. Some of the pitfalls with 64bit are the lack of flash support and the repositories tend to lag behind the x86. Some of the perks are compile times are dramatically faster, you can support more ram, and media encoding is a little faster if you can find 64 bit codecs.

That's my 2 cents.

Every time I see one of these FUD posts, I feel I have to respond to it. You know, I think I enjoy it. Now lets see. Flash is a problem? What alternate universe have you been living in?
1. [Nspluginwrapper install script]("http://ubuntuforums.org/showthread.php?t=425672") - This post has a script that installs the pluginwrapper and Flash for use on the 64bit Firefox browser! Click , wait a minute, restart browser, watch Flash.
2. [32bit Firefox install script ]("http://www.ubuntuforums.org/showthread.php?p=1174435") - This script installs the 32bit version of Firefox and flash, java, and mplayer plugins. No work, it just works!
The repositories lag behind 32bit ones? Could it be because there are fewer people running the 64bit version? Its a catch 22. Some geniuses cant get it through their head that they need to support the platform for it to be supported. Instead they spread FUD that drives people away! Thanks for doing your part. ](*,)

But lets see whos 2 cents we are reading. A search of your posts finds 3 today, then a few in Januarary. My your right up to date! We should all listen to someone who dosnt post for 4 months and then complains and posts FUD!
Tell you what, now that we know those 2 cents are made of wood, how about you keping them.  :D

---

### Post by LuisGMarine on 2007-05-13
Lol I think this might have been the guy in #IRC that told me Ubuntu-64bit sucks.

Anyhow, well put Kilz!  Show them FUD's who's boss!

---

### Post by david_2001 on 2007-05-13
You want flashplayer, you've got four options: First two as Kilz says, then add firefox32 in a chroot (variation of Kilz's second method) and the Windows plugin with the help of Crossover Linux.  I've got the latter two options working here.  Take a peek at the screenshot.

Feisty is the first amd64 distribution that I've tried and I found it remarkably easy to set up.  The result is a desktop that's far more responsive - it's like running Slackware but without the hassle of having to compile the applications I prefer to use 8).

What 64-bit codecs are you missing?

---

### Post by ronacc on 2007-05-13
If all he can find to complain about is that flash takes a minor effort to install and that some repositories sometimes lag a bit we are making great progress.

---

### Post by ahaslam on 2007-05-13
I've tired the 64 bit versions of Debian and Gentoo along with their popular derivatives, Ubuntu & Sabayon only to be very disappointed regarding speed & stability. I have now found Arch Voodoo 64 & all I can say is wow, if you want 64 bit this is the way to go ;)

---

### Post by insane_alien on 2007-05-13
wow, no flash. yeah thats totally a killer isn't it. i haven't even installed flash on the 32-bit version cos i use it so rarely(not at all) i'm sure theres a few thousand other people like me out there that are the same. but wait. its not even a problem since you CAN install flash on the 64-bit.

---

### Post by Neilguy on 2007-05-13
I'm a total newbie to Ubuntu and also Linux on the whole. I had earlier installed Edgy 64 and had numerous problems with getting the wireless running on my Broadcomm and flash on Firefox. But when i read about the ease of use and install on Fiesty, i decided to take the plunge,and know what.... I'm pleasantly surprised.. would be an understatement... Actually... i'm totally floored by the amazing ease of use, increase in speed and increased availability of support from such friendly users.
I would totally recommend the 64 bit Fiesty, for anybody who knows how to browse forums..

---

### Post by ronacc on 2007-05-13
> **Anthony Haslam said:**
> I've tired the 64 bit versions of Debian and Gentoo along with their popular derivatives, Ubuntu & Sabayon only to be very disappointed regarding speed & stability. I have now found Arch Voodoo 64 & all I can say is wow, if you want 64 bit this is the way to go ;)

Hmm I have Sabayon 3.3 64bit and Ubuntu 7.04 64bit both installed and they are rock stable and fast for me . What apps are you trying to run that are a problem ?

---

### Post by ahaslam on 2007-05-13
App's... if only...

Both of those systems throttled my 3.15G processor down to 2G, even after removing the relevant services & modules. Beryl & KDE went screwy on Sabayon when ran as user, though it was fine as root, strangely even new user accounts went postal. Ubuntu topped this off by completely screwing up the ext3 filesystem on its partition after only 3 days.

Enough said?

If you want a 64 bit distro for its speed potential Arch is the way to go.

---

### Post by rsambuca on 2007-05-13
As many linux users can testify to, a person's experience with a particular distro is very dependent upon their specific hardware, and the specific programs they like to run.

For you, Arch is best, for others, Sabayon, for others, ubuntu, etc...

Arch may be best for you, but to say it IS the best is nothing more than sheer arrogance and a lack of objectivity.

---

### Post by ronacc on 2007-05-13
all I can say is your experience is not normal . I had some throttling problems under edgy (6.10) byt none at all under feisty (7.04) and I have been using it since herd 2. heed the warnings about beryl and dont blame problems with it on the OS. other than that run what works for you, if arch is your game go for it. (heck I may just try it myself I've got some spare hd space).

---

### Post by Kilz on 2007-05-13
Isnt Arch 64 a pure 64bit distro, with no 32bit functionality at all?

---

### Post by ahaslam on 2007-05-13
> **Kilz said:**
> Isnt Arch 64 a pure 64bit distro, with no 32bit functionality at all?

That's right, pure x86_64 (only found that out yesterday), though 32bit libs are provided by the community. 

I'm not Ubuntu bashing, I'd used Ubuntu for a long time & I'm still here aren't I? I simply had bad experiences with the 64-bit versions of Debian Etch, Ubuntu 7.04, Gentoo 2007 & Sabayon 3.3. I only recently got a 64-bit CPU, so I'd been testing a few distro's. Judging by the loaded modules & services I suspect they're better suited to AMD rigs & perhaps that's where issues arose with my Intel. Please note that I didn't say  Arch was the best (it has its own problems), though I do recommend it if you're after performance.

I hope that cleared things up. Remember that forums often contain more opinions than facts (imo) ;)

---

### Post by Case_f on 2007-05-13
> **Kilz said:**
> Isnt Arch 64 a pure 64bit distro, with no 32bit functionality at all?

Used to be, and basically still is - if you stick to Current and Extra repositories. Arch 64 devs oficially do not support 32bit in any way except chroot. 
However, if you add the not so long ago opened Community repository, you'll get great 32bit support, better than Ubuntu, I dare to say. I'm currently running Arch 64 myself most of the time and I love it, I was amazed at how much it evolved not only as a multilib disto, but as a whole, in the few months since the last time I tried it.

---

### Post by emodro on 2007-05-14
I installed 64 bit feisty and i'm regretting it every day, I have to do alot more to get the applications I want to run, and I don't notice any performance enhancement, actually since the beryl xgl repos are so behind on the x86 versions, I  get the white cube unless I use "make copy" which slows my pc down greatly, I got ubuntu so that my pc could look a little and run a little bit more on Mac, writing C programs is alot easier, but i'm basically here for the multiple desktops and the effect where all the windows minimize so you can select one (top right mouse on beryl... i don't know the name) I had to do the firefox 32bit just so i could watch you tube.. I had to force dc++ down to 32bits... whats the point?
ps. if i'm wrong about the xgl+beryl stuff please let me know!!! (i have version 0.2)

---

### Post by gbesso on 2007-05-14
The unstable repository [here]("http://ubuntuforums.org/showthread.php?t=392156") is very up to date.

As for stable 0.3.0 packages, there aren't any because the latest release was 0.2.0
Note that beryl is in beta, even the release versions are.

Almost nobody really compiles beryl now because it is VERY unstable at the moment because they are in the process of merging the beryl and compiz codes, you won't find x86 packages easily either.

---

### Post by interval1066 on 2007-05-14
Feisty runs like a charm on my amd 64 lappy. I've found ports or warppers for everything I need to run. There is one thing lacking however that I'm surprised no one has mentioned. If you want 32-bit support on your sata disk i/o you'll have to wait. The sata drivers aren't done yet. But I'm sure that support will be along soon.

---

### Post by ahaslam on 2007-05-16
This is a strange one... Has anyone noticed a quieter rig while running 64 bit? Should this even be possible?

---

### Post by david_2001 on 2007-05-16
> **Anthony Haslam said:**
> This is a strange one... Has anyone noticed a quieter rig while running 64 bit? Should this even be possible?
Yup.  It seems that the CPU (Pentium D 820) is working less hard to do what I normally do.  As a consequence, the CPU fan - the only potential source of noticeable noise in my system - is mostly just idling along at 950 rpm.  In fact, I cannot recall it revving up to full speed at all in the two weeks since I went 64-bit.  We'll see how long the quiet lasts ;-).

---

### Post by dabl on 2007-05-16
I've got (on different hard drives) a Ubuntu Feisty 64-bit and a Kubuntu Feisty 32-bit running on my Intel Core 2 Extreme platform.  I set up the 64-bit with the low-latency kernel to do some audio work (recording off old record albums, cleaning up using Audacity and Gnome Wave Cleaner).  Here's what I've noticed in the comparison for a month now:

- Kubuntu must have been short CD space, because they ditched my Epson printer driver in going from Edgy to Feisty.  It is still in the Ubuntu installation CD. Lots of other printer drivers disappeared from Kubuntu, according to posts in their forum.
- Beryl and its windows decorators won't stabilize on 64-bit Ubuntu (I don't care, since I don't really need  it there).  It is rock solid on Kubuntu 32-bit -- it hasn't had a problem in 6 weeks.
- The only thing that will rev up my Arctic Cooler CPU fan in either OS is running an audio file through gwc.
- I ran some benchmark comparisons of a big, clunky Visual FoxPro genealogy database that I use, and proved (as if there was any doubt) that 32-bit apps actually run slightly slower under the 64-bit OS.
- Other than the intellectual satisfaction of observing that the 64-bit OS is seeing more of my 4 GB of installed RAM than the 32-bit does, I haven't figured out how to actually take advantage of that feature.

That's my 2 cents' on it.  :)

---

### Post by brennydoogles on 2007-05-16
I just purchased a new computer from dell, and i am trying to find the best version of Ubuntu for my new hardware. I have been using edgy for a few months now, and I really like it, and I have heard that Feisty is still kinda buggy. Here are my specs: Dimension E521,Athlon 64 X2 4000+ (2.1GHz,512Kx2), 2GB DDR2 SDRAM at 667MHz, 250GB SATA II Hard Drive (7200RPM), and an integrated Nvidia Video card. I am hoping to eventually get Call of Duty running under Wine, but other than that I am planning on running a pretty standard dual-boot with XP. As for Beryl and Compiz, I don't really need all of the eye candy, but if it installs easily and won't cause problems I don't mind having it. Thanks for the help!!

---

### Post by lintoolman on 2007-05-16
> **brennydoogles said:**
> I just purchased a new computer from dell, and i am trying to find the best version of Ubuntu for my new hardware. I have been using edgy for a few months now, and I really like it, and I have heard that Feisty is still kinda buggy. Here are my specs: Dimension E521,Athlon 64 X2 4000+ (2.1GHz,512Kx2), 2GB DDR2 SDRAM at 667MHz, 250GB SATA II Hard Drive (7200RPM), and an integrated Nvidia Video card. I am hoping to eventually get Call of Duty running under Wine, but other than that I am planning on running a pretty standard dual-boot with XP. As for Beryl and Compiz, I don't really need all of the eye candy, but if it installs easily and won't cause problems I don't mind having it. Thanks for the help!!

I've had Feisty (x64) on my Dell E520 for a couple of weeks now with no problems.   Granted I haven't had time to apply all of the tweakage yet, so YMMV.

---

### Post by ahaslam on 2007-05-16
Feisty is somewhere between Dapper & Edgy regards stability for me. Wine also offers a repository for that now includes binaries for x64. Many would agree that a standard Feisty install is also noticeably quicker than previous releases. Considering all of this, Feisty is the better option if you want COD to run nicely under Ubuntu (I read somewhere that it already works, worth a google). 

;)

---

### Post by jvc26 on 2007-05-20
I've actually been pleasantly surprised with Ubuntu Feisty 64. I have run both dapper and edgy 64 in the past, and the 32bit versions more recently as I didnt see much benefit for the extra effort you had to put in back then. However, now I see easy installs for the 32bit firefox (cheers killz your guide was really useful) as of yet I havent had any major issues (bar when I first installed it it was as stable as a piece of butter in a frying pan - a reinstall fixed that so Im guessing it was some messy package/bad burn/error or something, but now its pretty good stability wise and seems to me to be pretty stable and reliable.
Il

---

### Post by nss0000 on 2007-05-21
Gents:

The short answer is ... it depends.

1) If you need kit to absolutely/positively/100%bulletproof "just work" -- out.of.the.box  then install DAPPERx32.
Say ... if the woman-of-your-dreams  or ... curing cancer depended on it then x32 is your choice.

2) If you have infinite time/patience/talent/gura_pals ... or if ya just don't give a flying flip then --- by all means stumble around with U_ x64. Many of us have ..... 

3) but don't tell Big-K cause having created somany work-arounds he's real sensitive.

nss
*******

---

### Post by rsambuca on 2007-05-21
> **nss0000 said:**
> Gents:

The short answer is ... it depends.

1) If you need kit to absolutely/positively/100%bulletproof "just work" -- out.of.the.box  then install DAPPERx32.
Say ... if the woman-of-your-dreams  or ... curing cancer depended on it then x32 is your choice.

2) If you have infinite time/patience/talent/gura_pals ... or if ya just don't give a flying flip then --- by all means stumble around with U_ x64. Many of us have ..... 

3) but don't tell Big-K cause having created somany work-arounds he's real sensitive.

nss
*******

Maybe it's the programs I'm using, but I can't believe that 64bit is so tough that anyone needs "infinite time/patience...".  I am by no means a linux expert, but I don't think I have spent more than 10 or 15 minutes on any particular issue regarding 64-bit stuff.

---

### Post by strumluff on 2007-05-22
> **rsambuca said:**
> Maybe it's the programs I'm using, but I can't believe that 64bit is so tough that anyone needs "infinite time/patience...".  I am by no means a linux expert, but I don't think I have spent more than 10 or 15 minutes on any particular issue regarding 64-bit stuff.

Same goes for me, once setting up firefox32 with flash and java (thanks to Kilz's script, didn't take more than 10 minutes of my time) I never really had trouble with any other software. I run beryl on my dekstop, compiz on my laptop with xgl, without any difficulty. Any other software I required there was almost always a 64bit version, only on a couple of occasions were there only i386 debs or repos, but that didn't pose any problem as I just compiled my own version from source. 

All my multimedia worked out of the box, just installed the 64bit codecs and my fav players (vlc, xmms) and I was away. The addition of network manager in Feisty meant I didn't need a workaround to get wireless working either.

I even got wine up and running in 5 minutes before these 64bit packages came out so you really shouldn't have any problems, and should there be any you'll most likely find a solution with a quick search on the forums.

It's been running stable too and it seems noticeably faster than 32bit when compiling and on loading large apps (gimp opens almost immediately, never did before). Well thats my experience, I won't be going back to 32bit Ubuntu, Windows however may be a different story.

---

### Post by Jouke74 on 2007-05-22
Many here use the Ubuntu distro for a desktop computer, with basic internet function, mail, office stuff and playing multi media. Here 64bits can be nasty sometimes and has no real advantage. I guess I am one of the few using Ubuntu for something else: simulations of gene flow over generations. This requires a whole lot of integer calculations with large arrays of data. Here is where 64bit computing really shines: I easily gain about 2 days worth of calculation time on a single 2 "week" project as compared to 32 bit.

The nice thing about Ubuntu is that I additionally have lots of free software on my hands to program tools, use the internet during calculations, type my results, make PDFs or compile new versions of programs. Ubuntu is furthermore my favorite since I don't need to understand all of linux to get it quickly installed and running with just the things I want.

---

### Post by nss0000 on 2007-05-22
RSAM:

I do not doubt your talent. Fact is many of us x64 lusrs have run-into brick walls. Not always the same bricks and not always the same walls ... but sufficient to stop-some-task-dead.

Very different IMVHE with Dapperx32 .. where everything just-works.

BigJ:

Yep me too -- Now and then I run the 64-bit version of geo-analytic proggie GRASS on my AMD5400 / Dapperx64 kit. The program installed and functions without issue. It is VERY demanding -- with a variety of 3-D imaging tasks -- and it just ZIPPS on my x64 kit. No question here that benefit far outweighs costs. 

nss
******

---

### Post by jespdj on 2007-05-22
> **nss0000 said:**
> Gents:

The short answer is ... it depends.

1) If you need kit to absolutely/positively/100%bulletproof "just work" -- out.of.the.box  then install DAPPERx32.
Say ... if the woman-of-your-dreams  or ... curing cancer depended on it then x32 is your choice.

That isn't always true. Ubuntu 6.06 (Dapper, 32-bit or 64-bit) does not work on my hardware: there's a kernel bug that causes my DVD player to be invisible to Linux (the kernel can't handle the JMicron IDE controller on my motherboard to which my DVD player is connected). There is another kernel bug that causes the clock on my computer to run much too fast (every 30 seconds, the clock advances one minute). These bugs have been fixed in Edgy (6.10).

> 2) If you have infinite time/patience/talent/gura_pals ... or if ya just don't give a flying flip then --- by all means stumble around with U_ x64. Many of us have ..... 

64-bit Feisty runs perfectly fine on my computer; the only thing I had to tweak was the screen resolution, but that most likely is because of ATI's crappy Linux driver and doesn't have anything to do with whether I'm using the 64-bit version.

64-bit is not a lot harder to get working than 32-bit Ubuntu.

---

### Post by jusmurph on 2007-05-23
I thought half the fun of Linux was the challenge?

---

### Post by nss0000 on 2007-05-23
JES:

True. No question that HW issues constrain choice  -- actually it's lousy that UBUNTU has not 'backported' such fixes to DAPPER. I've got two HW issues on my ASUS-m2n I had to kludge.

BigJ:

Challenge? Mybad. When I want a challenge -- at my fav speckled_trout hole -- I change out my killa brass KastMaster for a Lazy_Ike.  Do you know how tough it is to cast plastic into a coastal breeze?? No fish, no bites and no mermaids calling from across the tidal.

%^] ... nss
*************

---

### Post by mrreality13 on 2007-05-23
hi all ,
im kinda a noob  compared to you all but i was readind around the fourms and saw this thread and figured i would pose my question here im running an amd x2 4200 /2 gigs ram/7600 gs pci-e on feisty  upgraded  from 6.10 (64 bit)i now have to wonder,(also using firefox 32)
 IF a fresh clean 64 bit re install will help my machine run a little better OR since it works now should i leave well enough alone?
 I do have some minor issues with not ,even after a removal and re install be able to run any torrent p-grams(i click on it and it wont even load) as well as a re occuring mouse issue(wheel up or down makes it think i right clicked)

thanx all:popcorn:

---

### Post by nss0000 on 2007-05-24
MR:

Works fine, eh? IMHO do NOT change your x32 install.

FYI: I run Dapper with two kits ... one Dx32 ( AMD2600/GB-7vt600 ) and one Dx64 (AMD5400/ASUS-m2n ) . 

I've shifted most daily work to the 64-bit kit : browser, word_processing, spreadsheets and bshell_programming. OTOH it's back to x32 if I want to play JAVA_chess as I have not got that to work on x64. There's actually one proggie (TOPSPICE) I still need to run on my seven-year-old WINME box as WINE baffles me.    

Others seem to have done much better in transitioning completely to 64-bit UBUNTU. 

nss
******

---

### Post by dyrer on 2007-05-24
I wonder why is so hard usually apps to convert to 64bit? Like flash, java etc
Everyday apps should work in both versions like windows vista. I have vista 64bit and i have Flash, java etc

---

