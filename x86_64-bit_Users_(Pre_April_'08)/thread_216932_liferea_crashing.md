---
title: "liferea crashing"
date: 2006-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by jamesford on 2006-07-16
all the time..is it just me or is the 64 bit liferea fcked?

---

### Post by hajk on 2006-07-16
Hmm... I have it running all the time without problems. What do you mean by "crashing"? Some sites are just busy or difficult to reach during scheduled update, resulting in a red error message... nothing to do with Liferea proper.

---

### Post by jamesford on 2006-07-16
i mean crashing as in closing, disappearing, and doing it again as soon as i restart it and click on a feed

---

### Post by hajk on 2006-07-16
Try to do a reinstall, after first purging the package from /var/cache/apt/archives. If it then still crashes, chances are that it is something in your own setup.

---

### Post by jamesford on 2006-07-16
i found the fix, i changed 'view headlines with' from gtkhtml2 to mozilla. weird cos using gtkhtml was the only one that worked for me in 32 bit

---

### Post by hajk on 2006-07-16
Well, there you go then. People are creatures of habit, isn't it?

---

