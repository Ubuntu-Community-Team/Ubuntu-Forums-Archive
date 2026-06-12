---
title: "alsa drivers no 5.1 surroundsound"
date: 2006-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by luh3417 on 2006-11-05
I am running Dapper for x64 on an ASUS A8N-SLI motherboard with Creativelabs soundblaster Audigy Live! soundcard. (The native Nvidia soundcard drivers and generic drivers all work very badly; all I can get is stereo sound in 2 speakers) With my Audigy card I can get sound in all 5.1 speakers but not surround. A dvd will only play the surround and no front or centre channels. I gather I am not alone. I have loaded  snd-emu10k1. Is there a newer/other driver or patch that overcomes this problem. Help will be hugely appreciated. I notice there is no wav levels available in alsamixer.  Attached is a log from a speakaer test and amixer:

---

### Post by .t. on 2006-11-05
Have you run gnome-volume-control, added the channels to adjust (not there by default for me), and increased the levels on Surround, and such?

---

### Post by luh3417 on 2006-11-06
I had not tried that but I have now. No sound at all in 5.1 dvd playback. Here is stdout from mplayer playing a 5.1 dvd

Playing dvd://6.
There are 7 titles on this DVD.
There are 24 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: fr aid: 129.
audio stream: 2 format: ac3 (5.1) language: es aid: 130.
audio stream: 3 format: ac3 (stereo) language: en aid: 131.
audio stream: 4 format: ac3 (5.1) language: en aid: 132.
number of audio channels on disk: 5.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: fr
subtitle ( sid ): 2 language: es
number of subtitles on disk: 3
Cache fill:  0.00% (0 bytes)
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 6 ch, s16le, 448.0 kbit/9.72% (ratio: 56000->576000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================

alsa-lib: confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
alsa-lib: conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
alsa-lib: confmisc.c:242:(snd_func_getenv) error evaluating default
alsa-lib: conf.c:3493:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
alsa-lib: conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
alsa-lib: pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM surround51
alsa-init: playback open error: No such file or directory
Could not open/initialize audio device -> no sound.

Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12
V:   0.7  16/ 13 ??% ??% ??,?% 0 0 41%
demux_mpg: 24000/1001fps progressive NTSC content detected, switching

---

### Post by cyriq on 2006-11-06
[http://www.ubuntuforums.org/showthread.php?t=285065&highlight=audigy]("http://www.ubuntuforums.org/showthread.php?t=285065&highlight=audigy") should help you getting started and this: [http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml]("http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml") to configure mplayer for 5.1.

---

### Post by kuja on 2006-11-06
> **luh3417 said:**
> I am running Dapper for x64 on an ASUS A8N-SLI motherboard with Creativelabs soundblaster Audigy Live! soundcard. (The native Nvidia soundcard drivers and generic drivers all work very badly; all I can get is stereo sound in 2 speakers) With my Audigy card I can get sound in all 5.1 speakers but not surround. A dvd will only play the surround and no front or centre channels. I gather I am not alone. I have loaded  snd-emu10k1. Is there a newer/other driver or patch that overcomes this problem. Help will be hugely appreciated. I notice there is no wav levels available in alsamixer.  Attached is a log from a speakaer test and amixer:
ALSA is a PITA to configure. You basically have to turn surround on in an app by app basis. The thing is though, that for most occasions the sound coming out will only be regular stereo sound, rather than surround, and as thus will only come out of two of the speakers - to remedy this you have to turn on duplicate front in your mixer, and turn it off when you need real surround sound (ie: when watching a dvd, or similar).

---

### Post by luh3417 on 2006-11-07
I have tried every mixer setting I can. The problem is if I set mplayer to 6 channels there is no centre sound at all.

---

### Post by luh3417 on 2006-11-07
This thread had the answer
[http://ubuntuforums.org/showthread.php?t=204030](http://ubuntuforums.org/showthread.php?t=204030)
ie "Try renaming or deleting these two hidden files in your home directory:
.asoundrc and .asoundrc.asoundconf"

It worked :-)

---

