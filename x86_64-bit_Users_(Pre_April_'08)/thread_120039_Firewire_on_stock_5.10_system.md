---
title: "Firewire on stock 5.10 system?"
date: 2006-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ottojschlosser on 2006-01-20
Hi all. I tried plugging a Firewire HD into my B & W G3 running 5.10, but it doesn't seem to be recognized. Is Firewire support compiled into the standard 5.10 PPC install? If not, what is involved in adding it? Thanks...

---

### Post by ssam on 2006-01-21
it works for me, but some other people have reported problems.

one suggestion is to upgrade pmount. you can do this using the synaptic package manager. (system -> administration -> synaptic package manager).

click reload, mark all upgrades, then apply to get the latest updates. (if you don't broadband and can't manage too large a download you can do a search for pmount and just update it, rather than the "mark all upgrades")

---

### Post by alari on 2006-01-21
I tried the 5.10 LiveCD on my iBook G4, i had an External Firewire HDD connected, and when i got to the Ubuntu desktop, it was mounted on the desktop, though i could only read and not write on the disk (HFS+ filesystem is supported read-only, or at least the last time i checked, it was).

---

### Post by felix_stegerman on 2006-01-21
[QUOTE=alari]HFS+ filesystem is supported read-only, or at least the last time i checked, it was.[/QUOTE]

I can write to my iPod's HFS+ filesystem just fine.
I'm not sure whether the new HFS+ used by Tiger is supported yet though.


Felix

---

### Post by ottojschlosser on 2006-01-23
[QUOTE=ssam]one suggestion is to upgrade pmount. you can do this using the synaptic package manager. (system -> administration -> synaptic package manager).[/QUOTE]

I appear to have the current version of pmount installed. It occurs to me that the HD may not be in a format that ubuntu/ppc can read. I'll try reformatting it and reconnecting. Thanks...

---

### Post by sulobanks on 2006-01-25
I have an external firewire HD I use with my ibook g4 running breezy.  It's very inconsistent in detecting the drive.  Usually, if I have the drive turned on for a long time before I boot up, it will detect it. There doesn't seem to be any rhyme or reason to it.  I've read some posts by a few others who have said it worked fine in hoary, but are having similar problems as me in breezy.  I might actually step back down to hoary until dapper comes out.

---

