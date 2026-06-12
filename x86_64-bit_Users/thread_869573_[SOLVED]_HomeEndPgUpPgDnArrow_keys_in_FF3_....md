---
title: "[SOLVED] Home/End/PgUp/PgDn/Arrow keys in FF3 ..."
date: 2008-07-24
forum: x86 64-bit Users
---

### Post by xen-uno on 2008-07-24
... are not working. They do work as expected on other Ubuntu x64 apps. I've done some searching and it may be a key binding issue. Anyone experienced this with FireFox and know of a fix?

---

### Post by lswb on 2008-07-24
Try pressing the F7 key. This toggles a feature called "caret browsing" which drove me nuts before I found out what it was and how to shut it off.

---

### Post by xen-uno on 2008-07-24
That's not it. Everything I've read regarding Linux Firefox is that it should behave like Windows as far as accelerator keys are concerned (Home: Top of page, End: Bottom, etc). I'm positive it did on 7.10 and FF2. Something is broken.

---

### Post by EBAR on 2008-08-01
> **lswb said:**
> Try pressing the F7 key. This toggles a feature called "caret browsing" which drove me nuts before I found out what it was and how to shut it off.

Oh my god, thank you...That was driving me insane!

---

### Post by xen-uno on 2008-08-01
Fixed the problem by Edit>Preferences>Advanced>General(tab) and checking "Always use the cursor keys ...", saving, hitting a few of the problem keys, then going back and unchecking that option. I also uninstalled the Paste and Go 2 extension as it doesn't work correctly under Linux. One or both corrected the problem.

---

