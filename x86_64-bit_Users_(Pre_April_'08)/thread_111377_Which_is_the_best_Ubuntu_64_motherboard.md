---
title: "Which is the best Ubuntu 64 motherboard?"
date: 2006-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by vph on 2006-01-02
Which is the best Ubuntu amd64 motherboard?

Thanks,

---

### Post by bonzodog on 2006-01-02
most mobos should work with ubuntu 64 just fine, but I always err on the side of caution and avoid ATI hardware (gpu's included). I built my system with linux in mind as it's primary OS, so it is all nvidia hardware. (MSI Nforce 3 mobo, with onboard GBLan, and Sound, and Nvidia Geforce 6200GT 256MB Graphics Card).

---

### Post by handy on 2006-01-02
Who would dare say what is the best board :p 

My Gigabyte GA-K8NS Ultra-939 


[http://www.giga-byte.com.au/Motherboard/Products/Products_GA-K8NS%20Ultra-939.htm](http://www.giga-byte.com.au/Motherboard/Products/Products_GA-K8NS%20Ultra-939.htm)

is not cutting edge - nForce-3 & AGP - but it is fast & reliable, I have had **NOT** a spot of trouble with Ubuntu, the initial install was aware of the motherboard chipset, & everything on it except for the video capture card (probably?  I've not persued that as yet).

The graphics card is primarily responsible I know, but my rig runs UT2K4 in 1600x1200 with everything maxed out in the setup. With LOTS of action the framerates are always fast & smooth.    

If you are looking to play 3D games, the graphics card & probably lots of ram, is probably more important than mainboard & cpu speed.

I've not looked at the difference in price for an nForce-4, PCI-x board, you can save money & loose very little by staying just behind the cutting edge...

Good luck, you really would be hard pressed to make a bad choice these days.  :p 

handy

---

### Post by bmk789 on 2006-01-02
Asus A8N-SLI Premium

works perfect, great performance

---

### Post by hdownin on 2006-01-03
[QUOTE=bmk789]Asus A8N-SLI Premium

works perfect, great performance[/QUOTE]

I have the same mb but trying to install any distro my puter keeps rebooting. I want to install breezy. Any help for this newb would be great.

---

### Post by wjp.reg on 2006-01-03
I went the nVidia route as well :)

Gigabyte GA-K8N51GMF-9
Socket 939 / Athlon 64 3200
GeForce 6100/ nForce 430 Chipset
onboard GB LAN
onboard ALC880 HD Audio (not running) 
onboard nVidia 6100 VGA (using nVidia driver 1.0-8178)

economy system running "cool and quiet"

---

### Post by dabang on 2006-01-10
I think you shouldn't have any problems with nForce chipset and nVidia based graphics card. I'm using ASUS A8N-E mobo (nForce4) and Gigabyte graphics card with GT6600 chip - works great. Everything worked out of the box, tried several distros. Only Debian 3.1 would have let me choose the network card module manually, but it worked then!

---

### Post by batteries on 2006-01-11
I'm not having any out ot the ordinary issues with my Epox EP-9NPA+Ultra which is an nForce4, onboard sound works fine, same with LAN.. though I think i'm going to just end up using the 32 bit version of kubuntu since all the chroot stuff and work arounds i feel turn into a pain sometimes..

---

### Post by Aphorism on 2006-01-11
Perhaps an easy answer is to rephrase the question:

Who do you want to support?  Who utilizes truly open chipsets?

While both NVidia and ATI work with Linux, they are NOT open.  Unfortunately, we have no alternative if we wish to use 3D accelleration.  If you purchase one of these products, please send email telling them that you want a completely open driver -- no binary blobs.

If you do this, and they eventually comply, we will no longer be worrying about problems with 'their' drivers, as the community can develop our own.  And when a new chip appears on the market, guess who will have it working first?  Speak up.


[http://www.openbsd.com/amd64.html#hardware](http://www.openbsd.com/amd64.html#hardware)
[http://www.openbsd.com/i386.html#hardware](http://www.openbsd.com/i386.html#hardware)

The above are two good listings showing you exactly what chipsets have either been 1) reverse engineered, or 2) released documentation in full.  If it works with OpenBSD, developers have access to the documentation and specifications.

---

### Post by bannerboy on 2006-01-11
I just bought a cheep motherboard and it works just fine. for audio/networking nVidia works, as does VIA, and Realtek. Linux is just getting better, and most motherboards are now supported. If you are REALLY worried that it won't work on linux, buy a motherboard that uses either nVidia, or VIA. if you are going to purchase one that has built in sound, Realtek sound chips work well.

---

### Post by linix on 2006-01-11
Hiya,

           I just thought i would post my working board up to add to the list, The sound worked straight away although i do not know which settings to use or not to use in volume control, i have OS sounds and have played a cd in the dvd, i have the digital 2pin cable from the back of the drive to the card. i have not tryed the tv card yet and i cannot play music or vid streams from the BBC site but i understand i have to enable them somehow as i only installed the ISO download to CD.

   Nick
ps, i only have linux on my best computer, it is not on the gigabit one.

---

### Post by Bandit on 2006-01-11
You shouldnt have any issue with a good quality brand and a VIA chipset.:KS

---

### Post by datacles on 2006-01-11
[QUOTE=bmk789]Asus A8N-SLI Premium

works perfect, great performance[/QUOTE]

I bought the same board and the documentation is the die for!  In fact, I refered to ASUS's manual for the motherboard to install all of the other components.  The only problem I have had is the ATI video card I bought.  Once I pulled it out and stuck in an old PCI Nvidia.... smoothness.  I have discovered though that a few of the apps I'm used to using or their plug-ins may not support 64 bit architecture.  Of course, being new to Linux is probably 98% of my problem.  But that'll change!

---

### Post by tooCanad on 2007-02-02
Biostar GeForce 6100-M9.
AMD Athlon 3700

Ubuntu 6.10

Worked pretty much out of the box. Nvidia video & RealTek audio.  Needed to do a little futzing to get nvidia recognized. More related to stupidity than the mobo.

---

### Post by pseudonym on 2007-02-03
Dunno about 'best', but I use the [Abit KN9 Ultra]("http://www.abit.com.tw/page/au/motherboard/motherboard_detail.php?pMODEL_NAME=KN9+Ultra&fMTYPE=Socket+AM2"), which was well reviewed by [this Linux hardware site]("http://www.phoronix.com/scan.php?page=article&item=530&num=1"). My last 3 systems had ASUS motherboards, but the current crop of their boards didn't have a 'performance mid-range' one that I liked. I was interested in the [M2N-E]("http://au.asus.com/products4.aspx?l1=3&l2=101&l3=308&model=1181&modelmenu=1") model, but noticed lots of people having nasty RAM compatibility issues with it, plus it doesn't work with DDR2-800 which I may upgrade to later. So I switched to Abit this time.

The default kernel in Edgy wouldn't boot without the 'noapic' option, but I very quickly built and installed a 2.6.19 kernel from kernel.org and everything worked fine after that.

Also, the onboard Realtek ALC883 HD audio wouldn't play well with ALSA until I set a special module option for it. But I've since installed a specialised dedicated sound card anyway.

Other than that, no problems at all. Everything is smooth, fast, and hassle-free.

---

### Post by cmost on 2007-02-03
I would urge users to avoid the ASUS K8V-X SE motherboard like the plague.  In fact, I would urge users to just avoid ASUS entirely.  The aforementioned motherboard has a serious flaw when it comes to running 32 Linux operating systems.  I don't fully understand how the bug works, but, suffice it to say you won't be able to use AGP and 3D acceleration via nvidia's proprietary driver is buggy.  AIGLX also does not work (XGL will though.)  With a 64 bit operating system, this bug is irrelevant and the MB works great.

---

### Post by John.Michael.Kane on 2007-02-03
Im running a Biostar T-Force 6100 939,and everthing on it works out the gate.

To the OP the bottomline is that the best board is one you find that fits all your needs,and works as you need it. 

Sure the endusers here all have fine board and setups,however their boards may not have all the options you may need.

Your best bet make a list of four to six boards that you like,and post that list in this thread.

---

### Post by fabertawe on 2007-02-05
> **cmost said:**
> I would urge users to avoid the ASUS K8V-X SE motherboard like the plague.  In fact, I would urge users to just avoid ASUS entirely.  The aforementioned motherboard has a serious flaw when it comes to running 32 Linux operating systems.  I don't fully understand how the bug works, but, suffice it to say you won't be able to use AGP and 3D acceleration via nvidia's proprietary driver is buggy.  AIGLX also does not work (XGL will though.)  With a 64 bit operating system, this bug is irrelevant and the MB works great.

That's interesting. I'm using a K8V-X. I never tried the 32bit version and 64bit Ubuntu works great, like you say. I also have an Asus GeForce 6800 and have found their customer support to be non-existent.

Paul

---

### Post by kuja on 2007-02-05
> **bmk789 said:**
> Asus A8N-SLI Premium

works perfect, great performance
I second that board.

---

### Post by dad311 on 2007-02-05
Asus 8AN5X.  Bought it @ newegg.com 35.00 open box.  This is one of the best boards Ive ever purchased.  Lots of BANG for the BUCK.

---

### Post by PhatKat on 2008-05-17
Am writing this on my shiny new buntu box which i assembled 3 weeks ago :P 
Biostar K8M800AM2 mobo, had to ask for help to get above 800 x 600 resoulution in Hardy but everything else works out of the box!I was thinking of a 478/939 project but looking at prices for used entry level dualcores i went for an x2 4000+ brisbane...

---

