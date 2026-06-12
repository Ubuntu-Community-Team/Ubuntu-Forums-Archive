---
title: "w64codec vs. w32codec"
date: 2007-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sunnz on 2007-10-15
There are various reasons why I want to run 64-bit version of ffmpeg on 64-bit OS.

ffmpeg would use w64codecs right? Just wondering how does it compare to w32codecs? Can it decode everything w32codecs decodes?

---

### Post by Corbelius on 2007-10-15
FFmpeg dont use anyone w32/64 codecs.

---

### Post by Kilz on 2007-10-15
> **Sunnz said:**
> There are various reasons why I want to run 64-bit version of ffmpeg on 64-bit OS.

ffmpeg would use w64codecs right? Just wondering how does it compare to w32codecs? Can it decode everything w32codecs decodes?

w64codecs/w32codecs are no longer needed because of ffmpeg.

---

### Post by Sunnz on 2007-10-15
Oh, I thought that MPlayer uses ffmpeg, which needs w*codecs?? So can ffmpeg decode wmv/real files?

Thanks.

---

### Post by Kilz on 2007-10-15
> **Sunnz said:**
>  So can ffmpeg decode wmv/real files?

Thanks.

Yes.

---

### Post by Sunnz on 2007-10-15
Oh, so w*codecs are needed at all?

---

### Post by John.Michael.Kane on 2007-10-15
> **Sunnz said:**
> Oh, I thought that MPlayer uses ffmpeg, which needs w*codecs?? So can ffmpeg decode wmv/real files?

Thanks.

From what I have read.ffmpeg/libavcodec1d In theory should cover the end user for the codecs below. 

Codecs
    * ATRAC3[2]
    * H.261,[2] H.263[2] and h.264/MPEG-4 AVC[2]
    * Indeo 2 and 3[2]
    * QDesign Music Codec 2, used by many QuickTime movies prior to QuickTime 7.
    * Sorenson 3 Codec used by many QuickTime movies
    * Theora (together with Vorbis makes a base for the .ogg format)
    * Truespeech
    * TXD[3]
    * VP5[2] and VP6[2]
    * Vorbis
    * Windows Media Audio
    * Windows Media Video- version 7 and 8 version 9 (decoding only)

Note: One reason that w32/64 might still be available is that some users have issues ffmpeg/libavcodec1d,however. This is only a guess.

---

