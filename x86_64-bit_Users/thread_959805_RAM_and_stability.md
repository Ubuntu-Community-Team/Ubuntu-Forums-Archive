---
title: "RAM and stability"
date: 2008-10-26
forum: x86 64-bit Users
---

### Post by stevek42 on 2008-10-26
I am using 8g RAM on an Asus P5N-E mobo.  I get constant blue screens in vista 64 which MS blamed on the RAM.  I've replaced the RAM 3 times and now they blame the mobo!

I have a sneaking suspicion it's Vista.  Is it possible the memory address BSODs are the OS?  I want to put Ubuntu 64 on here and hope it will be more stable.

---

### Post by jerome1232 on 2008-10-26
Was there a question? Personally it may very well be a hardware problem, or a bad driver.

But at any rate if you can boot off of a live cd I would suggest running memtest for a few passes to test the ram. If that passes then try and install Ubuntu, if you can get the OS installed and such I would assume vista has a driver that's not playing nice.

---

### Post by dagrump on 2008-10-26
I have 8 GB on an Abit FP-IN9 (overkill), I had to tweak voltages & timing in the bios. It still has weird issues every so often, mainly lock ups trying to shut down. If your ram mfg has a user forum I'd look there, that's how I got mine to run.
Just as a side note the mobo is supposed to support 32 Gb of ram, I have my doubts. I think I've about reached the upper limits on voltage, & if I lower it, she won't POST. As always YMMV.

---

### Post by stevek42 on 2008-10-26
Dagrump, that sounds like my issue.  With 4GB I can set auto timings and have better stability.  With 8gb I have to manually set my timings and it still crashes here and there.

I guess I'll go ubuntu and stay on 4GB just in case.

---

### Post by dagrump on 2008-10-26
I will go back to 4 GB soon myself, I find I didn't play with virtualbox enough to justify the hassle of extra ram. It was a good idea that just didn't play out. But ram is so cheap it was easy to justify. I'm sure if I drop to 4 GB & reset the bios the lock ups at shut down will go away. Tweaking voltages worries me, I'm waiting for the puff of smoke & the death rattle.

---

### Post by Manice on 2008-10-26
You may want to flash your system BIOS.  The Asus website has a new BIOS version for P5N-E released this month.  You might get lucky and fix the problem.

---

### Post by Jouke74 on 2008-10-27
I am with Jerome, first sort out if your memory + mobo is running stable using memtest (let it run for several hours). If this program crashes, or if it reports errors installing any OS is bound to result into problems sooner or later.

---

### Post by null_pointer_us on 2008-10-27
At higher speeds, DDR2 is very finicky. High performance RAM may require extra voltage to run at its rated frequency and timings, and, depending on the board and the RAM, it may not even boot or be stable at stock settings for the DDR2-800 standard. Burning a bootable CD with Memtest86+ 2.x is a good idea. One pass over 8 GB should take like 70 minutes.

---

### Post by inxygnuu on 2008-10-27
It is most likely vista. If Microsoft is going to tell you 2 different problems, then Vista is simply trying to keep a customer. I would definitely try the Ubuntu-64 bit, That is $2-400 you are wasting if you are just going to give up and not use 4 GB of ram.;)

100th post! yahoo!

---

