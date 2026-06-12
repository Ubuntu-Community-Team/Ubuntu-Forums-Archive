---
title: "[Sound] Alsa, OSS, ESD HDA Generic"
date: 2007-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by #Reistlehr- on 2007-02-09
Hey guy's and girls. Well it just turned to 1 week on ubuntu, and i gotta say i love it. Only thing is, it's been a trip. I have a Dv9000z, HP, and have had quite  a few problems. I'm kind of hoping that someone could give me some pointers, and get my last couple problems worked out.

I could not get my Broadcom 4310 wireless to work, i tried everything from ndiswrapper, fwcutter, and  a few other things. I think it might be a result of noapic in the boot line. If i take it out, x crashes, and i have  afeeling that it's also part of my sound problem.

Without the noapic, x crashes, and i get could not initialize nvidia device. screens found, but no are usable. took me about 2 days to figure out that problem. I also have to run acpi=off in the boot line, or ill freeze on boot, like a lot of people.

i went out, bought a Zonet ZEW2500p, and now i have my wireless working, somehow. it was not plug and play, i had to play with the drivers, and it just randomly started working after installing ndiswrapper, but no drivers, and network manager, but when network manager loads on start, it wont work, but if i uninstall it, it wont work. im so confussed!!!!

the one thing i really want to figure out is my sound. 
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
 It's not the intel chip like i've heard some people say. those drivers dont work. i cant get alsa, oss, or esd to work. It recognizes the card, i can raise, lower, and mute sound, only i dont have any. when i go to system -> preferences -> sound, and hit test, i get  

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not negotiate format
```

im at a loss. i miss windows, it's so much easier to get everything configured, and takes about 30 seconds. linux, it takes weeks, and nothing works...

i tried to make a 2.6.20.0/1 kernel but kept getting corrupt errors.

hopefully someone can help me!!!!!!

---

### Post by #Reistlehr- on 2007-02-10
also, i noticed, the first fresh edgy install, i had a battery life indicator that worked fine. is it because of noapic and acpi=off that i dont have that funcionality either?

---

