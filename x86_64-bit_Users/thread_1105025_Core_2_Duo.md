---
title: "Core 2 Duo"
date: 2009-03-24
forum: x86 64-bit Users
---

### Post by houcem on 2009-03-24
I have an Intel core 2 duo processor and would like to know more about its 64bit capabilities. When I search a GNU/Linux media I find that there is support for many architectures like amd64 ia64...Wich one fits my processor?

---

### Post by KCG102282 on 2009-03-24
AMD64 fits yours best however in my opinion it isnt worth it to switch to 64-bit yet.

---

### Post by houcem on 2009-03-24
Yes that's what I think too. But what about these: i386 i586 i686 ???

---

### Post by Seiji338 on 2009-03-24
Those are all 32 bit. Amd64 is what you want for 64 bit.

---

### Post by kpatz on 2009-03-24
> **KCG102282 said:**
> AMD64 fits yours best however in my opinion it isnt worth it to switch to 64-bit yet.In my opinion there is no reason NOT to use 64-bit if your hardware supports it.  Unless you're already running a 32-bit OS and are happy with it, if you're doing a fresh install, go 64.

If you have 4 GB or more of RAM, it's best utilized in 64-bit.

That said, AMD64 is the architecture that your Core2 uses.

I run Hardy 64-bit on my Core2Duo Myth box.  Works great.

---

### Post by KCG102282 on 2009-03-24
Flash is still a little buggy with 64bit which is why I dont use it.

---

### Post by Slim Odds on 2009-03-24
> **KCG102282 said:**
> Flash is still a little buggy with 64bit which is why I dont use it.

Which "flash" are you using?

Most folks that are using the new Adobe alpha 10 for 64 bit are having no problems. Works great for me.

My opinions is that the 64 bit no longer has the kinds of issues that it did years ago, but that most people are still afraid because they think that it does.

---

### Post by philinux on 2009-03-24
Flash not buggy here.

---

### Post by VastOne on 2009-03-24
> **Slim Odds said:**
> Which "flash" are you using?

Most folks that are using the new Adobe alpha 10 for 64 bit are having no problems. Works great for me.

My opinions is that the 64 bit no longer has the kinds of issues that it did years ago, but that most people are still afraid because they think that it does.

Totally agree with this statement.  Been using 64 bit since I began using Ubuntu 3+ years ago and have never had any issues that were not easily resolved and with Alpha 10 flash, it is a supreme machine, all flash issues dead and buried

V1

---

### Post by 3Miro on 2009-03-24
I can only see 3 reasons not to go 64-bit:

1. Hardware doesn't support it.
2. Already have 32-bit system working and you don't want to go trough the backup - install procedure again.
3. There is some very and I mean VERY specific driver that doesn't have a 64-bit version and you cannot or don't want to go trough the trouble of hacking around it.

---

### Post by Slim Odds on 2009-03-24
> **3Miro said:**
> I can only see 3 reasons not to go 64-bit:

1. Hardware doesn't support it.
2. Already have 32-bit system working and you don't want to go trough the backup - install procedure again.
3. There is some very and I mean VERY specific driver that doesn't have a 64-bit version and you cannot or don't want to go trough the trouble of hacking around it.

Understood, but 1 & 3 are rare. And, if you have recent machine with a 64 processor and at least 4G of RAM, you're not getting the most out of your machine. So 2 would just be lazy in that case.

But, each to his/her own.....

---

### Post by VastOne on 2009-03-24
> **philinux said:**
> Flash not buggy here.

Howz the Jaunty 64 doin for ya?

---

### Post by stchman on 2009-03-25
> **houcem said:**
> I have an Intel core 2 duo processor and would like to know more about its 64bit capabilities. When I search a GNU/Linux media I find that there is support for many architectures like amd64 ia64...Wich one fits my processor?

The Core 2 Duo is a 64 bit processor.  I have a Core 2 Duo laptop and a Core 2 Quad desktop that run 64 bit excellent.

Go with the 64 bit, allows you to have massive amount of RAM.

---

### Post by stchman on 2009-03-25
> **KCG102282 said:**
> AMD64 fits yours best however in my opinion it isnt worth it to switch to 64-bit yet.

That is your opinion.

I have been using 64 bit for a long time.  With the Flash 10 64 bit plugin that problem is resolved.  When I ran Flash 9 with the 32 bit nspluginwrapper I frankly could not see a difference between it and the 32 bit version of Flash 9.

I use openJDK and the GCJ plugin that give me Java capability.

I paid for a 64 bit processor so why not use it?  To me it was a no brainer.  Besides how else would I be able to use my 6GB RAM?

---

### Post by stchman on 2009-03-25
> **3Miro said:**
> I can only see 3 reasons not to go 64-bit:

1. Hardware doesn't support it.
2. Already have 32-bit system working and you don't want to go trough the backup - install procedure again.
3. There is some very and I mean VERY specific driver that doesn't have a 64-bit version and you cannot or don't want to go trough the trouble of hacking around it.

BS, in Linux the drivers are contained in the kernel.  The kernel is compiled using a 64 bit compiler so viola, 64 bit kernel, 64 bit drivers.

Give me examples of #3.  If you have the source code then you can make the driver, presto 64 bit module.

Nvidia and ATI have 64 bit drivers for their video cards.

Go 64 bit if you can.  Use 32 bit if your processor does not support 64 bit.

---

### Post by stchman on 2009-03-25
> **KCG102282 said:**
> Flash is still a little buggy with 64bit which is why I dont use it.

Flash 10 64 bit works GREAT on my (3) 64 bit Hardy boxes.

---

