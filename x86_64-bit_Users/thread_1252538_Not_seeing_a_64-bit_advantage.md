---
title: "Not seeing a 64-bit advantage"
date: 2009-08-29
forum: x86 64-bit Users
---

### Post by lenticular on 2009-08-29
About six months ago I switched from 32-bit Ubuntu to 64-bit Jaunty on my home machine just for fun.  There were some migration hassles (getting VMware, Amazon downloader, and a few other things) to work, but I've basically been stable at 64-bit for several months.  The thing is, I've seen no advantage whatever.  I'm using a Core2 Duo 2.4Ghz system with 4Gb of RAM, running Firefox, OpenOffice, Evolution and the odd Linux game like Alien Arena.

I switched for fun, and am not unhappy, but for my configuration and needs 64-bit doesn't do a thing for me.  

-John

---

### Post by 3Miro on 2009-08-29
Depends on what you are doing. Overall there is a slight improvement of speed, but for most apps it is negligible (for some, however, the benefit is huge).

You can see all of your 4GB of RAM, that should count for something, especially if you are moving a lot of files around (or using torrent clients).

Try things like video/audio encoding.

---

### Post by djchandler on 2009-08-29
Lenticular,

If you have a discreet graphics card, you have a BIOS setting for VGA aperture. However much that is set for adds to addressable ram for the OS to access even though it is dedicated for the video card. You may be disabling part of your video ram by rendering it inaccessable if you don't use a 64-bit OS.

So it depends on if you have a discreet graphics card whether or not you need to run a 64-bit OS with 4 GB of ram. And if you have open dimm slots, if you upgrade your ram, you won't then need to re-install the 64-bit OS.

---

### Post by sanderj on 2009-08-29
> **lenticular said:**
> ... 64-bit Jaunty ... for fun ... Core2 Duo 2.4Ghz system with 4Gb of RAM

Those words match my reasons for 64-bit: fun, 64-bit CPU and 4GB RAM.

---

### Post by credobyte on 2009-08-29
> **sanderj said:**
> Those words match my reasons for 64-bit: **fun**, 64-bit CPU and 4GB RAM.

Ehh ?? :-s x64 is funny/entertaining ?

---

### Post by Slim Odds on 2009-08-29
Just exactly what did you expect? Double the speed?

There are many advantages to the 64 bit version depending on your hardware. But it's not a miracle worker.

A lot of it depends on what applications you use. It's not going to light a fire under your web browser. If you do video encoding you might see a lot of improvement there.

If you have more than 4G of RAM, it will make use of it.

Personally, I love the 64 bit version and have found it to be more stable than anything I've used before.

---

### Post by Copernicus1234 on 2009-08-29
I dont think its worth it. There are still LOTS of applications where you see "this wont work with 64-bit".

The minimal performance gains are not worth the problems.

---

### Post by Perfect Storm on 2009-08-29
> **3Miro said:**
> Depends on what you are doing. Overall there is a slight improvement of speed, but for most apps it is negligible (for some, however, the benefit is huge).

You can see all of your 4GB of RAM, that should count for something, especially if you are moving a lot of files around (or using torrent clients).

Try things like video/audio encoding.
+1

and movie/audio/image editing and creations there significant improvement.
Just do some work with Gimp and kdenlive is a breeze on 64-bit.

---

### Post by Perfect Storm on 2009-08-29
> **Copernicus1234 said:**
> I dont think its worth it. There are still LOTS of applications where you see "this wont work with 64-bit".

The minimal performance gains are not worth the problems.

Not true, it's FUD that is floating around. Even Flash and Java you can get 64-bit version now.
An even if there's a close source app/game that are only 32-bit, you can easely use it by installing ia32libs.

---

### Post by P.KO on 2009-08-29
Well,

What applications do you have in mind? And beside that you can run 32 bit in a 64 bit environment. You just have to add libraries for 32 bit as well.

I don't think that Ubuntu is not having both 32 and 64 bit in repoes when it comes to applications.

