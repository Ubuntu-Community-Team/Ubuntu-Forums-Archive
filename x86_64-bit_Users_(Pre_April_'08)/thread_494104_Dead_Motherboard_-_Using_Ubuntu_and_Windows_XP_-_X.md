---
title: "Dead Motherboard - Using Ubuntu and Windows XP - XP no longer boots?"
date: 2007-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by fierystorm123 on 2007-07-06
Hello all,

Err..first of all I apologize if someone has posted a similar question..I spent a couple of hours searching through the forums but didn't find anything.. So my apologies if I am wasting anyone's time, but I am really hoping to have a bit of experienced wisdom bestowed upon me:-/

Here is my situation..

Two weeks ago I was running an older system.

Compaq Desktop 6000 Series
Compaq Motherboard (System Board) - 261671-001 (or AMD Athlon XP (K7) Processors) 2.0 ghz
1.5 DDR ram
2 x hard drives... Master - Windows XP..Slave - Ubuntu

In short, everything was fine in the world despite it being an older system. I was planning to upgrade this Christmas.

Then two weeks ago..

I woke up, tried booting my computer.. it began to boot to the boot screen where it asks if you would like to press Del to enter into options. It would never go any further than that. It would immediately restart. Come to the same point, restart. And it wouldn't stop resetting. Boot disks didn't work and when I attempted to simply restore the computer, it would shut off in the middle of that too. 

So I thought "virus". I use AVG 7.5 professional, so was surprised I might have an issue, but I scanned using that. I scanned using Norton. Microhouse Inscan too. Nothing.. Then after conversing with a friend, he suggested it could be the power supply. So I switched it out. Stayed on until windows xp logo, then restarted. After that, same point. So I pulled the battery on the motherboard, cleared everything. Didn't work.

Figuring it might be the motherboard, I pulled it and replaced it with a nice new 64 bit MSI (AMD 2.0 ghz cpu) motherboard that was a model made about the same time as my old one to avoid any technical problems, or so I thought... And finally.. It worked. No more resetting.

Now, as I am running a 64 bit system, I installed the all new Ubuntu 7 64 bit (love it already despite being confused at where things are at times). But Windows XP...

XP gets to where it just shows a HINT of the xp logo showing up...then it resets. I tried booting into safe mode..it restarts (now I am starting to wonder about that motherboard, but it still restarted no matter what hard drive I had connected to it). I have access to my files (switched the master/slave setup so Ubuntu now plays king when I couldn't get it to boot) so that is good.. but I can't get windows to boot up. Also, when I F8, the system restore option does not appear..which is throwing me for a loop because that is a first.. I tried scanning for viruses again, but still nothing. Ordinarily, as I have access to my files, I would say to heck with it and just reinstall everything.. One problem - my particular compaq model has XP imbedded (hope that is the right worse) into the hard drive itself..so no windows CD.

Now I promise, I am NOT one of those guys (although I am a noob in regards to Ubuntu and Linux - fell in love with it after my ex's father introduced me to it) who doesn't back up his files or create restore disks. I DO have restore disks..however, they won't work with the new motherboard :-/ (I am sorry for the lengthy post!) or so the disks claim..

So I am stuck, I like having the option of using either XP or Ubuntu..and I can't afford to buy a copy of XP or *shudder* switch to Vista (even though I doubt my system could run it even with the new motherboard).

So does anyone have any options to fix XP? I can't boot in safe mode..I can't system restore..my files aren't a problem and I do have my product key. Microsoft says "oh, how unfortunate..can't help you but we'll gladly sell you a new copy". I'm stuck, guys.. I did download Trinity-Rescue Kit as supposedly that can help fix some XP probs but..I'm clueless in using linux beyond very basic Ubuntu..so I am working at learning it, but it's taking me a long time..I'm a self taught basic computer user.. And I don't know if its the motherboard that windows is having problems dealing with or what (wouldn't XP have automatically adapted to it?)

Again, sorry for the seriously long post.. Hopefully if nothing else I gave an amusing distraction to someone having a long day? :-X Any help given I would be forever grateful! ;)

---

### Post by logos34 on 2007-07-06
So you can't boot windows but still can access the files from Ubuntu...What's the loss?  

Joking aside, I agree that XP is having trouble with the mobo...it's configured with drivers for the hardware on the old board. Linux is a lot better at adapting to a hardware change.  I could be wrong but I think that's what's happening here.  Maybe you could find a cheap (pirated?) edition of xp somewhere and then just use your product key to activate it.
I think there;s a way to do that...you'll have to search it out yourself...But it's not like you'd be stealing anything--you paid for a copy of windows already when you bouhgt the computer, and stingy MS can't even give you COPY of something that is rightly yours.  

If all else fails, just get ntfs-3g driver for linux so you can write to as well as read those files on your ntfs partition or back them up and reformat as ext3.

If you need windows for some reason (work), there is also the option of downloading an evaluation/trial version of winxp pro x64 edition--good for 120 days.  You will have to reinstall at that point but you can keep applying ad infinitum for new product keys (maybe just use a different email subaccount each time)--I've been running mine for a year and a half now (even though I almost never use windows anymore).  Make a separate data partition (D:) so reinstalling to C: won't disturb those files every time.

---

### Post by fierystorm123 on 2007-07-06
Ok, I will check that out.. Thanks Logos :-)

---

### Post by brainsaw on 2007-07-06
You usually have to reinstall windows every time you make a major hardware change (like a motherboard). It's just how it is.

---

### Post by Jouke74 on 2007-07-07
That is an affirmative, you have to reinstall Windows. Mind yourself that Windows might overwrite Grub when reinstalling, so be careful and read around how to install OSes dual boot with Ubuntu first... 

Second point, you should have gotten a restore CD with your Dell probably. You might want to check if you can find most of your other hardware drivers on there. Those also need to be reinstalled. Anyway, borrow a XP CD from one of your friends, and use your own product key (or ditch windows all together).

Good luck.

---

### Post by Zorlin on 2007-07-14
If you've got a proper windows XP pro cd lying around, I can probably PM you a [proper] product key...
My dad used to work for Microsoft and was part of the XP launch... thus the 31 or so genuine copies I have lying around my house. :popcorn:

---

