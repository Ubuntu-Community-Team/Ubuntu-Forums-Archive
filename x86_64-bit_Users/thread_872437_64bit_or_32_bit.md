---
title: "64bit or 32 bit?"
date: 2008-07-28
forum: x86 64-bit Users
---

### Post by Disastorm on 2008-07-28
Hi, I have Dapper Drake 64 bit on my laptop.  I'm going to download the newest Ubuntu and install it.  Back when I got Dapper drake, some 64 bit stuff didn't work too well like the flash plugin for firefox, had to do some weird stuff in order to install firefox32 (I think the same thing with wine).  Are all that stuff working by default now, or is it better to just get the 32 bit Ubuntu?

---

### Post by Rhubarb on 2008-07-28
Flash works fine in 64bit (flash sometimes does stop working, just quit firefox, and re-open it and it'll work again).

It's very nice, and very stable, definitely give it a go.

[Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=765428")

Make sure to get Ubuntu 8.04.1, it's got most of the recent updates, and has firefox 3 (rather than firefox 3 beta 5).
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by hardyn on 2008-07-28
the 32bit flash isn't that stable either... quite often crashes firefox.

---

### Post by Disastorm on 2008-07-28
oh thanks, nice to see it has flash.  Previously, the 64 bit firefox didnt even have flash, in order to run flash you had to install the 32 bit firefox.

---

### Post by Rhubarb on 2008-07-28
To install flash in 32 / 64bit, just grab the **flashplugin-nonfree** package from the ubuntu repos.

Flash 10 has come out, not sure if it's more stable or not, I haven't had the need to try it out yet.

---

### Post by Disastorm on 2008-07-28
Hey another question, my laptop has only 512 ram with integrated video taking up 128 or 64 of it (i forgot what i have it set to).  I see one of the main advantages of 64 bit is the ability to have over 4 gb ram which doesnt affect me since i have such little ram.  it also says that 
"1) One disadvantage of 64-bit architectures is compared to 32-bit architectures the same data will occupy more space in memory (due to larger pointers and possibly other types and alignment adding). The increases in the memory requirements of a given process can have implications for efficient processor cache utilization."

Does this mean it might be better for me to get 32 bit since i  have low memory or still stick with 64 bit?

---

### Post by Rhubarb on 2008-07-28
The memory requirements aren't significantly more (perhaps less than 5% more), but in your case I think you may be better off with 32bit.  Any extra megabytes of free ram may help you out there.

---

### Post by hal10000 on 2008-07-28
I recently installed 64 bit hardy and and by now i can say that everything works fine. I didn't try all of the apps, but no errors in firefox, flash, wine, zattoo, java (sun), OpenOffice and any other apps i tried out.

It work fine, so give it a try.

---

### Post by Sef on 2008-07-28
To install flash, read [Kilz's sticky]("http://ubuntuforums.org/showthread.php?t=772490"), and for Java, read [Java on 64-bit]("http://ubuntuforums.org/showthread.php?t=774956").

---

### Post by John.Michael.Kane on 2008-07-28
Flash-plugin, is installable though synaptic. Wine appears to be installable though synaptic, it also has it's own repo which a user can add to their sources list. 

The thread below should help you with installing most of the items you want.

[Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=765428")

---

### Post by stchman on 2008-07-28
> **Disastorm said:**
> Hi, I have Dapper Drake 64 bit on my laptop.  I'm going to download the newest Ubuntu and install it.  Back when I got Dapper drake, some 64 bit stuff didn't work too well like the flash plugin for firefox, had to do some weird stuff in order to install firefox32 (I think the same thing with wine).  Are all that stuff working by default now, or is it better to just get the 32 bit Ubuntu?

I run 64 bit on three different machines with no difficulty.


Stick with the repos and use Icedtea instead of SUN for a Java browser plugin.

---

### Post by Midahed on 2008-08-01
I used to run 7.04 Feisty 64-bit as my first venture into the world of Linux, but I've just finished re-installing my system from scratch, using 8.04 Hardy 32-bit.

I bought a 64-bit motherboard and processor because.... well, because it was there to be bought. :mrgreen:

I didn't need the processing power of the 64-bit environment and, to be honest, I don't use the sort of apps that would benefit from 64-bit crunch-power.

Although I got _most_ things working OK under 64-bit, it was sometimes a bit of a struggle.

I haven't noticed any speed degradation in moving back to 32-bit.  Most important of all, things just work.  There's no need to constantly wonder if x or y will work in a 64-bit environment.

For me, 64-bit was too 'bleeding edge'.

If you _need_ the processing power, then go for it.  But if you want a problem-free PC, I'd stick with 32-bit for the moment.

I'm still using the same 64-bit kit, so I could return to the fold in the future but, for now, I'm taking the easy way out.

Sorry if that's heresy on this section of the forum. :D

---

### Post by cszikszoy on 2008-08-01
If your hardware supports it, and most of the software you will be using can be found in the repos (or if you have no problem compiling from source) then go wit the 64 bit.

Also, if you want to use more than 4 gb of ram or more, you'll have to use the 64 bit environment.  Unless you want to use the 32bit server kernel, or compile your own with PAE enabled.

---

### Post by Krydahl on 2008-08-01
If it's any help, my 64bit hardy install is using 620mb of RAM with no apps running (except the system monitor and compiz). Mind, it might be using less if I'd just rebooted. I think it keeps some bits of recently used apps in RAM.

No idea what a 32bit install uses because I haven't got one.

---

### Post by Disastorm on 2008-08-04
Thanks for the all the comments, although I installed the 32-bit OS.

---

### Post by XxOsurfer3xX on 2008-08-04
I'm using 64 bit 8.04 and for now apart from a couple of headaches because of some driver issues for my x-fi, everything else is working fine...

---

### Post by Kilz on 2008-08-04
> **Disastorm said:**
> Thanks for the all the comments, although I installed the 32-bit OS.

Why would you want to do that?

---

### Post by Roasted on 2008-08-05
> **Kilz said:**
> Why would you want to do that?

"Things just work." Perhaps?

---

### Post by Thelasko on 2008-08-05
Since Gusty, 64-bit has become much more civilized.  Thanks to a lot of work from developers, "things just work" in 64-bit.  With the release of Hardy, I've noticed a massive slowdown in the number of support questions for 64-bit machines.  Please don't compare your experiences with Dapper and Feisty, to those of Hardy.  They are worlds apart.

---

### Post by tuxxy on 2008-08-05
64bit the only drawback is 32 bit flash plugin as stated, it still runs fine for me :)

---

### Post by stchman on 2008-08-05
> **tuxxy said:**
> 64bit the only drawback is 32 bit flash plugin as stated, it still runs fine for me :)

The flash that is in Hardy 64 bit is 64 bit.

---

### Post by Thelasko on 2008-08-05
> **stchman said:**
> The flash that is in Hardy 64 bit is 64 bit.
Where did you get that information?  Are you sure you aren't talking about Gnash, or Swfdec?

---

### Post by insane_alien on 2008-08-05
the flash in hardy 64-bit is 32-bit thats why when you install it, it installs the 32-bit libraries as well.

---

### Post by Roasted on 2008-08-05
> **Thelasko said:**
> Since Gusty, 64-bit has become much more civilized.  Thanks to a lot of work from developers, "things just work" in 64-bit.  With the release of Hardy, I've noticed a massive slowdown in the number of support questions for 64-bit machines.  Please don't compare your experiences with Dapper and Feisty, to those of Hardy.  They are worlds apart.

Oh, I agree. I'm not dogging 64 bit... but no matter how you cut it, the functionality of 32 bit still exceeds 64 bit. The gap is closing, but there hasn't been a tie breaker yet.

Example I ran into:

I bought a Turtle Beach Montego 7.1 PCI sound card with a C-Media chipset. It was said to be 100% working with Alsa (considering C-Media chipsets are supported by Alsa) and other users have said they love the card and it works great.

I install it... my audio is quiet. Yes, PCM is maxed. Not whisper quiet, but CERTAINLY not loud enough as it should be. Amarok and Frostwire were also freezing on me left and right completely unprovoked.

I installed 32 bit this afternoon. Needless to say, my ears now hurt from the amazing output this card gives me. Works out of the box. Completely fine. Perfect. I love it. But, 64 bit didn't offer me what I needed. So I had to resort to "what just works" and I was left with 32 bit.

...as if it really matters to me, anyway, considering my motherboard maxes out at 4gb of RAM and the fact that I'm only running 2gb of RAM anyway.

The day 64 bit Ubuntu offers full blown support of my sound card, I'll be a believer. And perhaps it's not even a lack of support from Ubuntu. It may simply be that Alsa isn't fully supporting 64 bit drivers yet. I have no idea. I'm not trying to blame anybody, since everybody has done a great job with the open source projects. BUT, just stating my experiences. 

:guitar:

---

### Post by stchman on 2008-08-06
> **insane_alien said:**
> the flash in hardy 64-bit is 32-bit thats why when you install it, it installs the 32-bit libraries as well.

Then why do they have (2) different flashplugin-nonfree packages?


[http://packages.ubuntu.com/hardy/flashplugin-nonfree](http://packages.ubuntu.com/hardy/flashplugin-nonfree)

```

Architecture  	Package Size  	Installed Size  	
amd64             18.3 kB	   164 kB               
i386 	           18.2 kB	   164 kB        

```

Please elaborate.....

---

### Post by jerome1232 on 2008-08-06
> **stchman said:**
> Then why do they have (2) different flashplugin-nonfree packages?


[http://packages.ubuntu.com/hardy/flashplugin-nonfree](http://packages.ubuntu.com/hardy/flashplugin-nonfree)

```

Architecture  	Package Size  	Installed Size  	
amd64             18.3 kB	   164 kB               
i386 	           18.2 kB	   164 kB        

```

Please elaborate.....
flash is 32 bit period just google it, there are 32 bit programs a plenty packaged for 64 bit.

---

### Post by stchman on 2008-08-06
> **jerome1232 said:**
> flash is 32 bit period just google it, there are 32 bit programs a plenty packaged for 64 bit.

Not uncommon.  Many 64 bit applications are 32 bit code recompiled using a 64 bit compiler.  Also 64 bit Ubuntu runs 32 bit apps.

I wish there were more apps that were 64 bit and also optimized for SMP.

---

### Post by Thelasko on 2008-08-06
> **stchman said:**
> Then why do they have (2) different flashplugin-nonfree packages?


[http://packages.ubuntu.com/hardy/flashplugin-nonfree](http://packages.ubuntu.com/hardy/flashplugin-nonfree)

```

Architecture  	Package Size  	Installed Size  	
amd64             18.3 kB	   164 kB               
i386 	           18.2 kB	   164 kB        

```

Please elaborate.....

Read more carefully.
> nspluginwrapper  (>= 0.9.91.4-2ubuntu1) [amd64]
    A wrapper to run Netscape plugins on other architectures 
As it states, nspluginwrapper allows the 32-bit version of flash to work on 64-bit.

---

### Post by insane_alien on 2008-08-06
you'll notice that the 64-bit installer still downloads the 32-bit flash and installs it in nspluginwrapper. and all the 32-bit libraries required to support it.

---

