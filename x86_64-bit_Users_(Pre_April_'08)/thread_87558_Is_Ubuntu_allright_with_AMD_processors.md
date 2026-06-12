---
title: "Is Ubuntu allright with AMD processors?"
date: 2005-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by eeried on 2005-11-08
Hello,

I'll have to buy a new computer in the near future, and I was wondering if AMD processors are any trouble with Ubuntu or debian-based distro. I'm thinking of
- drivers
- deb packages
-...? :confused: 

I'm rather fed up with Intel arrogance, and wouldn't mind a change.

Many thanks in advance!

---

### Post by Who on 2005-11-08
Absolutely fine! if you buy an Athlon64 then you can get Ubuntu built _just for_ that AMD processor (and you can run normal 32bit i386 Ubuntu too, if you want!)

Broadly speaking if it isn't MacOS, and it runs on an Intel x86 it will run on an AMD x86...

---

### Post by jvictor on 2005-11-08
Go ahead no problems, I'm a 64 bit user...

---

### Post by eeried on 2005-11-08
Many thanks for your swift replies.

I'm not knowledgeable at all about processors. 
You speak of AMD64, now what if I get another kind of AMD processor? -- are there any types I of AMD ought to avoid with Linux/Ubuntu?
- Are some AMD not x86 then?
- Are they all as flexible as AMD64?
- What's the drawback of run a 32-bit i386 ubuntu (the one I have been running on my Pentium II) on and AMD64? 

Sorry for being so dumm!

---

### Post by lcg on 2005-11-08
[QUOTE=eeried]
I'm not knowledgeable at all about processors. 
You speak of AMD64, now what if I get another kind of AMD processor? -- are there any types I of AMD ought to avoid with Linux/Ubuntu?
[/QUOTE]
AMD has a 64bit processor line, the Athlon 64 (and its server counterparts), which also runs normal 32bit code fine, and a 32bit only product line, the Sempron (which is supposed to also get 64bit capabilities, although I'm not sure if those have reached resellers, yet).
Either one works fine with every software running on Intel's x86.

[QUOTE=eeried]
- Are some AMD not x86 then?
[/QUOTE]
No.

[QUOTE=eeried]
- Are they all as flexible as AMD64?
[/QUOTE]
No. The Athlon 64 can execute both 64bit and 32bit code. Obviously, the 32bit Semprons can only execute 32bit code.
However, if you are not using your computer for some serious databases or simulation of fluid dynamics, IHMO 64bit is not really necessary.

[QUOTE=eeried]
- What's the drawback of run a 32-bit i386 ubuntu (the one I have been running on my Pentium II) on and AMD64? 
[/QUOTE]
Personally, I would recommend running 32bit Ubuntu, as the 64bit has some issues with closed source libraries only available as 32bit binaries (e.g. SUN Java, Macromedia Flash). Other than that, Ubuntu for AMD64 works fine.

Hope this helps to clarify,
Lars

---

### Post by eeried on 2005-11-08
Many thanks, lcg, for your explanation. yes it's much clearer to me now. ;) 

I thought I might do some video in the future, that's why I thought of an AMD64...

---

### Post by jvictor on 2005-11-08
Whether to go or not to go 64 is a matter of what u r gng to use it . 

If u r gng for graphics i'd recommend 64 bit bcoz u can get things done more faster. Again 64 bit java is a concern if u r a java programmer who wants to use Jav abut not sun's, even though there is a 64 bit implementation form Sun for linux, theres some opensrc 64 bit version of blackdown java which u can use to get things done.

Yes Flash maybe a big pain if u go for 64 bit. For me i dont visit many flash sites so it doesnt matter

---

### Post by kozimodo on 2005-11-08
[QUOTE=lcg]Personally, I would recommend running 32bit Ubuntu, as the 64bit has some issues with closed source libraries only available as 32bit binaries (e.g. SUN Java, Macromedia Flash). Other than that, Ubuntu for AMD64 works fine.

Hope this helps to clarify,
Lars[/QUOTE]
But can't 64bit Ubuntu still run 32bit programs?

---

### Post by RAOF on 2005-11-09
Yes, but you need all the necessary 32bit libraries.  This is not hard, but no where near as easy the "out of the box" performance of 32bit breezy.

---

### Post by Mayfairy on 2005-11-09
I just got myself a new machine after tackling with this old one for several years. I'm tempted to try out 64-bit version now that I'm able. No more slow machines for me. Yay! :D 
The question is, will I bang my head on my keyboard if I try to go with 64-bit or is it safer to stay in 32-bit? I've used Ubuntu for about a year now and I'm not a complete newbie, but I still can't say I know Ubuntu. 
I've read through some issues with 64-bit and it doesn't seem too bad. I can do without flash for now (I think), but is there any work around to get 32-bit flash working on 64-bit system? What about java; is there any decent, working java thingie I could use so I'd be able to use Azureus bittorrent client? 
Thanks for your answers.

---

### Post by lupine_nickt on 2005-11-09
Just to clarify; some Sempron processors (some 754 and ?all? 939 sockets) are also AMD64. I'm running one :)

xF,

...Nick

---

### Post by ThirdWorld on 2005-11-09
as far as i know it works perfectly with AMD

---

### Post by Big Venus on 2005-11-09
[QUOTE=Mayfairy]I just got myself a new machine after tackling with this old one for several years. I'm tempted to try out 64-bit version now that I'm able. No more slow machines for me. Yay! :D 
The question is, will I bang my head on my keyboard if I try to go with 64-bit or is it safer to stay in 32-bit? I've used Ubuntu for about a year now and I'm not a complete newbie, but I still can't say I know Ubuntu. 
I've read through some issues with 64-bit and it doesn't seem too bad. I can do without flash for now (I think), but is there any work around to get 32-bit flash working on 64-bit system? What about java; is there any decent, working java thingie I could use so I'd be able to use Azureus bittorrent client? 
Thanks for your answers.[/QUOTE]

No I've been waiting for 1.5 years and nothing yet. I don't even think that Macromedia thinks that 64bit is the new wave of the future. When Intel came out with Pentium D, I was hoping that they would get the hint and make it but still doesn't look like they are. But hay, you do have dchroot if it will work on your system that is. This allows you to run 32bit programs in a 32bit environment on a 64bit system and still be using a 64bit OS.

Me personally, I would get one of the new AMD64-X2 dual core 64bit chips, namely the 4000+ AMD64-X2... very expensive...

good luck on your decision.

---

### Post by WebDrake on 2005-11-09
> AMD has a 64bit processor line, the Athlon 64 (and its server counterparts), which also runs normal 32bit code fine, and a 32bit only product line, the Sempron (which is supposed to also get 64bit capabilities, although I'm not sure if those have reached resellers, yet).
Either one works fine with every software running on Intel's x86.

What about the new Turion 64 that is appearing in some laptops?


> The Athlon 64 can execute both 64bit and 32bit code. Obviously, the 32bit Semprons can only execute 32bit code.
However, if you are not using your computer for some serious databases or simulation of fluid dynamics, IHMO 64bit is not really necessary.
... but if you *are* doing some heavy number-crunching at some point, then 64-bit is a serious advantage, right?

> Personally, I would recommend running 32bit Ubuntu, as the 64bit has some issues with closed source libraries only available as 32bit binaries (e.g. SUN Java, Macromedia Flash). Other than that, Ubuntu for AMD64 works fine.
Shouldn't you be able to get round that by running a 32-bit web browser?  I seem to remember hearing that 64-bit Firefox had this problem with the Flash plugin but that if you used 32-bit Firefox it was not an issue.  It was a problem relative to the web browser, not the OS.

  -- Joe

---

### Post by RAOF on 2005-11-09
Sun releases 64bit java packages.  Azureus works fine.  They **don't** release as 64bit java browser plugin, though.

As for flash.  Yes, the browser is a part of the reason it won't work - you can't use 32bit plugins from a 64bit browser.  Getting a 32bit version of firefox to work is not that hard, though, and you can get it to think it's on a 32bit system, so it will download 32bit plugins.  The 32bit flash player doesn't quite work for me, though.  It loads, and plays the sound, but I don't get any video.

---

### Post by Nrvnqsr on 2005-11-09
[QUOTE=WebDrake]What about the new Turion 64 that is appearing in some laptops?
[/QUOTE]

I have a Turion Laptop, I ran both 32 and 64, both seem to run equally the same so far, but I'll stick with  32-bit for more compatibility for the moment

---

### Post by WebDrake on 2005-11-10
> I have a Turion Laptop, I ran both 32 and 64, both seem to run equally the same so far, but I'll stick with  32-bit for more compatibility for the moment
I guess one imperfect but possible solution would be to install 64-bit as the main OS, but then to use Xen to run a 32-bit system as a guest OS when necessary.  More complicated in principle than just installing the right 32-bit libraries and apps under 64-bit Ubuntu, but it might help keep the 64-bit system "cleaner".

Incidentally if I were to install both 32- and 64-bit versions of Firefox on 64-bit Ubuntu, would I be able to use the same profile for both?

Since I do some serious number-crunching from time to time I'd like the 64-bit performance.  Java and Flash plugins are less important to me and indeed it might be nice to go without their distracting influence for a while... ;-)

---

### Post by RAOF on 2005-11-10
[QUOTE=WebDrake]...Incidentally if I were to install both 32- and 64-bit versions of Firefox on 64-bit Ubuntu, would I be able to use the same profile for both?...[/QUOTE]
Yes.  Although, you might not want to mix version numbers too much.  For example, I'm running the Ubuntu packaged 64bit firefox (1.0.7) with the 32bit firefox 1.5RC1 from mozilla.org.  They share my profile almost perfectly, but it seems that 1.5RC1 has slightly messed up the layout for my 1.0.7 (there's a thick grey bar at the bottom of the window).  Sticking to **released** versions of firefox, you shouldn't have a problem ;)

---

### Post by ThirdWorld on 2005-11-11
Im also thinking in buying a new laptop, I want a 64 bits. Do you guys think dapper drake developers will release a solution to this problem next year? mmm a 32 bit emulator or something more ingenious? or is just a 3rd party problem that they are not supposed to fix?

---

### Post by BoyOfDestiny on 2005-11-12
[QUOTE=ThirdWorld]Im also thinking in buying a new laptop, I want a 64 bits. Do you guys think dapper drake developers will release a solution to this problem next year? mmm a 32 bit emulator or something more ingenious? or is just a 3rd party problem that they are not supposed to fix?[/QUOTE]

just follow the chroot howto floating in these forums. I was shocked how simple it was (got it setup plus installed my zsnes deb, in under 20min...). Anyway, [I think] as more time passes either things will be ported/run better, or they will add more ia32 libs like they do with open office now.

---

### Post by Ryba on 2005-11-13
[quote=WebDrake]Shouldn't you be able to get round that by running a 32-bit web browser? I seem to remember hearing that 64-bit Firefox had this problem with the Flash plugin but that if you used 32-bit Firefox it was not an issue. It was a problem relative to the web browser, not the OS.[/quote] No. Using 64-bit version of ubuntu is not as smooth of a user experience as it sounds here.

I have used the 64-bit for like 4 or 5 months now (and will still continue to). It is missing wmv codecs. Of course at least up until 2 months ago the 64bit version of windows xp was also missing those :rolleyes:

Also, flash plugin has not yet been ported over for amd64. Macromedia has put out a job position or 2 for this specific purpose (to port flash 8 over to linux x86 and amd64) but nobody has filled that position yet. They have promised to support it as soon as they are able to however.

Running firefox 32bit under the 64bit kernel does not work. You would think it would but they hardlinked (at least the one you can download from [www.mozilla.org]("http://www.mozilla.org") does) the dynamic library paths which cause it to find the 64bit libraries and then blow up on startup. But I only tried the 1.5beta version. Not sure about the stable 1.0.7 but I would presume it has the same issue.

Almost all emulators are not available (including wine and zsnes).

If you use Cisco VPN software that won't work (fortunately the open source vpnc is craploads better anyway hehe).

Hope that gives you an idea. I use 64bit linux and play games and everything on it just fine. I love it, it IS faster and noticably for day to day tasks (compared to 32bit linux install on the same system). Games and other big tasks take the same amount of time. No noticable difference. Of course your milage may vary depending on what the support cast of hardware components to go along with your system may be.

---

### Post by BoyOfDestiny on 2005-11-13
[QUOTE=Ryba]No. Using 64-bit version of ubuntu is not as smooth of a user experience as it sounds here.

I have used the 64-bit for like 4 or 5 months now (and will still continue to). It is missing wmv codecs. Of course at least up until 2 months ago the 64bit version of windows xp was also missing those :rolleyes:

Also, flash plugin has not yet been ported over for amd64. Macromedia has put out a job position or 2 for this specific purpose (to port flash 8 over to linux x86 and amd64) but nobody has filled that position yet. They have promised to support it as soon as they are able to however.

Running firefox 32bit under the 64bit kernel does not work. You would think it would but they hardlinked (at least the one you can download from [www.mozilla.org]("http://www.mozilla.org") does) the dynamic library paths which cause it to find the 64bit libraries and then blow up on startup. But I only tried the 1.5beta version. Not sure about the stable 1.0.7 but I would presume it has the same issue.

Almost all emulators are not available (including wine and zsnes).

If you use Cisco VPN software that won't work (fortunately the open source vpnc is craploads better anyway hehe).

Hope that gives you an idea. I use 64bit linux and play games and everything on it just fine. I love it, it IS faster and noticably for day to day tasks (compared to 32bit linux install on the same system). Games and other big tasks take the same amount of time. No noticable difference. Of course your milage may vary depending on what the support cast of hardware components to go along with your system may be.[/QUOTE]


Agree with most of what you said here. But you can certainly run 32-bit firefox and 32-bit zsnes... if you use chroot :). There is a simple howto here on the forums (was for hoary, but pretty much the same just substitute breezy), and I had them running [first try at chrooting] in about 15min. 

Ubuntu and Linux in general can be a rough ride or smooth as silk, it just varies (architectures not withstanding). I can assure the curious that one can run many 32-bit apps successfully in a chroot. If things don't work like they should, by all means wipe ubuntu 64 and put the 32-bit version.

Also there is dosbox, fceu, stella, vice, dgen, visualboyadvance, snes9x etc... It seems most emulators [in the Ubuntu Repos] are available for 64-bit.

EDIT: Here is a picture of zsnes (32-bit) running on my breezy 64-bit. It has sound, smooth graphics, works with my usb psx gamepad adapter, etc. As good if not better than the windows version I started with (well actually started with their dos version)

[[IMG]http://img387.imageshack.us/img387/3529/mydesktop6fw.th.jpg[/IMG]](http://img387.imageshack.us/my.php?image=mydesktop6fw.jpg)

Summary:
Give it a go! Not everything may run natively in 64-bits! If not try the 32-bit version, try it in chroot, or dual boot, or just stick to 32-bits! Linux is about choice!
Have any trouble, and the kind folk on the forums will lend a hand!

---

### Post by crypto178 on 2005-11-13
I purchased an amd64 recently but I didn't upgrade from ubuntu i386 yet. I've been thinking about switching lately though (not really for performance but I like tinkering). A few questions remain :
Is it possible to "dist-upgrade" to ubuntu 64? Otherwise it's not a problem I'll download the iso.
The chroot trick doesn't appeal to me much, but I've seen posts like this one - [http://ubuntuforums.org/showthread.php?t=72984](http://ubuntuforums.org/showthread.php?t=72984) - which, to me, sound much more sensible. I guess that the same method is possible for firefox, flash and mplayer-plugin too, are there any HOW-TOs on the subject? I'm using the firefox beta and not the one from the repositories already so it wouldn't be a big change.

---

### Post by estel on 2005-11-13
No, a dist-upgrade is not possible - a full reinstall is necessary.

---

### Post by Teroedni on 2005-11-13
Amd have zero problems with Ubuntu:)
I have both the older amdxp and the newer turion ml30(Desktop)

My xp is running Ubuntu Perfect

On my Turion i ran fist 32 bit and i ran perfectly.
Then i changed to 64 bit and have had none problems :)
I think the 64bit version is faster, but it is hard to say without benchmark.
I also think gcc works much faster on 64bits, (correct me if i wrong).
If you can , buy a dual core Itis the future;)
I will buy one myself when i have more money, but i have to wait a little:(

---

### Post by Ryba on 2005-11-14
[quote=Teroedni]Amd have zero problems with Ubuntu:)[/quote] You don't run enough stuff or you are not a newbie user (probably both :razz:)

