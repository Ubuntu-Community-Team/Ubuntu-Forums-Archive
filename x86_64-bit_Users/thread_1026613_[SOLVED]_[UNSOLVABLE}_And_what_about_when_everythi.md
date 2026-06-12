---
title: "[SOLVED] [UNSOLVABLE?} And what about when everything goes wrong? (8.10 and 8.04)"
date: 2008-12-31
forum: x86 64-bit Users
---

### Post by bfinan0 on 2008-12-31
It seems that I have every possible Ubuntu/Nvidia problem, and all at once, to the extent that even reinstalling 4 times and downgrading to 8.04 don't solve more than one part of the situation at a time.

The trouble all started with the open/save dialog problem
[http://ubuntuforums.org/showthread.php?t=989581](http://ubuntuforums.org/showthread.php?t=989581)
except mine was worse (total freeze whenever one of these dialogs should have appeared.

There were updates available, including the new kernel (2.27..11), and completing those made the system revert to 640x480 monochrome, and did not solve the open/save dialog problem to begin with.

I tried reinstalling Nvidia 180.16, and lost GDM entirely 
[http://ubuntuforums.org/showthread.php?t=868411&highlight=seteuid](http://ubuntuforums.org/showthread.php?t=868411&highlight=seteuid)
(more or less same problem) and nothing I tried for this worked; for one thing, I get my internet exclusively through wifi, and thus have no access from the terminal.

Then I reinstalled Ubuntu Ibex from the liveCD, which accomplished nothing.

Then I reinstalled Ubuntu Ibex from the liveCD, and reformatted / , which gave me the minimal graphics mode.  Implementing the restricted 177 driver gave me the open/save problem as it appears in the above thread regarding it.  Upgrading to 180.18, the latest version, took away graphics entirely (again).

Then I reinstalled Ubuntu Ibex from the liveCD (3rd time) and the same exact thing happened.

Then I downgraded to Ubuntu Hardy from another liveCD, and now have no access to the internet on that system.  I tried ndiswrapper and what appeared to be my Windows wireless driver (netathr.inf) which it rejected as an invalid driver.  Therefore, I cannot even try the correct Nvidia yet.

Does anyone out there have as many or as severe graphics problems as this?  It seems worse than any of the problems discussed in the forum, to the point of being unsolvable (considering that 3 reinstalls and a downgrade did nothing at all)

---

### Post by hyperdude111 on 2008-12-31
can you post the entire specs of your pc?

---

### Post by bfinan0 on 2008-12-31
HP G60-120 notebook, purchased new 12/15/08 (yes, only two weeks old and all these problems)

AMD Turion X2 RM70 amd64 CPU
NVidia 8200M G GPU
128/108/8/6GB hard disk
3.0GB RAM
Atheros AR5009 802.11abgn wireless card
NVIDIA NForce gigabit Ethernet (but no connection for it)

---

### Post by 2hot6ft2 on 2008-12-31
> **bfinan0 said:**
> HP G60-120 notebook, purchased new 12/15/08 (yes, only two weeks old and all these problems)

AMD Turion X2 RM70 amd64 CPU
NVidia 8200M G GPU
128/108/8/6GB hard disk
3.0GB RAM
Atheros AR5009 802.11abgn wireless card
NVIDIA NForce gigabit Ethernet (but no connection for it)
I have almost the exact same pc (mine is the G60-125NR) and I'm running Ubuntu Ultimate Edition 2.0 32 bit on it will no problems at all. You can get it here.
[http://ultimateedition.info/ultimate-edition-20/](http://ultimateedition.info/ultimate-edition-20/)

---

### Post by 2hot6ft2 on 2008-12-31
For the wifi the kernel 2.6.27-7 works great without changing anything.

---

### Post by bfinan0 on 2008-12-31
> **2hot6ft2 said:**
> For the wifi the kernel 2.6.27-7 works great without changing anything.

but how do I get 8.04 with that kernel?  Or 8.10, for that matter?  The live CD starts with 2.6.24.22.

---

### Post by bfinan0 on 2008-12-31
> **2hot6ft2 said:**
> I have almost the exact same pc (mine is the G60-125NR) and I'm running Ubuntu Ultimate Edition 2.0 32 bit on it will no problems at all. You can get it here.
[http://ultimateedition.info/ultimate-edition-20/](http://ultimateedition.info/ultimate-edition-20/)

32 bit?  How does that work, it's a 64bit CPU, is it not?

---

### Post by 2hot6ft2 on 2008-12-31
> **bfinan0 said:**
> but how do I get 8.04 with that kernel?  Or 8.10, for that matter?  The live CD starts with 2.6.24.22.
It's in UUE 2.0 which is 8.10 but uses more current kernels. Don't know how you would get it in 8.04.
> **bfinan0 said:**
> 32 bit?  How does that work, it's a 64bit CPU, is it not?
Yes but just because the cpu is 64 that doesn't mean you have to use a 64 bit OS. The Vista that came on your pc is 32 bit.

A 32 bit cpu couldn't run a 64 bit OS though.

---

### Post by 2hot6ft2 on 2008-12-31
I put the 64 bit UUE on it first but switched it to the 32 bit so I could have more options including lightscribe without forcing it to 64 bit. The 32 bit runs better on it than the 64 bit did too.

---

### Post by bfinan0 on 2008-12-31
> **2hot6ft2 said:**
> I have almost the exact same pc (mine is the G60-125NR) and I'm running Ubuntu Ultimate Edition 2.0 32 bit on it will no problems at all. You can get it here.
[http://ultimateedition.info/ultimate-edition-20/](http://ultimateedition.info/ultimate-edition-20/)

I have the same problems again as far as I can tell.  The open/save problem is still present, for one thing.  What graphics driver are you using, and is it intolerably slow?  My problem is definitely not hardware, Vista still runs as well as Vista ever does.

---

### Post by 2hot6ft2 on 2008-12-31
> **bfinan0 said:**
> I have the same problems again as far as I can tell.  The open/save problem is still present, for one thing.  What graphics driver are you using, and is it intolerably slow?  My problem is definitely not hardware, Vista still runs as well as Vista ever does.
Did you put /home on a separate partition? When I tried I had a problem with trying to save anything. It wouldn't let me choose a location to save it. Same went with opening things like windows wireless drivers wouldn't let me browse to where they were.

Wasn't using them but that's an example.

I think it's the 177 driver I'll have to boot it up and check.

---

### Post by 2hot6ft2 on 2008-12-31
It's the 177.80 driver as recommended in hardware drivers.

---

### Post by bfinan0 on 2008-12-31
> **2hot6ft2 said:**
> Did you put /home on a separate partition? When I tried I had a problem with trying to save anything. It wouldn't let me choose a location to save it. Same went with opening things like windows wireless drivers wouldn't let me browse to where they were.

Wasn't using them but that's an example.

I think it's the 177 driver I'll have to boot it up and check.

I have the following partitions:
/sda1 (108GB) NTFS [Windows]
/sda2 (008GB) NTFS [HP_Recovery]
/sda3 (128GB) ext3 [/]
/sda4 (006GB) swap

---

### Post by 2hot6ft2 on 2008-12-31
Since I have the laptop on here's my /etc/modprobe.d/madwifi I have 2 blacklisted.
ath5k
and
ath_hal

---

### Post by 2hot6ft2 on 2008-12-31
> **bfinan0 said:**
> I have the same problems again as far as I can tell.  The open/save problem is still present, for one thing.
Can you get a screenshot of it?
> **bfinan0 said:**
> I have the following partitions:
/sda1 (108GB) NTFS [Windows]
/sda2 (008GB) NTFS [HP_Recovery]
/sda3 (128GB) ext3 [/]
/sda4 (006GB) swapOk, so it's not the same as I was having then. I don't remember if it was the 64 bit where I had that issue, I think it was.

---

### Post by bfinan0 on 2008-12-31
> **2hot6ft2 said:**
> Since I have the laptop on here's my /etc/modprobe.d/madwifi I have 2 blacklisted.
ath5k
and
ath_hal
My wifi actually is working, it's everything else I initially had wrong, that is still wrong...but thanks for solving the one problem that upgrading to Ultimate Edition did solve anyway.

---

### Post by bfinan0 on 2008-12-31
> **2hot6ft2 said:**
> Can you get a screenshot of it?
Ok, so it's not the same as I was having then. I don't remember if it was the 64 bit where I had that issue, I think it was.

It looks EXACTLY normal, it is just nonresponsive (only the cancel button does anything), just as referenced in the thread I linked to in the original post.

---

### Post by 2hot6ft2 on 2008-12-31
Use the graphics driver that it recommends in System>Administration>Hardware Drivers and let it do the install and activation. I'll look at what else you have listed and see what I can find.

---

### Post by bfinan0 on 2008-12-31
> **2hot6ft2 said:**
> Use the graphics driver that it recommends in System>Administration>Hardware Drivers and let it do the install and activation. I'll look at what else you have listed and see what I can find.

That's the one I'm using, NVidia 177.  I'm trying 180.11 because some people had better results with that one, I'll tell you how that fails.

---

### Post by 2hot6ft2 on 2008-12-31
> **bfinan0 said:**
> 
The trouble all started with the open/save dialog problem
[http://ubuntuforums.org/showthread.php?t=989581](http://ubuntuforums.org/showthread.php?t=989581)
except mine was worse (total freeze whenever one of these dialogs should have appeared.
The last post in that thread says.
> A recent update appears to have fixed the problem.
So update everything.

---

### Post by bfinan0 on 2008-12-31
> **2hot6ft2 said:**
> The last post in that thread says.

So update everything.

I have--that's why I'm now updating whatever I can find to alpha and beta versions as well, since the 274 updates found by the update manager did nothing (and might have made things slightly worse)

---

### Post by 2hot6ft2 on 2008-12-31
> **bfinan0 said:**
> 
There were updates available, including the new kernel (2.27..11), and completing those made the system revert to 640x480 monochrome, and did not solve the open/save dialog problem to begin with.

I tried reinstalling Nvidia 180.16, and lost GDM entirely 
[http://ubuntuforums.org/showthread.php?t=868411&highlight=seteuid](http://ubuntuforums.org/showthread.php?t=868411&highlight=seteuid)
(more or less same problem) and nothing I tried for this worked; for one thing, I get my internet exclusively through wifi, and thus have no access from the terminal.
That thread is from someone that upgraded from Hardy to Intrepid. Assuming you did a clean install you shouldn't have that issue. Also I use kernel 2.6.27-7 and don't even have that kernel yet.

---

### Post by 2hot6ft2 on 2008-12-31
Make sure your graphics driver has been activated in Hardware Manager. My last attempt at upgrading to a newer unsupported graphics driver had my desktop (not the laptop) screwed up for about an hour until I had the old one back in and set up again.

---

### Post by 2hot6ft2 on 2008-12-31
Here's a thread that may have a solution. [http://ubuntuforums.org/showthread.php?t=811795&highlight=open+save+issue&page=2](http://ubuntuforums.org/showthread.php?t=811795&highlight=open+save+issue&page=2)

---

### Post by bfinan0 on 2008-12-31
180.11 made the entire GDM crash again...bye bye Ubuntu :-4
Is there any way to get rid of a graphics driver from the terminal?  Would that even be enough to make the login screen appear?

---

### Post by 2hot6ft2 on 2008-12-31
reboot into recovery mode and fix xserver bottom choice then when it finishes boot normally the top choice.

---

### Post by bfinan0 on 2008-12-31
> **2hot6ft2 said:**
> reboot into recovery mode and fix xserver bottom choice then when it finishes boot normally the top choice.

That got rid of the bad driver (maybe) but now all I get when I boot is a black screen. (not even the terminal unless I do Ctrl-alt-F2 to get one)

---

### Post by 2hot6ft2 on 2008-12-31
use ```
startx
``` or ```
gdm start
```

---

### Post by bfinan0 on 2008-12-31
> **2hot6ft2 said:**
> use ```
startx
``` or ```
gdm start
```

startx: makes irretrievable black screen on all 8 ttys

gdm start: gives seteuid error
sudo gdm start: makes irretrievable black screen

...and the fails continue...

---

### Post by 2hot6ft2 on 2008-12-31
ctrl+alt+del to try again if it will even work. May have to use the power button. I really don't know what else to suggest. Someone with more knowledge will have to jump in here as I've only put myself in your position once and I just told you how I managed to get out of it. By shear chance.

---

### Post by bfinan0 on 2008-12-31
> **2hot6ft2 said:**
> ctrl+alt+del to try again if it will even work. May have to use the power button. I really don't know what else to suggest. Someone with more knowledge will have to jump in here as I've only put myself in your position once and I just told you how I managed to get out of it. By shear chance.

I think the next thing I'll try is a different linux, maybe Debian or PARSIX, see if one of them might work?

---

### Post by 2hot6ft2 on 2008-12-31
Well good luck. There are plenty to choose from here [http://www.livecdlist.com/](http://www.livecdlist.com/)

---

### Post by bfinan0 on 2009-01-01
Ditching GNOME and replacing it with KDE solved everything! :D :D :D

Does that mean I'm using KUbuntu now?

---

### Post by lyricalpapa on 2009-01-02
I've been using various flavors of Linux now for over 10 years.

I really like UBUNTU, but then I went through the same sequence of problems with my UBUNTU.

Changing to KUBUNTU temporarily solved my problems, but then my KUBUNTU went belly up and it was back the same problems.....

I've switched to Fedora 10 as my primary system for the time being.

It's not nearly as convenient as UBUNTU or KUBUNTU, but it doesn't appear to have the bugs that have cropped up in the recent 8.04/8.10 upgrades.

Fed10 Loaded without problems and it was off to the races.

There appears to be a problem associated with Debian based packages in general (like UBUNTU/KUBUNTU/..) that seems to be related to the maintainers decision to begin forcing the usage of IOMMU memory addressing option in the kernel. Only high end boards have this capability right now, and it can otherwise cause memory/video conflicts on some peoples motherboards. But the server administrators as a group are the people that take care of the high end development on Linux and they really appear to have wanted to force the adoption of IOMMU.

Fedora and other non-Debian packages apparently are not taking this step for now.

Good luck!](*,)

---

### Post by bfinan0 on 2009-01-03
> **lyricalpapa said:**
> I've been using various flavors of Linux now for over 10 years.

I really like UBUNTU, but then I went through the same sequence of problems with my UBUNTU.

Changing to KUBUNTU temporarily solved my problems, but then my KUBUNTU went belly up and it was back the same problems.....

I've switched to Fedora 10 as my primary system for the time being.

It's not nearly as convenient as UBUNTU or KUBUNTU, but it doesn't appear to have the bugs that have cropped up in the recent 8.04/8.10 upgrades.

Fed10 Loaded without problems and it was off to the races.

There appears to be a problem associated with Debian based packages in general (like UBUNTU/KUBUNTU/..) that seems to be related to the maintainers decision to begin forcing the usage of IOMMU memory addressing option in the kernel. Only high end boards have this capability right now, and it can otherwise cause memory/video conflicts on some peoples motherboards. But the server administrators as a group are the people that take care of the high end development on Linux and they really appear to have wanted to force the adoption of IOMMU.

Fedora and other non-Debian packages apparently are not taking this step for now.

Good luck!](*,)

That all makes sense except that I was able to trace my problem to Nautilus, of all things, not directly with the graphics drivers, since even when I did nothing with the drivers the same problems still happened.  It was only because so many other people (including you?) had various NVIDIA-related Ubuntu epic-fails that I started messing with video drivers, and immediately pinned those down as the cause when changing them made things appear even worse...

---

### Post by bfinan0 on 2009-01-09
Maybe it wasn't Nautilus after all.  Got rid of Compiz, returned to GNOME, installed 180.23, and everything works, better even than before this whole !@#$ing mess started!

---

### Post by duanedesign on 2009-01-21
I am on a HP G60-120us.
The Save As dialog box bug has a workaround (thanks to the_Ben) for this.
If you click the maximize button the dialog box will start responding, or redrawing. I noticed that even though the dialog box doesnt "appear" to be working, it is. I could save a file blindly and go to that directory and it would be there even though the dialog box didnt appear to do anything

If you use metacity instead of Compiz you will not experience this bug.

Also I am no longer experiencing this bug. One of the updates must have fixed it. I am using security/recommended/proposed updates.

Other than that bug and some choppy Flash videos my G60 works great. I am running Ubuntu Intrepid Ibex 8.10 and Linux kernel 2.6.27-11-generic.

---

### Post by bfinan0 on 2009-01-21
> **duanedesign said:**
> I am on a HP G60-120us.
The Save As dialog box bug has a workaround (thanks to the_Ben) for this.
If you click the maximize button the dialog box will start responding, or redrawing. I noticed that even though the dialog box doesnt "appear" to be working, it is. I could save a file blindly and go to that directory and it would be there even though the dialog box didnt appear to do anything

If you use metacity instead of Compiz you will not experience this bug.

Also I am no longer experiencing this bug. One of the updates must have fixed it. I am using security/recommended/proposed updates.

Other than that bug and some choppy Flash videos my G60 works great. I am running Ubuntu Intrepid Ibex 8.10 and Linux kernel 2.6.27-11-generic.
see my previous post, i knew that already, that was why it's marked [SOLVED] now.

---

