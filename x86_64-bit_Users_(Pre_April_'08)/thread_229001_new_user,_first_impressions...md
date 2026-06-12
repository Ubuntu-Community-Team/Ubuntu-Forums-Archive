---
title: "new user, first impressions.."
date: 2006-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by aceracer24 on 2006-08-03
Well let me start by saying I am not totally new to linux, i have over the years "tried" distro's with Suse being a favorit for some time. I evnetually found Gentoo as I think most people do when they are looking for something ne w and cutting edge. First time around I wasn't running a 64 bit CPU and everything went great. But like some/alot of people, the compiling from scratch even if it might make a diferance, can be long and boring. 

This time around I thought i would try Gentoo again this time with an AMD X2. I figured my compiling time would be much shorter. Well thier directions as far as I am concerned have gotten bad since my first time isntall a few years ago. Very confussing. But i muttled through hoping for the best. Finally getting the base gentoo installed I tried my first real emerge trying to get KDE. Ya, didn't go well, I think I got to about file 70 something before it failed. Ok, well I'll try to emerge gnome...again failed. I don't have alot of patience anymore like i used to so said screw gentoo I'll look for something else. 

Along comes Ubuntu. Decided to go for the 64 bit LiveCD. I must say, i was VERY impressed. Brings new meaning to the words "Just works". Sound worked, internet worked, both CPU's show, my HD's and video card work too! So I started right in trying to update/modify to my liking. This is when problems cropped up. 64 bit seems to be the bastard child when it comes to alot of things. Last to get updates, first with problems. I am sure this is the case with Gentoo and other distro's as well. So off to 32 bit land I went. 

I am not sure what the HUGE differance between the 32bit Live CD and the 64 bit one is but someone needs to fix the 32 bit version. It's slower by far then teh 64 bit. It does NOT support both CPU's out of the box either. Simple synaptic fixed that but still, kinda sucks. The reposatories (are they differant between the 32bit and 64bit) really pissed me off. SLOW and broken seemed to be the word for the day. So back to gentoo after some major frustration. 

Well I am back now, in Ubuntu 64bit because ..well Gentoo's LiveCD blows....Unbuntu's 64bit LiveCD is so much better ..even better then thier 32bit CD for some reason. 

I plan to hopefully stay, I hope some problems get addressed like the lack of 64bit stuff and someone PLEASE update with ALSA 1.0.11! Oh and can we get some updated kernels? Kernel.org is at 2.6.17 and we're still stuck with 2.6.15....

Sorry for the long boring post :)

---

### Post by tymek666 on 2006-08-04
If everything is working propertly with 2.6.15 kernel why do you need to upgrade to 2.6.17? Upgrade just for upgrade?

---

### Post by aceracer24 on 2006-08-09
> **tymek666 said:**
> If everything is working propertly with 2.6.15 kernel why do you need to upgrade to 2.6.17? Upgrade just for upgrade?

I like to compile my own kernel, to make it slimer, which I believe is what alot of people like to do. If I am going to go through all the trouble, then I might as well use the latest kernel. Plus, the newer kernels may address certain issues or add new stuff. Just to upgrade? No not really but...

---

### Post by RAOF on 2006-08-10
New versions of programs won't enter the official Dapper repositories, unless they are purely (or primarily) bugfixes.  You won't be seeing a different kernel, newer ALSA, mono, etc in the official repositories.  That's what a release is about; stabilise and freeze.

This, of course, doesn't stop you from building your own new packages.  It can occasionally be useful to build a recent kernel.org kernel (if it supports something you need that the Ubuntu kernel doesn't).

And I don't think that you'll find many people on this forum who like to compile their own kernels to make it slimmer.  Disc space is cheap; why not build every available module?  Maybe I'll buy one of those one day, and when I do, it'll work when I plug it in.  I won't have to recompile my kernel to get it to work.

---

### Post by KhaaL on 2006-09-02
correct me if im wrong, but dosen't compiling your own kernel let you choose what modules you want and what modules to no include at all? this makes the kernel also more optimized and less hogging on the RAM.

---

### Post by amgeex on 2006-09-02
There's a how to here in the forums that will show ya how to compile the latest kernel.org kernel, snoop around and you'll find it.

I've got a 64bit processor, but I run 32bit ubuntu and I've got no problems with the repositories, they're fast, stable. Also, the system runs fast as a whole, same as windows xp imo.

---

### Post by Kilz on 2006-09-02
> **amgeex said:**
> There's a how to here in the forums that will show ya how to compile the latest kernel.org kernel, snoop around and you'll find it.

I've got a 64bit processor, but I run 32bit ubuntu and I've got no problems with the repositories, they're fast, stable. Also, the system runs fast as a whole, same as windows xp imo.

As fast as Win XP? That isnt saying much.

---