### Post by wangsuda on 2009-03-25
A couple of you mentioned large amounts of RAM for running 64 bit. Would 2 gig of RAM and an Intel Pentium dual-core processor T4200 (2 GHz) be enough to run 64 bit Jaunty?

---

### Post by VastOne on 2009-03-25
> **wangsuda said:**
> A couple of you mentioned large amounts of RAM for running 64 bit. Would 2 gig of RAM and an Intel Pentium dual-core processor T4200 (2 GHz) be enough to run 64 bit Jaunty?

Most certainly!

---

### Post by 3Miro on 2009-03-25
> **stchman said:**
> 
Give me examples of #3.  If you have the source code then you can make the driver, presto 64 bit module.


My printer driver. Canon did not release source, just a source RMP which in itself contained already pre-build 32-bit libraries so it could not be recompiled. As a result of that I have to mess around with VirtualBox and sharing the printer on the network from a virtual machine, works but it is ugly.

---

### Post by ameyer on 2009-03-26
> **Slim Odds said:**
> Understood, but 1 & 3 are rare. 
Actually, option 1 isn't that rare.
There's quite a bit of non-64 bit hardware out there (and quite a bit still in production.  CeleronM-based netbooks and IIRC most Atom-based netbooks don't support 64 bit).
If you're not counting hardware that doesn't support 64 bit because the processor just doesn't support 64 bit, I agree, though.

---

### Post by movieman on 2009-03-26
> **ameyer said:**
> CeleronM-based netbooks and IIRC most Atom-based netbooks don't support 64 bit

I don't think any netbook Atom CPU supports 64-bit; I believe Intel removed 64-bit support from the netbook chips to reduce the power consumption even further.

The desktop Atoms run AMD64 Ubuntu fine though.

---

### Post by lisati on 2009-03-26
> **ameyer said:**
> Actually, option 1 isn't that rare.
There's quite a bit of non-64 bit hardware out there (and quite a bit still in production.  CeleronM-based netbooks and IIRC most Atom-based netbooks don't support 64 bit).
If you're not counting hardware that doesn't support 64 bit because the processor just doesn't support 64 bit, I agree, though.

Hmmmm. I have one machine (not a netbook but a regular notebook/laptop) that uses a Celeron M. I must get round to putting in more RAM. I'm off to replace the 32-bit Ubuntu on the laptop I'm using now with 64-bit. Catch you later.

---

### Post by stchman on 2009-03-26
> **wangsuda said:**
> A couple of you mentioned large amounts of RAM for running 64 bit. Would 2 gig of RAM and an Intel Pentium dual-core processor T4200 (2 GHz) be enough to run 64 bit Jaunty?

Yes, the use of a 64 bit OS gives you the ability to use > 4GB RAM.

---

### Post by stchman on 2009-03-26
> **ameyer said:**
> Actually, option 1 isn't that rare.
There's quite a bit of non-64 bit hardware out there (and quite a bit still in production.  CeleronM-based netbooks and IIRC most Atom-based netbooks don't support 64 bit).
If you're not counting hardware that doesn't support 64 bit because the processor just doesn't support 64 bit, I agree, though.

The Celeron M and Intel Atom processors are not 64 bit.

---

### Post by stchman on 2009-03-26
> **3Miro said:**
> My printer driver. Canon did not release source, just a source RMP which in itself contained already pre-build 32-bit libraries so it could not be recompiled. As a result of that I have to mess around with VirtualBox and sharing the printer on the network from a virtual machine, works but it is ugly.

You can use Alien to convert the .rpm to a .deb, then use the ---force-architecture.

---

### Post by Slim Odds on 2009-03-26
> **stchman said:**
> You can use Alien to convert the .rpm to a .deb, then use the ---force-architecture.

That won't resolve all of the 32 libs that you may need to run it.

Search for "getlibs"

---

### Post by movieman on 2009-03-26
> **stchman said:**
> The Celeron M and Intel Atom processors are not 64 bit.

As I mentioned above, some Atoms are 64-bit and some aren't.

---

### Post by LowSky on 2009-03-27
> **VastOne said:**
> Howz the Jaunty 64 doin for ya?

I'll answer for Phil, 9.04 works well, but it is a BETA and it does have some thing not working so well, but that has little to do with using a 64bit OS. I have been using 64Bit for quite some time and it work well, flahs/java were never an issue, I just ran the 32bit versions at the time.


People are kidding themselves when they say "64bit isn't worth it" or "its buggy", Its fine!

---

### Post by wangsuda on 2009-03-27
[QUOTE=LowSky;6966284
People are kidding themselves when they say "64bit isn't worth it" or "its buggy", Its fine![/QUOTE]

Well, I'm ready to give it a try. When Jaunty has its final release, I'm going to 64 bit and the ext4 and everything. I want to see what my computer can do!

---

### Post by ameyer on 2009-03-27
> **stchman said:**
> The Celeron M and Intel Atom processors are not 64 bit.

Not exactly true, there are some Celeron M processors (going as far back as January 2007) that are 64 bit.
And the desktop Atom processors are also 64 bit.

But none of those chips are in netbooks.

---

### Post by loomsen on 2009-03-27
Jaunty here, 64 bit, don't see any reason why I wouldn't go for it...

Flash 64 not buggy at all, sun released a java64 RE, so...Just posted how to install it yesterday:

[How will I make Sun JRE amd64 version working](http://ubuntuforums.org/showthread.php?p=6958099#post6958099)

---

### Post by racerraul on 2009-03-27
Been using 8.10 64bit for a few months now...

No issues whatsoever, and I am still learning the ropes.
But from a beginners point of view, I have everything working on 4 diff machines... (2) 32bit and (2) 64bit.

Java & Flash are working just fine on all 4...
I do hate Java, though,,, but I hate Java even in Windows.

---

