---
title: "glx in 32bit chroot"
date: 2005-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by valadil on 2005-01-14
I built a 32 bit environment the tutorial at [http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

I also loaded snd_ioctl32 since it seems to help with sound.

Anyway, after a couple reboots the chroot environment stops working.  glxgears segfaults immediately as do other apps using glx.  Considering that the whole point of the chroot is to give me opengl games this is unacceptable.  

apt-get remove glx does in fact help.  Nothing segfaults per se, but I get errors in other games (specifically savage) concerning agpgart.  I've poked around the forums a bit and people seem to insist that agpgart shouldn't be used and that using nvagp 1 is a good thing.  Back in debian agpgart seemed to fix this, but I don't seem to have that module now.  I've experimented with nvagp and sisagp, but nothing seems to make glx in the chroot run consistently well.

Has anyone figured out how to make glx happy inside their chroot?

While I'm at it, how about alsa?  mpg321 will gladly produce sound, but games bitch and moan about not having any sound drivers.

---

### Post by ahyden on 2005-01-16
Do you have the same version of the graphic card driver in your system and your chroot environment?

---

