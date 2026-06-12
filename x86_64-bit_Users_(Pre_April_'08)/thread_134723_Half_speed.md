---
title: "Half speed"
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hoskins on 2006-02-22
Just put Ubuntu on my powerbook (last but one rev), running well except the cpu is stated as running at half speed in hardware info, 883mhz not 1.67ghz (kernal 2.6.12-10). The system does seem a little sluggish screen redraw is slow like Tiger on my old G3 ibook, though could this be the vid driver? Suggestions anyone, couldn't find a thread on this here and go easy on a linux newb???

---

### Post by Ptero-4 on 2006-02-23
Do you have powernowd with powerprefs. Your problem may be a misconfigurated power saving daemon or no power saving daemon at all.

---

### Post by Hoskins on 2006-02-24
Thanks for coming back Ptero-4. As is always the way, the morning after the post I found an explanation that the previous 2 days of searching missed. The speed is automatically stepped, shake a few windows and the cpu frequency jumps up to deal with load. The window redraw lag may be a gnome issue according to others, may have to try a different WM.

---

