---
title: "solved: Sound Acer Aspire 5051 Amd Turion 64"
date: 2009-05-23
forum: x86 64-bit Users
---

### Post by allp on 2009-05-23
After installing Ubuntu 9.04 my laptop Acer Aspire 5051 Amd Turion 64 could not play any sounds, although it could do that if I plugged in headphones.

To solve this problem you have to follow these directions:

1. Inside terminal,

$ sudo nautilus

2. When the navigator opens, go to the folder modprobe.d (in the etc folder) and doubleclic the file alsa-base.conf to edit it. Once opened, you have to add the following three lines at the end of it:

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer-aspire
options snd-hda-intel index=0 probe_mask=3 position_fix=3

Save and close

3. Open AlsaMixer:

$ alsamixer

Turn up the volume controls of Master, PCM and Front, using the arrow keys.

That's it. We can hear sound in our laptop again!

---

### Post by rols on 2009-07-06
Thanks for that - I'm pretty new to Ubuntu and had tried several suggestions to get the onboard sound to work on this laptop to no avail ( resorted temporaily to using a USB adapter!).

This worked a treat.

Rols.

---

### Post by skohari on 2009-09-08
oh this worked like a dream... thank you so much!!!
and also to the guys behind Jaunty, am absolutely loving it! Thanks to all!!!

---

### Post by jaret100 on 2009-09-11
This too worked for me and i have an hp tx 2525! apprec!

---

