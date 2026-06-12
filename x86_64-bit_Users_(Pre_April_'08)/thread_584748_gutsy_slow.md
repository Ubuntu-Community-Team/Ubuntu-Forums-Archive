---
title: "gutsy slow"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by xieu90 on 2007-10-21
hi everyone
somehow I feel like my gutsy is sleepy
it is quite slow much more slower than it was with feisty
when I open a program it take around 1-4 seconds to react to my command (when I was in feisty it reacted immediately)
does anyone know how to make it faster ? 

+ when I download update programs from ubuntu server its speed is much more slow (around 100 kb in gutsy and 300 in feisty) 
when I download films it can be 300 in gutsy so ... what is going on ?

---

### Post by xieu90 on 2007-10-21
yeah and it drinks my ram like hell
first it used only around 250 - 350 mb ram
then after a while (only firefox is running) it uses more than 400 from 512 mb ram of me
take a look at my screenshots

and I can see a bunch of programs use GB ram of mine (I have only 512 mb)

---

### Post by Thelasko on 2007-10-22
Sounds like the same problem I'm having.  64 bit runs like 32 bit.  I'm starting to think it has to do with the generic kernel.

---

### Post by John.Michael.Kane on 2007-10-22
Gutsy slowness under certain case's can be attributed to the tracker program. [http://ubuntuforums.org/showthread.php?t=586789&highlight=tracker](http://ubuntuforums.org/showthread.php?t=586789&highlight=tracker) You should be able to adjust it or remove it using synaptic.

---

### Post by chrisccoulson on 2007-10-23
> **xieu90 said:**
> yeah and it drinks my ram like hell
first it used only around 250 - 350 mb ram
then after a while (only firefox is running) it uses more than 400 from 512 mb ram of me
take a look at my screenshots

and I can see a bunch of programs use GB ram of mine (I have only 512 mb)

From your screenshot, it seems you're running Xgl, which seems to be whats drinking your RAM ;)

---

### Post by xieu90 on 2007-10-23
yeah it is true I'm running xgl 
and I managed to find out how it drink my ram
because of animation inside compiz, I removed that package and it run better now, but now I have another problem, my computer removed my video card's driver, so I'm blind now 
take a look here
[http://ubuntuforums.org/showthread.php?t=587311](http://ubuntuforums.org/showthread.php?t=587311)

---

### Post by Thelasko on 2007-10-23
I have configured my video drivers from the command line a few times.  Try following the instructions in this link:
[http://ubuntuforums.org/showthread.php?t=155029](http://ubuntuforums.org/showthread.php?t=155029)

before you configure it you can install the video driver package by typing 
```
sudo apt-get install xorg-driver-fglrx
```
you might use a different driver than fglrx but I'm guessing that's the one you want.

---

### Post by mis4mike on 2007-10-25
I had a similar issue with firefox eating my cpu.  It would max out one core of my 2.33 Intel dual core and still hang for relatively long intervals.  

When I upgraded to gutsy I was using the "restricted" nVidia drivers that I had installed, but after removing these and restarting, the problem seems to have gone away.  Hopefully this is not something that is going to creep back up if I leave firefox open.

---