[quote=Teroedni]I also think gcc works much faster on 64bits, (correct me if i wrong).[/quote] If you are referring to gcc 4.0 then yes. Especially if you are comparing it to 32bit apps compiled with gcc 3.4. The performance boost is probably close to around 30%. Otherwise you're wrong but here have a gold star :KS

[quote=Teroedni] If you can , buy a dual core Itis the future;)[/quote] Ah yes lots of money to geek out your system in ways you will hardly use and not benefit from really. Hey, I hear quantum computing and optical networking is the future as well, you should get in on it early hehe.

Seriously though, yeah it is very nice and quite impressive but for 90% of the users I'd bet (gamers included) it is nothing more then a big waste of money.

---

### Post by Ryba on 2005-11-14
[quote=BoyOfDestiny]Agree with most of what you said here. But you can certainly run 32-bit firefox and 32-bit zsnes... if you use chroot :).[/quote] This I know but that is not the same thing really and I'm sure you know it. The author of this post asked a simple thing and my point to him was that he should probably go with the 32bit install if he wants no hassles or the 64bit install if he is willing to accept that he will have to do a bit of work for various things.

chrooting is work (and not always an option for everyone on your computer if you are trying to keep it safe from the lethal hands of your children or SPOUSE :o). you still have to setup the chroot system for instance it doesn't just magically exist for you to use ... though I have always been curious as to why ubuntu doesn't have a package that sets up a core 32bit chrootable environment (or maybe they do and i just have not noticed it:confused:)