### Post by RAOF on 2006-09-03
> **Khalid Rashid said:**
> correct me if im wrong, but dosen't compiling your own kernel let you choose what modules you want and what modules to no include at all? this makes the kernel also more optimized and less hogging on the RAM.
Modules that you don't use only take up HD space, not RAM.  Since the full Ubuntu kernel, including all the modules, takes up less than 100MB, you're going to save less than 100MB of harddrive space.  Since the kernel doesn't load modules that it doesn't use (ie: if you don't have the hardware, it doesn't load the driver), you won't really save any RAM at all.

The only worthwhile reason for compiling a custom kernel, in my opinion at least, is if the newer kernel **supports** something that the Ubuntu one doesn't (like a new piece of hardware, the Reiser4 filesystem, whatever).  There's no point in stripping stuff out - the kernel does that automatically.

---

### Post by aceracer24 on 2006-09-10
True, if things are loaded as a module then they won't run. But not everything in teh stock kernel is loaded as a module. Not afaik anyway. Besides compiling a kernel to slilm it down and what not, it makes for a good linux experience. Gives the user a chance to see what is actually in the system. Take into consideration that windows users never get to see the windows kernel.

---

### Post by RAOF on 2006-09-11
> **aceracer24 said:**
> True, if things are loaded as a module then they won't run. But not everything in teh stock kernel is loaded as a module. Not afaik anyway. Besides compiling a kernel to slilm it down and what not, it makes for a good linux experience. Gives the user a chance to see what is actually in the system. Take into consideration that windows users never get to see the windows kernel.

It's true that not everything is built as a module.  However, at least some of the things that aren't built as modules **need** to be built in.  If you build them as a module, you can't boot with the kernel :).

I'm skeptical about how much education building a kernel gives a linux user.  What do they learn?  That there's a bunch of cryptically named kernel modules?  Unless you **already** know what everything is, how does clicking some boxes in the kernel config help you?  Sure, there's the help (almost always along the lines of *Enables support for working around the broken **foo3.5** BAR protocol*).

The kernel is a black box, anyway.  Knowledge of kernel internals doesn't really help you in any **user** task, and I contend that configuring the kernel doesn't even give you any insight into the kernel internals.  The kernel is pretty much the least important (from a user-perspective) part of the system, anyway.  It's job is to run the interesting stuff, not be interesting in itself.

---

### Post by aceracer24 on 2006-09-11
It's true that it may not be as important as it used to be. Alot of common hardware now tyically runs out of the box so compiling a kernel isn't what it used to be in terms of need. Ubuntu does a great job with thier stock kernels. I'm a power user though. I can't keep everything stock. It's not my nature. I've compiled my kernel to include the beyond patch. Performance is my goal. Granted, I probably won't SEE a differance but in my mind, it's there. It's like overclocking a CPU or video card. Generally you don't see the speed increase with your eye, but damn those benchmarks don't lie!! ;)

---

### Post by tomdkat on 2006-09-11
> **aceracer24 said:**
> This time around I thought i would try Gentoo again this time with an AMD X2. I figured my compiling time would be much shorter. Well thier directions as far as I am concerned have gotten bad since my first time isntall a few years ago. Very confussing. But i muttled through hoping for the best. Finally getting the base gentoo installed I tried my first real emerge trying to get KDE. Ya, didn't go well, I think I got to about file 70 something before it failed. Ok, well I'll try to emerge gnome...again failed. I don't have alot of patience anymore like i used to so said screw gentoo I'll look for something else. I did this same thing.  :)  I got the base system installed and then said "then what" and could find instruction how to install the rest of it.  So, I gave Ubuntu a try and I've been mostly happy ever since.

I've been able to install just about anything I've wanted through the repositories.  I've built Gimp 2.3.1x from source and once I got all the development packages I needed installed, the build went flawless.

I must admit I've been itching to upgrade glib/gtk+/pango to the latest releases to see what Gimp 2.3.1x does differently but I'km scared I'll break something.  So, I'll wait for the next major Ubuntu release and see how things go.

My last Linux distro was Slackware 8 that I kept updated manually, which wasn't a bad deal.  :)

Good luck with your Ubuntu 64 experience.  :)

Peace...

---

### Post by aceracer24 on 2006-09-12
Every distro I have ever installed I have always said, ok, this is the time i will removed windows and never look back...every time I say that, I have always run back to windows because of a game, or because of some software I needed and end up staying with Windows for good. 

Ubuntu has been a fabulous experience into the latest Linux. It's been very easy to install, setup and use. So far, The only reason I have logged into windows is to share one of my game folders so that I can copy the game over to cedega. I'm not going to say I will never go back to windows, I am afraid of jinxing myself, but...Ubuntu gets used about 98% of the time and has been now for a few months. Whats that tell you?

---

