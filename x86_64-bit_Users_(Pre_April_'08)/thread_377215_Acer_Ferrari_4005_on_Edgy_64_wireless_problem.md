---
title: "Acer Ferrari 4005 on Edgy 64 wireless problem"
date: 2007-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by nancom on 2007-03-05
After i install edgy x64 on my ferrari. Every think work except wireless and card reader slot.
For my wireless , I try to follow ndiswrapper method from this forum but it's not work . who can help me.

---

### Post by amd-64 on 2007-03-10
Can you give me more information on what steps you followed to set up the wireless networking. 
Mine works with ndiswrapper and with bcm43xx, except that for bcm43xx you need to be within 3-4 m from the access point, power is set too low. 
If you use ndiswrapper, make sure to remove or blacklist the bcm43xx module

---

### Post by moktod on 2007-03-13
I was unable to get the bcm43xx module to work so I use ndiswrapper, but passing the irqpoll option to the kernel seems to cause the laptop to lock up a couple times a day.  Very frustrating.

---

### Post by amd-64 on 2007-03-15
I am using feisty with a vanilla kernel (2.6.20) and need no kernel parameters anymore. 

With edgy, the laptop did lock up at times. I used to use kernel parameters irqbalance noapic irqpoll but unfortunately, there is also a slight loss of performance.

---

