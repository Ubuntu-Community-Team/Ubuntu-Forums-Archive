---
title: "Totem sound stopped working"
date: 2009-06-29
forum: x86 64-bit Users
---

### Post by xigen on 2009-06-29
Last night I installed Adobe Air and Gnome do.  Prior to installing Air and Gnome DO - Totem would play ASX playlists.  Specifically: kexp.org (windows media ->play).

I have reinstalled Totem, the restricted codecs and Gstreamer.  

Any suggestions on how to diagnose what is happening?   When Totem is running the visualization looks like everything is fine -- however, I do not hear any sound.

In firefox (3.xx) [http://kexp.org/audio/kexp-uncomp.asx](http://kexp.org/audio/kexp-uncomp.asx) ... works just fine.

AMD 64, Ubuntu 9.10, using ALSA,  Delta 66 sound card.

Cheers,
MW

---

### Post by xigen on 2009-07-10
I solved the issue.

Updates kill my ALSA server/settings and replace them with broken PulseAudio.

UGH!

Time to remove PulseAudio (again) and set up ALSA... again.

---

