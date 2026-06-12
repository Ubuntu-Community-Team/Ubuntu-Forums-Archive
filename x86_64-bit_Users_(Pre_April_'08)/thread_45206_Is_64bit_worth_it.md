---
title: "Is 64bit worth it ?"
date: 2005-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by phantom on 2005-06-29
I just received my shipment with Ubuntu CD's  :) 

The funny part is that they arrived before my Mandrake 10.1 Powerpack got here, and they announce 3-4 days delivery compared to 6 weeks delivery with Ubuntu  :-? 

Anyway,

I'm hesitating now to pop in the 64bit cd and reinstall but is it worth it ?

How are the repositories, I mostly need stuff like:

- KDE 3.4.(1)
- OpenOffice 2.0
- DVD and Music ripping/authoring (DVD, DivX, Xvid, Mp3)
- CD/DVD Burning (K3B)
- Pan
- Ndiswrapper (I have 64bit drivers for my wifi card)
- ATI Drivers
- Point2Play / Cedega

Are there any slowdowns for runnin stuff in a Chroot env, like for example 32bit games with Cedega?

Thanks for the help  :razz:

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=phantom]
How are the repositories[/QUOTE]

Best in the land. But you have to deal with the chroot stuff.

---

### Post by phantom on 2005-06-29
Thanks :D I know they're great, I had Ubuntu installed for a while but I've been testing Mandrake up 'till now.

What I ment was, how are they compared to the I386 repo's ?

---

### Post by Big Venus on 2005-06-29
[QUOTE=poofyhairguy]Best in the land. But you have to deal with the chroot stuff.[/QUOTE]
Try is the more logical word, because I can't get the chroot to stop crashing the system, so I had to reinstall the whole OS, just to get rid of it.

For Gaming and Graphics, yes it is worth it. And besides you have to love the more faster operations than a 32bit one has. Heck, it loads most things directly into physical memory and then you go out and they are right there for you to use.

I'll give you this analogy used by Apple to convince people to buy the 64bit G5 chips,

running in 32 bit versus 64bit is like drinking a glass of water versus the Niagra Falls...

(32bit being the glass of water and 64 bit the falls)

---

### Post by bassgoonist on 2005-06-30
[QUOTE=Big Venus]Try is the more logical word, because I can't get the chroot to stop crashing the system, so I had to reinstall the whole OS, just to get rid of it.

For Gaming and Graphics, yes it is worth it. And besides you have to love the more faster operations than a 32bit one has. Heck, it loads most things directly into physical memory and then you go out and they are right there for you to use.

I'll give you this analogy used by Apple to convince people to buy the 64bit G5 chips,

running in 32 bit versus 64bit is like drinking a glass of water versus the Niagra Falls...

(32bit being the glass of water and 64 bit the falls)[/QUOTE]
 last time I tried drinking from a water fall I almost drowned...

---

### Post by Optimal Aurora on 2005-06-30
[QUOTE=bassgoonist]last time I tried drinking from a water fall I almost drowned...[/QUOTE]
You know what Venus meant, come on... Yes, personally I can imagine drowning, but the speed is there and it is really cool to use, but then I will tell you like someone told me, "...it is not always wise to have the lastest and greatest if you don't understand how to use it and aren't willing to make a few sacrifices to use it..." So in some ways it is up to you...

---

### Post by bassgoonist on 2005-06-30
I fail to see how having 64 bits will inherently make everything faster...
twice as many registers...
tons more memory addresses...
I just seems for some applications it will be slower not faster.

---

### Post by Optimal Aurora on 2005-06-30
[QUOTE=bassgoonist]I fail to see how having 64 bits will inherently make everything faster...
twice as many registers...
tons more memory addresses...
I just seems for some applications it will be slower not faster.[/QUOTE]
because instead of having to take 4 cycles to do something the 64bit AMD actually does it in 1 or 2 cycles... From another thread on this forum or on this thread, a person said they had memory usage problems, in fedora I haven't noticed those memory problems, heck for that matter not even in ubuntu...

