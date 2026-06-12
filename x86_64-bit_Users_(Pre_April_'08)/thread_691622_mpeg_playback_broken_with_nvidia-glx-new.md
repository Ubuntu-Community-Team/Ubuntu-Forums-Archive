---
title: "mpeg playback broken with nvidia-glx-new"
date: 2008-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by exp(x) on 2008-02-08
Mpeg playback with any program (tried mplayer, xine, vlc, totem) is totally messed up when using the nvidia-glx-new driver on my 64-bit Gutsy with an Nvidia 6600. The sound works fine, and there is no problem with non-mpeg videos. This doesn't happen with the "nv" module.
[IMG]http://exp.mancubus.net/files/mpeg-broken.png[/IMG]

---

### Post by crjackson on 2008-02-08
Did you do a ctrl+alt+backspace, and log in again?  I had this issue with my nVidia 7900GTO but then we got a Kernel update and it fixed the issue.

---

### Post by exp(x) on 2008-02-08
Yeah, that didn't work. I ended up just switching to the non-new nvidia-glx package. I know the newer drivers should work, but I guess I don't really need them.

---

