---
title: "Will 64bit allow me to run everything I'm running in 32bit?"
date: 2008-11-05
forum: x86 64-bit Users
---

### Post by birdd on 2008-11-05
I have installed and got a nicely working 32bit install of Intrepid... Now I have 4GB of Ram and 32Bit only "sees" 3.xGB of it as you know...

Now I use my Desktop for general usage including web browsing (inc flash), music, movies, and gaming... Now I have a Nvidia 8800GTX Graphics card... I also run wine/CrossOver Games for some Windows Games...

Will i have any problems running 64bit on my pc (see my signature for all the details)... Is it worth upgrading to 64bit for the Ram and also to fully use my Quad Core Q6600?

I did attempt to run 64bit when i first installed ubuntu (about a week ago) and it ran alot slower, was a lot slower to boot up and shut down... but i hadn't installed the Nvidia drivers so would that have caused the problem? or is 64bit slower to boot up and shutdown, etc?

---

### Post by jdong on 2008-11-05
64-bit isn't necessarily faster than 32-bit for any reason. In fact, maybe with some of its long-pointer overhead it might be a tad slower, but overall you shouldn't be worried about it from a performance standpoint. You need a 64-bit kernel or a -server kernel to see your 4GB RAM, so running 64-bit is your best bet.

The official answer that I can give is that we've attempted to make everything that was working in 32-bit Ubuntu also working in 64-bit Ubuntu, and stuff that doesn't work should probalby be added to our 32-bit emulation libraries. If you ask, I'm sure we can figure out most of the incompatibilities :)

---

### Post by tuxxy on 2008-11-05
Yes there is a 64-bit equivelant of most apps now and if you find one that isnt which will be difficult, you could just install the 32-bit version anyway :)

YOu will also see performance increases in video/photo manipulation, virtualisation etc

---

### Post by velja27 on 2008-11-05
Well i have 64-bit for a few months now,and i haven't been on a 32-bit Ubuntu but i could find all the applications i wanted in 64-bit on [www.getdeb.net](www.getdeb.net) and those 32-bit applications there were guides on how to install them so it ain't hard at all.
Good luck with it.

---

### Post by jdong on 2008-11-05
> **tuxxy said:**
> 
YOu will also see performance increases in video/photo manipulation, virtualisation etc


[citation needed]

---

### Post by felker2 on 2008-11-06
> **birdd said:**
> 
Will 64bit allow me to run everything I'm running in 32bit?

Depends on what you're running in 32bit. For example: a 32bit-only hardware driver won't work on a 64bit OS.

FWIW: I switched to 64bit last year, and everything just worked and works fine.

> **birdd said:**
> 
I did attempt to run 64bit when i first installed ubuntu (about a week ago) and it ran alot slower, was a lot slower to boot up and shut down... but i hadn't installed the Nvidia drivers so would that have caused the problem? or is 64bit slower to boot up and shutdown, etc?

No, 64bit is not slower to boot or shutdown. However, a live CD *is*...

My advice to you: If you don't feel comfortable with 64bit, don't use it.

---

