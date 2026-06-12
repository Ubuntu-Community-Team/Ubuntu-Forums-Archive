---
title: "Core 2 Dou laptop: install 32 or 64 bit?"
date: 2007-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by psi36 on 2007-01-03
I've just bought a HP NX7400 notebook and it's arriving tomorrow or the day after tomorrow.
It's this configuration: [http://www.backoffice.be/shop/details.asp?partid=RH399EA%23UUG](http://www.backoffice.be/shop/details.asp?partid=RH399EA%23UUG)
So with a Core 2 Duo processor.

My question is quite simple: 
Should I install the 32 or 64 bit version of Ubuntu? 
What are the good points and the bad points of Ubuntu 64 compared to 32?

I'll be using it for surfing (Firefox 2), some coding, maybe some photo editing (GIMP), listening to MP3's (Amarok), DJ'ing (Mixx), VJ'ing. 
I've heard that a lot of progs aren't 64 yet, does that mean they won't run at all on a 64 bit Ubuntu?

---

### Post by Azakus on 2007-01-03
A Core 2 Duo processor has 64-bit registers, so it can run the 64-bit Ubuntu.
I would recommend the 64-bit as you will see significant speed increases (I've seen specs of ~30%) that make applications open faster and heavily reduces time on CPU dependent processes such as video and audio transcoding (I have transcoded 600 MB of MP3's to Ogg vorbis in 1min 36 seconds).
As for the "not many 64-bit applications" myth, I have yet to find a program that doesn't have a 64-bit build. The only programs I need to run 32 bit are Flash and Java in a 32-bit Firefox so that they work correctly since Flash hasen't released a 64-bit Linux version yet and Java support is flaky on 64-bit Firefox (but Blackdown's free Java has a working 64-bit version).
That being said, even if a tool isn't 32-bit and you can't compile it yourself, 32-bit programs work perfectly in a 64-bit operating system with the ia32 libs and the tool linux32 (just not the other way around).

---

### Post by psi36 on 2007-01-03
Is it possible to have both 32 and 64 bit versions of Firefox installed? The fist only for websites that use Flash and Java and the second for normal browsing?

---

### Post by kleeman on 2007-01-03
> **psi36 said:**
> Is it possible to have both 32 and 64 bit versions of Firefox installed? The fist only for websites that use Flash and Java and the second for normal browsing?
Yes that is exactly what I do. The 64bit version will be standard and you can get the 32bit version from 
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)

---

### Post by chronusdark on 2007-01-03
if i were you i would save yourself some trouble and keep to 32bit for a bit longer my experience shows 64 bits apps a lil buggy and if something isint released as 64 you will have to do a bit of hacking to get it running

i will prolly stick with 32bit for another year or so when more people get 64bit processors and developers start recognizing it more

just my 2 cents you do whatever you want..i like hacking but i need a stable system more

---

### Post by psi36 on 2007-01-04
I was gonna go for dual boot Win XP and Ubuntu 64, but maybe I should make a triple boot with Ubuntu 32. Problem is I only have 80 Gig hard disk, so triple boot is even less space to spare.

---

### Post by psi36 on 2007-01-04
In the downloads section I only see 64-bit PC (AMD64) desktop CD. 
Is this only for AMD's 64 bit processors (that's what it says) or does this work on Core 2 Duo? Or what should I download?

---

### Post by rajeev1204 on 2007-01-04
hi

As far as i know intel core 2 duo is a 32 BIT PROCESSOR. Only Xeon range is 64 BIT.

All that 64 bit register and extended memory 64 technology is marketing mumbo jumbo.Intel nomenclature is confusing .

AMD 64 is the only one for desktop that is true 64 bit.

I think when  u insert the cd , it will say incorrect processor version


I could be wrong !

regards

rajeev

---

### Post by kleeman on 2007-01-04
> **rajeev1204 said:**
> hi

As far as i know intel core 2 duo is a 32 BIT PROCESSOR. Only Xeon range is 64 BIT.

All that 64 bit register and extended memory 64 technology is marketing mumbo jumbo.Intel nomenclature is confusing .

AMD 64 is the only one for desktop that is true 64 bit.

I think when  u insert the cd , it will say incorrect processor version


I could be wrong !

regards

rajeev
I'm not sure what you mean exactly here. The Core 2 Duo has the standard intel em64t extension which is basically the amd64 extension. This enables both 32bit and 64bit apps. 
This extension definitely speeds things up. Look at this comparison for a mac:

