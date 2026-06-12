---
title: "qmpdclient on 64bit???"
date: 2007-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by stinkinrich88 on 2007-07-29
Hello! 

I've just switched to 64bit and there is one program I can not live without! It's qmpdclient and I can't get it to work on 64bit!!

The best I can do is:

download the source files, "qmake" them, "make" them then "sudo make install" them. When I run qmpdclient the application pops up (looks fine) for a split second, then I get "Segmentation fault (core dumped)" Argh!!

Any help is much appreciated!!! Thank you!!!!!

---

### Post by plug_n_play on 2007-11-16
I'm not on 64 bit as far as i know

I'm on gutsy with a centrino dual core (not core2) which is to the best of my knowledge 32bit 

I get the segmentation fault/core dump.  when running it as root, the window stays on the screen (empty and half-drawn) and the terminal I run it from says something about threads and mutex's

It happens whether I install qmpdclient (32 bit) either his .deb package for qt 4.3 or 4.2, or building from source

I have qt 4.3 here (according to help).  I might try installing the 64 bit version...

Edit:
There is no 64 bit version...
I managed to install version 1.0.6.2-1 i386 from the .deb, but the buttons up the side are off the edge of the application.

---

### Post by stinkinrich88 on 2007-11-16
hey, yeah I never had any luck getting it to work in the end. I had been using qmpd for ages, but recently stopped because I got so annoyed with mpd messing up and freezing firefox until i forced it to quit. I can't be dealing with that. good luck though!

---

