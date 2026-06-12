---
title: "[SOLVED] Wine and USB headset"
date: 2008-07-11
forum: Wine
---

### Post by Prefix100 on 2008-07-11
I'm trying to get my USB headset to work in wine.

Primarily for my MIC in ventrilo.

My microphone works in linux, specifically audacity when I set the mic to mono.

I have tried this guide, what 3 times now? [http://forums.worldofwarcraft.com/thread.html?topicId=2200220013&sid=1](http://forums.worldofwarcraft.com/thread.html?topicId=2200220013&sid=1)

I think its outdated and Ubuntu uses different stuff so it doesn't work.

When launching winecfg from terminal I'm told that my usb headset is disabled - I think I need this to stop first.

```
ALSA_MixerInit No master control found on C-Media USB Headphone Set  , disabling mixer

```

---

### Post by Drk Guy on 2008-07-11
This looks like an issue in ALSA/Wine, "No master control found"?, weird, maybe some switch at compilation time, can you try another repo's wine?, maybe mine will work, go wine's sub-forum for more details

---

### Post by Prefix100 on 2008-07-12
Got it fixed :)

Turns out that error is standard. 

I had to mess around with vent settings and stuff to get it to work then applied the ptt hack for vent - and now im alllll goood :)

---