Java is now native 64.
Flash is in beta with 64 version.
Skype though is a wrapped 32 bit application however version 2.1 works perfectly.

So I don't see any show stopper for not using 64 bit.

---

### Post by Gen2ly on 2009-08-29
I've been using 64-bit for about 6 months now and notice about what you do, lenticular.  Occasionally I'll use LAME or Audacity and it's nice but I don't use it enough to really notice a difference.  When I install again I'll probably go back to 32-bit just cause it is a little less fuss.

---

### Post by sanderj on 2009-08-29
> **Copernicus1234 said:**
> 
I dont think its worth it. 


That's OK.

> **Copernicus1234 said:**
> 

There are still LOTS of applications where you see "this wont work with 64-bit".

I'm on 64-bit since 2007 (Ubuntu 7.04), and I've never had a problem with a program not working on 64-bit. So can you please name those applications, otherwise it could sound like FUD.

---

### Post by lenticular on 2009-08-29
Given the applications I'm using and the good performance I had with 32-bit, I didn't expect 64-bit to be much faster or cooler, and I'm not disappointed.  

I've been running Ubuntu at work and home for 4 years, and it always takes a little bit of tweaking.  Most of the time I find this enjoyable. To me, it seemed like 64-bit Ubuntu just needs more tweaking.  

What got me thinking about this was last night when the Amazon downloader that I had configured with advice from this forum didn't work.  Amazon was ready to give me a 32-bit deb, but didn't have a 64-bit.  I solved this before, I'll solve it again, no big deal.  Still, in the 32-bit world I would not be tweaking this. VMware server 1.7 (not in the repos) was harder to install in 64-bit than 32, although great assistance from this forum got me over that hurdle. Since I moved to 64-bit, I get infrequent black bands in my monitor.  My guess is that it has something to do with the restricted drivers I'm running for my Nvidia card.  If it really bothered me, I'd search the forums, try different drivers, etc. until I figured out the right tweak.  It may not even be related to running 64-bit Ubuntu (although I never saw this inn 32).

For someone unlike myself, who did not enjoy tweaking 64-bit Ubuntu, the benefits of going 64-bit might not be sufficient to make the jump.  For me, it's like a hobby, and I'm happy to tinker.

---

### Post by SinCityBlues on 2009-08-29
> **Artificial Intelligence said:**
> Not true, it's FUD that is floating around. Even Flash and Java you can get 64-bit version now.
An even if there's a close source app/game that are only 32-bit, you can easely use it by installing ia32libs.

This is true, but everything I know to this day, is from trying to get 64 Bit Flash/Adobe Air, installed LOL . I sleep at night and see pandora half loaded in my browser LOL

Much easier when you're just beginning to migrate and be able to download the 32-bit and install and be done with it :-)

---

### Post by steveneddy on 2009-08-30
> **lenticular said:**
> About six months ago I switched from 32-bit Ubuntu to 64-bit Jaunty on my home machine just for fun.  There were some migration hassles (getting VMware, Amazon downloader, and a few other things) to work, but I've basically been stable at 64-bit for several months.  The thing is, I've seen no advantage whatever.  I'm using a Core2 Duo 2.4Ghz system with 4Gb of RAM, running Firefox, OpenOffice, Evolution and the odd Linux game like Alien Arena.

I switched for fun, and am not unhappy, but for my configuration and needs 64-bit doesn't do a thing for me.  

-John

You probably will not notice any SPEED increase if you are only surfing the web, typing a letter or answering e-mail.

If you were doing something that actually used the 64 bits of processing power you would notice a difference between 32 and 64 bit.

64 bit on a Core 2 will be much smoother and perform at a more optimum level than  32 bit OS on the same architecture.

And if you don't like it, it is your choice to go back to 32 bit.

---

### Post by Slim Odds on 2009-08-30
> **Copernicus1234 said:**
> I dont think its worth it. There are still LOTS of applications where you see "this wont work with 64-bit".

OK, name them?

This is nonsense. There are very few apps that have issues between 32 and 64.

---

