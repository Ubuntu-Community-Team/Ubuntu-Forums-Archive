---
title: "What types of DDR2 RAM?"
date: 2008-09-22
forum: x86 64-bit Users
---

### Post by davidw89 on 2008-09-22
Yeah i only got 2x1GB DDR2 667 Kingston ram. It's pretty old. My computer has 4 slots of ram so i can add 2 more for a total of 4 GB. So my question is"

What happens if i add like a faster 2x1GB DDR2 ram stick? like 800mhz or more?

Should i go for the 2GB sticks or stick with 1x2gb?

What rams are compatible with Ubuntu? Named brand cost more.

Any recommendation?

---

### Post by jespdj on 2008-09-22
If you add faster RAM (800 MHz), then it will work with the slower speed of your current RAM (667 MHz).

It's better to add an even number of RAM modules (2 x 1 GB) so that you can take advantage of [dual channel](http://en.wikipedia.org/wiki/Dual-channel_architecture) mode.

The right question to ask is "What RAM is compatible with my motherboard?" rather than what's compatible with Ubuntu. For Ubuntu, the brand of the RAM doesn't matter. Look in the manual of your motherboard (or look it up on the website of your motherboard manufacturer), there should be a list of RAM modules / vendors that have been tested and are guaranteed to work with your motherboard.

---

### Post by malrost on 2008-09-22
Definitely check the specs for your motherboard. With four slots, you may actually be able to max it out at 8GB in a 4x2GB configuration, or even 16GB. One of the points of using the 64 bit version of Ubuntu is that it can address more than 4GB of memory. 

It's easy to get bogged down by all the numbers when shopping for RAM. It will be very helpful to bone up on DDR2 info, or you'll just get swamped by the marketing throwing terms around.

There are a few factors that will affect your performance: 
[LIST]
[*]size (GB), higher is more powerful
[*]frequency (667 versus 800, which, confusingly can also be referred to in terms of PC2-5400 versus PC2-6400), higher is faster
[*]and latency (measured in ns. and represented either as a single number "4" or a string of four "4-4-4-12"), lower is faster.
[/LIST]


These links are short and to the point:

[http://en.wikipedia.org/wiki/DDR2_SDRAM]("http://en.wikipedia.org/wiki/DDR2_SDRAM")

You should also read the sections on latency: 

[http://en.wikipedia.org/wiki/SDRAM_latency]("http://en.wikipedia.org/wiki/SDRAM_latency")

[http://en.wikipedia.org/wiki/Memory_latency]("http://en.wikipedia.org/wiki/Memory_latency")

---

### Post by Yellow Pasque on 2008-09-22
If you're looking to sell the 2 GB's of DDR2-667, I'm interested.

---

### Post by davidw89 on 2008-09-23
lol they're so cheap now days go to one of your wholesale computer store they have it.

---

### Post by Yellow Pasque on 2008-09-24
> **davidw89 said:**
> lol they're so cheap now days go to one of your wholesale computer store they have it.
I don't have a good wholesale hardware store near me, and I was hoping to get used RAM a bit cheaper and do someone a favor who wants to upgrade to DDR2-800 (or higher). I have some DDR2-667 already and was looking to add some more.

---

### Post by Artemis3 on 2008-09-27
I use 4 of these 1g 667 kingston on purpose. You see, while 800mhz sounds tempting, it is of very little advantage, plus your motherboard might not like them. You should test them before purchase, or be absolutely sure the model/brand works with your motherboard model, brand, revision and bios version (it is THAT picky). I'm assuming you will sell the 667 to use 800 alone, Do NOT mix them.

---

### Post by Jive Turkey on 2008-09-27
The number to look for in your existing hardware is the "front side bus" this determines the maximum spped of the RAM you can take advantage of.  If your FSB has a max speed of 667Mhz, then using faster ram will not have any advantage.  You could benefit from having more RAM though.  Both your motherboard and your processor have a maximum supported FSB spec.  Generally it is cheaper to get slower ram but not always.  If your other hardware has higher FSB than 667, then you might consider pulling out the sticks you have now and getting a pair or 2 of matching sticks at the higher speed.  If your motherboard has dual channel mode it may show the FSB speed as 2x your ram speed.  ie, if you have 1333Mhz FSB, that might mean you should have 2 sticks running at 667Mhz, or 800Mhz FSB that uses 2 sticks at 400Mhz.

---

