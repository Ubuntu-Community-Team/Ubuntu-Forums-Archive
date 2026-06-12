---
title: "Is Gutsy-64 can be installed on Intel T7200 mechine?"
date: 2007-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by shayke on 2007-10-17
I am trying to figure out if Intel core 2 duo (T7200) is 64 bit processor, and if it is possible to install Gutsy-64 on a machine with that processor?

---

### Post by Kilz on 2007-10-17
> **shayke said:**
> I am trying to figure out if Intel core 2 duo (T7200) is 64 bit processor, and if it is possible to install Gutsy-64 on a machine with that processor?

Yes, its 64bit and the processor is compatible with 64bit Gutsy

---

### Post by John.Michael.Kane on 2007-10-17
> **shayke said:**
> I am trying to figure out if Intel core 2 duo (T7200) is 64 bit processor, and if it is possible to install Gutsy-64 on a machine with that processor?

From what I could find on the processor in question it would seem your golden for 64bit support.

Processor Number T7200	
Cache 4 MB L2	
Clock Speed 2 GHz	
Front Side Bus 667 MHz
Intel Virtualization Technology (IntelVT)± checks out as supporting  this as well.

Processor specs aside. Your main concern will be the laptops hardware as a whole eg: gpu/main board card reader sound/networking chip etc. These items will dictate support more so then the processor.

---

### Post by shayke on 2007-10-17
Thanks Klitz!

It must be a stupid question, but just for being sure: do I need to make any changes in the bios for enabling the 64-bit virtue? Is it 64-bit processor "totally", like AMD-64 processors, or it just makes kind of virtual 64-bit processor? 

I ask that because most of the places that I found that talk about 64-bit software mostly direct their conversation on AMD-64 processors (for example: even the headline of this is "For the discussion of Ubuntu on the AMD 64 platform")

Thanks again, appreciate your help!

---

### Post by John.Michael.Kane on 2007-10-17
> **shayke said:**
> Thanks Klitz!

It must be a stupid question, but just for being sure: do I need to make any changes in the bios for enabling the 64-bit virtue? Is it 64-bit processor "totally", like AMD-64 processors, or it just makes kind of virtual 64-bit processor? 

I ask that because most of the places that I found that talk about 64-bit software mostly direct their conversation on AMD-64 processors (for example: even the headline of this is "For the discussion of Ubuntu on the AMD 64 platform")

Thanks again, appreciate your help!

No you should not have to make any adjustments in the bios. Simply download the 64bit Ubuntu version .iso file that you want to use, and install it.

---

### Post by shayke on 2007-10-17
Thanks SD-Plissken!

Where can I figure out if the other components of the machine support the 64-bit (my machine is dell Latitude D620, if it makes it easier)

---

### Post by John.Michael.Kane on 2007-10-17
> **shayke said:**
> Thanks SD-Plissken!

Where can I figure out if the other components of the machine support the 64-bit (my machine is dell Latitude D620, if it makes it easier)

I did a quick search on that particular machine, and unless the spec's have changed. for the most part it should be supported.

The only parts that "might" be a sticking point is the wireless card, and sound as it seems to High Definition Audio based on STAC9200. These are only two pieces I'm not sure about.

---

### Post by shayke on 2007-10-17
Thanks again, really appreciate it!

---

### Post by michael37 on 2007-10-17
> **shayke said:**
> Thanks again, really appreciate it!

64-bit Ubuntu should work very well for you.

A quick advice: since T7200 is a mobile CPU, I assume you have a notebook.  I recommend downloading Desktop AMD64 CD, and then just in case Alternate Desktop AMD64 CD, just in case the first CD doesn't start on your laptop.

---

