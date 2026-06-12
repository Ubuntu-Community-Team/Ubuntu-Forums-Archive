---
title: "Kernel Size Reduction"
date: 2005-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by blinksilver on 2005-03-11
I was wondering if anyone would be interested in starting an effort to reduce the size of the amd64 kernel to under 1024KB? why you ask?  weil that is the size of your level2 cache on most athlon64 and if we can fit the kernel on the L2 we would see a performance boast,  it really cant be that hard, it is currently just a little over at 1.2MB.

oh i know we can all recomple the kernel with a few less modules in kernel and we would be set, but why can't the kernel in the respository do this?  

The Only reason i don't do this myself is that i don't know what should and should not be in kernel for most amd64 system and hence cannot help all users, i was hoping that someone or ones more well versed could help.

---

### Post by kubla on 2005-03-11
[QUOTE=blinksilver]I was wondering if anyone would be interested in starting an effort to reduce the size of the amd64 kernel to under 1024KB? why you ask?  weil that is the size of your level2 cache on most athlon64 and if we can fit the kernel on the L2 we would see a performance boast,  it really cant be that hard, it is currently just a little over at 1.2MB.

oh i know we can all recomple the kernel with a few less modules in kernel and we would be set, but why can't the kernel in the respository do this?  

The Only reason i don't do this myself is that i don't know what should and should not be in kernel for most amd64 system and hence cannot help all users, i was hoping that someone or ones more well versed could help.[/QUOTE]
 perhaps one way forward would be to have two kernels:

one for laptops and one for workstations...

I'm sure laptop users are carrying around loads of bunk that's useless to them and workstations can, at the very least, get rid of the pcmcia stuff.

Ian

---

### Post by Pse on 2005-03-11
Holy cow! I never even cared about that...what's more, my A64 has 512KB of L2 Cache #-o! I was thinking of doing a Kernel recompile specifically for my system...I still have to read some docs about doing that for AMD64...Luckily, Gentoo's documentation should be good enough =).

---

### Post by blinksilver on 2005-03-11
some of the A64 do have 512 (an ever decreasing %), and i have heard of people gettiing there kernel to fit 512K, but sadly i think that is to much of a push for the ubuntu developers to say yes.

the two kernel Idea on the other hand is something to consider,  that seems like an idea solution, stuff like raid arrays could be remove from laptop and pcmica from workstations,

but this only a start i don't think we are going to get two kernels if we just ask that two things be changed, anymore suggestions

---

### Post by Pse on 2005-03-13
The main problem with the two-kernel solution is that Ubuntu still has to remain compatible with most systems without a Kernel Recompile... As there are so many configurations where Ubuntu is supposed to boot, most of those drivers cannot be removed...
I'd agree, however, in making most drivers modules instead of having all of them compiled in the kernel... As I haven't recompiled the kernel yet, I don't know how many drivers are compiled in the kernel and how many are modules :???:

---

### Post by blinksilver on 2005-03-13
sadly this looks like it is going be something each user is going to have to do, darn, i was kinda hoping i would not have to recompile each kernel every time there was an update

---

### Post by wmcbrine on 2005-03-13
No offense, but it's naive to think that you can keep the kernel in cache just by trimming it down. Even if you could, that situation wouldn't last long, as parts of the kernel would soon be displaced by other data. And the whole kernel is probably never going to be cached at one time in the first place, regardless of its size, because it's not all *used* at one time. The real key is to reduce the size of the *working set*. This is the sort of thing that the kernel developers already do. In short, no worries. :smile:

---

### Post by blinksilver on 2005-03-13
not really if you think about it, there are times, for example really intense multiplayer  player online gaming when almost the entire kernel is firing full force, and then it would be ideal for it be on the L2, i don't mean to keep it a resident of the L2, would know how, but it would come in handy, for that little last minute boast in performance

there are people i know that will swear by it

---

### Post by wmcbrine on 2005-03-13
No, there really aren't such times. Think about everything that's in the kernel. And then think about how much of the *game's* code is in the cache while you're playing it, as well as X code, etc. It probably outweighs the kernel code by a large margin.

I'm sure you can find people who swear by the technique; but you can find people who'll swear by anything. For example, I've just been reading from people who say that setting "browser.turbo.enabled" in about:config gives Firefox a nice performance boost. So I looked it up, and it turns out that this option has done *nothing* since version 0.9 or so; has *never* done anything on Linux; and even when it worked (in old versions, on Windows), it affected only the startup time. So the perceived speedup is purely psychological.

---

### Post by BaffledMollusc on 2005-03-14
I have to go with wmcbrine on this one, I'm afraid. In general, the number of CPU cycles expended on kernel routines is small - a few percent at best. This is the whole idea; after all, you want as much CPU time as possible to go to the user applications, not the OS. If you could suddenly magically make the kernel 10 times faster it would make very little difference in situations where the CPU is maxed out at 100% on user applications (I guess there are extreme IO bound situations where it might conceivably make some difference, but not as a general rule).

And, finally you really wouldn't want the kernel monopolizing the cache even if you could. The whole point of cache is to keep heavily used code (i.e. the application code) close to the CPU, and the memory controller in conjuction with (ironically) the kernel  decides what should be in cache at any point in time in order to optimize performance, and generally does a very good job of it.
 
Nice thought though!  :-D

---

### Post by blinksilver on 2005-03-14
alright, looks like i lose this one, hey you can't win the all, logical enough, i agree

---

### Post by Pse on 2005-03-14
LOL, what if suddenly the Kernel decided to take over the whole L2 cache for it, MWaHaHAhAHA! :twisted: The memory controller wouldn't have a chance!

Ok, sorry, I'll stop now.

---

### Post by sehe on 2007-06-07
> **wmcbrine said:**
> No offense, but it's naive to think that you can keep the kernel in cache just by trimming it down. Even if you could, that situation wouldn't last long, as parts of the kernel would soon be displaced by other data. And the whole kernel is probably never going to be cached at one time in the first place, regardless of its size, because it's not all *used* at one time. The real key is to reduce the size of the *working set*. This is the sort of thing that the kernel developers already do. In short, no worries. :smile:

Everybody take note of what the wise man said.

Would you be happy if you could (provably) keep the kernel on-chip all the time? This would mean that you wouldn't be allowed to run any actual software because it would spoil your nice cache-pipe-dream as soon as it would execute a bit of code...

Don't sweat it. Go Gentoo and optimize the kernel *and all software for that matter*  for your processors' features. And, measure your performance. Use faster main memory if you feel you *really* need it (it will be cehaper). If you absolutely must combine two AMD 64 FX on the Quad FX board, this will double the effective cache, plus you run the chance that once you get the processor affinities right (VM anyone?) the kernel could actually sit in cache undisturbed, as long as all usermode/daemon code lives on the other CPU.

Bonus: you could scale this up once the Quad-core Barcelona is available, because it uses the same socket :)

In other words, have a ball, but keep REAL. Measure your performance, don't blindly set a goal :)

Seth

---

