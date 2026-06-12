---
title: "CPUINFO 3800 X2 - low mhz report"
date: 2006-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by cowmix on 2006-03-13
Memtest reports that I have 2000+mhz X2 Athlon.. but Ubuntu (stock plus the latest updates and SMP kernel) says that I am a little over 1000mhz.  

I know things are slow because my 64bit 2.6ghz Celeron is processing thing 40% faster than my Athlon..

Anyone have any ideas?

**Update**

Ok.. I have just read some posts here and there about CPU scaling... and when I do something processor intensive  the CPU mhz goes up to 2000+mhz according to CPU info.. and now that I have ran the test again.. the Athlon is still slightly slower than my Celeron.

Here is my test btw..  if anyone wants to try it...

Running this statically linked MPEG2OGG encoder:

[http://v2v.cc/~j/ffmpeg2theora/ffmpeg2theora-0.16.linux.bin.bz2](http://v2v.cc/~j/ffmpeg2theora/ffmpeg2theora-0.16.linux.bin.bz2)

On this mpeg file:

[http://www.archive.org/download/vd_is_for_everybody/vd_is_for_everybody.mpeg](http://www.archive.org/download/vd_is_for_everybody/vd_is_for_everybody.mpeg)

-----------------

When I run these with 'time' I get this result:

Celeron 64bit 2.6ghz:     2m 2s
Athlon X2 3800:          2m 33s

---

### Post by RAOF on 2006-03-13
[QUOTE=cowmix]...
Anyone have any ideas?
...[/QUOTE]
The ffmpeg2theora binary is poorly optimised for the Athlon64 architecture?  (maybe it doesn't use 3dnow, doesn't support SSE2/3 on your Athlon)?  It's a 32bit binary, so it's probably not as well optimised for the Athlon as the Celeron.

The binary is unlikely to be using multiple threads (video encoding doesn't parallelise very well), so the dual-core nature of your X2 isn't going to help (very much).

---

### Post by cowmix on 2006-03-13
[QUOTE=RAOF]The ffmpeg2theora binary is poorly optimised for the Athlon64 architecture?  (maybe it doesn't use 3dnow, doesn't support SSE2/3 on your Athlon)?  It's a 32bit binary, so it's probably not as well optimised for the Athlon as the Celeron.

The binary is unlikely to be using multiple threads (video encoding doesn't parallelise very well), so the dual-core nature of your X2 isn't going to help (very much).[/QUOTE]

Yeah.. it is a 32 bit binary.. but my Celeron is also 64 bit too.. so all things are equal there..

HOWEVER.. the other optimizations (3DNOW / SSE / etc) very well could be a factor..

Here is a new interesting fact.. If I run the test twice (at the same time) each instance gets the transcoding done in **LESS** time.. 1m 53s each..

---

### Post by RAOF on 2006-03-13
[QUOTE=cowmix]Yeah.. it is a 32 bit binary.. but my Celeron is also 64 bit too.. so all things are equal there..

HOWEVER.. the other optimizations (3DNOW / SSE / etc) very well could be a factor..

Here is a new interesting fact.. If I run the test twice (at the same time) each instance gets the transcoding done in **LESS** time.. 1m 53s each..[/QUOTE]
The 64bit Celeron is also running an x86-64 version of Breezy?  'Cause there is a certain amount of overhead switching between 32bit & 64bit modes.

The second run could be eliminating the influence of the disc, as the input file is probably being cached after the first run.

Anyway, it's hardly a rigourous benchmark either way ;)

---

### Post by cowmix on 2006-03-13
[QUOTE=RAOF]The 64bit Celeron is also running an x86-64 version of Breezy?  'Cause there is a certain amount of overhead switching between 32bit & 64bit modes.[/QUOTE]

Yep.. I installed x86-64 Breezy at the same time.. doing almost exactly the same steps..


> The second run could be eliminating the influence of the disc, as the input file is probably being cached after the first run.

Could be.. but the name of the second file is different (and its a distinct copy) and I have the second instance of the test start 10 seconds after the first so that should minimize caching.. but I think you still could be right.

> Anyway, it's hardly a rigourous benchmark either way ;)

Good point.. what would be a good, quick benchmark?

---

### Post by queenorych on 2006-03-14
Are you by any chance running powernowd?

X2 is dual core, are you running a smp enabled kernel?

I would using something other than the theora/ogg to benchmark your system.  These utilities may be utilizing your AMD and celron processors in ways that the celron comes ahead.  See other benchmarks compring processors.  My amd64 comes up 4x faster than a comparable p4 in some tests, but horribly slower in others.  They are different processors.  Different ACLU, different memory controllers, different micro-codes, etc.

---

