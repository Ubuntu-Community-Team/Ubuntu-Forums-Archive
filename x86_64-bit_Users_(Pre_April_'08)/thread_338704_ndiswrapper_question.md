---
title: "ndiswrapper question"
date: 2007-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by euler_fan on 2007-01-14
This isn't a tech support question, but just for my general curiosity . . . 

I am running a compaq v5000 (with an AMD Turion64 ML-40 and 512 RAM) with the Broadcom 4318 wireless card of eternal ubuntu forum infamy. I could get ndiswrapper working great with 32bit via ndiswrapper. Thanks go out to compxiw18 for the great setup package. It is the only one I have ever gotten to work.

But there is something about the 64 bit kernel (which I installed not realizing there would be a problem) which doesn't like ndiswrapper. I can't complain too much--I am in college and most places I would want to use wireless are within 15 feet of an Ethernet connection and I dual boot WinXP just in case I'm desperate.

However, I am curious (not being a programmer), is there anything keeping the necessary adjustments (I believe it was also compwiz18 who implemented an alternative kernel incorporating them I will be installing in a few days) out of the standard kernel? I love the current version I am running (64-bit edgy) and I'm not mad, just curious. I have no doubt the developers work really hard at getting a great product out and it shows.

By the same token, can we expect the necessary changes to come through in the feisty or an updated version of the 64-bit edgy kernel? If not, I am more than happy to post about tri-booting winXP, 32-bit edgy and 64-bit edge so I can still do wireless and have 64-bit for those times where I really need it/can plug in my Ethernet cable.

---

### Post by Hallavej on 2007-01-15
If you are using a 32 bit windows driver with ndiswrapper then you must use a 32 bit linux kernel. But if you can find a 64 bit windows driver for your wireless card then it should work, I think.

---

### Post by euler_fan on 2007-01-15
That was dumb of me! ](*,) Thanks.

---

