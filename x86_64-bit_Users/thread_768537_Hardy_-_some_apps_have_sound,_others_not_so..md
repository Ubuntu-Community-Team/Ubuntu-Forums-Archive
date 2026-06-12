---
title: "Hardy - some apps have sound, others not so."
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by allywilson on 2008-04-26
Hi folks,
        Upgraded to Hardy Heron. Had a few issues, nothing I've been able to get around yet though. Until now...

Scenario: Boot up - logon screen - Ubuntu bongo drums sound come out of the speakers. Excellent thinks I, sound working from the word go.

Nonono.

If I play an MP3 using mpg123 from the shell - it works fine. If I try to play the MP3 from any other player (VLC, xine, totem, serpentine, etc, etc.) I get nothing. No errors when I increase the verbosity when launching. So, I'm stumped. Wine will still play back sounds (tested by downloading and installing the original GTA and GTA2 for some nostalgia before GTAIV comes out).

Now, I've obviously checked the config on all of the apps - except I can't seem to find any reference to using anything that it shouldn't be (ALSA, Nvidia on-board card). The only weird thing is that when increasing the verbosity on mpg123 shows that it's using "Audio device: <none>" - which for the one app that's working I find strange.

I can't seem to find any reference to audio or whatnot in /var/log/messages or dmesg...

Anyone got any suggestions?

---

### Post by soxs on 2008-04-26
I have the same problem, but a it is limted to totem.
Totem does not give me *any* beep while exaile (gstreamer-based) and amarok(xine-based) work like a charm.

---

