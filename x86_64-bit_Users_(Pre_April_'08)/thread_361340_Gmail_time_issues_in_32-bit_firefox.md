---
title: "Gmail time issues in 32-bit firefox"
date: 2007-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by fieldstone on 2007-02-14
Okay, here's my problem. I'm running Firefox on Feisty from a 32-bit chroot, mainly because this was the only way I could reliably get the mplayer plugin to work without tearing my hair out. No problems there so far.

However, I've recently noticed that the times listed on my messages in Gmail are completely wrong - for instance, at 9:50 this morning I received a message saying it was about 1:50 in the afternoon. I've tinkered around with "date" and "hwclock" in the chroot a bit, but it hasn't made any difference so far.

Is this a problem with gmail, or is it something I need to fix on my system?

---

### Post by fieldstone on 2007-02-14
After opening Gmail in 32-bit Opera, which is installed outside the chroot, I found that the times are displayed perfectly there. So there's most likely something about the chroot that I need to change, but I don't know what it is.

---

### Post by RAOF on 2007-02-15
Almost certainly the timezone setting.  Either **tzselect** or **tzconfig** are your winners.

---

### Post by hubert.muchalski on 2007-02-20
I have the same issue in Edgy. In all google services the date is shifted +24h
Opera/Konqueror shows correct date/time
Epiphany (Gecko based) - the same problem like with FF

Any idea?

Timezone/date/time are correct.

---

