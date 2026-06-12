---
title: "64 Bit advantages"
date: 2006-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Garfield360 on 2006-08-15
Hi, im sorry if this has copyed other posts but i was wandering what the benefits of the AMD 64 bit version on ubuntu is over the standard desktop version:confused: 

Many thanks

---

### Post by Kilz on 2006-08-15
> **Garfield360 said:**
> Hi, im sorry if this has copyed other posts but i was wandering what the benefits of the AMD 64 bit version on ubuntu is over the standard desktop version:confused: 

Many thanks

For the most part I think its slightly faster in common tasks. In some applications there is a 30% speed improvement. Things that do number crunching like encoding, 3modeling, etc. That's because you are using your 64bit chip with 64bits of data not 32bits.
It would be like taking an 8 cylinder car and making it run on all 8 , or taking the spark plugs out of 4 of the cylinders and running it. You will get more power with the 8.

---

### Post by Garfield360 on 2006-08-15
cheers, would non-64bit applications see any imporvement?

---

### Post by Kilz on 2006-08-15
> **Garfield360 said:**
> cheers, would non-64bit applications see any imporvement?

32bit applications will run on amd64 ubuntu. But no, they are 32bit so they wont see any improvement. Maybe they will load faster because the os is 64 bit. But there are not a lot of 32bit appliacions needed on the amd64 version. Most of the applications are 64bit.

---

### Post by azmrb on 2006-08-15
It is my understanding that the amd64 kernel is inherently SMP so you get multiple processor support if you have the right hardware.

The 32 bit kernels are only SMP if you install one specifically compiled
for SMP support.

I am NOT an expert but that is my understanding and is why I decided to go
with amd64 even though I knew a fair number of 32bit apps wouldn't work or would need massaging.

---

### Post by Kilz on 2006-08-15
> **azmrb said:**
> 
I am NOT an expert but that is my understanding and is why I decided to go
with amd64 even though I knew a fair number of 32bit apps wouldn't work or would need massaging.

That is FUD. For the common applications there is no difference that I can tell, and I have both running on my network. To save typing , this is from another post of mine

There really isnt that big a difference in the amout of packages
According to launchpad:
Amd64 has 18609 binary packages
i386 has 19029 binary packages
Its hard to tell exactly if anything is missing because some of the packages for i386 may not be needed for the amd64 platform. They may be libraries that have been combined or are not needed.

The difference is 420, or 2% of avaiable packages.

---

### Post by azmrb on 2006-08-15
> **Kilz said:**
> That is FUD. For the common applications there is no difference that I can tell, and I have both running on my network. To save typing , this is from another post of mine

There really isnt that big a difference in the amout of packages
According to launchpad:
Amd64 has 18609 binary packages
i386 has 19029 binary packages
Its hard to tell exactly if anything is missing because some of the packages for i386 may not be needed for the amd64 platform. They may be libraries that have been combined or are not needed.

The difference is 420, or 2% of avaiable packages.

Well if you install amd64 and you want ( Flash, Java plugins, streaming multimedia... wmv, Real,... ) you are in for a long haul.  First to install a 32 bit version of FF, then follow the howtos of forcing forementioned browser addons to work. 

Don't get me wrong it is doable, I did it.  But what I was trying to tell the original poster was after all that work I ended up with a 32bit browser running 32bit plugins and forcing 32bit architecture application installs and I am not certain that at this point I can tell the difference between speed, reliability, or usability between 32 and 64bit Ubuntu.

No FUD there at all!

---

### Post by RAOF on 2006-08-15
> **azmrb said:**
> ...

Don't get me wrong it is doable, I did it.  But what I was trying to tell the original poster was after all that work I ended up with a 32bit browser running 32bit plugins and forcing 32bit architecture application installs and I am not certain that at this point I can tell the difference between speed, reliability, or usability between 32 and 64bit Ubuntu.
...

It depends on what you do.  If you're just using your system for Web/Email/Office work, then you almost certainly won't notice any benefit from the AMD64 version, and would be advised to use the 32bit version, where it is easier to get (a small range of) things working.  Basically, if you just use Web/Email/Office stuff, you would get roughtly the same performance with a 10 year old processor, so making your current processor a bit faster won't be noticable.

If you use your system for anything CPU intensive, though, like audio/video encoding/decoding, these things will benefit tremendously.  About 30% faster, on average.

