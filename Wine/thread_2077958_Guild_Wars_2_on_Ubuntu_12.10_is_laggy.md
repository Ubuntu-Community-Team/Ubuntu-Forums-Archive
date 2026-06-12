---
title: "Guild Wars 2 on Ubuntu 12.10 is laggy"
date: 2012-10-29
forum: Wine
---

### Post by Nanur on 2012-10-29
Hey everyone, as the title implies I am playing Guild Wars 2 on Ubuntu 12.10 (recently upgraded from 12.04.1 LTS) and the gameplay is awfully laggy, as in 8-10 fps in areas with little activity, and then it drops to as low as 2-3 fps in areas with a lot of activity. The gameplay was also the same in Ubuntu 12.04.1.

A couple tech specs of my machine:
Processor: Intel Pentium D 2.66 GHz dual core
Graphics Card: nVidia GeForce 550 Ti

I am using PlayOnLinux to run the game, and so far.. it had gotten the job done, but not well enough.
Basically what I'm asking if there is something that I need to do in order to have the game run smoother, or if it just my piece of junk processor. I am beginning to think that it is my processor since I am tried multiple combinations of methods..

Any tips?

Thanks, 
   Nanur

---

### Post by Zirts on 2012-10-30
I run it with 30 FPS on my dual-core 2.20 so it's not the processor I'd say. Most probably it is the bad graphics card drivers that are creating this hassle for you :/

Sadly there is not much to do about that while on Linux at the moment.

---

### Post by Nanur on 2012-11-01
I will try updating my graphics card's drivers.. I hate to see my card go to waste like this.

---

### Post by holastickboy on 2012-11-01
> **Zirts said:**
> I run it with 30 FPS on my dual-core 2.20 so it's not the processor I'd say. Most probably it is the bad graphics card drivers that are creating this hassle for you :/

Sadly there is not much to do about that while on Linux at the moment.

It basically comes down to WINE performance at the moment.  I am running a quad core 3.4ghz processor with an Nvidia GTX 460 and tend to only get about 15-25 fps.  Used to be the same back in the early World of Warcraft on WINE days, but now that runs at nearly 200fps. Hopefully it will be all sorted soon!

---

### Post by Tweak42 on 2012-11-01
> **Nanur said:**
> Hey everyone, as the title implies I am playing Guild Wars 2 on Ubuntu 12.10 (recently upgraded from 12.04.1 LTS) and the gameplay is awfully laggy, as in 8-10 fps in areas with little activity, and then it drops to as low as 2-3 fps in areas with a lot of activity. The gameplay was also the same in Ubuntu 12.04.1.

A couple tech specs of my machine:
Processor: Intel Pentium D 2.66 GHz dual core
Graphics Card: nVidia GeForce 550 Ti


The biggest problem is wine doesn't really utilize multi-core processors for those games that really need multi-core.  This is an ongoing problem hopefully we will see some developement addressing this in the future.

In the mean time the latest Nvidia beta drivers 310.14 has some new optimizations that does make an measureable impact by offload rendering to the gpu but I'm not sure if it can help in your case, or might make things worse.  (I don't play GW2)

---

### Post by holastickboy on 2012-11-03
> **Tweak42 said:**
> The biggest problem is wine doesn't really utilize multi-core processors for those games that really need multi-core.  This is an ongoing problem hopefully we will see some developement addressing this in the future.

In the mean time the latest Nvidia beta drivers 310.14 has some new optimizations that does make an measureable impact by offload rendering to the gpu but I'm not sure if it can help in your case, or might make things worse.  (I don't play GW2)

I can confirm that the Nvidia drivers do make a difference, but the performance is still not great.  Think we need a few Wine tweaks.  Guild Wars 2 is a very highly rated "Please Support" game for the Crossover people, and they make a lot of contributions to Wine, so if it becomes fully supported there, that support might trickle into the Wine builds.

---

### Post by Nanur on 2012-11-05
I downloaded and installed the lastest Nvidia drivers and still no change in FPS.. I am just hoping the folks working on the WINE versions for Guild Wars 2 will eventually get everything sorted out here pretty soon and I will get 20+ fps.. (which for me.. that'll be amazing compared to 8-10, or even 2-3 in some areas.

---

### Post by Tweak42 on 2012-11-06
> **Nanur said:**
> I downloaded and installed the lastest Nvidia drivers and still no change in FPS.. I am just hoping the folks working on the WINE versions for Guild Wars 2 will eventually get everything sorted out here pretty soon and I will get 20+ fps.. (which for me.. that'll be amazing compared to 8-10, or even 2-3 in some areas.

Two areas you can monitor for tips and updates, and even lobby for support are:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=26558](http://appdb.winehq.org/objectManager.php?sClass=version&iId=26558)
[http://www.codeweavers.com/compatibility/browse/name/?app_id=7951;forum=1](http://www.codeweavers.com/compatibility/browse/name/?app_id=7951;forum=1)

I'm really hopeing with Nvidia recent interests in linux support will help those of us stuck using wine for games.

---

### Post by holastickboy on 2012-11-07
I find the game runs reliably, it doesn't crash, it just needs a little fine tuning. They could probably use crossover to convert it.

---

### Post by Nanur on 2012-11-10
> **holastickboy said:**
> I find the game runs reliably, it doesn't crash, it just needs a little fine tuning. They could probably use crossover to convert it.

It does run reliably.. However, for me at least, it is quite difficult to play, and as you said.. It needs a little fine tuning.

---

### Post by Nanur on 2012-11-17
Is anyone else getting this awful fps?
I'm getting sick of it. So discouraged to play..

---

### Post by arrizaba on 2013-02-27
Me too. Laggy fps. 
Any improvements since november?

---

### Post by myromance123 on 2013-03-03
The last Wine version I tried was 1.5.12, but that was with my AMD HD6850. The fps was 10 on average, very much like Nanur's experience.

I just downloaded 1.5.23 in PlayOnLinux, and since I'm using an Nvidia card now I'm going to give it another go. Going to have to reinstall it though. Stopped playing because the fps was so painful...
Heck you can even see the bad fps on my video here: [https://www.youtube.com/watch?v=RtZvqPBx2O4]("https://www.youtube.com/watch?v=RtZvqPBx2O4")

EDIT: Oh my goodness, Wine 1.5.25 is already out... They really work fast! Hopefully this is a good release.

---

### Post by zobo90 on 2013-04-15
I have an AMD graphics card (HD Radeon 6700) at the moment and GW2 was running at about 10FPS on average.  I did manage to speed it up a bit more by switching to XFCE desktop, removing Pulseaudio and going back to ALSA, but it was still quite hard to play in areas with lots of activity.  Definitely better than nothing though :)  

I'm upgrading my graphics card to 7700 this week, but still not too optimistic!  (And reading what others have said about the 7700 on these forums isn't filling me with confidence! :P )   Will let you know how it goes! 

On a slightly unrelated topic - Diablo 3 works great, so that's something to keep me entertained until GW2 works better! :D

---

