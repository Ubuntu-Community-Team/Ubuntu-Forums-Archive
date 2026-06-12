---
title: "Poor (Choppy) Performance in Urban Terror, 64bit"
date: 2008-12-16
forum: x86 64-bit Users
---

### Post by PreviousN on 2008-12-16
Hi everyone. In Gutsy I would regularly be able to play urban terror at around 100FPS. I've got a pretty good computer. Specs:

AMD Phenom 9600
4 GB of RAM
GeForce 8800gs

Anyways, my problem is that ever since installing Ibex I've been getting around 80FPS, then after about 10 minutes it slows down to about 40fps (in a choppy kind of way, making it unplayable). I've been trying to fix this FOREVER, and am now giving up and posting a help request to the forums. 

At first I thought it was my drivers, so I installed the newest drivers. I've got: 
* 177.80 NVIDIA drivers

I next thought it was my video card overheating. So I installed windows XP. I've never gotten the same fps in XP as in ubuntu (usually faster in ubuntu). 
* In ubuntu I'm getting ~40-70 fps
* In windows I'm getting 60-80 fps

So I know that my video card isn't over heating. 

I then thought, hey, maybe my hard drive is dying? Since I was playing off a diff hard drive when using windows. So I created a RAID (1), which technically doesn't speed up the process as much as a 0, but I care about my data. Anywho, I am still experiencing the problem. 

I've checked out top when the game is running, and its sucking down a lot of horsepower. About 90% of my cpu. I think that is 90% of one cpu, btw. My computer is a quad-core. 

I've read about problems with processor affinity, which only really occurs on windows, and can't find info about it on ubuntu.

Well, that is about it. I make sure to set my cpu scaling monitors to 2.2GHz before I start playing, and I make sure to switch to Metacity, so no desktop effects. 

Any ideas?

---

### Post by Perturbed Penguin on 2009-11-12
I know this is WAY after the fact... but I was having similar problems and switching to metacity fixed everything... just in case you need it here is the command(use 'alt+f2' to open the 'run application' dialog):

metacity --replace

...and then when you want to switch back to compiz:

compiz --replace

This probably won't help at all especially considering this is what, a year late? But thats how I got things up and running.

---

