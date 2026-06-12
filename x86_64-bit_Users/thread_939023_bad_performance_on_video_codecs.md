---
title: "bad performance on video codecs"
date: 2008-10-05
forum: x86 64-bit Users
---

### Post by LoneWolfJack on 2008-10-05
Is it just me or are we getting a terrible performance on most video codecs? 

I own a movie production company (just commercials and short films so far, you understand :) ) and so I'm dealing with 100 to 200 of short videos that need to be reviewed every day.

Now every time I run a video in totem or vlc, my CPUs go to 100% load ad the fans go off, which is pretty annoying.

My office machine is a dual processor Xeon system (3.8 GHz) with 4 GB of RAM so I really wouldn't expect such performance issues.

I assume that the devs who ported the codecs to linux just wanted to get them working and didn't optimize the code, but that's just guessing. But if it's only me who is having those problems, I may have to buy a new system.

This ain't no bashing the dev's, just wondering.

---

### Post by jespdj on 2008-10-05
It might be a problem with your graphics card driver. What brand and model is your graphics card and what drivers are you using - are you using the restricted drivers made by your graphics card manufacturer or open source drivers which don't offer accelerated graphics?

---

### Post by LoneWolfJack on 2008-10-05
that's quite possible... I have an ATI 1800XT and I am using the restricted drivers, but it never worked out right. compiz seems to work fine, but for wine etc. I always have to specifiy Display:=0 to get hardware acceleration.

---

### Post by tuxxy on 2008-10-05
Its very possiblly your card, I had issues with ATI drivers in the past, never got an ATI card functioning flawlessly with compiz or videos for example, even on numerous cards.

I stick with nvidia chips now for my main desktop where I will be using multimedia apps and run effects etc

---

### Post by LoneWolfJack on 2008-10-05
yeah, I'll probably get a new office machine with the release of ibex and that one certainly is going to have an nvidia card.

but good to know those performance issues are none that are specific to linux.

---

### Post by joshuachad on 2008-10-05
I hate to even suggest this but it has been the case at one time. Are you running 64bit Ubuntu and if so maybe try the 32 bit version. Sometimes not always I have expirienced more bugginess on the 64bit side of the fence especially when it comes to drivers. Im no expert but I would suggest trying that especially if it can be done easily for you. Easier than getting a new box at least.

---

### Post by Kilz on 2008-10-06
> **joshuachad said:**
> I hate to even suggest this but it has been the case at one time. Are you running 64bit Ubuntu and if so maybe try the 32 bit version. Sometimes not always I have expirienced more bugginess on the 64bit side of the fence especially when it comes to drivers. Im no expert but I would suggest trying that especially if it can be done easily for you. Easier than getting a new box at least.

Please, unless you have some proof that a specific problem exists. Do not post suggestions that problems may be based on the bit someone is running.

I personally think its all FUD, and people posting these kind of uninformed guesses tend to make it spread farther. 

You may have had a driver issue, if you like I will pull up a dozen posts from the forums of people running the 32bit version with driver issues.

---

### Post by Yellow Pasque on 2008-10-06
It sounds like the ATI driver might be installed incorrectly. What is the output from:
```
fglrxinfo
glxinfo | grep direct
```

> Are you running 64bit Ubuntu and if so maybe try the 32 bit version.
Video processing uses large integers, an area where 64-bit computing excels in performance. Downgrading to 32-bit is not going to make performance better.

---

### Post by LoneWolfJack on 2008-10-06
Temüjin, I know these commands... have used them far too often. quite frankly, I don't have the time to fiddle with those stupid drivers.

But here's the output nevertheless:

> 
fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 2.1.7281 Release


> 
glxinfo | grep direct

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


Mesa means no hardware acceleration, but here's something else which has been puzzling me for months:

> 
DISPLAY=:0 glxinfo | grep direct

direct rendering: Yes


---

### Post by Yellow Pasque on 2008-10-06
> quite frankly, I don't have the time to fiddle with those stupid drivers.
So you just made a thread to complain and hope it will magically fix itself?

Make sure this is in your /etc/X11/xorg.conf (gksudo gedit /etc/X11/xorg.conf)
```
Section "DRI"
	Mode 0666
EndSection
```

---

### Post by LoneWolfJack on 2008-10-06
> So you just made a thread to complain and hope it will magically fix itself?

I started this thread to find out whether the performance issues are a known problem. In fact, I was pretty sure the problems were a result of bad codec ports. Yet I'm glad to hear that they're not but whether or not I will have time to fiddle with graphics card drivers again is a whole different story.

But thanks a lot for trying to help, I will try that (as my xorg.conf is indeed missing those lines) and report back later today.

BTW: I was not complaining, I was pointing out a problem. There's a difference.

---

### Post by Robstarusa on 2008-10-06
> **LoneWolfJack said:**
> I started this thread to find out whether the performance issues are a known problem. In fact, I was pretty sure the problems were a result of bad codec ports. Yet I'm glad to hear that they're not but whether or not I will have time to fiddle with graphics card drivers again is a whole different story.

But thanks a lot for trying to help, I will try that (as my xorg.conf is indeed missing those lines) and report back later today.

BTW: I was not complaining, I was pointing out a problem. There's a difference.

IMHO, The preferred graphics choices under Linux (for X) are:
1) Intel
2) Nvidia
3) ???
4) Ati.

It may have changed recently but I've never had much luck with ATi.

---

### Post by Kilz on 2008-10-06
> **Robstarusa said:**
> IMHO, The preferred graphics choices under Linux (for X) are:
1) Intel
2) Nvidia
3) ???
4) Ati.

It may have changed recently but I've never had much luck with ATi.

I wouldnt use anything but ATI. My experiences with nvidia are awful, and I would not use intel in any way shape or form.

---

### Post by krazyd on 2008-10-06
@OP the open source drivers in the latest ubuntu intrepid support your card. keen to upgrade to the beta?

---

### Post by Kilz on 2008-10-06
> **krazyd said:**
> @OP the open source drivers in the latest ubuntu intrepid support your card. keen to upgrade to the beta?

It has been pointed out that he uses this for work, beta are not recommended for mission critical machines. I also have a feeling that anyone who cant be bothered to play with video driver settings is not the best candidate to run a beta.

---

### Post by LoneWolfJack on 2008-10-06
right. also, even when ibex comes out, I will certainly not be among the first to upgrade to make sure I'm not upgrading to a version that is as buggy as hardy was (for me).

that aside, I tried to add those lines to my xorg.conf but to no avail. Does it take a special command to make the changes become effective? I think I remember something like that.

---

