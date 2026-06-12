---
title: "[SOLVED] 64bit and speed concerns"
date: 2007-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Krextyl on 2007-10-08
I heard a nasty rumor which maybe speculation and unbased, which is similar to that of what I heard way back in the days of early explosion of ram and windows memory management issues.

The rumor that I heard is that you may actually loose speed using a 64bit OS and Proc with exceptions of the times when you really are putting a load on the system, but for normal use like just browsing the web and what have you not serious multitasking and such the computer has trouble utilizing the extra resources and therefore has to manage all 64 bits when it doesnt need to therefore a slowdown occurs in system performance.

This kinda sounded funny to me anyway but at the same time could see the point but since you would only notice the speed differences during heavy use or require them anyway I don't see how one would notice anyway if there was a loss in performance ( i.e. wouldn't notice any slowdowns for example webbrowsing because your still able to work at the speed even if the computer is trying to manage the full potetential of the unused 64bit if that makes sense???) anyway that was my counter arguement and didn't really know.

does anyone know if the statement above (2 above) has any merit? I'm just curious on the schools of thought out there.

---

### Post by Kilz on 2007-10-08
Double post somehow.

---

### Post by Kilz on 2007-10-08
Sounds like some FUD aimed at people willing to believe anything that sounds remotely possible. If anything the performance is the same with advantages running some applications.

---

### Post by Krextyl on 2007-10-08
thats kinda what I was thinking, At worst equal and if not much better.

---

### Post by rsambuca on 2007-10-08
I remember reading somewhere in my travels how certain applications, depending on how they were coded, could result in slightly lower performance in their 64bit version.  There was a long explanation of what was happening, and frankly I understood almost nothing of it.  The little bits that I could follow did make sense though.  If memory serves, it was something like 1 to 2% decrease in these few cases.

---

### Post by Krextyl on 2007-10-08
ok, speculating here but maybe something like a computer to run backwards compatibilty which would maybe take a little performance off since its working with older code. That sorta makes some sense, but the approximation of only 1 or 2% is cool to know.

---

### Post by rsambuca on 2007-10-08
Don't quote me on those exact numbers, but I am sure it was low enough that I remember thinking people can't really use it as an argument against using 64bit.

---

### Post by Krextyl on 2007-10-08
not gonna quote ya to it, just an order of magnitude sorta thing. And I concur about the justification for the argument, it's like the same as when we needed to progress into the 32bit world from the 16bit.

---

### Post by steveneddy on 2007-10-08
I just installed the 64 bit version of Feisty a few days ago and have already noticed a small increase in speed overall. It seems like the lappie got a tune up, or something. It just seems to be working just right, finally. Very smooth and very responsive.

:popcorn:

---

### Post by stmiller on 2007-10-09
It's not a rumor. There are a few programs where this is the case, but it's not noticeable and you shouldn't worry about it. The advantages of 64bit far outweigh anything like this.

LAME encodes *slightly* slower in 64bit vs. 32bit. But the difference is maybe milliseconds in encoding time. You can't tell a difference. This is because LAME is coded to use nasm which doesn't exist in 64bit.

The powerpc world sees this a lot, and it's not a big deal. Some things take advantage of altivec well, and some things are only coded to use differing versions of SSE (which doesn't exist in powerpc), etc, etc.

Some cpu gurus could perhaps explain all of this better, but it basically depends if the program has been coded to take advantage of the processor instructions it will potentially be running on.

---

### Post by Yellow Pasque on 2007-10-09
I'm going to guess what you've heard is mainly based on software that's been compiled for the AMD64 platform with older compilers. If history is a good indication, (it usually is), we'll see more and more tangible benefit as compilers get better. Even if there is a negligible slowdown, the performance gains that exist already (and that I've personally noticed) in boot time, software compilation, and media encoding outweigh it by far.

---

### Post by scourge on 2007-10-09
> **stmiller said:**
> Some cpu gurus could perhaps explain all of this better, but it basically depends if the program has been coded to take advantage of the processor instructions it will potentially be running on.

True. Here's my example of how much faster 64-bit can be for some tasks: [http://koti.mbnet.fi/~ilaripih/sloppy/](http://koti.mbnet.fi/~ilaripih/sloppy/)
Any 64-bit users can easily compare the performance on their system:
- Download both the Linux x86 and Linux x86-64 binaries
- Make sure you have the 32-bit libc: sudo apt-get install libc6-i386 ia32-libs
- Run both binaries from the console and enter the command "divide 7". It runs a benchmark which should take about 10 - 300 seconds, depending on your cpu and how many cores it has.
- Compare times, shorter is better. On my Core 2 Duo E6600 I get 26.84 seconds for 32-bit and 12.98 seconds for 64-bit. That's a nice speedup of 107% or more than twice as fast.

---

### Post by Jouke74 on 2007-10-09
I posted this some days ago: [http://ubuntuforums.org/showthread.php?t=552551](http://ubuntuforums.org/showthread.php?t=552551)

Real gain is found in numbercrunching applications, not really much with other utilization in my experience. With other utilization 64 bit is certainly not slowing down either. In 95%-99% of the cases programs work at the same speed as the 32 bit versions. Basically the slowdown is caused by the increased size of the data segments that the computer has to handle. Funny enough most "32 bits" are considered "64 bits" by the hardware / compiler so the end size is the same. It is all very program and architecture dependent, and if a program slows down on 64 bit (and i don't mean 0.2 sseconds) it probably says more about the way the program was coded. 

One sideonote is the point that some (windows) 64 bit drivers are underdeveloped. Here is a (rare) possibility for speed loss. 

It's a long read but this might alo be useful: [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

More sidenotes: 64bit vs 32 bit is hardly noticable as compared to other changes to the OS. Try running Xubuntu for a while instead of Ubuntu, start Abiword instead of Openoffice, or install Compiz-fusion and XGL server using an Ati card :) Also please note that if you are surfing the internet or typing a letter most modern CPU's even slow down out of boredom and also to save the environment (frequency scaling). 

I think you can see it as taking a Ferrari to go and get your cigarettes in a big crowded city, the end result in time spend is probably quite the same as taking a Volvo. However, on a nearly empty highway 70 miles from the next gas station, the Ferrari it is going to outrun the Volvo dramatically.

---

