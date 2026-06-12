---
title: "Only stereo instead true 5.1 sound in WoW"
date: 2008-08-19
forum: Wine
---

### Post by gutko on 2008-08-19
Hi,
Im trying to get WoW to sound the same way as in win xp - i mean in real 5.1 - no duplicating channels etc...
I have 8.04 with recompiled alsa 1.0.17 and Xonar DX card.
Problem is that WoW in Wine 1.1.2 detects only stereo mode as SESound.log file in wow logs says:
```
8/18 16:22:22.509   - Detected Control Panel Speaker Mode = STEREO
8/18 16:22:22.509   - Setting WoW Speaker Mode to STEREO
```

but in winxp WoW detects real 5.1 (set to 5.1 in control panel):
```
8/18 13:31:20.421   - Detected Control Panel Speaker Mode = 5.1
8/18 13:31:20.437   - Setting WoW Speaker Mode to 5.1
```

And the difference in sorrounding sound is HUGE.

As control panel's settings in Ubuntu are handled by wine i was trying to find number of channels setting in wine registry but with no luck.
Any suggestions where to look next?

---

### Post by gutko on 2008-08-20
I have found answer on wine forums. wine supports only stereo mixing mode:(
[http://forum.winehq.org/viewtopic.php?t=2075]("http://forum.winehq.org/viewtopic.php?t=2075")

---

### Post by MemoryDump on 2008-08-22
> **gutko said:**
> I have found answer on wine forums. wine supports only stereo mixing mode:(
[http://forum.winehq.org/viewtopic.php?t=2075]("http://forum.winehq.org/viewtopic.php?t=2075")

that really sucks :(
really wish Blizzard would release a Linux client.. it's not like it would cost them a fortune.. and it's not like they don't have the money.. I don't care if it would be released with NO support, we'd be able to take care of ourselves here :P

---

### Post by Swarms on 2008-08-22
> **MemoryDump said:**
> that really sucks :(
really wish Blizzard would release a Linux client.. it's not like it would cost them a fortune.. and it's not like they don't have the money.. I don't care if it would be released with NO support, we'd be able to take care of ourselves here :P

Compared to how many new customers they would get I would not be too sure about that.

---

