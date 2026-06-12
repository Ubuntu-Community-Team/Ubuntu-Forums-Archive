---
title: "64-bit: More than just the RAM"
date: 2007-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by praxis22 on 2007-10-16
This should appeal to those who want to know what the 32/64bit differences are:

[http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1](http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1)
> 
The 64 million dollar question
So, what is all this 64-bit stuff, anyway? Well, for a moment we'll keep this relatively simple, as some much deeper definitions will follow on the next page. For now, if you're not aware, 64-bit deals with how your computer works with the data it is given, called **words.**

Words (which are composed of a piece of data, instructions to manipulate that data or both) are the key to computing. As such, the size of word that a computer's system allows can greatly alter how quickly it can process data and how accurate that data is - the larger the word, the more information that can be passed through a processor in every clock cycle, or the more transformations that can be performed on that data.

The concept of words is a tricky thing that we'll get into much deeper in the next page, but for now what's important to know is that 64-bit computers can theoretically process double the information per cycle. However, that is very different than running twice as fast!



Fairly technical but it does explain what the differences are, windows centric, but most of the world still is.

---

### Post by stmiller on 2007-10-16
Nice article. Thanks for the heads up!

---

### Post by dcstar on 2007-10-17
Summary: More modern 64bit hardware will execute 32bit code quicker and native 64bit code more efficiently than the 32bit equivalent, but you will have problems waiting for updated 64bit support for a lot of things.

---

### Post by FredB on 2007-10-17
As I can use my computer flawlessly, this is not really a problem. And 64 bits CPU are really happy with more than a Gb of ram.

I upgraded from 1 to 1.5 Gb of ram, and my computer is *very happy.*

---

### Post by dcstar on 2007-10-17
> **FredB said:**
> As I can use my computer flawlessly, this is not really a problem. And 64 bits CPU are really happy with more than a Gb of ram.

I upgraded from 1 to 1.5 Gb of ram, and my computer is *very happy.*

If you have an AMD64 processor that uses DDR2 RAM, then using 2 identical RAM sticks (in the paired slots) will basically run at twice the RAM data transfer rate as single (or mixed) DDR2 RAM - because the architecture then treats the two sticks as one big one with double the bus width (I think...) and moves the data in "chunks" twice as big as otherwise.

2 1G DDR2 sticks should work much faster than a single 2G stick.

---

### Post by FredB on 2007-10-17
> **dcstar said:**
> If you have an AMD64 processor that uses DDR2 RAM, then using 2 identical RAM sticks (in the paired slots) will basically run at twice the RAM data transfer rate as single (or mixed) DDR2 RAM - because the architecture then treats the two sticks as one big one with double the bus width (I think...) and moves the data in "chunks" twice as big as otherwise.

2 1G DDR2 sticks should work much faster than a single 2G stick.

Well, my motherboard doesn't support DDR2... Only DDR1... But my gutsy works flawlessly. So ;)

---

### Post by barkej on 2007-10-17
It seems that 64bit support is not an issue any more. (At least with linux, MS XP 64bit is another story all together.)

---

### Post by FredB on 2007-10-17
> **barkej said:**
> It seems that 64bit support is not an issue any more. (At least with linux, MS XP 64bit is another story all together.)

The only missing thing ? A java plugin younger than blackdown one... Java 7 will be the answer when it will be stabilized and released.

With a little luck for Hardy Heron...

---

### Post by GepettoBR on 2007-10-17
What do people mean when they talk about "64-bit support"? If 32-bit applications run fine in 64-bit OSes, then what's missing? Why not use 32-bit drivers and Java until a stable 64-bit version comes along? Surely it's less than ideal, but it isn't a disadvantage from 64-bit to 32-bit, right? Or am I missing something?

BTW I use 32-bit but I intend to buy a new PC soon and I'm tending towards a 64-bit Core 2 Duo Conrad.

---

### Post by FredB on 2007-10-17
Using 32 bits applications is a waste of power ;)

More seriously, I prefer having 99% of my software built for 64bits... The only 32 bits software in my computer is... Flash plugin !

---

### Post by rsambuca on 2007-10-17
> **FredB said:**
> As I can use my computer flawlessly, this is not really a problem. **And 64 bits CPU are really happy with more than a Gb of ram.**

I upgraded from 1 to 1.5 Gb of ram, and my computer is *very happy.*

The 64bit OS works perfectly with 'only' 1 GB RAM.  Why do you think otherwise?

---

### Post by Jouke74 on 2007-10-17
I have 2 GB dual channel 3200 memory with a cas latency of 2.5 which is ideal for my AMD cpu. Both 32 bit and 64 bit systems run fine here. Gee I wonder why? :lolflag: 

There is quite a difference of computer hardware and software knowledge level under computer users of Ubuntu.

Above 1 Gb the memory does not influence your general Ubuntu use speed much I guess.

---

### Post by GepettoBR on 2007-10-17
> **Jouke74 said:**
> I have 2 GB dual channel 3200 memory with a cas latency of 2.5 which is ideal for my AMD cpu. Both 32 bit and 64 bit systems run fine here. Gee I wonder why? :lolflag: 

There is quite a difference of computer hardware and software knowledge level under computer users of Ubuntu.

Above 1 Gb the memory does not influence your general Ubuntu use speed much I guess.


That obviously depends on what kinds of applications you're running. Java apps, for example, tend to use more memory when compared to non-Java apps that perform the same functions (Azureus x uTorrent, for example)

---

### Post by Jouke74 on 2007-10-17
Yes but only rarely I have seen my program memory usage go above 1 Gb when not doing serious video editing, gaming or running genetic simulations. Cache basically takes most of the memory when doing the things I had in mind (surfing, typing in office etc.).

---

