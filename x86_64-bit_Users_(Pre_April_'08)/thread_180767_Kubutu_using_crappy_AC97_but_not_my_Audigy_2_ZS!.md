---
title: "Kubutu using crappy AC97 but not my Audigy 2 ZS?!"
date: 2006-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by JAB Creations on 2006-05-22
I installed Kubutu Linux on my AMD64.  It decided that it was going to use my crappy onboard AC97 instead of my Audigy 2 ZS.  Now I know exactly how you'd change this in XP however I'm mostly a Linux noob and while I've wandered in to what appears to be the control panel (system settings) there is for lack of any explenation the ability to change the main audio device (though I am able to change the midi device).  Brilliant!

So ahh, how the hell do I change it?! ](*,)

---

### Post by DrBair on 2006-05-24
I believe all that good stuff should be fixable in the alsactl program. But I've never messed with multiple sound cards.

---

### Post by warp99 on 2006-05-26
If you only want to use the Audigy 2 ZS card you first need to go into the BIOS and disable the AC97. Boot into ubuntu and from a terminal run "sudo alsaconf" to setup your Audigy 2 ZS. After setup run "alsamixer" to turn up the sound levels because after alsaconf sound is muted by default. :cool:

---

