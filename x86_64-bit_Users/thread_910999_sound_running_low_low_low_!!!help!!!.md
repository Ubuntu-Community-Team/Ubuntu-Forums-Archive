---
title: "sound running low low low !!!help!!!"
date: 2008-09-05
forum: x86 64-bit Users
---

### Post by x_error on 2008-09-05
hey there i have an  intel DG965RY mothereboard i installed ubuntu but the sound is too much low i can barely hear a sound while on windows the sound is running well so i dont have a problem with my hardware and my sound drive on windows is "sigmatel audio" or "Idt" so please help and thx

---

### Post by soxs on 2008-09-05
use alsamixxer to tune up master/front:
type the following into a terminal and adjust via arrow keys:
```
alsamixer
```

---

### Post by Crafty Kisses on 2008-09-05
If alsamixer doesn't work, post the results of > lspci

---

### Post by x_error on 2008-09-05
thanks  i owe you my life ! it worked but can you tell me about microphone configuration because when i run  sound recorder now an error message saying  "Your audio capture settings are invalid. Please correct them in the Multimedia settings." popsup !

---

### Post by soxs on 2008-09-05
> **x_error said:**
> thanks  i owe you my life ! it worked but can you tell me about microphone configuration because when i run  sound recorder now an error message saying  "Your audio capture settings are invalid. Please correct them in the Multimedia settings." popsup !

Use the thank button if you feel like ;-) (bottom right of each post)

Btw. to fix that new upcomming error, try alsa output instead of the new (and still a little wacke pulseaudio)
goto
System -> Preferences (or similar, using german locale) -> Audio and edit everything so it says "alsa - advanced linux sound architecture"
if it still doesn't work, try to reboot and recheck.

---

