---
title: "Installing 32bit version instead of 64bit"
date: 2005-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by !nkubus on 2005-10-19
I just installed the 64bit version of kubuntu.
i'm having a lot of troubles configuring it the way I want.

1.Couldn't get win32codecs to work properly even after trying all the tutorials on the forum.
2.Couldn't get flash to work properly either. even afer reding on teh forum .. gplflash make my firefox crash
3.Some of my games aren't starting anymore... Neverwinter Nights,Eternal-lands etc.

So i'm strongly thinking installing the 32bit version of kubuntu on my computer, so i<m asking is there a real performance drewbaxk in doing that ?

Since my Athlon64 is a Dual core would I loose also this performance Gain??

Thanks for your help :D

---

### Post by jecos on 2005-10-21
No you probably won't notice the difference.. unless you actually ran benchmarks to see..  I won't go 64bit till everything works like 32bit, cause no minor performance boost is worth the lack of working programs there are..

---

### Post by !nkubus on 2005-10-21
[QUOTE=jecos]No you probably won't notice the difference.. unless you actually ran benchmarks to see..  I won't go 64bit till everything works like 32bit, cause no minor performance boost is worth the lack of working programs there are..[/QUOTE]

I've managed to get the Chroot thing working, and i'm impressed everything works like a charm
so now my system is cleanly Hybrid

---

### Post by WiFi Net Guy on 2005-10-24
!nkubus,

I've just built a 64-bit AMD machine, but because of things I've read on the forum, decided to install 32-bit Kubuntu. I was a little scared-off due to the impression that most of my programs that I use won't work in the 64-bit version. Any suggestions or advise on whether to  go 64-bit or not?

Thanks...

---

### Post by !nkubus on 2005-10-24
Well actually all opensource programs work out of the box, without an hitch, but for the propriatay codecs like flash w32codecs won't work, so the solution is to build a 32bit userland in your chroot and install programms that need those codecs in there.

here is an interesting link on how to do that:
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)


a part from that it works #1 :)

hope it helps a bit :)

---

### Post by Hitman1 on 2005-10-25
This is an interesting thread. I'm thinking about upgrading my P4 3.06 Desktop to AMD64 dual core. However, reading these type of posts makes me can't help but think "Is there really enough performance gain that would offset the trouble?"

Guys with AMD64, can you please answer this dilema to me before I start spending cash and calories on installing a new system.

---

### Post by !nkubus on 2005-10-25
The performance gain will be with applications like: DVDRip, transcoce, mplayer mencoder. but for the rest I think there is not a big difference. I just think you feel better inside having the right Distribution for your processor.

Even if 90% of the applications works like a charm, you have troubles with propriatary software, and Backports who don't do 64 bit at that time.


If you don't want issuses go for 32 bit, but if you use a lot of multimedia ,encoding or DVD ripping ,as long you don'T use propriatary codecs like quicktime.. wmv, go for 64bit the performaces will increase a lot in those type of software.

For me the chroot trick kept me for changing back to 32 bit :)

hope it helps

---

### Post by gomadtroll on 2005-10-31
[QUOTE=Hitman1]This is an interesting thread. I'm thinking about upgrading my P4 3.06 Desktop to AMD64 dual core. However, reading these type of posts makes me can't help but think "Is there really enough performance gain that would offset the trouble?"

Guys with AMD64, can you please answer this dilema to me before I start spending cash and calories on installing a new system.[/QUOTE]

You might bee asking different questions. I am not familiar with the P4, but you may be asking to compare, possibly,  dual core (smp) to a single proc. Dual core does many things better? than a single core. Depends on how you work, or play.

The 64bit vs 32bit on a AMD64 proc is another question altogether, mostly the same answer though :-) 

Greg

---

