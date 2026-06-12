---
title: "Some questions about 64bits"
date: 2006-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by XioNoX on 2006-06-27
Hello,

I wil sooner have an dual core 64bits laptop ([see here]("http://www.fnac.com/Shelf/article.asp?PRID=1850497"))

I would know, what differences there are between 32 and 64bits. How much speed ? Applications who don't works ? Hardware not supported ?
What I have to know about 64 bits ?
Finnaly if I should install ubuntu 64 or 32 ?

I will use it principally for web, sound (ardour jackd, ReZound), game, Movies, and IM (webcam and microphone). And normal stuff like CD burning, downloading, scanning/printing (with Brother drivers), and maybe use XGL/Compiz.
(Ive seen the Sticky topic)

Thanks
XioNoX

---

### Post by Dr. Nick on 2006-06-27
You can run ubuntu 32bit on a 64bit chip just fine. Last time I used 64bit ubuntu was breezy and some things like macromedia flash, w32codecs, and a few other packages didnt work (not ubuntus fault, the same is true of almost all 64but distros)

Their really isnt any noticeable speed increases between 32/64 bit right now so that isnt a big deal.

If your new to linux and want to learn the basics first then 32bit is probably best, 64bit had a few kinks last I tried, many may have been fixed though.

If you are fimilar with linux already you may be able to use 64bit, 64bit isnt hard and doesnt look any different then 32bit, You just may have trouble with a few apps

---

### Post by jvictor on 2006-06-27
IMHO the feeling that you are not able to run a 64 bit OS gets on you more than anything else ;) Thats the reason why I chose 64 bit :)

As Dr Nick said some apps wont work well on 64 bit coz its a maturing platform and will take some time to break thru..

However u can try the flock browser and get Flash working without much hassles on 64 bit. Its a 32 bit browser but the devs somehow got the flash plugin to work on 64 bit . Dont ask me how and why dont Firefox ppl do it ;) 

I have *read* posts telling that ripping encoding etc are faster on a 64 bit machine but Ive never tried them .

EDIT
Also multimedia codecs are a doubtful thing on 64 bit.

I just use the 64 bit machine for reporting bugs to dapper team :D so that we have a stabler and more viable platform in the future releases..

---

### Post by Dr. Nick on 2006-06-27
Some 64bit distros (suse and maybe others I think) have flash in Firefox. Basically it includes all the 32bit libraries so that you can run the 32bit version of firefox/flash on 64bit. I imagine it is possible to do with ubuntu aswell, I just never had the time to look into it, Ill be back in 64 bit land maybe on next release when it will be a bit more mature.

---

### Post by joshrobinson on 2006-06-27
[QUOTE=jvictor]IMHO the feeling that you are not able to run a 64 bit OS gets on you more than anything else ;) Thats the reason why I chose 64 bit :)

As Dr Nick said some apps wont work well on 64 bit coz its a maturing platform and will take some time to break thru..

However u can try the flock browser and get Flash working without much hassles on 64 bit. Its a 32 bit browser but the devs somehow got the flash plugin to work on 64 bit . Dont ask me how and why dont Firefox ppl do it ;) 

I have *read* posts telling that ripping encoding etc are faster on a 64 bit machine but Ive never tried them .

EDIT
Also multimedia codecs are a doubtful thing on 64 bit.

I just use the 64 bit machine for reporting bugs to dapper team :D so that we have a stabler and more viable platform in the future releases..[/QUOTE]

i have 64bit dapper, with 32bit firefox and flash works perfect.. theres a thread around here somewhere that has a howto.. that is if you want to switch to firefox

---

### Post by XioNoX on 2006-06-27
I'm able to use 64bits, but I just want to know if there are some program who don't run with 64bits whatever we do...

why w32codecs don't work ? why there are no "w64codecs" ?
When gnash will be ready ? there are somewere an roadmap for this project ?
Where can I found a deb file for gnash 64 bits ?

---

### Post by Kilz on 2006-06-27
[quote=Dr. Nick]You can run ubuntu 32bit on a 64bit chip just fine. Last time I used 64bit ubuntu was breezy and some things like macromedia flash, w32codecs, and a few other packages didnt work (not ubuntus fault, the same is true of almost all 64but distros)[/quote]

Why on earth do some people come to the 64 bit section and tell people to install the 32 bit OS based on the last release?
So many things have changed, Dapper is not like Breezy.


[quote=XioNoX]why w32codecs don't work ? why there are no "w64codecs" ?[/quote]
Because they are Windows codecs, and windows 64bit sucks and is way behind 64bit Linux. Because they are windows codecs they are proprietary formats and it would be hard if not impossible to create 64 bit versions of them because the code for them isn't freely available.
w32codecs do work, [check the sticky]("http://www.ubuntuforums.org/showthread.php?t=191205"), you just need a 32 bit player, also available in the sticky.

---

### Post by Dr. Nick on 2006-06-27
I wasnt necessarily saying to install the 32bit version, just letting people know its possible to use 32bit ubuntu if needed; and trying to make them aware to the fact that a few applications may take a bit of work to get going. I have done a little research and see that the w32codec issue isnt a real big deal, VLC is a good player that will play most everything without the need for the w32codecs.

The reason the w32codecs wont work really is because they are 32bit windows binaries.

The hardware support between 32/64bit is the same really. The only spot where you may hit problems on 64bit is if you are needing ndiswrapper to get a wireless card running. Ndiswrapper isnt real usefull with 64bit unless you can find 64bit windows drivers, the 32bit windows drivers wont cut it.

I used amd64 all the way through breezy and into the middle portions of the dapper test period. Happy most of the time too. I messed it up though and was needing to repartition my drive, I had the new dapper betas for 32bit I used on other computers and decided to dump that onto my 64bit instead of redownloading it all.

---

