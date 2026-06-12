---
title: "sound running low low low !!!help!!!"
date: 2008-09-05
forum: x86 64-bit Users
---

### Post by x_error on 2008-09-05
hey there i have an  intel DG965RY mothereboard i installed ubuntu but the sound is too much low i can barely hear a sound while on windows the sound is running well so i dont have a problem with my hardware and my sound drive on windows is "sigmatel audio" or "Idt" so please help and thx

---

### Post by cariboo on 2008-09-05
Have you double clicked on the volume icon in the upper panel and made sure that the master volume and pcm are turned up?

Jim

---

### Post by dudude on 2008-09-05
You could also try running "alsamixer" in the terminal and pushing everything up to 100. 
To exit press escape twice.

---

### Post by x_error on 2008-09-05
ok thx it worked with alsamixer but now the sound recorder encountered a problem ! it says "Your audio capture settings are invalid. Please correct them in the Multimedia settings" so what can i do now ??

---

### Post by dudude on 2008-09-05
If it happened after you changed the settings in alsamixer, then try changing the settings in there again to see if that will fix the problem, and if it is not already installed, install the padevchooser package to view the PulseAudio settings for the computer.

I also have sigmatel audio. I don't know if this is relevant to you, but I have all of the input source things set to Front Mic  in alsamixer.

---

### Post by x_error on 2008-09-05
i opened the alsamixer but the microphone is set off how can i set it on ? there is no bar for mic, linein,analog l , swap gen ?!!1

---

### Post by dudude on 2008-09-06
Try pressing tab in alsamixer to get more options. 

I think you might have to press the spacebar to activate or deactivate things, but I could be wrong.

---