Another reason 64bit is faster, is because it allows for more accurate calculations of floating point math (graphics are excellent).

And yet another is, even if you don't use 6 or 8 or 1.2 TB of RAM you can still see the advantages because the AMD64 has built-in buffer overrun protection...

For me personally, I do agree that you don't need 64bit for office or web surfing, but its at least safer to use the 64bit for surfing and office work because you don't have to worry about having problems like I had when I was using my old 32bit system about you don't have enough memory left use this program or you have actually ran out of virtual or swap space... So that is what I like about...

---

### Post by Kuolio on 2005-06-30
Yes. It's worth it. Support for 64bit is getting better (seems like)almost every day :) Those nasty few things I need chroot are for video and dvd-playback, and to use java1.5. Oh, and firefox with flash.

I havent had any problems with using chroot, its quit easy and straight-forward to set up and use. In the future chroot will slowly (hopefully faster) die and fade away. Thats just bcause all new PC's are soon gonna come equipped with 64bit processors, both amd and nvidia are shipping even budget processors with 64bit support (Celerons and Semprons).

---

### Post by subterrific on 2005-06-30
I've done work to get cedega running in 64bit without needing a chroot. I run a 64bit kernel w/ no chroot and I play Half-Life 2 and CS:Source. However, lately I've been thinking about moving to Fedora Core 4 or using a 32bit kernel because the speed difference isn't all that great compared to the amount of work it takes to maintain a 64bit machine. I've been missing things like mplayer w32codecs, flash, java plugin, wine, etc. just working instead of taking a ton of hacking.

see this thread for my work getting cedega running without a 32bit chroot:
[http://ubuntuforums.org/showthread.php?t=16143](http://ubuntuforums.org/showthread.php?t=16143)

---

### Post by Malbojia on 2005-07-01
Well whats this chroot business here. i must of kept myself out of the loop once more. but if someone can explain it or give a link then i'd know cuz yikes having the chroot for many things. I a *nix OS in all just takes 20 minutes to install and a bloody week to get it working how you want it lol

---

### Post by bassgoonist on 2005-07-02
[QUOTE=Kuolio]Thats just bcause all new PC's are soon gonna come equipped with 64bit processors, both amd and nvidia are shipping even budget processors with 64bit support (Celerons and Semprons).[/QUOTE]
Eeeer....uuuuuhm...wow man. I think you lost most credibility in this discussion right there. ](*,)

---

### Post by Big Venus on 2005-07-03
[QUOTE=bassgoonist]Eeeer....uuuuuhm...wow man. I think you lost most credibility in this discussion right there. ](*,)[/QUOTE]
You know that he or she is right even though they had that mistake show, they meant AMD64, IA-64 (extreme edition P4 might as well be the same cheap thing), Opteron, Turion, etc...

---

### Post by jon_gunnar on 2005-07-11
[QUOTE=phantom]I just received my shipment with Ubuntu CD's  :) 

The funny part is that they arrived before my Mandrake 10.1 Powerpack got here, and they announce 3-4 days delivery compared to 6 weeks delivery with Ubuntu  :-? 

Anyway,

I'm hesitating now to pop in the 64bit cd and reinstall but is it worth it ?

How are the repositories, I mostly need stuff like:

- KDE 3.4.(1)
- OpenOffice 2.0
- DVD and Music ripping/authoring (DVD, DivX, Xvid, Mp3)
- CD/DVD Burning (K3B)
- Pan
- Ndiswrapper (I have 64bit drivers for my wifi card)
- ATI Drivers
- Point2Play / Cedega

Are there any slowdowns for runnin stuff in a Chroot env, like for example 32bit games with Cedega?

Thanks for the help  :razz:[/QUOTE]

I just installed the AMD64 version and it works great. But as soon you want something that is not on the cd your'e out of luck. I got no sound, no dvd support, no nothing. I really likes Ubuntu, but I will probably make a switch to FD Core 4. I need a working system.

