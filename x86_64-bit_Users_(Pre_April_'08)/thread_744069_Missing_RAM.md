---
title: "Missing RAM"
date: 2008-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by dglkn on 2008-04-03
[IMG]http://i25.photobucket.com/albums/c78/dglkn/Screenshot-SystemMonitor.png[/IMG]

The user memory should read 2.0 GB instead of 1.9 GB. 

I'm running Ubuntu Gutsy 64-bit 7.10 (upgraded to Studio) 

running on the -rt kernel

I don't have any hardware such as onboard video that would do this

---

### Post by stefangr1 on 2008-04-03
can you also post what you get if you run (in a terminal):

free -m   ?

---

### Post by Diabolis on 2008-04-03
I think that 1.9 is correct. You'll never get "exact numbers". For example I have a 2 gb flash drive, but its actual size is 1.92988 gb. Thats because this metrics are based on a binary system where you have bits.

8  bits = 1 Byte

1024 B = 1 Kilobyte
.
.
.

1024 mb = 1 Gigabyte

You can notice this also on your hard drive, probably you saw it announced as a 40 gb hdd (just an assumption) when you bought your pc, but its actual size is 38.xxx gb.

---

### Post by luisromangz on 2008-04-03
That is posibly because advertised RAM is measured using Gigabytes, and the system monitor uses GibiBytes (binary Gigabytes).

2 GB =  2000MB = 1.95 GiB

---

### Post by Diabolis on 2008-04-03
**binary system**

1 Gigabytes = 1024 Megabytes = 1,048,576 Kilobytes = 1,073,741,824 Bytes = 8,589,934,592 bits

2 Gigabytes = 2048 Megabytes = 2,097,152 Kilobytes = 2,147,483,648 Bytes = 17,179,869,184 bits

**decimal system**

1 Gigabyte = 1,000,000,000 Bytes

Since your ram has  2,147,483,648 Bytes its merchandise as a 2 gb.

luisromangz is correct.

It's just a matter of conversions.

---

### Post by Slushdoot on 2008-04-09
Sorry to bump an old thread, but I don't think is a gigabyte vs gibibyte problem.  RAM is sold in gibibytes.  It's hard disks that use the phony ratings.  

If I had to guess I'd say that the extra RAM is being eaten by the fremebuffer.  What graphics card do you have, dglkn?  Does it have discrete RAM?  Might some other peripheral like a sound card be borrowing any RAM?

---

