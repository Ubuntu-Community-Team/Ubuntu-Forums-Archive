---
title: "Avidemux aborts when I append a movie"
date: 2006-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryan76 on 2006-11-24
I'm trying to splice some VOB files together using Avidemux. I have tried in both 64-bit and 32-bit environments on my computer and with both of them it aborts as soon as I try to play or scroll through a file I have appended onto another one.

EG I open a vob file, then Append another one to put them together, and as soon as I play or scroll to the appended file, it aborts. 

Here's the output:

```
________Video______________
 Video : 0, nb video  :1796, audio size:4030208  audioDuration:3448320
 Video : 1, nb video  :2156, audio size:4836608  audioDuration:4139520
______________________
 Seg : 0, ref: 0 start :0, size:1796 audio size : 4030208 audio start : 0 duration:3448320
 Seg : 1, ref: 1 start :0, size:2156 audio size : 4836608 audio start : 0 duration:4139520
_________Clipboard_____________
 Editor :Audio streamer initialized
 Audio codec:  AC3
 One frame : 40, err=0 ms

 1 audio frame = 7680 bytes (1).. Offset ...40 ms

 Syncing on 8192
Sync found at offset 1344
A52 sync found at 2240 + 1344

 OSS  : 48000 Hz, 2 channels
No accelerated IMDCT transform found
 OSS  : 48000 Hz, 2 channels
 AC3 decoder initialized.
=============
No accel used for rendering

 Syncing on 8192
Sync found at offset 0
A52 sync found at 0 + 0
EditorPacket : switching to segment 1
avidemux: ADM_image.cpp:104: uint8_t ADMImage::duplicateMacro(ADMImage*, uint32_t): Assertion `0' failed.
Aborted
```

I'd appreciate help with this particular error, rather than suggestions of other software to use. Kino will not do what I need either and I am too inexperienced to try Cinelerra.

Thanks

---

### Post by FluffyElmo on 2006-11-24
This actually works for me, Avidemux version 2.1.2, 64bit. When opening the .vob it asks if I wish to index and I click yes. The same for the second.vob. 

I get the same "No accel used for rendering" message you do and several "A52 sync messages" when it hits the join but it doesn't crash.

---

### Post by ryan76 on 2006-11-25
Yes that's the version I'm running. I've tried running it as root since then with no success either.

---

### Post by ryan76 on 2006-11-29
So I guess no one knows what to do...

---

