---
title: "Big even huge wine problem"
date: 2008-07-22
forum: Wine
---

### Post by KOTAPAKA on 2008-07-22
I get this when I try to run an application:
[HTML]ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"

      after 61 requests (61 known processed) with 4 events remaining.

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"

      after 24 requests (24 known processed) with 0 events remaining.
[/HTML]

I know it's something with my X but everything seems to be OK. fglrxinfo and the gears commands give the correct output. What actually happens is my display goes black then when I move the mouse it clears and I can see that the 2 identical displays are shown on my monitor with a lone in the middle of the monitor separating them. I am using wine-1.0 but this shouldn't be the problem - this happened even when I run wine for the first time (stopped in subsequent runs).

---

### Post by PRMan on 2008-07-22
I don't know the solution, but it's saying that it can't find ALSA (a sound driver) at /dev/snd (where your sound card lives).

I got a simliar issue one time when I had disabled sound on my motherboard to save power.  I use it as a server and just wanted to look at a video to make sure what it was and I got a very similar error.

I hope that helps somewhat.

---