---

### Post by Garfield360 on 2006-08-16
thanks , i shall see which to go with as i also hear suise linux is good also

---

### Post by checkup on 2006-08-16
There are some advantages with amd64:

- you have about twice as much registers (and the additional ones are general purpose registers) -> few transfers to/from ram. (big speed increase!)

- no memory segmentation -> speeds up memory access 
- all registers are 64 bit which speeds up some apps
- in linux nearly all can be easely build against amd64
- (fglrx is available for amd64 and xorg 7.1!)


-> disadvantages:

- no flash player
- wine
- java


I run amd64 smp here with 2.6.17 kernel + compiz cvs + xgl cvs + xorg 7.1 and it is a true beauty  compared to i686!

---

### Post by michux on 2006-08-16
> **checkup said:**
> 
-> disadvantages:

- no flash player
- wine
- java


I would add:

- unacceptable DVD support

to the cons. I'm talking about the 64-bit version of libdvdcss which in my case causes multiple DVD movies to crash while playing. I need to run a 32-bit GeexboX (a live-cd with mplayer) to play those movies without a hassle (or install a 32-bit version of mplayer with the dependencies which is troublesome).

So, my advicre is - don't go for 64-bit unless you have a demanding server/desktop or do a lot of audio editing/video rendering or other niche stuff.

---

### Post by Kilz on 2006-08-16
> **checkup said:**
> 


-> disadvantages:

- no flash player
- wine
- java


How are these disadvantages? 

1) no flash player - Flash plugin available, see my signature or the sticky in the 64bit section.
2) Wine - Wine available, see my signature or the sticky in the 64bit section.
3) Java - Java is available in synaptic - apt for development and applications. Plugin is available see my signature or the sticky in the 64bit section.

---

### Post by a-musing amazon on 2006-08-16
[QUOTE=azmrb;1384315]
> Well if you install amd64 and you want ( Flash, Java
> plugins, streaming multimedia... wmv, Real,... ) you
> are in for a long haul.  First to install a 32 bit
> version of FF, then follow the howtos of forcing 
> forementioned browser addons to work. 

This is one way of doing it.

Alternatively you /can/ run a 64-bit browser (I use epiphany), though you will need to use nspluginwrapper to run some 32-bit apps such as realplayer and flash and the 32-bit mplayer if you need to run 32-bit windows dlls to see some wmvs.

Java (if you use Blackdown Java) will run natively in 64-bit.

64-bit totem-xine is OK for Quicktime (including HD), DVD (if you add CSS descrambling) and /some/ wmvs.

---

### Post by Kilz on 2006-08-16
> **azmrb said:**
> Well if you install amd64 and you want ( Flash, Java plugins, streaming multimedia... wmv, Real,... ) you are in for a long haul. First to install a 32 bit version of FF, then follow the howtos of forcing forementioned browser addons to work.
Is that long haul running [a setup script]("http://home.comcast.net/~deletebox/Firefox32-flash-java-mplayer-4.tar.gz") with 2 commands in the terminal? Is that forcing using the [.deb file]("http://home.comcast.net/~deletebox/firefox32-1.5.0.6_amd64.deb") I made that installs a 32bit browser with 2 clicks and gdebi? 
I think you are just a little behind the times.
> **Garfield360 said:**
> thanks , i shall see which to go with as i also hear suise linux is good also

SuSE? Dont use version 10.1 . It was an absolute mess when I left it. 10.0 is nice, but it doesnt have easy xgl support.

---

### Post by azmrb on 2006-08-16
Kilz, please don't get overly defensive.  I know what you are saying.  I followed those instructions to get all of the 32bit plugins and addons to work with the 32bit FF I installed.  It took me HOURS to get everything working the way I wanted it too.  And I ended up running mostly 32 applications on top of my 64bit OS.  But the point is NOT to run an OS but to run the applications.

The only thing I am saying is that for the masses of users we all want to attract to linux in general and Ubuntu in particular it is not practical.  The vast majority of them won't even know about this forum much less find the instructions and be able to follow them.

In the long run the road lies in convincing software producers that linux is viable and growing so that they become invested in linux software and customers.  That will lead to more 64bit software being released

In the short run the road lies in convincing ordinary users to switch from Windows to Linux so the customer base grows as fast as possible.  A positive customer experience is vital to that goal.

---