---

### Post by Jet2k5 on 2005-07-11
Well I don't know how that is going to work, but it's going to take sometime in your part to get things to work.  When I still my 64-bit version on my new system I'm going to stick to it no matter what.  Making sure that I write down all my problems and all the solutions to it.  I feel that if I want to work I have to contribute, which I'm going to do by helping out with bug tracking and also keeping and eye out here on the forums  .

---

### Post by jon_gunnar on 2005-07-12
[QUOTE=Jet2k5]Well I don't know how that is going to work, but it's going to take sometime in your part to get things to work.  When I still my 64-bit version on my new system I'm going to stick to it no matter what.  Making sure that I write down all my problems and all the solutions to it.  I feel that if I want to work I have to contribute, which I'm going to do by helping out with bug tracking and also keeping and eye out here on the forums  .[/QUOTE]

I have been using linux in dualboot with windows since -97. Linux have been used for everything except movie work where windows have been easier. I've used linux for it's stability, ease of use and so on.
But like it is now, you feel a little stupid with the brand new system not being able to print out a document, if I try, the whole system hangs solid. And it's a plain simple HP 1100 printer.
And java is importent for me. I don't blame Ubuntu for anything of this, it's a great distro.
But like it is now, I don't trust the system, and that is a first for me with linux.

---

### Post by mfoulon on 2005-07-17
[FONT=Verdana][SIZE=2]I'm new to linux for the most part, but I'm not new to the AMD 64 athlon and it's perfomance as I work on such a system for almost a year now. Actually to be honest, I don't experience a lot of speed difference when working on a 32bit or 64 bit system in a plain office working environment. Not under Windows XP 32 bit versus 64 bit or under Linux installations. Actually, until now I found that I experience the Windows XP 32 bit system as faster than linux 64 bit installations like SUSE and now for instance Ubuntu. The actual speed experience depends on quite a lot of issues and the processor is only one of them. Actual speed experience usually is quite different from benchmarks of testing programs so my advice would be, just try installing different distro's and don't go for the numbers but for the actual experience of the system.

**Maurice Foulon**[/SIZE]

[SIZE=1]Teacher in Human Technology at the School of Engineering
Groningen, the Netherlands.[/SIZE][/FONT]

---

### Post by Flac on 2005-07-17
is it worth it. I think so. yes, things arent supported well atm. But umm... Just to remind you... This is err, linux after all. Support comes from enough people choosing to stick with it and get things supported. Why should anyone waste time creating applications that may/may not be used.

 Look at tamir(who i may even venture to say, is THE man), He's taking requests and popping out new 64 bit packeges all the time. If you've got a prog you need, you'll get support for it. Maybe not today, maybe not tomorow. But you will get it. if everyone just say's "theres no support, whats the point" then there will never be support.

Anyway, This is just my humble opinion on the matter. 64 bit ubuntu is pretty rocking. :)

---

### Post by fistfullofroses on 2005-07-17
[QUOTE=phantom]I just received my shipment with Ubuntu CD's  :) 

The funny part is that they arrived before my Mandrake 10.1 Powerpack got here, and they announce 3-4 days delivery compared to 6 weeks delivery with Ubuntu  :-? 

Anyway,

I'm hesitating now to pop in the 64bit cd and reinstall but is it worth it ?

How are the repositories, I mostly need stuff like:

- KDE 3.4.(1)
- OpenOffice 2.0
- DVD and Music ripping/authoring (DVD, DivX, Xvid, Mp3)
- CD/DVD Burning (K3B)
- Pan
- Ndiswrapper (I have 64bit drivers for my wifi card)
- ATI Drivers
- Point2Play / Cedega

Are there any slowdowns for runnin stuff in a Chroot env, like for example 32bit games with Cedega?

Thanks for the help  :razz:[/QUOTE]
 IT IS ONLY WORTH IT IF YOU ARE WILLING TO PUT IN SOME EFFORT!
though most of us have found this effort to be rewarding.
:-)

---

