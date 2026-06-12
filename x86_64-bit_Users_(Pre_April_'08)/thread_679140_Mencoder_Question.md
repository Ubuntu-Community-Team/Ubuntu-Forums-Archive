---
title: "Mencoder Question"
date: 2008-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by gambrjl on 2008-01-26
I'm using mencoder to convert some vob files that are already on my harddrive.  I'm learning slowly and have it creating mpeg4's (Xvid and mp3).

Are there any flag options or something that I can do to use my quad core processor a little more.  Seems to be using 1 core almost exclusively and about 1/2 a second core

---

### Post by nutz on 2008-01-26
I have been looking for something like this also.

---

### Post by andrew.46 on 2008-01-29
Hi,

 Well I don't have such a flashy cpu:

> **gambrjl said:**
> I'm using mencoder to convert some vob files that are already on my harddrive.  I'm learning slowly and have it creating mpeg4's (Xvid and mp3).

Are there any flag options or something that I can do to use my quad core processor a little more.  Seems to be using 1 core almost exclusively and about 1/2 a second core

But I note under the x264 encoding options:

>        threads=<0-16>
              Spawn threads to encode in parallel on multiple  CPUs  (default:
              1).   This  has  a  slight penalty to compression quality.  0 or
              'auto' tells x264 to detect how many CPUs you have and  pick  an
              appropriate number of threads.

which I imagine is what you are after?

                        Andrew

---

### Post by nutz on 2008-01-29
> **andrew.46 said:**
> Hi,

 Well I don't have such a flashy cpu:



But I note under the x264 encoding options:



which I imagine is what you are after?

                        Andrew

That is it, you have solved it Andrew. But for some reason it doesn't work with Xvid and it only seems to use about 90% of each core. Even when the program has complete access with no other applications running it still stays below 90% on each core. Can someone else confirm this so I know it isn't some other variable in my PC that restricts it?

I am using the 64 bit build of Ubuntu 7.10...

---

### Post by gsmanners on 2008-02-01
> **nutz said:**
> That is it, you have solved it Andrew. But for some reason it doesn't work with Xvid and it only seems to use about 90% of each core. Even when the program has complete access with no other applications running it still stays below 90% on each core. Can someone else confirm this so I know it isn't some other variable in my PC that restricts it?

I am using the 64 bit build of Ubuntu 7.10...

A fairly modern CPU will encode xvid a lot more efficiently than the filters can supply the data. To peg your CPU at 100%, you'll probably have to run more than one instance at the same time (have two or more encode jobs going at once).

---

