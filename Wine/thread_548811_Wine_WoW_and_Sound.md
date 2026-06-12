---
title: "Wine WoW and Sound"
date: 2007-09-11
forum: Wine
---

### Post by ExSuSEusr on 2007-09-11
Been searching around and can't find any documentation on this issue - so maybe someone here has had the same thing happen, or can point me in the right direction on a fix.

WoW is working great.  Logging, playing, everything - nice and stable.

Even the sound works greats - until - I move the Wine window, open a browser, switch to a different desktop, or anything else... then the sound goes completely off (in the game).  Over all the sound still works - I can start up XMMS and it'll play just fine.  But the only way to get sound back in WoW is to log out and back in again.

Strange?

Oh and the game play stays nice and smooth - just the sound shuts off if I move the window or "do" something other than WoW while it's active.

---

### Post by Dark Aspect on 2007-09-12
What are you using under wine config,ALSA or OSS sound?

I have never played WOW but you might want to try switching your sound to whatever audio driver your not using.I prefer ALSA under wine config for most of my games.

---

### Post by galroth on 2007-09-12
This is a documented bug on winehq.org.  I've read that if you enable the "Play sound while in background" option under the Sound menu in WoW it will still work.

---

