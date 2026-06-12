---
title: "64bit lappy 1st time questions"
date: 2006-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by starscalling on 2006-09-20
my brother has a laptop that runs with a turon64 cpu [64 bit]
when i installed ubuntu on it i left it all in 32bit mode
but that makes his chip act like a 800MHz chip [the cpu] instead of about 1800MHz. this is all well and good and fine for now; but i would like to update his lappy to the 64bit proggies so that its as powerful as it can be.
one beautiful attestment to ubuntu is that it currently runs faster like that than his windows install does ;p 
so how do i go about updating his install? [please dont tell me i gotta reinstall.. :/]

---

### Post by Kilz on 2006-09-20
> **starscalling said:**
> my brother has a laptop that runs with a turon64 cpu [64 bit]
when i installed ubuntu on it i left it all in 32bit mode
but that makes his chip act like a 800MHz chip [the cpu] instead of about 1800MHz. this is all well and good and fine for now; but i would like to update his lappy to the 64bit proggies so that its as powerful as it can be.
one beautiful attestment to ubuntu is that it currently runs faster like that than his windows install does ;p 
so how do i go about updating his install? [please dont tell me i gotta reinstall.. :/]

You cant update from the 32bit version to the 64bit version. You have to start over and install the 64bit version.

---

### Post by starscalling on 2006-09-21
so i need a different install disk right?
what one is for amd / 64 bit

---

### Post by RAOF on 2006-09-21
> **starscalling said:**
> my brother has a laptop that runs with a turon64 cpu [64 bit]
when i installed ubuntu on it i left it all in 32bit mode
but that makes his chip act like a 800MHz chip [the cpu] instead of about 1800MHz. 
...

That's probably the CPU frequency scaling kicking in.  That will happend in the 64bit version, too, and it's no bad thing.  It saves power and makes the laptop run cooler.  When you do something processor intensive (the default is using more than 20% of current CPU capacity, from memory), it will scale the CPU back up to full speed, and then back down again when the CPU utilisation drops again.

You'd need the AMD64 install disc (either desktop or alternate, it doesn't matter).

---

### Post by starscalling on 2006-09-21
oh wow
didnt realize such an advanced feature was avaliable in ubuntu lol
are there any laptop specific programs i should make sure are in there?
i have heard a few horror stories about lappies going brick :/
[outside of 64-bit install of course i mean]

---

### Post by acefreely on 2006-09-22
Its not an ubuntu feature, it is the BIOS of the laptop.  

I have the same problem on my Dell D800 (POS).  However I don't see it as a good thing.  I want my CPU full speed all the time.  There is a setting in my BIOS to turn the feature off but it does not work.  If running on battery or battery not fully charged CPU scalling kicks in...pain in the arse!

---

### Post by kick6 on 2006-09-22
> **acefreely said:**
> Its not an ubuntu feature, it is the BIOS of the laptop.  

I have the same problem on my Dell D800 (POS).  However I don't see it as a good thing.  I want my CPU full speed all the time.  There is a setting in my BIOS to turn the feature off but it does not work.  If running on battery or battery not fully charged CPU scalling kicks in...pain in the arse!

My laptop is like this as well.  I HAVE to have it plugged into the wall to be able to game.

---

### Post by Jmurray on 2007-11-01
I have the 64 bit CD and a turon64 laptop.  ubuntu refuses to install saying i need 32bit version?.  i remain docked so i am not concerned about power usage.

hp dv5139us 2ghz  2gb

---

