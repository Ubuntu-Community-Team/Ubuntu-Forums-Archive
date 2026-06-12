---
title: "Suggestions for AMD64 System"
date: 2006-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by 2fargon on 2006-06-17
Hi Folks,

I want to build an AMD 64 based system, and after a couple of hours of searching on the net I still have a few questions buzzing in my brain. So I'll let the more knowledgeable tell me how to start.

I have trouble finding whether things work with Linux or not, so that's what made me think of asking here. Please be kind, I am a total n00b when it comes to building systems, and yet my education has seen to it that I am broke, too, presently.

I want to build an AMD 64 based system to replace my 1998 IBM Intellistar (I know, the dinosaur :) )

I have some leftovers:
A DVD Burner and a DVD Reader (both IDE internal)
A 200 GIG harddrive and a 40 gig HDD (IDE internal)
Keyboard + Mouse + Monitor

I need:
Enough graphics performance to be able to play most games decently. Perhaps not a cutting-edge gaming machine, but good enough for WoW, MS Flight simulator etc.
Good sound, with a sound card.
Most importantly, keep the cost below $500 (I already have the HDD, Optical Drives, Monitor)

So,
1) Nvidia, or ATI? (Which has 64 bit drivers that work easily with Dapper?)
2) Which video card? (for the casual gamer)
3) Which motherboard?
4) Which soundcard - I tend to like Creative cards, but do they work without issues?

I will appreciate tips when it comes to keeping the desktop silent. My current PC sounds like a Jet engine :)

Thanks for you help. If I get a few starting points, I can go off on my own, but the sum of the things I have read so far confuse me.

---

### Post by x64Jimbo on 2006-06-17
You should keep several things in mind:
Gaming is improving on the Linux desktop, but it is a Far Cry (tm) from perfect. If you're planning to play a lot of games, you should dual boot with WinXP. And make sure your Windows is 32 bit, though. 64bit windows is powerful but not very compatible with stuff.
There's a pretty big bug in the ati drivers right now that causes the machine to hang whenever the window manager is terminated, effectively preventing clean shutdowns on those machines. I'd suggest going with an nVidia for now, until that problem is fixed. 
I've had great luck with MSI motherboards. They are quite robust in features, and typically incorporate the best chipsets for audio. For that reason, I usually don't need to buy a sound card because they come with full surround capabilities. 
As far as noise goes, try to find a case that has few but large fans. The small ones tend to have to spin faster to get the same amount of work done. My case just has one 120mm fan in the back. It's pretty quiet compared to my other homebrew creations. Use the factory CPU fan. Don't overclock, and you won't need anything better. You can get even quieter by going with an aftermarket fan, but you have to be selective. Make sure you check the dB specs and compare before you buy.

---

### Post by Kilz on 2006-06-17
[QUOTE=x64Jimbo]There's a pretty big bug in the ati drivers right now that causes the machine to hang whenever the window manager is terminated, effectively preventing clean shutdowns on those machines. [/QUOTE]
This mainly effects people with the radon x200 onboard graphics. I had the problem. The problem is with the 8.25.18 drivers from ATI. The 8.24.8 drivers work fine and the 8.25.18 drivers offer no noticeable improvement over the old ones. Sadly if you have upgraded to 8.25.18 it is almost impossible to completely remove them from  your system without a reinstall. You can get the drivers to revert, but you wont get acceleration.

---

### Post by flip314 on 2006-06-18
[QUOTE=x64Jimbo]There's a pretty big bug in the ati drivers right now that causes the machine to hang whenever the window manager is terminated, effectively preventing clean shutdowns on those machines. I'd suggest going with an nVidia for now, until that problem is fixed. [/QUOTE]

As Kilz said, that depends on your card.  I've got a 200M and get clean shutdowns every time.

That said, if you have the choice, nVidia has MUCH MUCH better linux driver support at this time.  Unfortunately, NOBODY sells turion64 laptops with nVidia cards, so I had to go with a radeon >.<

---

### Post by hajk on 2006-06-18
[QUOTE=2fargon]
I will appreciate tips when it comes to keeping the desktop silent. My current PC sounds like a Jet engine :)
[/QUOTE]