[http://www.geekpatrol.ca/2006/11/macbook-core-2-duo-performance/](http://www.geekpatrol.ca/2006/11/macbook-core-2-duo-performance/)

---

### Post by Azakus on 2007-01-04
Uh, when a processor has 64-bit registers, then it is a 64-bit processor. That's what 64-bit registers means. The _Core 2 Duo_ is a 64-bit processor that can use the 64-bit Ubuntu.
The original _Core Duo_ did not have 64-bit extensions, so it was not a 64-bit processor.

---

### Post by rajeev1204 on 2007-01-04
ok 

Intel wont advertise properly so i got confused.So this means all new intel processors are 64 bit?Or only the core 2 duo? Are all core 2 duo's 64 bit?

Even the ubuntu download page mentions iso for the AMD 64 architecture, i think that is why this thread exists.

---

### Post by psi36 on 2007-01-04
Well, the question is: 
Are there any off you who are using Ubuntu 64 on Core 2 Duo?
And is that the version that says AMD64?

---

### Post by rajeev1204 on 2007-01-04
yaaa

U summed it up well psi

I use AMD ATHLON 64 with 64 bit dapper .

ok i will try to find some more about ur processor


good luck and stick in here


regards

rajeev

---

### Post by rockets on 2007-01-04
I think the original Core Duo, which is in my laptop and labeled "Centrino Duo", is 32 bits. It is a very confusing nomenclature from Intel.

---

### Post by rajeev1204 on 2007-01-04
Hi again

I confirmed that all new intel core 2 duo processors are 64 bit( THEY SHOULD PUT THAT ON THE COVER PHEW ! ) . Of course they will run 32 bit fine just like the AMD 64.

So psi , go ahead and download the amd 64 version

As for advaantages / disadvantages between 32 and 64 bit

Almost everything in repos is available for 32 and 64 bit . Games too run fine.

I only found 1 problem .ie . wmv 9 doesnt play on 64 bit .( But with some extra software that too is possible . Automatix is that software tool ( [www.getautomatix.com](www.getautomatix.com)) . Streaming media over the internet is a sore point .

Otherwise 64 bit is cool and definitely faster with multimedia applications like DVD authoring and stuff. 

One more thing - there is no flash for 64 bit  but a program called nspluginwrapper lets u use the 32 bit flash plugin with 64 bit firefox which is really simple to follow . I will guide u with that.

64 Bit is the way to go forward.
so go ahead and install .Good luck

regards

rajeev

---

### Post by psi36 on 2007-01-04
> **rockets said:**
> I think the original Core Duo, which is in my laptop and labeled "Centrino Duo", is 32 bits. It is a very confusing nomenclature from Intel.
What I read/heard is that Core Duo is 32 bit only and Core 2 Duo also supports 64 bits.
Once you know that it isn't that confusing anymore. ;)

---

### Post by mikewhatever on 2007-01-06
Core 2 Duo definitely supports both 32 64 bits architectures. However tempting, I was totally new to Linux/Ubuntu, so decided to avoid possible problems and go for 32 bits version. It's been working for a month with no major inconveniences. If you feel ok with what's been suggested above, go for 64 bits. You may have 32 bits application issues to deal with. I am also afraid, no advice can really help you, so go for it and find out.

I think I'll try 64 bits at some point in the future.

---

### Post by psi36 on 2007-01-12
I think I'll be reinstalling the 32 bit version of Ubuntu.
I'm having some issues I didn't have with the 32 bit version: hibernate doesn't work (suspend didn't work in 32 version either) and when I close the lid or the screen goes black when I don't use my laptop for a while, I can't get it back.
Wireless (WiFi and Bluetooth) isn't working either, but I think that didn't work (yet) under 32 bit Ubuntu.

---

### Post by Rui Pais on 2007-01-12
hi,
i have a core 2 duo for a few days. (my first pentium that is not hot :shock:)

i dual boot between an dapper 32   and a edgy 64. 
So i can securely work and i'm configuring and learning the 64 tricks in the mean time (my short free time) ;) 

Why have only one?

---

### Post by miceagol on 2007-01-12
> **psi36 said:**
> I think I'll be reinstalling the 32 bit version of Ubuntu.
I'm having some issues I didn't have with the 32 bit version: hibernate doesn't work (suspend didn't work in 32 version either) and when I close the lid or the screen goes black when I don't use my laptop for a while, I can't get it back.
Wireless (WiFi and Bluetooth) isn't working either, but I think that didn't work (yet) under 32 bit Ubuntu.

Just installed 64-bit Ubuntu, and I'm also having troubles with power save. When my screen goes black, I can't get get it back again by moving mouse or punching keyboard. All I can do is Ctrl+Alt+SysRq SUB. Anybody know a fix? :cry:

---

