---
title: "AMD64 3700+ and ATI X800XT"
date: 2006-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by TFX360 on 2006-08-25
Hello all,


I have got Dapper up and running 32bit with Xgl and all. I was curious about the 64-bit edition. 

I booted the live cd and get a Xorg error screen. In the safe graphics mode my flat panel led only blinks at me without giving screen. 

It can't find the device. I checked it in /etc/X11/xorg.conf and it looked ok, stating X800 and all. I saw the depth was at 24. I changed it to 16 but X still doesn't start. Not that I think it would but I saw it in a solution somewere reading up on Xgl.

I'm in absolutely no hurry. I can't find anything on this subject and there is now way known to me to get this under the developers attention. This is core and I should work, even if it only runs in Safe Graphics mode.


Be glad to hear from you,


Kind regards,


TFX

---

### Post by TFX360 on 2006-08-26
Nobody an idea?

---

### Post by Kilz on 2006-08-26
> **TFX360 said:**
> Nobody an idea?

Did you install the os, or is this the live cd that has no graphics?

---

### Post by kaffelars on 2006-08-30
You have to manually change the driver to "vesa" when running the live CD, the "ati" driver doesn't work for the ATI x-series cards.

---

### Post by TFX360 on 2006-08-30
> **Kilz said:**
> Did you install the os, or is this the live cd that has no graphics?

Live CD

---

### Post by TFX360 on 2006-08-30
I'll try that!

---

