---
title: "ape files"
date: 2008-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by hvacr on 2008-03-01
I am trying to play ape files on my system. I have tried a few programs with no luck. So far I am reading that this cannot be done in ubuntu 64. Do I need to dump Ubuntu 64 and go with the 32 bit version just to be able to play ape files?

---

### Post by ung/xunil on 2008-03-01
Yes, ape files are hard to read in Linux. There was some debian package somewhere in the internet to use ape files, but couldn't find it anymore.

I solved the problem with Wine and installed Monkey's audio. Runs without any problem with the wine package from wine website (didn't tested with wine from Ubuntu repositories). After I get the wav file, I use bchunk to split the music files:

```
bchunk -w bigfile.wav bigfile.cue music_
```

"music_" will be the start of the filenames of all musics: music_1.wav music_2.wav music_3.wav etc.

---

