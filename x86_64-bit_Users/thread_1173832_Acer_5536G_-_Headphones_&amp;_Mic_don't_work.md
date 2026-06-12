---
title: "Acer 5536G - Headphones &amp; Mic don't work"
date: 2009-05-30
forum: x86 64-bit Users
---

### Post by edu77pose on 2009-05-30
Hi all,

After purchasing an Acer Aspire 5536G I put Ubuntu 9.04 Jaunty on it.  I'm very happy with it.  Everything works quite well, however the external headphone & microphone don't work.  Now the notebook comes with it's own internal mic & speakers.  The speakers work however the internal mic & external mic and headphones don't.

Don't ask me too much on code because I'm more gui orientated.

Any help will be appreciated.

Eddie
[SIZE="1"]Acer Aspire 5536G - AMD Dual Core X2 QL-64, ATI 4570, 4GB DDR2, 320GB HDD
Ubuntu 9.04 (x64)[/SIZE]

---

### Post by Yellow Pasque on 2009-05-30
Run this and make sure they're not muted:
```
alsamixer
```

Failing that:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Copy and paste this line onto the end of the file:
```
options snd-hda-intel model=acer
```
Save. Quit. Reboot. Run alsamixer again and see if any new controls/jacks show up.

---

### Post by edu77pose on 2009-05-31
Hey Temujin, thanks for the quick response!

I did the changes as you requested & several days later came back to try it & it worked!

Thanks for the advice, much appreciated.

Cheers Mate,

[SIZE="2"][SIZE="2"]Eddie
Acer Aspire 5536G - AMD Athlon X2 QL-64, ATI 4570, 4GB DDR2, 320GB HDD
Ubuntu 9.04 (x64)[/SIZE][/SIZE]

---

### Post by edu77pose on 2009-06-14
Ok, it worked for one day then issues arose again.

This time I put at the bottom of this file: **/etc/modprobe.d/alsa-base.conf ** 

options snd-hda-**ati** model=acer

The change from ati to intel seemed to work, (seeing as it is an ati card, it seemed logical).

The commands helped to determine which sound preference should be used:
```
cat /proc/asound/card0/codec#* | grep Codec
``` &

```
aplay -l
```

from this thread:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

There's a lot of playing around but hopefully this is a permanent fix!

---

### Post by Yellow Pasque on 2009-06-14
> The change from ati to intel seemed to work, (seeing as it is an ati card, it seemed logical).
No, it's not logical. "snd-hda-ati" is not a valid ALSA driver, so you effectively removed the line by making that change. The driver is named snd-hda-intel after the Intel Azalia HD Audio specification, regardless of what motherboard chipset or audio codec is used.

Why does it work one day and not the next? That's beyond me, but I'm glad your sound works and I wish you continued aural emanation.

---

### Post by edu77pose on 2009-06-15
> **Temüjin said:**
> No, it's not logical. "snd-hda-ati" is not a valid ALSA driver, so you effectively removed the line by making that change. The driver is named snd-hda-intel after the Intel Azalia HD Audio specification, regardless of what motherboard chipset or audio codec is used.

Why does it work one day and not the next? That's beyond me, but I'm glad your sound works and I wish you continued aural emanation.

Well, I can tell you it works. It may not fulfill the ALSA driver but the microphone is working properly.

Thanks for you help

---

