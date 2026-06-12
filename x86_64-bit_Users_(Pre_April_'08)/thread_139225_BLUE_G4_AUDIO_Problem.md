---
title: "BLUE G4 AUDIO Problem"
date: 2006-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by shreeswifty on 2006-03-03
hi

i just installed ubuntu breezy on my g4 533. Everything seems rather sexy so far except for a sound issue. 

All the sound is being emitted from the internal speaker.
The headphones do not work at all. 

I tried the regular mixer, gamix and alsamixer/alsamixergui without any success.
checking and unchecking [pc speaker] does nothing [sound remains on] and the headphones seem to be greyed out.

this is a blue G4 that did not come with a line in, so i am pretty sure something funky is amiss, but i am hoping somoene else has encountered this already. 

thanks in advance.

---

### Post by Ptero-4 on 2006-03-03
First. Try that on OSX. In that way you can confirm or rule out hardware issues. Then if it isn't a hardware issue. Check to see if there's need for drivers on the headphones (or anything in between the headphones and your soundcard). Also check your soundcard drivers to see if the capality to drive external sound output devices is implemented in your current soundcard drivers and update them if needed.

---

### Post by linear on 2006-03-06
Some Mac models have problems with sound due to bugs in ALSA. See [here]("https://wiki.ubuntu.com/MartinEricRacine").

---

