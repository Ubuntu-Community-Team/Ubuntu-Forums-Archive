---
title: "Is the 64 bit OS by itself any faster?"
date: 2008-09-02
forum: x86 64-bit Users
---

### Post by eotakos on 2008-09-02
... or it is just the layer for the 64 bit applications to run on


sorry - you must get a lot of this... but my pc is almost 2 years old and today i found out...  :confused:

---

### Post by Kilz on 2008-09-02
> **eotakos said:**
> ... or it is just the layer for the 64 bit applications to run on


sorry - you must get a lot of this... but my pc is almost 2 years old and today i found out...  :confused:

There have been reports that the 64bit version appears to be quicker by itself, but there are no benchmarks to prove it. I think its not as sluggish.

---

### Post by eotakos on 2008-09-02
a) thanks for the answer

b) i feel so stupid! i've just come to the point where i'm adequately satisfied with my 32 bit install and setup... and it's too early for another format.   so  i guess it'll have to wait

---

### Post by forger on 2008-09-02
I'd recommend to wait for the 8.10 release to come out in October, then try out the 64-bit :)

---

### Post by eotakos on 2008-09-03
hm... that sounds tempting alright! :)

---

### Post by philinux on 2008-09-03
In preparation I'd move home to it's own partition, if it's not there yet.

Then when you re-install almost all your settings will be preserved.

[Psychocats]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by jespdj on 2008-09-03
> **eotakos said:**
> ... or it is just the layer for the 64 bit applications to run on

sorry - you must get a lot of this... but my pc is almost 2 years old and today i found out...  :confused:
The whole OS is 64-bit.

One of the main reasons it is faster is that the microprocessor has more and larger internal registers available in 64-bit mode, which means that it works more efficiently; it doesn't have to get data from main memory as often, which is a relatively expensive operation. You'll notice this especially in applications that use the microprocessor a lot, such as multimedia applications. For technical details, see [Wikipedia: x86-64](http://en.wikipedia.org/wiki/X86-64).

You will not notice the speed difference between 32-bit and 64-bit with most applications.

---

### Post by kaligus on 2008-09-04
> **eotakos said:**
> ... or it is just the layer for the 64 bit applications to run on


sorry - you must get a lot of this... but my pc is almost 2 years old and today i found out...  :confused:

I ran 8.04 32 bit for a week and 64 bit since July.

It may well be my brain being tricked at times but there are things that are MUCH faster including some wine apps designed for win32 showing much improved time-to-complete.

---

### Post by eotakos on 2008-09-04
thanks for the replies

but if..

> **jespdj said:**
> The whole OS is 64-bit.
You will not notice the speed difference between 32-bit and 64-bit with most applications.

then why all the fuss... it can't be for nothing - that's for sure. if the application is 32bit running on a 64bit system, that's another story.

---

### Post by jespdj on 2008-09-04
Well, I said **most** applications. But for **some** applications, it makes a big difference - especially applications which heavily use the microprocessor, such as multimedia applications, movie editors, computer graphics programs, etc.

Also, if you have 4 GB of RAM or more, then you don't have to do any special tricks to use it all on 64-bit. 32-bit OS'es are limited to 4 GB, or even less (sometimes a 32-bit OS doesn't see more than 3.2 GB).

If you have a 64-bit capable microprocessor, why would you limit it by using a 32-bit operating system? That's like buying a fast car and never switching to 4th or 5th gear.

Also [read the sticky](http://ubuntuforums.org/showthread.php?t=765428).

---

### Post by eotakos on 2008-09-04
thanks! that's what i needed to read...

another thing is (now that i found out, i'm maybe digging further in a little bit) that my cpu is an intel p4 HT with intel 64 architecture... which - according to the guy that soled it to me - is not like the modern intel 64 bit systems. "it works the 64 bit way, but..." and that's where he got me a little comfused. is it? or is it not?... anyway - intel's tech page for the cpu says it is, so the next fresh install will be the way to test it.

bye for now

---

### Post by Yellow Pasque on 2008-09-04
> **eotakos said:**
> thanks! that's what i needed to read...

another thing is (now that i found out, i'm maybe digging further in a little bit) that my cpu is an intel p4 HT with intel 64 architecture... which - according to the guy that soled it to me - is not like the modern intel 64 bit systems. "it works the 64 bit way, but..." and that's where he got me a little comfused. is it? or is it not?... anyway - intel's tech page for the cpu says it is, so the next fresh install will be the way to test it.

bye for now
Either the chip has 64-bit registers and decodes the amd64 (err, intel calls it emt64) instructions or it does not. Unless your salesman was referring to Itanium (IA-64), I don't think he knows what he is talking about.

---

### Post by eotakos on 2008-09-04
A! I see Temüjin my friend you are into the technical stuff... help out here!

my cpu is this:
[http://processorfinder.intel.com/details.aspx?sSpec=SL8PQ](http://processorfinder.intel.com/details.aspx?sSpec=SL8PQ)

when i did intel's test it clearly came out with "intel 64 architecture"

my motherboard is this:
[http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2325](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2325)

further down in the order of features it reads "64bit Ready with Intel® EM64T"

so... i understand that the system is 64 bit - what else does it take(...?)

maybe the salesman was trying to show-off with stuff he barely knows to me  - who didn't know because i hadn't dug into -  / common strategy

anyway, when i bought the machine, i didn't care to have the super cpu and that's how i ordered it / now that i'm interested, it's nice to know :-)

---

### Post by tuxxy on 2008-09-04
Also 64-bit is incredibly fast when it comes to virtualisation.

Heres the link to the [64-bit user group]("http://ubuntuforums.org/group.php?groupid=258")

---

### Post by mikewhatever on 2008-09-04
Here are some good readings:
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)
[http://www.phoronix.com/vr.php?view=11837](http://www.phoronix.com/vr.php?view=11837)

My advice, it's a little faster, but it's not worth it if you use flash a lot.

---

### Post by eotakos on 2008-09-04
Jee! thanks for the invitation - i'll join when i'll switch to 64bit ubuntu - it'll be of more value to me then :popcorn:

---

