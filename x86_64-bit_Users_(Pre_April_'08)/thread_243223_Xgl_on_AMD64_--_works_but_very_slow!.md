---
title: "Xgl on AMD64 -- works but very slow!"
date: 2006-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by tegwilym on 2006-08-24
I just got Xgl/Compiz working on my computer.  It looks great, but its so slow it's pretty much unusable.  I do have a really good computer, so it should run fine, but I must have something screwed up.  Here is what I have - 
[LIST]
[*]AMD64 3200+ CPU
[*]Nvidia GeForce 6200 with 256 Megs
[*]1 Gig RAM
[*]Ubuntu 6.06 for 64bit (fresh install)
[/LIST]
I seem to have the common problem I read on here where it boots to a blank screen with the spinning pointer. I then do a CTL-ALT f2 (or similar) then go back to CTL-ALT F7 and I can log in.  Compiz and Xgl are up and running with no problem but the Wobble is very slow as well as everything else that I run on it.  CPU load doesn't seem too bad, but Xgl is at the top of the list of running resources.  Does anyone have some idea about what I should ajust to get this running at a usuble speed?

Tom 
- Victim of Vista Beta2 (and gave up!)

---

### Post by The Warlock on 2006-08-24
Assuming you have the nvidia drivers and such all running properly, it might be that the 6200 just doesn't have the oomph to push Compiz. You know that the 6200 doesn't actually have 256MB of RAM, it's just leeching off of the system memory, right?

---

### Post by John.Michael.Kane on 2006-08-24
@tegwilym i'm running xgl/compiz on the spec's listed.I'm not experiencing the issues you are.

AMD 3000+ 939
BioStar T-Force
1-GB DDR400
Geforce 6100-IGP Note: Xgl/compiz tested one this with 64 and 128MB Ram,
64bit dapper

What guide/howto: did you use to get xgl/compiz going?

---

### Post by quad3d@work on 2006-08-25
What does fglrxinfo returns on shell? Seems like you are not using optimized OpenGL libs.

My laptop has ATI X200 Xpress (shared RAM) and runs xgl/compiz adequately.

---

### Post by Lonthong on 2006-08-25
> **quad3d@work said:**
> What does fglrxinfo returns on shell? Seems like you are not using optimized OpenGL libs.

My laptop has ATI X200 Xpress (shared RAM) and runs xgl/compiz adequately.

Which how-to did you follow or do you mind to write down yr steps to get successful installation (AMD64 + ATI)?? :) 
I followed 2 different how-to & in the end I had to reinstall Ubuntu ](*,)

---

### Post by alesdoc on 2006-08-25
> My laptop has ATI X200 Xpress (shared RAM) and runs xgl/compiz adequately.

My laptop has also ATI X200 Xpress

```
alessandro@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

Xgl starts, but when i try start compiz --replace gconf (after i started gnome-window-decorator) my screen gets black. I can switch to another console (Alt+crtl+F1) but i can't see my desktop environment. Maybe is some option of compiz? 

Can you help me?

Thanks

---

### Post by tegwilym on 2006-08-25
I replied last night, but I guess it didn't get here.  
As for the 6200 being shared memory, I didn't realize it did that, but then my older Ti4200 on another computer at home works perfectly - well almost - I still have to get the title bars back, but it's quick at least and is running in KDE.  It's also a 32 bit machine if that makes a difference.

The computer that is giving me fits is my AMD64 here at work.  Of course Windows Vista Beta 2 gives it a 2/5 on hardware requirements for Vista, so of course it would run like crap!  HA!  ;) 

I was trying it in Gnome on the work computer, maybe I'll switch over to KDE and see if that works like the other computer I have at home.

Frustrating at times, but I'm not giving up just yet.

Tom

---

### Post by maubp on 2006-08-25
> **The Warlock said:**
> You know that the 6200 doesn't actually have 256MB of RAM, it's just leeching off of the system memory, right?
Pants.  I wouldn't have picked if I had known that :(

I just wanted a cheap passively cooled card for my new shuttle.

If I can get it to do Xgl/Compiz etc then it won't be too bad I guess...

---

### Post by John.Michael.Kane on 2006-08-25
@tegwilym,and maubp my 6100 geforce is on the mainboard it too is shared mem,and it runs xgl/compiz just fine. I'm not sure why you both are having issues.

---

### Post by hajk on 2006-08-25
Nothing wrong with GeForce 6200, Xgl/Compiz ran fine on my AMD rig (see sig) before I decided to ditch it for other reasons...

---

### Post by maubp on 2006-08-25
> **hajk said:**
> Nothing wrong with GeForce 6200, Xgl/Compiz ran fine on my AMD rig (see sig) before I decided to ditch it for other reasons...

I'll give it another go, but I was getting the window decorators vanishing when - something other threads had reported but with no clear resolution.

It is reassuring that the card is capable of it...

---

### Post by sarmadzhiev on 2006-08-26
> **alesdoc said:**
> My laptop has also ATI X200 Xpress

```
alessandro@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

Xgl starts, but when i try start compiz --replace gconf (after i started gnome-window-decorator) my screen gets black. I can switch to another console (Alt+crtl+F1) but i can't see my desktop environment. Maybe is some option of compiz? 

Can you help me?

Thanks
Same problem here. 
Xgl starts, compiz too, but blackscreen. 
My card is 7300 Nvidia, and Xgl and Compiz works fine under gentoo. 
Fresh ubuntu install - nada. Compiz is black screen. 

What I notice - Direct Render under Xgl does not work. Under X Direct render is fine. May be this is the problem or some libGL issue (nvidia mess this up badly when you install the driver). 
I am new on Ubuntu, any ideas how to fix it?

Update: if I use this repo
```

deb http://ubuntu.moshen.de/ dapper all

```
and then re-install xgl, compiz, gliz and libgl1-mesa compiz and Xgl start working. Use cgwd instead of gnome-window-decorator and start it before compiz. It is working just fine.

---

