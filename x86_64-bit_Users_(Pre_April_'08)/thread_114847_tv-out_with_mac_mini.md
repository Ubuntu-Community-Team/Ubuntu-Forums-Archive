---
title: "tv-out with mac mini"
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by slartibartfast42 on 2006-01-09
Hi,

how do I have to configure xorg.conf to use a pal-tv (attached with apple's dvi-to-tv-adapter) with a mac mini running with breezy?

greetings,
slartibartfast42

---

### Post by tariqf on 2006-02-06
you need to find the correct modeline for this. Once you get the correct modeline you should get the TV output Ok. Unfortunately I cannot find anyone that has managed to get this working although some people are close (e.g. black and white output nearly centered).

If you every get this working please let me know as I'd love to get my mini outputting to TV too.

---

### Post by slartibartfast42 on 2006-02-13
> you need to find the correct modeline for this.

Yep, that's what I'm looking for. I've already tried different configs without success. Unfortunately I wasn't able to find any tips on this topic on the internet so far.

> If you every get this working please let me know as I'd love to get my mini outputting to TV too.

I will put the solution here on this forum, but honestly I am quite pessimistic about it.

Bye,
slartibartfast42

---

### Post by slartibartfast42 on 2006-02-24
So this is what I found recently:

[http://lists.debian.org/debian-powerpc/2005/06/msg00250.html](http://lists.debian.org/debian-powerpc/2005/06/msg00250.html)
[http://lists.debian.org/debian-powerpc/2005/04/msg00255.html](http://lists.debian.org/debian-powerpc/2005/04/msg00255.html)
[http://www.unix-ag.uni-kl.de/~pfeffer/tvout/index.html](http://www.unix-ag.uni-kl.de/~pfeffer/tvout/index.html)
(last link just available in german, sorry)

I had no time to test the modlines, I will put the results into this forum when done.

Bye,
slartibartfast42

---

