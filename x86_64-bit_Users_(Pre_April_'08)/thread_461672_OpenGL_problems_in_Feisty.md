---
title: "OpenGL problems in Feisty?"
date: 2007-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sk8teOrDie on 2007-06-01
Beware..I'm a newb. I recently installed Feisty. I'm running an AMD 6400, with integrated GeForce 6150 (C51PV). I installed Tremulous last week. When I try to run it, the screen goes black, and then it logs me off. So, I tried another game, Open Arena. Same story. I've looked at a few other threads about this problem, but none of them on a 64 bit processor. I've come across a lot of other problems because of this. The most I've been able to gather is that my system is not able to support Open GL. However, [Nvidia]("http://www.nvidia.com/page/gpu_mobo_features.html") says that my hardware should. Has anyone else had Open GL problems with a 64 bit? Any suggestions?

Thanks

---

### Post by dreadlord_chris on 2007-06-02
Which drivers do you have installed for your GeForce? You're probably gonna need the propietary drivers from NVIDIA...

---

### Post by byrophyta on 2007-11-13
I'm sorry to bump this so far. but I've got the same issue, and I thought starting a new thread might be bad..

I'm running Kubuntu, an AMD64 proccessor and a generic Geforce mx 420-(t or p dunno?)

Basically I just switched because I was sick of trying to get the graphics card to work on mandriva, and viola out of the box kubuntu has no problems...

Except that open arena gives me a black screen before crashing/giving up. I assume it has no problems with the graphics card and might be the 64 bit processor? is there some unsatisfied dependency like Mesa gl (which I can't find in the add applications list)?

is there any other info that could help?

---

### Post by Cute Poison on 2007-11-13
Guday.. 
Mate I'm right there working on this lil problem..

First things first. have you managed to install and run your restricted drivers? a good way to tell if your computer is going to play games and do cool 3d effects is to run Beryl (compriz) if you can have windows burning up and your desktop rotating in a cube then you would have no doubt the Correct drivers installed and running.

My thoughts are you don't have any restricted drivers installed. and even when you do you may encounter the Black screen of death.

It's a good suggestion you try the newbie full proof method of installations via "Automatix" or "Envy" (use google to search for these. they should be 1st result) 

If you do encounter this screen of death (if you used Automatix2) you can recover your desktop by pressing escape before the Ubuntu splash screen and run this line "automatix-nvidia-recover" and your desktop will be revived. 

Lastly.. for those who suffer the Black screen of death you may try this thread for last resorts.. before you try a new video card. [http://ubuntuforums.org/showthread.php?t=57368&highlight=64bit+drivers+Nvidia]("http://ubuntuforums.org/showthread.php?t=57368&highlight=64bit+drivers+Nvidia")

Hope this helps you in your quest..

---

### Post by byrophyta on 2007-11-13
so I got the automatix .deb package and it won't install.

It says that I have some other package installer open and running, which is wrong. The last package handler (update handler) I had open asked if I wanted to upgrade the whole operating system, which I thought was ridiculous since I literally just downloaded kubuntu and installed on friday and I don't see any other  upgrades since then. so I figured it was a ploy to pay for something and I clicked on quit.

pressing quit on a package handler does mean that it has been quitted, right?

it's not in the run away process catcher, and there is no other evidence that any package handler for that matter is running at all except for "automatix2_2.0.1-7.10gutsy_amd64.deb"

did I miss something? can I find update handler in some other mystical place in the filesystem now that it has disappeared from the kmenu and the kicker in general?
thanks for the help and sorry for being such an ubuntu noob.

---

### Post by byrophyta on 2007-11-13
> **Cute Poison said:**
> 
My thoughts are you don't have any restricted drivers installed...



oh and I saw a pop-up when I first started to get "restricted and proprietary drivers" which I proceded to avoid like the plague in fear that they would ask for a credit card # and my money... I can't re-create this instance to install those drivers.

is there some command in the terminal that I can use to invoke this pop-up or wizard or handler or whatever it's called. 

thanks.

---

