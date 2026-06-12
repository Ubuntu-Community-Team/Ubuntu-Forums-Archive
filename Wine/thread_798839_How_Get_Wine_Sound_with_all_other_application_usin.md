---
title: "How: Get Wine Sound with all other application using sound"
date: 2008-05-18
forum: Wine
---

### Post by mysticmatrix on 2008-05-18
I found this method at a wiki explaining configuration of PulseAudio.

**Problem:** 
Wine/PulseAudio don't love to work with each other. So if you first start a MusicPlayer and then a application in Wine, you will not get sound in Wine.

**End Product:** 
I cannot play Counter-Strike with Rythmbox playing my favorite tunes.
[B]
Solution: [/B]
1. Change your sound device to OSS in the winecfg's Audio Tab 
2. Launch the application needed with 'padsp' in prefix

Eg. If you want to launch program WinAmp, use

```
padsp wine winamp.exe
```

If it works, reply back. This seemed to fix problem for me.

Downside: Not all applications work well with the OSS plugin, and in that case we are left with no choice

---

### Post by schtufbox on 2008-05-18
Pulseaudio seems to be weird. For some, myself included, it's working fine. I can play music in other apps while sound is also workign fine in wine. For others...well Wine and Pulse just don't play nice together :/

---

