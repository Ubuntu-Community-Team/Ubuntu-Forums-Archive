---
title: "WC3 stalls when launched"
date: 2008-02-15
forum: Wine
---

### Post by 3th0s on 2008-02-15
So i'm running wine 9.54. Previously, i was running .46 (i think) due to the battle.net bug. I hadn't played in a few months, and saw that the new wine versions had eliminated the battle.net bug.
Unfortunately now when I launch wc3 (I'm launching it via apps->wine->programs->wc3->TFT), it brings up the little "launching TFT" window thing, then it resets my screen resolution, and then the splash window goes away, and nothing happens. "Launching WC3 sits in my panel at the bottom, but it doesn't do anything. I can't right click and close it, i can't xkill it via terminal, and it won't get past this.
Any ideas?
I'm running 7.10 ubutu btw

---

### Post by SBFC on 2008-02-15
I'm actually experiencing the same problem. Just started recently too. Still worked 0.9.53 IIRC.

Anywho, since Wine 0.9.55 is out now I suppose I'll upgrade when I get home from work and see if that fixes it.

---

### Post by GCrew37 on 2008-02-15
I'm by no means an expert (in fact I just installed Linux for the first time yesterday), but I've been wrasslin' with WC3 for the last little while and I've found I can get it running if I open the System Monitor and find and shut down an application called Warcraft III.ex

I'm not sure what this program is related to, but it may be part of the copy protection.  This kinda confuses me as I thought that 1.21b removed the CD check.  Anyone else know more about this?

---

### Post by 3th0s on 2008-02-15
Sorry, but what is this system monitor you're talking about?

---

### Post by GCrew37 on 2008-02-15
It's under the System tab > Administration

I'm not sure if it makes a difference, but I installed it under Wine-Doors, which seemed to know what it was doing, so if closing the file doesn't work, that may be your next step.

Cheers.

---

### Post by SBFC on 2008-02-15
Unfortunately the problem persists in Wine 0.9.55. This is unfortunate. Warcraft III has worked since Wine was still in alpha...and now it breaks...dang.

---

### Post by 3th0s on 2008-02-15
Sigh. The system monitor quick-fix isn't working. Still lost >.<

---

### Post by SBFC on 2008-02-17
Noticed this error...

```
 Cannot change screen BPP from 32 to 16
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @75! (XRandR) 
```

The game is trying to start at a different color depth and xrandr can't change it for some reason. Thought it was because I didn't have any modes listed for 16 color depth in my xorg.conf file so I added them. Still receive the error.

@75...apparently it's looking for a mode with a refresh rate of 75? I'm not even sure if that's possible...think my monitor refresh rate is 60....

Anywho, did a lot of searching and couldn't really come up with anything. On one form I visited it sounded like people attributed it to the latest nvidia drivers...and a rollback apparently solved it. Haven't tried it myself, however.

Was trying to find an ini file that war3 stores it's settings in to change the res mode in hopes that it would work..but I can't seem to locate the file that stores settings.

---