---

### Post by RAOF on 2005-11-14
[QUOTE=Ryba]...Running firefox 32bit under the 64bit kernel does not work. You would think it would but they hardlinked (at least the one you can download from [www.mozilla.org]("http://www.mozilla.org") does) the dynamic library paths which cause it to find the 64bit libraries and then blow up on startup. But I only tried the 1.5beta version. Not sure about the stable 1.0.7 but I would presume it has the same issue....[/QUOTE]
Ha!  I now have a [howto]("http://www.ubuntuforums.org/showthread.php?t=90106") to refute this (at least for 1.5RC2) :).

---

### Post by Teroedni on 2005-11-15
[QUOTE=Ryba]

 Ah yes lots of money to geek out your system in ways you will hardly use and not benefit from really. Hey, I hear quantum computing and optical networking is the future as well, you should get in on it early hehe.

Seriously though, yeah it is very nice and quite impressive but for 90% of the users I'd bet (gamers included) it is nothing more then a big waste of money.[/QUOTE]

quantom  dribble:P

The dual core technology is beimg very much debated this day.But your right i does depend on what you will use it on.
Sorry if i let my feelings run away:P

My recomendation would be to get sempron if your not require too much of the cpu. Sempron is more than powerfull enough anyway and can be clocked if your need more performance

If your want a powerfull machine for example for hard work:Folding compiling and stuff dual core is the way.

But note that this is what i mean;)

---

