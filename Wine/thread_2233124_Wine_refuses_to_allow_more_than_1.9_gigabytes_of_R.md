---
title: "Wine refuses to allow more than 1.9 gigabytes of RAM"
date: 2014-07-06
forum: Wine
---

### Post by jandugacek on 2014-07-06
Hello,

I ran into a weird problem whose solution I can't google. I am trying to run the game Path of Exile on Wine on Ubuntu 14.04 64-bit (quite a fresh install). I remember that it run fine on With on my older laptop, but it was long ago. I've found guides how to run it and it worked to some extent. The problem was that the game has bad memory management and uses up more and more RAM over time, and peaks at about 2.5 gigabytes (seen this on Windows and also about a year ago on my old laptop), but on my Ubuntu, something strangely limits it to 1.9 gigabytes of RAM.

It still has about 4 gigabytes of RAM unused and 2 more unused gigabytes on swap, but it never goes beyond 1.9 gigabytes. Because it can't allocate extra space, extreme FPS drops build up and render the game unplayable, in some areas very quickly (before it reaches the breakpoint, it runs smoothly). I've seen this problem happening on an old PC that had a small RAM. This should not happen on a 64-bit OS that has many gigabytes of RAM available. I've asked the game's unofficial Wine supporter and he told me that he has never seen anything like that. I've tried different versions on Wine using PlayOnLinux, one of them was even dedicated to the game, but the problem was always happening.

Any ideas what's the problem?

Thanks in advance.

---

### Post by slooksterpsv on 2014-07-10
I believe this is the issue:
WINE uses 32-bit libraries which technically should be able to allocate up to 3GB of memory, but there's limitations with that too. I believe it can only use the lower 2GB of memory (1.9GB would sound about right) per application. Unless WINE implements some 64-bit code to use more than 32-bit minimum there's not much you can do.

---

### Post by jandugacek on 2014-07-10
There must be something I can do, I've seen the game use more than 2 gigabytes of memory on my old laptop on an older Ubuntu. Other people can play the game without problems like this. According to [this thread]("http://askubuntu.com/questions/203645/how-to-give-more-ram-to-wine-applications"), the limit can be 3 GB sometimes. There must be something bad in my system and that limit comes from it.

---

### Post by jandugacek on 2014-08-24
I have found what was the problem. It was set to emulate Windows XP which is 32-bit usually. By setting it to Windows 8 that is usually 64-bit, the problem disappeared and Wine programs can use more than 2 gigabytes of memory.

---

### Post by slooksterpsv on 2014-08-24
Awesome, I'll keep that in mind. Haven't really had to use WINE a lot lately. Glad you got it solved and can inform others. =D

---

