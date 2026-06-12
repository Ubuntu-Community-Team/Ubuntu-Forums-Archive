---
title: "World in Conflict Hyperthreading?"
date: 2007-12-19
forum: Wine
---

### Post by teamalpha on 2007-12-19
Hello, i have an Acer Aspire 5570-4765 with the Intel Core Duo processor T2050 with the following specs:
1.6Ghz, 
a 533 Mhz FSB speed,
 and a 2mb L2 Cache

I Have the game World in conflict, and it needs 2 Ghz to play. I heard about hyperthreading, and i would like to know if my processor supports hyperthreading, and the game can also use hyperthreading. If the laptop or the game can not do hyperthreading, is there anyway i can still play it, such as safely overclocking it ? If i must overclock it, then how? (please remember that this is a laptop, and i have a very low budget)

---

### Post by cogadh on 2007-12-19
You have a dual core processor, way beyond what hyperthreading was supposed to do. Essentially, hyperthreading emulated the presence of multiple processors, while your processor is actually two processors on a single chip. You should still be able to play the game without overclocking, if WiC can take advantage of a multiprocessor environment.

---

### Post by teamalpha on 2007-12-22
I am confused, hwat is hyperthreading then? and since i have  a dual core 1.6 ghz, and the game requires 2 ghz, will i be playing with 3.2 ghz, or will i be under the requirments?

---

### Post by cogadh on 2007-12-22
Like I said, hyperthreading was just a way to emulate two processors while not actually having two processors (in simple terms, what it actually did was way more complicated than that). It was an interim technology used by Intel at the end of the Pentium 4 series, before they came out with multicore processors.

With a dual core processor, you actually do have two processors, each at 1.6 GHz. That does not mean that you are running at 3.2 GHz, but your machine can do double the work, since one app can be using processor 1 while different app uses processor 2 (again, in simple terms, it is actually way more complicated than that).

However, if you check the system requirements for the game, it says you should be able to run it:
*Minimum System Requirements*

       &#8226; OS: Windows® XP, Windows Vista&#8482;
       &#8226; CPU: Single-core 2.0 GHz or faster (2.2 GHz for Windows Vista&#8482;)
       &#8226; **CPU: Dual-core Any Intel® or AMD®**
       &#8226; RAM: 512 MB (1 GB for Windows Vista&#8482;)
       &#8226; Graphics: 128 MB video RAM, DirectX® 9.0c-compatible (NVIDIA® GeForce® 4 MX, ATI® Radeon® 8500, 9200 not supported)
       &#8226; Sound: DirectX® 9.0c compatible
       &#8226; Hard Drive: 8 GB or more available hard drive space
       &#8226; Disc Drive: DVD (Not required for downloadable version)
       &#8226; Input: Keyboard and Mouse
       &#8226; Internet play: Cable/DSL or better
       &#8226; DirectX® 9.0c

*Recommended System Requirements*

       &#8226; OS: Windows® XP, Windows Vista&#8482;
       &#8226; CPU: 2.5 GHz or faster
       &#8226; RAM: 1024 MB (1.5 GB for Windows Vista&#8482;)
       &#8226; Graphics: 256 MB video RAM, DirectX® 9.0c-compatible
       &#8226; Sound: DirectX® 9.0c compatible
       &#8226; Hard Drive: 8 GB or more available hard drive space
       &#8226; Disc Drive: DVD (Not required for downloadable version)
       &#8226; Input: Keyboard and Mouse
       &#8226; Internet play: Cable/DSL or better
       &#8226; DirectX® 9.0c

---

### Post by SunnyRabbiera on 2007-12-22
> **cogadh said:**
>  It was an interim technology used by Intel at the end of the Pentium 4 series, before they came out with multicore processors.

Yeh I have one with hyperthreading, but really there is nothing wrong with intel 4, I find it just as good as owning a dual core system though I am aware of its limitations

---

### Post by teamalpha on 2007-12-24
errrrr, ......
So, the game will be able to run then, perhaps because it can utilize both the rocessors at the same time?

---

### Post by cogadh on 2007-12-25
> **cogadh said:**
> 
       • **CPU: Dual-core Any Intel® or AMD®**
       
That means it will just work. *Any* dual core processor, no matter the reported speed, is sufficient for this game.

---

### Post by teamalpha on 2007-12-25
Thanks!! I feel totally relieved ....

---

