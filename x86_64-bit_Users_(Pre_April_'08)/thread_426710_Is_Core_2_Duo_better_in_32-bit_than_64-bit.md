---
title: "Is Core 2 Duo better in 32-bit than 64-bit?"
date: 2007-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fraoch on 2007-04-28
My C2D 64-bit install is going along smoothly when someone at another forum suggested that 32-bit may be better on C2D because 64-bit is more of an afterthought on this processor and that it's tuned for 32-bit operation as opposed to the AMD processors which are the other way around.

Is this true or FUD?

I really don't want to uninstall the 64-bit version I just installed this morning because it's working so well.  However if I'm incurring a speed penalty I will consider it.

I will be doing a lot of audio encoding.

---

### Post by dabl on 2007-04-28
I have 32-bit Kubuntu Feisty on one drive/partition, and 64-bit Ubuntu Feisty on another.  This is on a Core 2 Extreme/X6800 platform, for about 4 weeks now.  I have to say, the 32-bit OS seems a little more stable and reliable. I'm having a hard time finding a reason to use the 64-bit system -- I'm told CD-ripping and audio encoding might be faster with 64-bit, but you can't prove it by me.:-|

---

### Post by jdong on 2007-04-28
It's pretty FUD. Intel and AMD 64-bit/32-bit are equally native. Right now, there's simply very few workloads that have been tuned to take advantage of 64-bit, so for almost all cases you will get identical performance and a little more RAM usage on 64-bit compared to 32-bit.

Both architectures are equally good; just 32-bit tends to have more proprietary plugins, codecs, etc readily available. If it works, don't change it :)

---

### Post by firebird84 on 2007-04-28
Due to the x86 arch that it's built on, if you plan on going to 3GB+ with any sizeable video card, I'd upgrade to 64bit.  I ran winxp32 on this pc first and had of course forgotten about memory-mapped IO on the x86.  I had 2.75 GB of ram instead of the 4GB I paid for.  Both my XP and linux partitions are now happily running x64 code, but I will say it was with great wailing and gnashing of teeth that I got Feisty working correctly.

---

### Post by Fraoch on 2007-04-28
I've been Googling around and reading up.  I have lots more reading to do, but here's one review that says there are no problems with 64-bit on the Core 2 Duo:

[http://www.xbitlabs.com/articles/cpu/display/core2duo-64bit.html](http://www.xbitlabs.com/articles/cpu/display/core2duo-64bit.html)

It's just saying that the AMD processors do better in 64-bit apps than C2Ds, but it doesn't show that the C2D is crippled or slows down for 64-bit apps (some run slower, most run faster).

Unfortunately I may have done the wrong thing though.  I have a RAM-limited system, 512 MB, and it will probably stay that way for about a year.  64-bit Feisty has been good so far though, and it's far from slow, so it seems OK to me.  I would rather not reinstall.  I haven't tested out all my apps yet, if I get significant problems I may reinstall (I'd only lose a days' work).  So far it hasn't been the nightmare so many comments said it would be.

---

### Post by jdong on 2007-04-29
Honestly the kind of "differences" and "slower" and "faster" that's being demonstrated are not things that you need to be concerned about, unless you are deploying a farm of CPU's that all are doing that particular task :) As I said, if it's working fine for you, then that's awesome. Personally I choose 32-bit for compatibility with 3rd party stuff and some proprietary plugins. But Ubuntu AMD64 is an equally supported platform around here, so the choice is really yours :) Just don't let people lure you into Intel-sucks-at-64-bit FUD or 32-bit is not taking "full advantage" of a 64-bit processor.

---

