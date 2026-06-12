---
title: "mplayer sound, but  no  video"
date: 2006-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by seatea on 2006-05-03
I am tring  to get all my video components working, but I am making progress at a snail's pace. My latest attempt is at playing  movie  trailers. After having no luck with the gxine plugin in firefox, I am now troubleshooting  mplayer. Gxine  would not play sound  or anything, but  would open and say I didn't have the  necessary software. I had  installed everything  I  could. I  switched to mplayer and can get the window to open and play the  trailers, trailers.apple.com, but I only get sound. Does anyone have any advice?


I have a PM G4 400 with ati technologies inc  rage128 pf/pro graphics card. I had considerable trouble getting  dvds to play and have decreased my color depth to 16 and disabled xv which means I am using X11/XShm. I don't know if dropping the color resolution helped, but using the X11/XShm definitely did.

---

### Post by linear on 2006-05-03
Try installing totem-xine (will replace totem-gstreamer). This seems to fix a number of multimedia problems.

---

### Post by bforbarry on 2006-05-03
I'm having almost the same problem as you, except the other way around. Got my Totem working by following this link from erik1397,   [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

But i have no sound. No sound at all. My little speaker icon up in the panel bar has an x beside it. In other words, it's not detecting my soundcard for some reason. I've tried checking all the posts, but no success yet. I've installed all the "alsa's" in synaptic manager. Anybody have any ideas ? One other thing, sometimes Totem won't play some dvds. I'll get the error message, "r u trying to play an encripted dvd without "libdvdcss" .  Where & how do I get, and install this. Bear with me, I'm really new and green with Linux.

Good luck !

---

### Post by linear on 2006-05-03
Keep on reading in the [RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats") wiki item. Instructions for installing libdvdcss are there.

What model Mac/soundcard do you have?

---

### Post by seatea on 2006-05-03
I tried using totem-xine  and its plugin, but nothing  happened. There was no attempt at playback of any kind. That is better than gxine, which causes Firefox to quit unexpectedly. The software message from gxine that I have gotten before Firefox quits  was about no "demuxer" being found. What is that? Totem plays dvds only if I don't use Xv.

---

### Post by bforbarry on 2006-05-04
Thanks linear. Should've mentioned what I had:   ibook G4, 1.42ghz, 768mb, with Texas Inst. TAS 3004 sound card.  Dual booting.
Went back to the restricted formats, and tried to get the libdvdcss, but came back with this;    Couldn't find package libdvdread3
barry@Barrys:~$   sudo /usr/share/doc/libdvdread3/examples/install-css.sh
sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found
barry@Barrys:~$
Checked the package manager, and totem-xine is installed..
thanks again, Barry

---

### Post by linear on 2006-05-04
[quote=bforbarry] tried to get the libdvdcss, but came back with this;    Couldn't find package libdvdread3[/quote]
That's odd - libdvdread3 should be there; I can see it in Synaptic.

---

### Post by bforbarry on 2006-05-04
Okay, thats right, libdvdread3 is there and installed. Haven't really tried a protected dvd yet, but still haven't got the sound thing worked out yet. Found a thread with this  suggestion, and came back with this:

barry@Barrys:~$ sudo gedit /etc/modprobe.d/alsa base
ALSA lib confmisc.c:672: (snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493: ( _snd_config_evaluate) function snd_func_card_driver return ed error: No such device
ALSA lib confmisc.c:392:  (snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:  ( _snd_config_evaluate) function snd_func_concat returned er ror: No such device
ALSA lib confmisc.c:1072: (snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned err or: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
barry@Barrys:~$
So still no sound card. Would really appreciate some more ideas on this problem, because if I got this working, I'd have pretty much all I would need. Got wireless internet, bluetooth mouse, printers, video, just no audio.
thnx again, Barry
sorry, tried to get rid of the frownies

---

