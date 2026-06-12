---
title: "amd 64bit + Nvidia - wierd crash"
date: 2008-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by mapkyca on 2008-03-07
Hi,

I have just got my shiny new Athlon 64bit with Nvidia GeForce 8400GS and am trying to install Ubuntu 7.10. This is a dual head card, with the first monitor connected to the VGA and the second to the digital.

I have two problems, firstly the screen is blank on boot which I can live with because the live CD does eventually come up (although it displays the same view on both screens - ie, dual view is disabled).

Installation proceeds normally, but when i reboot the monitors switch of for a while (presumably when the splash is being displayed), then spring back to life with a black screen and one frozen "wait" cursor on one screen (interestingly the one connected to the digital head).

If I move the mouse the cursor moves but the animation is stalled, keyboard doesn't function and no other activity can be seen. 

I've looked about and there is mention of the splash issue, but not my problem. Graphics are clearly working otherwise I wouldn't be able to see anything...

Any ideas?

M

---

### Post by mapkyca on 2008-03-07
Additional: Just checked and I get the same fault using 32bit. Windows works fine, so I'm guess its not a hardware fault.

---

### Post by dabl on 2008-03-07
You need to install the proprietary Nvidia driver to have a prayer with that setup.  I recommend the Envy script installer, from here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

p.s. the 64-bit architecture is irrelevant to your video issue. :)

---

