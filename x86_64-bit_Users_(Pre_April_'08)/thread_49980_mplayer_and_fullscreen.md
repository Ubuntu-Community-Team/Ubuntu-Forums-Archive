---
title: "mplayer and fullscreen"
date: 2005-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Liakoni on 2005-07-18
I just install Ubuntu hoary in my new AMD64.
I installed NVIDIA drivers ang i compilled MPlayer.
But when i try to play a video in fullscreen i get a small video-size in the center of the screen.

Has anybody any idea that can help me?

---

### Post by Liakoni on 2005-07-18
I have the same problem with vlc.
I can't get fullscreen to work.
With totem it works just fine...

---

### Post by arunsub on 2005-07-18
sudo gedit /etc/mplayer/mplayer.conf
set zoom=yes and save and exit. See if that helps. This helped me for zooming mplayer in Firefox, but I'm not sure if it helps for stand alone play. It might help.

---

### Post by aglauser on 2005-07-18
[QUOTE=Liakoni]I have the same problem with vlc.
I can't get fullscreen to work.
With totem it works just fine...[/QUOTE]
 Probably the video driver that you have mplayer set to use does not support scaling.  I had the same problem when I first installed mplayer.  I just had to try different video drivers to get fullscreen to actually fill the screen.  Be warned that specifing a driver that doesn't work properly on your system may cause mplayer to hang, in which case you will probably have to kill it and set the driver manually in the mplayer.conf file.

Hope this helps,
Adam

---

### Post by Liakoni on 2005-07-18
The 'set zoom=yes' did't help, but the 'mplayer -vo xv' helped.
Thanks for your help!!!

---

