---
title: "Ubuntu Has Suddenly Become Really Unstable"
date: 2008-09-20
forum: x86 64-bit Users
---

### Post by Throne777 on 2008-09-20
Tonight may just be a bad night, but Ubuntu has decided it hates me. Or is ill. Whatever.
Anyway, twice it has failed to load the GUI (instead doing some sort of Blue Screen of Death followed by a text based terminal to log in), then when it didn't fail to load it Firefox crashed about 30 times for no apparent reason. Sometimes it'd just close itself as if I'd close it (doing the little animation), sometimes it'd just disappear, othertimes it'd do that whole 'I've decided to turn grey' thing and so on.
Then after another rebooting it just froze. The entire thing froze. Even the mouse, which I've never had happen in my two years or so running Ubuntu.
Does anyone know why this is happening?
Thanks.

---

### Post by ruffwuk on 2008-09-20
Sounds like your Xserver has been corrupted. you mentioned it was running smoothly for 2 years, well you must have installed something or the Xserver config has been corrupted.  check your settings and try to load backup xorg.conf and see what happens.  I am sure someone will come to your rescue so hang in there. I am a novice as well, for a few years myself, and the reason i use Ubuntu, is because this community is tight and we all try to help each other so someone who has more knowledge than me will probably post soon.

---

### Post by steveneddy on 2008-09-20
Maybe a hardware issue?

---

### Post by bford16 on 2008-09-20
Please try running a Failsafe GNOME session, and let us know the result.  You may simply have a corrupteds session file.

---

