---
title: "AMD64 Processor: Only 32bit Gibbon Works (?)"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by bosks.k on 2007-12-05
I've downloaded and burnt both 32 and 64bit versions of Gutsy. For some odd reason, only the 32b version works. When I try running the 64bit CD, as soon as I press 'enter' on the main CD menu, it does the whole 'kernel loading...' thing, then boots me to a console window where a really quick msg flashes (of which all I can read before it disappears is 'blah-blah-blah-random-numbers: out of memory").

At which point the screen goes blank. I *know* the CD continues to load. I can see it reading, and eventually it stops (at which I can only imagine it to be the LiveCD desktop) but the screen is just black the whole time.

I have 3GBs of RAM and an nVidia GTS8800.
Processor is AMD 64 X2 4800+

(... I *highly* doubt the system is /actually/ out of memory)

If there's a way to record the error msg, or if you need any more info, let me know. As of right now, I have no idea how to get the 64bit version running. :(

---

### Post by Mark76 on 2007-12-05
You can run 32 bit Ubuntu on a 64 bit machine!? :?

---

### Post by rsambuca on 2007-12-05
Using the liveCD's with an 8800 is pretty hit and miss at best.  It could also be a bad burn.  If you are going to install, I suggest using the alternate CD anyways.  Then you can install the nvidia driver after installation.

Mark76 - Yes.

---

### Post by anakrich on 2007-12-05
I have similar configuration and I run 64 bit version of Gutsy. Could you post the exact error you are getting?

---

### Post by jgrabham on 2007-12-05
Hmm, I have that problem with one of my monitors, but not the other; if you can try another monitor, could be something to do with trying an unsupported resolution or something.  (I dont have a dual monitor setup or anything, I just swap the monitors)

---

### Post by bosks.k on 2007-12-05
I wish I could post the exact error, but it only stays on the screen for a second or two before it goes blank. I thought it may be the unsupported resolution thing. I tried different settings. My monitor's native res is 1440x900@60Hz. I dunno if I could manually set it as an option while loading the kernel or something.

But I doubt the wrong rez would give me an OOM error.

What makes an 8800 install hit and miss? I mean, it works perfectly with the 32bit CD. Unless the drivers are fundamentally different for both versions, I don't know what the difference could be.

I noticed there's an option to install with an "updated driver cd". Would that help?

---

### Post by Kilz on 2007-12-05
> **bosks.k said:**
> I wish I could post the exact error, but it only stays on the screen for a second or two before it goes blank. I thought it may be the unsupported resolution thing. I tried different settings. My monitor's native res is 1440x900@60Hz. I dunno if I could manually set it as an option while loading the kernel or something.

But I doubt the wrong rez would give me an OOM error.

What makes an 8800 install hit and miss? I mean, it works perfectly with the 32bit CD. Unless the drivers are fundamentally different for both versions, I don't know what the difference could be.

I noticed there's an option to install with an "updated driver cd". Would that help?


It isnt just your card, as a rule it is best to use the alternate cd with the 64bit version. IMHO its because few people report bugs with the live cd on launchpad and so they never get fixed.

---

### Post by RAOF on 2007-12-06
> **bosks.k said:**
> ...
What makes an 8800 install hit and miss? 
...

Your card is very new, and has a significantly different architecture from previous nvidia cards.  There are undoubtedly bugs in the 8800 support, and there may well be amd64-specific bugs there (particularly since x86-64 generally gets less testing than IA32).  Using the alternate CD is a work-around here.

---

### Post by linuxuser187 on 2007-12-06
i don't know if this will help at all but when i installed i had the exact same problem, it would boot and you would hear the cd loading and nothing but a black screen, i used noapic irqpoll noirqdebug in my grub line boot up and it worked, press f6 when you have "install ubuntu" highlighted to gett the boot string options at the botom, if that doesn't work then try "start ubuntu in safe graphics mode", if that still doesn't work try selecting again safe graphics mode + f6 and put in noapic irqpoll noirqdebug, i suspect that perhaps the open source drivers might have a issue with these new cards, if you get ubuntu loaded from the live cd you could install from within, if you get it installed try to use the restricted driver and see if that works, hope it helps!

---

### Post by Jouke74 on 2007-12-06
Yup, see also the "Black screen on boot (with Nvidia 8800)" posts, because after you have installed the Alternate CD. You probably gone have this problem as well.

---

