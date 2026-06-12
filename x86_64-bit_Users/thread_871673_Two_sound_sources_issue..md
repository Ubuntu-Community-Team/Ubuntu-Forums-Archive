---
title: "Two sound sources issue."
date: 2008-07-27
forum: x86 64-bit Users
---

### Post by Kaisen on 2008-07-27
Hi, I'm new to ubuntu, and so far I'm REALLY digging on it. There's a problem though, whenever I play WoW (which I'm running through Wine) with sound in the background, using amarok, or youtube even, My WoW sound disables itself until I close amarok (or the other source) and re-open WoW. I've taken random stabs at why this is happening with no luck, And if there's already a hotfix posted for this, sorry. I'd love to have this issue resolved because, honestly I can't stand playing WoW without music. :(


Thanks in advance, Kaisen.


Also, what the heck is this error? 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by kochecc2 on 2008-08-04
I saw your other post about WoW and decided to look up your other post. Turns out I might be able to help with this one too. Wine uses one of two sound archetectures, ALSA and OSS. ALSA *can *handle multiple sound sources gracefully, while OSS cannot. Check your wine sound settings for that. Also, alt-tabbing out of WoW to change something in Amarok will kill not only your WoW sound, but also your framerate ingame. I use a keyboard with audio control buttons to change tracks so I don't have to use alt tab.

---

### Post by Yellow Pasque on 2008-08-04
> ALSA can handle multiple sound sources gracefully, while OSS cannot.

OSS4 can handle multiple sounds gracefully (much better than ALSA, which is why Ubuntu enabled PulseAudio in 8.04).

---

### Post by Nepherte on 2008-08-04
It's a pulseaudio issue. To verify your problem, you could run the following two commands simultaneously, each command in a seperate terminal:
```
gst-launch-0.10 audiotestsrc ! pulsesink
gst-launch-0.10 audiotestsrc ! alsasink
```
If you don't have sound from the last one, it means that pulseaudio blocks access to your sound card from any other program but the first one using audio.

This topic provides a solution for it: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Kaisen on 2008-08-04
Thanks a ton for the feedback, Nepherte. Sound's working great now. :)

---

