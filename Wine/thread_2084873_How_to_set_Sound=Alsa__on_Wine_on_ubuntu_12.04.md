---
title: "How to set Sound=Alsa  on Wine on ubuntu 12.04"
date: 2012-11-16
forum: Wine
---

### Post by lazarojhr16 on 2012-11-16
Winetricks won't remember settings and without sound=alsa I can't use RosettaStone because it doesn't recognize my microphone. On the Wine forums they say to ask here because Ubuntu has made modifications to wine. Is there a way to make winetricks remember my settings? maybe through a terminal command or something, or is there another way of getting the mic to work on RosettaStone. I'm using the new Wine version wine-1.5.17. Thank you for any help.

---

### Post by lazarojhr16 on 2012-11-16
this is what i get in the terminal when i try to make sound=alsa

Executing w_do_call sound=alsa
Executing load_sound alsa
Setting sound driver to alsa
Executing winetricks_early_wine regedit C:\windows\Temp\_sound=alsa\set-sound.reg
You opted in, so reporting 'sound=alsa ' to the winetricks maintainer so he knows which winetricks verbs get used and which don't.  Use --optout to disable future reports.

---

### Post by lazarojhr16 on 2012-11-23
This is what I did, and now it works.
I installed Playonlinux, then installed wine version 1.5.18 through Playonlinux. Then installed Rosetta Stone and now it recognizes my Mic. By the way I'm on 64 bit Ubuntu 12.10 now. Hope this helps someone else.

---

