---
title: "Unknow device"
date: 2006-08-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Matrixy on 2006-08-27
Hi,
i have seen now that i have unknown device installed???
i know it means the ubuntu has no driver for it.
how can i be sure wht it is?
my pc specs are:
AMD64 3800+ Dual core
MSI Geforce 7600GS 256MB
MSI k9n-SLI Platinum
Sata HDD - WD250GB 16MB buffer("KS series")
NEC DVDRW 3550
2X512 OCZ 667 Dual DDR of memory.

wht can it be??
p.s: my nvidia card is working fine - installed the driver.

---

### Post by Matrixy on 2006-08-27
Hi,
now i have added a Screen snapshot

---

### Post by ajgreeny on 2006-08-27
Looks like it is your soundcard that is unknown. Do you get sounds when using the system, eg at boot up or if playing cd's.  therevshould be a bit of music at boot time when the desktop appears.  If you hear that, then I shouldn't worry too much about the error message, though I agree it's always nice to know what all these things mean.

---

### Post by Matrixy on 2006-08-28
Hi,
i do hear sounds and music but i realy want to know which device is unknown.
is there a way to tell?

---

### Post by Ausus on 2006-08-28
Hi Matrixy,

"ALSA" is the generic Sound card driver under Linux.
At home my sound device is a "Realtek" IC chip part of the motherboard.
Under WinXP it is called AC97 sound device, that is generic.

But Linux structure can't identify you onboard sound chip.
It does not now what make is of your onboard sound IC chip.
All sound IC chip work on the same principle on generating sound.
That is why you can hear sound.
That is where generic comes in.

Regards

---

### Post by Matrixy on 2006-08-28
ok.
is there a way to change it??
so there no unknown devices...

---

### Post by kuja on 2006-08-28
You probably don't need to worry about it, so long as everything works. My system lists quite a handful of "unknown devices too"

---

### Post by Ausus on 2006-08-28
Hi Matrixy

As kuja pointed out if it works it works.
So dont bash your head about it.

Ubunto see's all my devices.
Mobo Ausus A8N32 SLI Deluxe

regards

---

