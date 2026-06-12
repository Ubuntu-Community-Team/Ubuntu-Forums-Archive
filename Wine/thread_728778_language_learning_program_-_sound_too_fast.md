---
title: "language learning program - sound too fast"
date: 2008-03-19
forum: Wine
---

### Post by DFreeze on 2008-03-19
So I installed some spanish course for Windows using Wine. I didn't change anything in the Wine config - simply because I don't know jack about the settings. But the sound is too fast, I guess at least twice the speed.

I've tried under Gutsy and Hardy, but both times the same. Is this fixable? How?

---

### Post by happyhamster on 2008-03-19
- You can experiment with the sound settings using the 

winecfg

- command. Select the Audio tab, choose a driver (start with the default alsa, then oss, etc) and try setting a different sample rate, acceleration mode, etc. Each time re-running the program. 
Another option is selecting another windows version from the Applications tab (default = win2000).

Even in the unlikely scenario that you bork wine completely, you can just get rid of it and start afresh. First delete the hidden .wine folder in your home dir (press ctrl-h to see hidden files). Then:

sudo apt-get remove --purge wine

sudo apt-get install wine

winecfg


Good luck.

---

### Post by DFreeze on 2008-03-20
Thanks. I'll try to tweak the sound settings and see what happens. I will report back with the results...

:: UPDATE ::
I've tried almost all combinations, but to no avail. The sample rate or bitrate can be anything, but the speed stays the same (you just hear the quality of the sound get worse). What else could it be?

---