### Post by ua6icab7 on 2008-11-06
Hot Promotion Storm of [WOW Gold](http://www.gold4power.com/) is Sweeping fiercely all around! Recently,we have tailored the unique World of Warcraft gold promotion for our valued customers.You could feel surprised that our [WoW gold](http://www.gold4power.com/) price are the cheapest on all the servers,especially on US server!Purchasing cheap WoW Gold from Gamelee.com is 100% safe; your account will not be suspended or banned for purchasing World of Warcraft Gold from us. Perfect Runescape Summoning! Recently we are offering the new skill of Runescape--Summoning.For all our valued Runescape Fans,it's no doubt that could be an unparalleled news.Do you want to miss this new skill?That can make you weather all the chanllenge and become the big cheese in Runescape!Plz trust us that our price is depend on the market,even cheaper than others,we will never set it random !Let's enjoy the hot storm you have never been to!

---

### Post by Yellow Pasque on 2008-11-06
Personally, I wouldn't ruin a working 32-bit install just to make use of some extra RAM, especially if I hadn't verified that I was actually using all of the RAM and data was being swapped out when I was doing intensive multitasking.
Take a look at swap usage under various usage scenarios:
```
free -m
```

> I did attempt to run 64bit when i first installed ubuntu (about a week ago) and it ran alot slower, was a lot slower to boot up and shut down... but i hadn't installed the Nvidia drivers so would that have caused the problem?
If you didn't have video hardware acceleration, that is going to make your OS feel slower. I've never heard that 64-bit boots slower, but there are also ways to speed up boot anyway.

---

### Post by duanedesign on 2008-11-06
> **jdong said:**
> [citation needed]

here is an article comparing 32 vs. 64. I would of liked to have seen some graphics/video benchmarks. However kernel compilation and Unreal FPS were faster with 64bit Ubuntu. If you are doing 3d animation heavy graphics and video work you could definetly see a performance increase. The average web surfer/open office user will not notice an increase and in some cases experience a slight decrease in performance.

[http://www.phoronix.com/scan.php?page=article&item=616&num=1](http://www.phoronix.com/scan.php?page=article&item=616&num=1)

---

### Post by jdong on 2008-11-06
> **duanedesign said:**
> here is an article comparing 32 vs. 64. I would of liked to have seen some graphics/video benchmarks. However kernel compilation and Unreal FPS were faster with 64bit Ubuntu. If you are doing 3d animation heavy graphics and video work you could definetly see a performance increase. The average web surfer/open office user will not notice an increase and in some cases experience a slight decrease in performance.

[http://www.phoronix.com/scan.php?page=article&item=616&num=1](http://www.phoronix.com/scan.php?page=article&item=616&num=1)

Remember that some of the performance differences seen can be explained by 64-bit processors having a "greater common denominator" of instruction sets and features, as opposed to inherent fastness of 64-bit long mode. Of course now I'm just splitting hairs and nitpicking, but I just wanted to get the point across that you don't necessarily require 64-bit mode to reap these performance benefits, sometimes a simple use of more aggressive compile-time flags can reap the same benefits.

---

### Post by birdd on 2008-11-07
Well last night i did it... I wiped my 32bit install and installed 64bit again... and its working much better than the first time i tried it... Not sure what happened last time?

I've got flash working.. got nearly everything i had installed on 32bit installed now on 64bit... except OpenOffice 3 as i downloaded the deb at work as its not in the Telstra Unmetered... :-P So i'll grab the 64bit version today...

---

### Post by felker2 on 2008-11-07
> **birdd said:**
> Well last night i did it... I wiped my 32bit install and installed 64bit again... and its working much better than the first time i tried it.

Congratulations!

:popcorn:

---

### Post by birdd on 2008-11-07
Is there a x86-64bit version of:

Wolfenstein: Enemy Territory
World of Padman
Mania Drive
Urban Terror

Or will the 32bit versions work?

---

### Post by borlosky on 2008-11-15
> **birdd said:**
> Is there a x86-64bit version of:

Wolfenstein: Enemy Territory
World of Padman
Mania Drive
Urban Terror

Or will the 32bit versions work?

i believe those should still work. as far as games go, i havn't noticed any different in getting games to work, provided you have all correct drivers installed to run them. (which some manufactures have yet to release 64 bit drivers, so you definitely wanna check that before switching to 64 bit, personally i didn't have any issues finding drivers for my pc, everything just loaded fine when installing, but some might not be so lucky depending on your hardware) remember MOST 32 bit applications will work in 64 bit environment due to 64bits backwards compatibility. (for instance, i have ut2004, doom 3, diablo 2, and steam all running fine under hardy 64 bit) the only "games" i've really had trouble with, is console emulators (zsnes ect...) those being 8/16/32 bit systems, they WILL NOT work on a 64 bit OS. there is no work around for that that i've come across.

---

### Post by inobe on 2008-11-15
i don't **see** 64 bit being faster, meaning its visually unnoticed.

i do notice it has a better feel, encoding and transcoding on a 64 bit system seems flawless, as for 32 bit doing these types of tasks affects how other applications perform during the process, i dislike that type of feel, this does not exist on my 64 bit box.

---

### Post by master5o1 on 2008-11-15
I was amazed that I could install flash (albiet 32bit flash) through synpatic ... dependancies were just some 32bit libraries and other random stuff.

---

