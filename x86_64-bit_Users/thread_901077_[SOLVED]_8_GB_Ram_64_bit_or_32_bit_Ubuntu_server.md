---
title: "[SOLVED] 8 GB Ram 64 bit or 32 bit Ubuntu server?"
date: 2008-08-26
forum: x86 64-bit Users
---

### Post by TusharG on 2008-08-26
Hi all,
I've purchased Dell Xeon Quad Core Server with 8 GB Ram and 12 MB Cache memory. The server will be mainly used for compiling the code. I've installed 32 bit Ubuntu server edition on the server. The server shown 8 GB ram when checked with cat /proc/meminfo however most of the posts say that 32 kernal cannot take the advantage of 4+ GB Ram. I'm also fine in installing 64 bit Ubuntu. Its basically I have to use 32 compilers to compile the code. Most of the developers are demanding 32 bit OS.
What I'd like to know is can i safely run Ubuntu 32 bit server edition with 8 GB Ram? Can 32 bit Ubuntu take the advantage of 8 GB Ram? Its not only processor important to me but ram is also important as this server will be shared between 8 developers who will be compiling their code in their own directories in parallel. The code compilation usually takes 1.5 hours on 2.5 GHZ machine with 2 GB Ram. I'd like to speed up the compilation as well.

---

### Post by nikobor on 2008-08-26
As far as I know,a 32 bit ubuntu can use up to 4 GB RAM. If you have 8 GB, you definitely should use 64 bit.

---

### Post by TusharG on 2008-08-26
Yah! but I also saw some topics that say even 32 bit can support 8 GB Ram!!!
and when I install 32 bit Ubuntu server edition it shows that 8 GB detected and in free also it shows its using 8 GB.
  Question is... is it really using 8 GB under 32 bit?

---

### Post by felker2 on 2008-08-26
[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel) states "For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB."

So, yes, your 8GB RAM will be used by the 32-bit Ubuntu Server Edition.

However, why not use the 64-bit version? In your post, I can only see one reason for 32-bit: if you want to compile and generate 32-bit applications, a 32-bit OS is probably easier. You *can* generate 32-bit applications on a 64-bit Ubuntu, but I think it needs more command line options and/or tweaking. So a 32-bit Ubuntu is saver in that case.

HTH

---

### Post by damvcoool on 2008-08-26
64 bit is my recomendation too. 32 bit can only handle a maximum of 4GB.
to learn more refer to:

[http://en.wikipedia.org/wiki/32-bit](http://en.wikipedia.org/wiki/32-bit)

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

Some old Pentium and some server class processors are 36 bit and can handle 64GB, which are processors with Physical Address Extensions (PAE). refer to link below for further explanation.

[http://en.wikipedia.org/wiki/Memory_addres](http://en.wikipedia.org/wiki/Memory_addres)

---

### Post by NilsHG on 2008-08-26
> **TusharG said:**
> Hi all,
 Its basically I have to use 32 compilers to compile the code. Most of the developers are demanding 32 bit OS.

as i have nothing more to say ontopic, which has not already been said, let me ask the following offtopic:

Why do ppl demand 32bit software? Is it harder to program for 64bit? Every PC sold in the last few years has a 64bit cpu. why do people not take advantage of that?

if microsoft made vista 64bit only (and i think they should have) there would be no problem and no shortage on 64bit software and drivers today. everyone would have made the switch.

so again, why is it so hard to create 64bit applications?

---

### Post by Thelasko on 2008-08-26
If you customer wants 32-bit, give them 32-bit.  Using more than 4 gigs in 32-bit requires [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") is installed.  Felker2 noted that the server edition comes with it installed.  You should be fine.

---

### Post by TusharG on 2008-08-27
Thanks everyone to discussing the topic, special thanks to "felker2" for clearing my doubt that 32 bit can also support 8 GB RAM.
 The topic was little bit getting drag into other direction so let me reply to that as well. The selection of 32 bit compilation is due to only one reason. The embedded devices on which we port our software all have 32 bit architecture so there is little we can do to fix that. Our clients demand 32 bit code/Os so the developers!

---

### Post by felker2 on 2008-08-27
> **TusharG said:**
> Thanks everyone to discussing the topic, special thanks to "felker2" for clearing my doubt that 32 bit can also support 8 GB RAM.


I'm glad I could help. You can press the little medal in the lower right corner of my post to thank me ... ;-)

---

### Post by Thelasko on 2008-08-27
Please mark this thread as solved.

---

### Post by Crafty Kisses on 2008-08-28
As stated above if you got 8, then you might as well use it.

---

