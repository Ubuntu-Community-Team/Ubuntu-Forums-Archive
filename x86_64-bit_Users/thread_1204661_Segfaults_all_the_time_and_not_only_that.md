---
title: "Segfaults all the time and not only that"
date: 2009-07-05
forum: x86 64-bit Users
---

### Post by alkisx on 2009-07-05
So I removed windows vista from my laptop (custom made) which was working with no problems in every aspect.

I decided to install ubuntu 9.04. Everything went perfect, install, and then boot from the new ubuntu installation.

The nightmare starts from the first update, through synaptic, update manager or apt-get.

from the very simple update, I will probably got segfaults here and there bad file descriptors on some files. I may get simple green screen on boot after I install restricted drivers for my nvidia. I may have problems using Add/Remove programs or Synaptic of update manager freezing the hole system for unknown reasons.

I installed ubuntu in about 10 or more times (had time to spent:)).

Oh and the best part, I may get hard disk errors (software not hardware) which are fixed after an fsck. 

Did ram check, and passed without errors.

The system may work well for about an hour most, but may present problems. It may crash an application (no matter what).

Anyway, I decided to replace ubuntu with kubuntu. I had similar problems (not so much though) in the past with ubuntu on some systems, and installing kubuntu made everything went great. Strange thing but's the truth (maybe there are some problems with gtk? I don't know).

So after installing kubuntu, everything seemed to work ok. Did my upgrades a couple or three times. All OK.

Then I tried to install some programms using the console with apt-get. every time I tried I get either segfault in the installation, or ever worst, a "Segmentation faulty tree...0%" terminating every further step.

And I wonder: Why both ubuntu and kubuntu work perfect without any update, but there is a total mess after it (at least 9.04 versions)?

I have to note here That I have installed ubuntu and kubuntu on lots of pcs last two years. Never faced such a mess.

Also, I installed slackware 32bit as also the new -current 64bit, both worked perfect (as always). But in this situation I want to install ubuntu.

My system: Intel Centrino T8300.
GPU: NVidia 8700M GT.

Every hardware on my laptop is recognized and work as it should (except that problem that may happen with nvidia, but I don't think its the problem).

---

### Post by seanbarman on 2009-07-05
I must admit that since i've installed jaunty 64, I feel like I need a new pc. I get smart errors, gimp crashes etc but my hardware
passes every test.. Everything worked fine with 8.10..
Ubuntu seem obsessed with boot times... things take time to initialize...

I have been with ubuntu since the start, but am seriously thinking
about moving on now.. maybe debian...

stability is more important than cutting edge..

---

### Post by alkisx on 2009-07-05
Well, I've installed jaunty in about 10 pcs, 1 server (the server version) and 3 netbooks. The only problem I had before was only with the server, I had 3 interfaces and it had problems recognising the nics in the right order even if I declared them manualy. Removed it and installed debian and is performing excellent.

Since desktop versions (even betas) installed well, I start thinkinh that there is something wrong with the quality of the last upgrade packages, and/or the last updated mechanism of the updates.

I prefer ubuntu for linux dekstop, but these problems last days is too much. This situation makes you think that backtrack, gentoo or ever freebsd would better fit the desktop than ubuntu! 

What is going on?

---

### Post by seanbarman on 2009-07-05
I do quite a lot of graphical work...I finally made the switch from ps to gimp with 8.10... took the time to learn it.. now it seems unusable freezing with multiple images open...

I have done hours of memory tests hard disk tests.. but nothing...
My main issue is gimp and nautilus crashing...

everything else is ok..
I burnt a dual layer dvd no errors.. so i doubt its my pc...

memory passed
smart extended passed
samsung diagnostics passed
cpu burn passed
orthos passed 
ubuntu failed

---

### Post by ShadowTek on 2009-07-05
The only segfault problems that I get is when trying to run pSX, but I can keep that from happening by doing **sudo killall pulseaudio** before starting pSX.

I have no idea if pulseaudio has anything to do with your problem or not, just thought I'd pass that along.

---

