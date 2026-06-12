---
title: "Killed?"
date: 2006-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pianoguy on 2006-01-16
Alright, I'm getting very fustrated.

I'm trying to install Ubuntu. Everything starts okay, as soon as its starts to install, it gives me the "Killed" message. Alright, I'm new with this..but..I need help? What does this mean?

---

### Post by ssam on 2006-01-16
we'll need some more info.

what computer do you have?
what version of ubuntu?
how far does the install get?
does the live cd work?

hopefully we can then help you.

---

### Post by Pianoguy on 2006-01-19
[QUOTE=ssam]we'll need some more info.

what computer do you have?
what version of ubuntu?
how far does the install get?
does the live cd work?

hopefully we can then help you.[/QUOTE]

Its a Laptop, Tobisha model No: PAS250U A Toshiba 1000 Series , 20GB 
The newest version 
After It checks for drives, As soon as it installs..It says, "Killed" and it stops.
Well? This laptops harddrive is reformated...

:) Hopefully, you guys can:D

---

### Post by Pianoguy on 2006-01-21
[QUOTE=Pianoguy]Its a Laptop, Tobisha model No: PAS250U A, 20GB 
The newest version 
After It checks for drives, As soon as it installs..It says, "Killed" and it stops.
Well? This laptops harddrive is reformated...

:) Hopefully, you guys can:D[/QUOTE]


HELLO!?

I should of stayed with Windows:confused:

---

### Post by slux on 2006-01-21
Something is killing the installation process and as the only mechanism that semi-randomly kills processes is the Linux kernel out of memory (OOM) killer, I think you are having problems with that. Your machine doesn't sound like it has low memory but how much does it?

---

### Post by Ptero-4 on 2006-01-23
Pianoguy. Is your laptop reporting all your ram. It may be an old shady BIOS. In that case write append="MEM=XXXMB" at the end of the grub boot entry (in /boot/grub/menu.1st) where the XXX is the amount of ram your computer have. It may also be bad or dodgy ram which needs to be replaced. Or it may be a TCPA protected BIOS (latest phoenix bios are like this) In this particular case. there's no solution. Your only course of action would be to take the laptop back to the store for a refund and get yourself an Apple PPC one (note that I refer to iBook/PowerBook, not the Intel based MacBooks, those seems a bit shady.).

---

### Post by Pianoguy on 2006-01-27
Well, I'm currently looking at the screen infront of me. I'm a newbie so I'll write all this down.
ACPI BIOS=7.20
MEMORY: 32768KB

---

### Post by Jason_25 on 2006-01-27
You may want to recheck that.  32mb isn't enough to run any modern OS with a gui.

---

### Post by h3xx3r on 2006-01-27
I was messing with an old laptop earlier this evening with 64MB of ram And hit exactly the same message when the install tried to load the disk partitioner , So I'm saying its a memory issue also :)
Mine almost booted the live cd though. Just got fed up after 20 minutes or so of booting :mrgreen: 
All this was just an experiment I never expected breezy to install or the live cd to be smooth.
We do some strange things when we're bored.

---

### Post by benjordan06 on 2006-01-27
try something lighter weight..... say... fluxbox...

---

### Post by tgunner on 2006-01-28
This may be a stupid question, but are you trying to install the PPC version?
Also, this post shouldn't be in the MAC section, try in the laptop section for x86.  :-k

---

### Post by Dragonfly_X on 2006-01-30
[QUOTE=tgunner]This may be a stupid question, but are you trying to install the PPC version?
Also, this post shouldn't be in the MAC section, try in the laptop section for x86.  :-k[/QUOTE]

Yeah,  Gunner is right! This post shouldn't be in this section but we all make mistakes especially the noobs, so we'll forgive you this time!

Try something like the new Slax or DSL(Damn Small Linux)! You might get away with that and 32mb of memory, however I would recommend that you at least double the ram in your machine to even think about running a modern OS with a GUI at an almost acceptable speed. :KS

---

