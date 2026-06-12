---
title: "Installation CD Freezes at root mount... help?"
date: 2006-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by cheuschober on 2006-09-11
trying to get ubuntu up as a myth solution on a mediacentre of mine. as the title says my install cd freezes at 'mounting the root filesystem.'

Any ideas?

distro:
ubuntu 6.06.0.1 - amd64

relevant specs:
msi k8n diamond plus
amd opteron 165
2gb gskill ddr400
320gb raid 0 array (si, samsung spinpoint-p, single pt - ntfs)
160gb samsung spinpoint p, single pt - ntfs
36gb wd raptor single pt - ntfs
gForce 6800GS

knoppix boots without a hitch.

Many thanks,
~Chad

---

### Post by mikeescott on 2006-09-11
It seems as though the hard drives are conflicting. That is what I was told.

---

### Post by cheuschober on 2006-09-11
So in otherwords I can't use any *buntu based linux distro on my system?

---

### Post by kuja on 2006-09-11
A lot of people seem to have trouble with the live install cd, perhaps the alternate one would work?

---

### Post by cheuschober on 2006-09-11
Is the alternate cd not a live cd?

I really need to test whether or not the analog and 24/96 spdif out functions work on my mb sound before I go using qtparted to resize and move partitions. The motherboard above has a unique onboard sound solution (the only one of its kind) in that it has a creative audigy instead of a more common realtek chip.

Thanks for the reply,
~Chad

---

### Post by kuja on 2006-09-11
Hmm, yeah, the alternate is a text mode installer, like ... no live, so I guess that wouldn't really work for you then.

The fastest way to check if the sound is supported is to check [http://www.alsa-project.org](http://www.alsa-project.org)... it seems to me that it's down for the moment though... I'll check it for you later.

---

### Post by cheuschober on 2006-09-12
Kuja-

Thanks so much for the help. ALSA was down yesterday, yes, hence why I was asking but I checked today and onboard or no it doesn't look like my card will be well-supported enough to hook it up to a $7k stereo.

I think the best case scenario for me will be to wait till Edgy. Because of the lack of a decent music application for my extremely specific needs I'm going to need to Xen up a copy of xp anyway (for foobar2k) and I'd rather wait a couple months for 'native' Xen support as opposed to a patched-in version in dapper.

Again, thank you so much for your help.

~Chad

---

