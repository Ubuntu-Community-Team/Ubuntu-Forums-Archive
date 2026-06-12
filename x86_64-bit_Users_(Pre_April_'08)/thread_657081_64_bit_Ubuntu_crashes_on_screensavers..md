---
title: "64 bit Ubuntu crashes on screensavers."
date: 2008-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by khensucat on 2008-01-03
Hi everyone!

I have been using Ubuntu since Fiesty. My hubby built me a nice computer with a 2 core Intel 64 bit processor and 2 gigs of ram for Christmas. I have some trouble, though. Every time I click to go to the screensaver configuration option, my whole OS crashes, except for the mouse cursor, but it won't click on anything. The keyboard is unresponsive, and control+alt+F1 doesn't bring anything up :(

I think it's also crashing things when the screensaver starts, but I can't access the screensaver menu to change anything. I have an LCD monitor, so I don't even really need one.

My hubby could probably fix it, but he won't. He uses Debian?, and said he won't work on a Ubuntu system, and that learning what is wrong and fixing it would be better for me than him just fixing it. Well, it's frustrating me!! I've finally registered here, so I could look around and ask this question! I'm not sure what the Debian thing is supposed to mean, but I think he is being a snobby pig  :mad: 

Anyway, I like Ubuntu. But I have some strange little problems on these new parts that I didn't have before. This is the biggest. Here is what I know I have on my new machine (he built it). I'm copying from the boxes :lolflag:

Asrock 775DUAL-VSTA
Intel E2140 Dual Core
2 gigabytes of Kingston ddr2 667 ram
500 watt NoiseTaker2 power suppy thing
NVidia Geforce 5500 AGP

Some pillaged drives from my old Dell 3000. 

Although I've tried and have the same problems on 32 and 64 bit, I'd like to use the 64 bit version because I do alot of photo-editing and similar activities both semi professionaly and for a hobby. I also have a very extensive CD collection that I'd like to import, so figuring this out on 64 bit is my priority.

ANY help would be so much appreciated. Looks like I'm on my own on this one :( Thank you everyone!

Oh, let me edit to add this: He says this motherboard overclocks VERY easily. He asked me if I wanted to "get 500 free megahertz (sp?) per core?", and I said "NO! Just leave things how they're supposed to be!" :D So everything is set to "default", I guess is how you'd say it.

---

### Post by ed_x on 2008-01-03
Looks like you can join the club, struggling with this issue: [http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905) (you do have desktop effects enabled?).

---

### Post by khensucat on 2008-01-03
I've tried with compiz both on and off, on both 32 and 64 bit :( I've even tried Dapper, and although it seemed to be running well, I coulnd't figure out how to get the Nvidia driver working through synaptic, and the Envy script for Dapper always left my system hanging at boot, no matter how I tried it :(

Is there simply a way, like possibly a command in the terminal, to disable screensavers without having to click on the menu? My system will lock up completely even if I simply try to click into that menu option just to turn them off :(

---

### Post by gururise on 2008-01-04
I have a Core 2 Quad with an Nvidia 8500GT.  Running the nvidia drivers, the **braid** screensaver will consistenly freeze my machine.

Any workarounds?  Right now I'm using another screensaver.

---

### Post by Moop on 2008-01-04
> **khensucat said:**
> I've tried with compiz both on and off, on both 32 and 64 bit :( I've even tried Dapper, and although it seemed to be running well, I coulnd't figure out how to get the Nvidia driver working through synaptic, and the Envy script for Dapper always left my system hanging at boot, no matter how I tried it :(

Is there simply a way, like possibly a command in the terminal, to disable screensavers without having to click on the menu? My system will lock up completely even if I simply try to click into that menu option just to turn them off :(

There is a post here with a command for disabling the screensaver. Use sudo to run it. 
[http://ubuntuforums.org/showthread.php?t=428967]("http://ubuntuforums.org/showthread.php?t=428967")

You can also delete the screensaver it's stuck on from the directory /usr/share/applications/screensavers. Navigate to that directory using sudo nautilus and delete the screensaver causing problems.

---

### Post by khensucat on 2008-01-04
I never did get Ubuntu solved, but installing Kubuntu 7.10 amd, and using Kilz' flash-installer, has produced a perfect and crash free *buntu Linux desktop. I simply cannot make it misbehave now :) Not the GNOME I am used to, but I'm quite happy to be rid of the useless "eye-candy", and it's sooooo stable now :guitar:

---

### Post by khensucat on 2008-01-05
Hmm. Used that to then install ubuntu-desktop.

Things are running perfectly in GNOME, with the benefit of some nice KDE apps as well, like Amarok and K3b. Might be the long way around, but things are perfectly stable, and no crashes, even while looking at the different screensavers :D

---

### Post by Nando777 on 2008-01-24
An easier way to change the screensaver without having to edit anything is by turning off the Desktop effects

Go to Preferences --> Appearance --> Visual Effects and choose None

If you do that your system won't crash.

It's been more than a year since this problem was discovered an nVidia hasn't done anything to fix it yet. 

Make sure you delete the screensaver file afterwards by going /usr/share/applications/screensavers/ 

The screensaver name is Braid. something.

---

