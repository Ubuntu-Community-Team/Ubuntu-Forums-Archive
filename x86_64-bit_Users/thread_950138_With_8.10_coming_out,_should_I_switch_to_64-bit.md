---
title: "With 8.10 coming out, should I switch to 64-bit?"
date: 2008-10-16
forum: x86 64-bit Users
---

### Post by gamelord12 on 2008-10-16
I've got a Dell laptop, Core 2 Duo, 2 GB of RAM, GeForce 8400M.  Assume everything works perfectly (as in hardware and Flash/Java), would I see an increase in performance or battery life?  Now assuming I'd have to test everything to make sure it works perfectly, is it likely that the following wouldn't work in the upgrade?

laptop LED lights for battery, wi-fi, etc.
Flash and Java in Firefox
graphics drivers
other 32-bit programs

I don't NEED to upgrade to 64-bit; I just want to know if it's usually a safe experience for the vast majority of people out there.

---

### Post by tuxxy on 2008-10-16
There will certainly be performance increases more noticeable in photo/video manipulation, virtualisation etc

Flash and Java will run just need to install the 32-bit plugin, its not perfect but neither is flash on 32-bit is it, graphics drivers and other 32-bit apps wil all be compatible, whether you will use a 32-bit app once you got it installed well thats another matter :)

---

### Post by cjm5229 on 2008-10-17
Yes, Flash 10 should be in the repos, Adobe is working on a 64 bit version but it is not out yet. Java is also available in the repos. Graphics Drivers have gotten much better since the alpha versions and should be working great by the time it goes final. I don't know about the LED's I don't use a laptop, however, My son does and he has Hardy 64 bit on it and his lights work. It also seems like there are very few apps for linux that don't have a 64bit version anymore.  If you keep a seperate /Home partition you can always reinstall 32 bit if it doesn't work for you. I switched to 64 bit with Dapper Drake and have had very few problems and what I have had, I found solutions to by just searching thes forums, using Google Linux search. Good luck and enjoy.

---

### Post by tofuconfetti on 2008-10-17
I've tried the 64 bit versions in the past and there was always some deal breaker that was just too much trouble to fix.  I tried 8.10 on an AMD AM2+ system and the performance difference it very noticeable.  So far everything works, even CUPS network printing (getting proper drivers was a problem with my printer in the past).  As the other poster mentioned, I always make my /home directory separate from the others, and I write a script to automatically install everything I want (very easy BTW), so I just leave all that in place and if something doens't work out, it only takes about an hour so reinstall and fully configure it like I want it.

I think you'll absolutely LOVE the performance difference.

---

### Post by Fatfool on 2008-10-18
> **tofuconfetti said:**
> I've tried the 64 bit versions in the past and there was always some deal breaker that was just too much trouble to fix.  I tried 8.10 on an AMD AM2+ system and the performance difference it very noticeable.  So far everything works, even CUPS network printing (getting proper drivers was a problem with my printer in the past).  As the other poster mentioned, I always make my /home directory separate from the others, and I write a script to automatically install everything I want (very easy BTW), so I just leave all that in place and if something doens't work out, it only takes about an hour so reinstall and fully configure it like I want it.

