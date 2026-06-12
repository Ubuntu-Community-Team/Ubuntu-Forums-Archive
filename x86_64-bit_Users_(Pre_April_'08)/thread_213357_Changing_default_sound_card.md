---
title: "Changing default sound card"
date: 2006-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by cocteau on 2006-07-11
Hi

   I'm having two sound cards with my laptop. One internal and the other is a usb one. I want to make my external one primary.

   However doing preferences/sound and changing the default card does nothing. Ubuntu doesn't register the change and opening the sounds menu again has reset the default card to the internal one.

   I have tried adding my internal one with low priority to the alsa-base file and forcing an alsa reload but when I cat the order of the sound cards the order still remains unchanged.

   What am I doing wrong?

/sorry. this is a cross post. I just found this exact problem discussed here:

[http://ubuntuforums.org/showthread.php?t=188148](http://ubuntuforums.org/showthread.php?t=188148)

---

