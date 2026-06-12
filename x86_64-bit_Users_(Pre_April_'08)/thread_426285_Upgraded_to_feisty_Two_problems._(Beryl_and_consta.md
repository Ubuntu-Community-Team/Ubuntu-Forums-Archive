---
title: "Upgraded to feisty: Two problems. (Beryl and constant CPU USE!)"
date: 2007-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by xeocub on 2007-04-28
Ok, so I updated Ubuntu to feisty from edgy (64 of course). First I had the same nvidia driver problems as I've had before with edgy (x wouldn't start), but installing the legacy drivers seemed to work. 
So it seems fine now, except that Beryl doesn't REALLY load (no window decorations, effects etc.. splash screen works fine though)

Second problem is that it seems that my CPU is 100% in use, (fan is on full speed too) but when I check system monitor and add up all the percentages form different programs it comes to about 15%

Can anyone help?

---

### Post by nevin on 2007-04-29
i'm having a similar problem with the CPU and I'm very certain it's beryl...

however, i ended up doing a clean install of fiesty when the upgrade sucked and then installed beryl, it started using all my cpu and heating up my laptop like crazy.

don't know what happened...
hopefully there will be a solution.

---

### Post by Meir on 2007-04-29
I had this problem and fixed it by tinkering with the settings in my xorg.conf. Unforuntately I don't remember exactly what I changed so I can't be of much help there but maybe you should post a copy of it here and someone will catch something.

---

### Post by BIGtrouble77 on 2007-04-29
I find that beagle is an HUGE cpu hog.  Might want to make sure that beagle's not the culprit.  On my system I notice that beryl does use the system resources quite a bit, but rarely causes my cpu to step out of 1ghz mode.  Beagle, on the other hand, will make my cpu race at random times.

---

### Post by xeocub on 2007-04-29
> **BIGtrouble77 said:**
> I find that beagle is an HUGE cpu hog.  Might want to make sure that beagle's not the culprit.  On my system I notice that beryl does use the system resources quite a bit, but rarely causes my cpu to step out of 1ghz mode.  Beagle, on the other hand, will make my cpu race at random times.

Actually, even though system monitor didn't tell me this it was Beryl that was eating all my resources... 
It seems to work for certain animations etc and then not at all for others. It just bogs my PC down when I attempt to run it

anything I could try?

---

### Post by xeocub on 2007-04-30
.... Why is beryl not working?

---

### Post by ronocdh on 2007-05-01
> **xeocub said:**
> .... Why is beryl not working?
Trying starting Beryl by typing **beryl-manager** in the terminal; do you get any error output?

---

### Post by xeocub on 2007-05-01
> **ronocdh said:**
> Trying starting Beryl by typing **beryl-manager** in the terminal; do you get any error output?

I've tried that and no I do not. Beryl seems to work fine like I said. But it does not have some of the effects etc... and continuously uses my CPU 100%

It seems like it is a driver issue with the nvidia drivers, but everything I've done has worked with edgy. 
So far I am pretty unhappy with feisty, it seems much slower when compared to edgy and I've already had more problems

---

### Post by ronocdh on 2007-05-01
> **xeocub said:**
> I've tried that and no I do not. Beryl seems to work fine like I said. But it does not have some of the effects etc... and continuously uses my CPU 100%

It seems like it is a driver issue with the nvidia drivers, but everything I've done has worked with edgy. 
So far I am pretty unhappy with feisty, it seems much slower when compared to edgy and I've already had more problems
By and large I agree with you; Feisty seems "edgier" than Edgy in a lot of ways! But what I like about this is that the community is talking a lot to solve the issues, and the steps taken toward integrated things like desktop effects is absolutely a smart move. With Leopard pushed back to October (Leopard will be shipping with core animation), and Vista hopelessly behind the times, a feature like this is very important to the GNU/Linux community in terms of marketshare; have you noticed the number of hits the Beryl videos get on YouTube? ;)

That said, I hope you solve the problem soon. I have Radeons in all my computers, and the issues are all different, with the sole similarity being that nowhere does everything work. :popcorn: But progress happens...

---

### Post by xeocub on 2007-05-02
I'm almost tempted to downgrade back to Edgy with all this... it really runs terribly slow. Even open office, it gets very annoying when it has to reload the entire window simply because it was minimized (and it does so very very slowly)

Is there a way to downgrade as easily as upgrade?

---