I think you'll absolutely LOVE the performance difference.
hmm... got a relatively new scanner? the Xsane version in 8.04 was still stuck on 0.95(I can't quite remember)

has it been updated in Ibex? getting the unstable version of sane to work for newer scanners is a real pain.... even when there is manufacturer support, there still doesn't seem to be a driver for AMD64. (experience with the MP220/210 where there was a 32 bit driver from canon)

---

### Post by philinux on 2008-10-18
xsane in Intrepid is version 0.995-3ubuntu2

---

### Post by steveneddy on 2008-10-18
I would run 64 bit regardless of what version of Ubuntu you were using at the time.

Why have a car capable of blinding speeds and performance and superior handling and only drive it two blocks up the street to get a soft drink and cigs on weekends?

Take advantage of your hardware and use a 64 bit OS.

---

### Post by phlembob on 2008-10-18
Hi,  Intel processors seem to do 32 bits even when run under 64 bit Operating Systems.  You need a performance utility which looks at the processing.  Yeah, the old utilities are written in 32 bit also, but that is the best I can get at the moment.  Looking at a comparison graphs of 64 and 32 bit transfers you can see that Intel processors are consistent in time verses numbers of processes.  The final products as little to no timed saved.  AMD processors show more acceleration in processing with 64 bit OS-s.  For an example, AMD may take 1.5 seconds to run 100 lines at 32 bits, then with 64 bits the same program will run in 1.25 seconds.  The difference is small enough that without an utility you won't notice the difference.  Later

---

### Post by Fatfool on 2008-10-19
> **philinux said:**
> xsane in Intrepid is version 0.995-3ubuntu2
hmm... so its the same as in hardy?

---

### Post by Fatfool on 2008-10-19
> **steveneddy said:**
> I would run 64 bit regardless of what version of Ubuntu you were using at the time.

Why have a car capable of blinding speeds and performance and superior handling and only drive it two blocks up the street to get a soft drink and cigs on weekends?

Take advantage of your hardware and use a 64 bit OS.
hmm my old 3500+ single core does crawl on 64 bits hardy...... (hell, I can't even get large flash embedded videos to play properly ie the starcraft II trailer)

so i'll probably switch to 32 bit intrepid.

---

### Post by lamborghiniwang on 2008-10-19
For some of the numerical C/C++ code that I wrote, I have seen as much as 30-50% performance increase when I switch from 32-bit Feisty to 64-bit Hardy, not sure if it is caused by different versions of gcc though.

---

### Post by sethvath on 2008-10-19
Take a look at [http://www.linuxmint.com/rel_elyssa_x64.php](http://www.linuxmint.com/rel_elyssa_x64.php) for the performance test between 32 bit and 64 bit version of linux mint. 

There is little difference between the 2, unless you plan on heavy video editing and the likes - which 64 bit will handle better. 

Want more compatability and less work arounds with java/flash etc? Stick to 32 bit.

Feeling a little more adventurous? Try out 64 bit and squash some bugs while you're at it. You learn more from fixing your own problems than mindlessly following the instructions of HOWTOs on this forum. 

To lead or be led its your choice.

---

### Post by lonoy on 2008-10-20
I have been using the Linux Mint X64 version for the past few weeks and have noticed that it is "snappier" than the 32 bit version. My programs load and close quicker than they did on the 32 bit version. 

Everything runs for me as per the 32 with the exception of Wine which I feel I can live without now anyway.

Mint X64 comes with Flash 9 which is okay by me as I seem to have trouble with some sites not recognizing version 10 anyway. The Mint forum has a work around  for the more adventurous around if you want to use version 10.

Overall I am please with my shift from a 32 to a 64 bit system.

Cheers.

---

### Post by cjm5229 on 2008-10-20
Wine should work, I have several Microsoft Apps running in wine on mine, in both Hardy, and Intrepid. I do use the Wine HQ repos though. But then, I would do that with wine even if I ran 32 bit. Just go to Wine HQ and follows the directions for Ubuntu Downloads.

PS. Flash 10 final will be in the repos for Intrepid. both 32 and 64 bit. It's fantastic, try it. Of course you Mint users will have to wait a few months for Mint to catch up.

---

### Post by lonoy on 2008-10-20
I followed the directions for the Ubuntu downloads without success over the last weekend. This page seems to sum it all up and what they are suggesting is a little above my abilities:

[http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit")

Cheers

---

### Post by morganevans on 2008-10-20
I for the record won't be installing 8.10 on my AMD 64 seeing as the kernel hasn't been fixed since I last reported the problem and I doubt it will in the next 10 days.

I tried installing the beta and after 2 hours (and 75% complete) I reset and went back to Windows.  I suggest whoever is in charge of developing AMD64 support for the new Kernel shouldn't quit their day job - or should if that's what he/she/they get paid for.

Ubuntu was once a great OS - now it just sucks.  I just wish they'd stop releasing every six months and concentrate on doing things right, which seems to be at the bottom of the agenda these days.

---

### Post by cenwesi on 2008-10-20
> **tofuconfetti said:**
> I've tried the 64 bit versions in the past and there was always some deal breaker that was just too much trouble to fix.  I tried 8.10 on an AMD AM2+ system and the performance difference it very noticeable.  So far everything works, even CUPS network printing (getting proper drivers was a problem with my printer in the past).  As the other poster mentioned, I always make my /home directory separate from the others, and I write a script to automatically install everything I want (very easy BTW), so I just leave all that in place and if something doens't work out, it only takes about an hour so reinstall and fully configure it like I want it.

I think you'll absolutely LOVE the performance difference.


Hi, can i get a copy of the script you wrote....also can you also send me a copy of how you layed out your partitions?

---

### Post by sune_cph on 2008-10-20
What problem did you report?

> **morganevans said:**
> I for the record won't be installing 8.10 on my AMD 64 seeing as the kernel hasn't been fixed since I last reported the problem and I doubt it will in the next 10 days.
.

---

### Post by jdos2 on 2008-10-20
Posted from a Lenovo X61 tablet running 8.04 in 64 bit, though I have a Dell laptop running 8.10 in the same way.

Okay. To answer the specifics:

laptop LED lights for battery, wi-fi, etc.
Flash and Java in Firefox
graphics drivers
other 32-bit programs


The LEDs work fine. I'm actually going over BlueTooth to my cell phone to get to the internet direct right now, and I have a blinking Bluetooth light- with a solid WLAN light showing me that I've no traffic (but the device is on and working). No worries. They didn't in the original 8.04 build, but with the backports, everything is good that way.
Flash is fine. Heck, I use Flashblocker to keep the amount of flash DOWN. Java is fine, too. The installation programs are smart enough to install the plugins correctly.
All my laptops on which I've installed lately use the Intel 3100 chipset for their graphics. All work fine, if a  tad slowly. WoW is out of the question, sadly.
Other 32 bit programs? XPlane runs well enough. That's a 32 bit native flight simulator of some regard. 


Now for some opinion.

I like 64 bit, but I quickly learned that the Brave New World of Linux on the Desktop is almost exactly the same as it was 15 years ago when I started. My expectations were formed from Mac OS X, and to a much lesser extent, Windows.
My laptops are almost completely useable in all ways, lacking nothing that the Windows software could provide, with the normal Linux exceptions of extreme complication of performing some of the seemingly simplest tasks. On the other hand, they do work fine, and battery life seems very much the same between all platforms.
Do NOT shy away from the 64 bit version of the OS until you've tried it. There's no reason not to, it seems, unless you have a corner case that won't be met by that version of the software.

When I started with Ubuntu I had 7.04 loaded on a Toshiba. I was excited to run it in 64 bit mode (it came with Windows Home) and immediately found I needed to compile a new Alsa, and then find and patch (and compile, of course) the not-working-so-well WLAN drivers. The hard drive gave errors in the Kernel dmesg log constantly, and Flash/Java was a True pain to install and KEEP working. Lord help me if I installed Gnash (which I did) and wasn't able to watch my YouTube because of incompatibilities.

Now? It's not like that. Alsa works better out of the box. I still do have to compile the WLAN driver, and yes, it's still a pain (veer slightly the wrong way and the driver locks the system HARD- no blinking Caps Lock!). NO errors in dmesg, and Flash/Java installed... Well, with the exception of having to download the documentation from Sun, quite smoothly. 

I'm glad everything is working as well as it does. I've not found <anything> for which there isn't a working solution in 8.04, or 8.10.

Go for it.

J

---

### Post by gmjs on 2008-10-20
Hi,

Please forgive my ignorance, but I've got a 64-bit processor and am running 32-bit Vista at the moment (through necessity rather than choice) and Ubuntu 8.04.1 32-bit.

I would like to try Ubuntu 8.10 64-bit when it is released, but wonder if the support for applications will be poor.

Does anyone know if you can run all 32-bit applications under Ubuntu 64-bit as (I think I'm right in saying) you can do with OS X Leopard?

I've seen instructions for installations using dpkg with a **--force-architecture** flag.  Is this a requirement?  I occasionally compile items from source (e.g. my wired network card doesn't work without drivers compiled from source).  Will 32-bit apps struggle to run if its dependencies were compiled for th 64-bit OS?

I'm very new to 64-bit, but would like to make use of the processor now that I've bought it!

Many thanks for any help,

Graham

---

### Post by wangmaster on 2008-10-20
> **phlembob said:**
> Hi,  Intel processors seem to do 32 bits even when run under 64 bit Operating Systems.

I'm not even sure what this means.  But if you're saying what I think you're saying, you're way way way off and you really need to understand how CPUs work before making this statement.  The Intel and AMD 64-bit capable x86_64 CPUs are not 32-bit processors.  They contain 64-bit registers and also twice as many registers than the old x86 architecture  The processors themselves are capable of 64-b addressing and operations.  We are truly dealing with 64-bit processors that also happen to be able to run 32-bit code.

Now, the performance difference that's dependent on the application.  Some heavily register dependent applications may get a performance boost just by recompiling with an optimized compiler to 64-bit.  Otherwise there are performance/overhead tradeoffs between 32-bit and 64-bit depending on the app.  In general though, most applications will not gain much by going to 32-bit.  But it doesn't make a 64-bit OS a bad choice.

Beyond this though, Linux distributions are failing to do what I think is the right thing, and that's  32-bit/64-bit multiarch environment where all libraries are built both 32-bit and 64-bit and userspace is primarily 32-bit with 64-bit userspace where appropriate.  This of course necessitates a 64-bit capable kernel, but also capable of supporting 32-bit execution.  This is what Sun has done with Solaris for years, and it's one reason why a 32-bit Java Plugin and a 32-bit flashplugin work perfectly fine with a 32-bit browser on their platform.

I have a number of gentoo x86_64 installs and a ubuntu 64-bit install, and I have to say, ubuntu's multiarch is significantly behind gentoo's.  Gentoo's in turn significantly lags behind redhat and suse's multiarch configuration.  There are just too many critical libraries (openmotif for example) that are just not available to 32-bit binaries under ubuntu that unless you enjoy hacking your linux OS, I'd say stick with 32-bit.

Ubuntu's built-in 64-bit Java plugin (the iced tea plugin) is immature and missing many of the features of the sun plugin, so in order to use Java plugin you pretty much have to go with a 32-bit browser, so some hacking is required. :).  There are alot of useful forum threads though.  Also, Sun has now committed to a 64-bit java plugin in Java 6 Update 12.  This is great.  Now if only Adobe would for flash.

---

### Post by mikewhatever on 2008-10-20
> **gamelord12 said:**
> With 8.10 coming out, should I switch to 64-bit?

No, although the things you mentioned should work, there is no compelling reason.

> **cjm5229 said:**
> Yes, Flash 10 should be in the repos, Adobe is working on a 64 bit version but it is not out yet.

Can I ask for the source of this info, or is it just an all too common wishful guessing.

> **steveneddy said:**
> Why have a car capable of blinding speeds and performance and superior handling and only drive it two blocks up the street to get a soft drink and cigs on weekends?

This comparison totally out of proportions. There was no significant speed gain (let along blinding), last time I checked Hardy64 on core2duo.

---

### Post by wangmaster on 2008-10-20
Below is taken from an adobe site.  Take it with a grain of salt since it's been there for over a year :).  But according to Adobe they're "working" on it :)


[http://labs.adobe.com/wiki/index.php/Flash_Player](http://labs.adobe.com/wiki/index.php/Flash_Player)

When will a 64-bit version of Adobe Flash Player for Linux be available?

The Adobe Flash Player team is working on support for 64-bit platforms as part of our ongoing commitment to the cross-platform compatibility of Adobe Flash Player. We have not yet announced timing or release dates.

---

### Post by mikewhatever on 2008-10-20
Thanks wangmaster, good find.

---

