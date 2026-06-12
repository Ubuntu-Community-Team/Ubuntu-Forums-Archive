---
title: "How to have Ksensors on startup?"
date: 2007-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by eddieb on 2007-05-11
Hi, Before using Ubuntu 64 bit, I had Mepis 64 bit and liked one of the features of having the Cpu temp on the Taskbar. I've checked and found that Ksensor and lm-ksensor is already in my setup. I would like to know how to have them running at Bootup. Is it possible to have just the Temp on the Taskbar in Ubuntu?

---

### Post by John.Michael.Kane on 2007-05-11
Have you tried adding Ksensors to the KDE control center module?

---

### Post by eddieb on 2007-05-11
Hi, I didn't have the Control centre configured but I do now. Ksensors has a Green box beside it (synaptic) How do I add Ksensors to the Control centre? Cheers, Dened

---

### Post by John.Michael.Kane on 2007-05-11
Frist make sure kcontrol-autostart is installed via adept manager. if it is follow the steps below

Click on Kmenu

Then click run command type autostart 

You will then be able to add the programs you want.

---

### Post by eddieb on 2007-05-11
Hi, I have managed to get control autostart installed, I then rebooted but  cannot see or find Kmenu. I looked in synaptic and all I can see is Kmenu edit. I know what Kmenu looks like because it was in Mepis. Cheers,
Dened

---

### Post by John.Michael.Kane on 2007-05-11
> **eddieb said:**
> Hi, I have managed to get control autostart installed, I then rebooted but  cannot see or find Kmenu. I looked in synaptic and all I can see is Kmenu edit. I know what Kmenu looks like because it was in Mepis. Cheers,
Dened

Pull up your menu on kde.  

Then click on Run Command 

Now type autostart 

You will now be presented with a panel that allows you to place programs that you want to automatically start.

---

### Post by eddieb on 2007-05-12
Got it working through System-administration-sessions. cheers.

---

