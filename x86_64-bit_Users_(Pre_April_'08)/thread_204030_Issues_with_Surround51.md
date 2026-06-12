---
title: "Issues with Surround51"
date: 2006-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Beamerboy on 2006-06-26
I am trying to get 6 channel sound working with my AC97 onboard sound (Nforce4 mainboard) and I am having some issues.

speaker-test -c6 is giving me the following results:

Front Left - Works
Front Right - Works
Center - This is being output on Rear Left
Rear Left - No Output
Rear Right - No Output
LFE - This is being output on Rear Right

If I use speaker-test -c6 -Dplug:surround51 I get the following errors:
```

paladine@main:~$  speaker-test -c6 -Dplug:surround51

speaker-test 0.0.8

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory

```

Any help appreciated.

BeamerBoy

---

### Post by Sevmpe on 2006-06-28
Hi,

Try renaming or deleting these two hidden files in your home directory:
.asoundrc and .asoundrc.asoundconf

Cheers.

---

### Post by peter07 on 2006-09-12
I have the same problems.

>  	Hi,

Try renaming or deleting these two hidden files in your home directory:
.asoundrc and .asoundrc.asoundconf

Cheers.

OK, i've moved .asoundrc and .asoundrc.asoundconf, and now i can do:

```
speaker-test -c6 -D surround51
```

Now I get:

Front Left - This is being output on Rear Left
Front Right - This is being output on Rear Right
Center - Works
Rear Left - No Output
Rear Right - No Output
LFE - Works

But that's only in test. For example, when I use XMMS (with double front option)

Front Left - Works
Front Right - Works
Center -No Output
Rear Left - Works
Rear Right - Works
LFE - No Output

5.1 sound doesn't work, and quality of 2+2 is really bad :(
I need help !!

---

### Post by Tomcat_ on 2006-09-24
> **Sevmpe said:**
> Hi,

Try renaming or deleting these two hidden files in your home directory:
.asoundrc and .asoundrc.asoundconf

Cheers.

Thank You so much... I had multiple problems getting 5.1 to work with totem (although it always worked some time ago). I switched on debug and found "surround51" problems... found this thread. Moved the files. Works!

Thanks man! :-D

---

### Post by luh3417 on 2006-11-11
> **Sevmpe said:**
> Hi,

Try renaming or deleting these two hidden files in your home directory:
.asoundrc and .asoundrc.asoundconf

Cheers.

I have this same problem and when I renamed .asoundrc and asoundrc.asoundconf to .asoundrc.old and asoundrc.asoundconf.old surround worked fine. But since re-booting I get no sound. If I rename these files I get no sound and alsamixer defaults to the onboard soundcard. The only way I can get any sound is to leave the files  in tact. What do I do to get the Audigy soundcard hw 2,0) to work without the .asoundrc and asoundrc.asoundconf files?

Thanks

---

### Post by kleeman on 2006-11-11
Here is a good howto
[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)
BTW the xmms howto on this page works for beep-media-player as well. The difference in the sound of internet radio is simply amazing!

---