You don't need a super graphics card for those games, cards based on nVidia GeForce 6200 PCI-E are cheap and *passively* cooled (e.g.silent). Most mother boards come with a noisy fan on the Northbridge chipset: replace it with a Zalman 
NB47J passive aluminum heatsink (will cost you all of five dollars), which is most easily done before you mount the mother board in the case. Invest in a new PSU with a large temperature/speed-controlled fan, and may be put another 8cm fan with separate manual speed control (a resistor) on the case. Needless to say, that's what I did -- my system is eerily quiet now: inside of the case runs about 4 degrees C above ambient. 

See my sig for a recommendation on the stuff that you don't already have -- definitely go dual core, as you can then do more things *simultaneously*.

---

### Post by steabert on 2006-06-18
MSI K8N Neo 4 FI mobo ~100$
NVIDIA Geforce 6600GT ~160$
AMD Athlon 64 X2 3800+ ~310$

---

### Post by craiglarry on 2006-11-28
You sound like me.I'm here on Ubunut Forums looking for an answer to this non specific question. I've been trying for a month to get some good results. In addtion to facing being a newbie on Linux Ubuntu, I have chosen 64 bit because I have a AMD 64 and want a OS that advantages the processor. I had no idea what added difficulties there would be because so many progs and utilities are not going to work on 64 bit even natively written and even for the experienced users. I try to install and it does install, but the program never comes to the light of day. I could perhaps find a solution to this particular problem, though I have not yet. I also have a problem because the adsl in China, where I live, also doesn't recognize Linus base. Because so many, even the tech people, have never even heard of Linux, so how could they be prepared technically for it?
So here is the BIG QUESTION! After a month of beating my head against all these walls, shouldn't I just trash 64 bit and install over it with i386 (32 bit)and perhaps be happy with something that has at least a small chance of success? The 64 bit issue has just made the difficult impossible, I think.  

> **2fargon said:**
> Hi Folks,

I want to build an AMD 64 based system, and after a couple of hours of searching on the net I still have a few questions buzzing in my brain. So I'll let the more knowledgeable tell me how to start.

I have trouble finding whether things work with Linux or not, so that's what made me think of asking here. Please be kind, I am a total n00b when it comes to building systems, and yet my education has seen to it that I am broke, too, presently.

I want to build an AMD 64 based system to replace my 1998 IBM Intellistar (I know, the dinosaur :) )

I have some leftovers:
A DVD Burner and a DVD Reader (both IDE internal)
A 200 GIG harddrive and a 40 gig HDD (IDE internal)
Keyboard + Mouse + Monitor

I need:
Enough graphics performance to be able to play most games decently. Perhaps not a cutting-edge gaming machine, but good enough for WoW, MS Flight simulator etc.
Good sound, with a sound card.
Most importantly, keep the cost below $500 (I already have the HDD, Optical Drives, Monitor)

So,
1) Nvidia, or ATI? (Which has 64 bit drivers that work easily with Dapper?)
2) Which video card? (for the casual gamer)
3) Which motherboard?
4) Which soundcard - I tend to like Creative cards, but do they work without issues?

I will appreciate tips when it comes to keeping the desktop silent. My current PC sounds like a Jet engine :)

Thanks for you help. If I get a few starting points, I can go off on my own, but the sum of the things I have read so far confuse me.

---

### Post by arjaybe on 2006-11-28
craiglarry said: I have chosen 64 bit because I have a AMD 64 and want a OS that advantages the processor.

That's a good choice.

craiglarry said: I had no idea what added difficulties there would be.

There's nothing wrong with not knowing.  That just means you get to learn something.

graiglarry said: adsl in China, where I live, also doesn't recognize Linus base.

That's a little off the topic of 64-bit vs 32-bit.

craiglarry said: shouldn't I just trash 64 bit and install over it with i386 (32 bit)

Yes, you should.  You've satisfied your curiosity over 64-bit and I can tell that you'll be happier using something that is more mature.  You can try 64-bit again later.

---

