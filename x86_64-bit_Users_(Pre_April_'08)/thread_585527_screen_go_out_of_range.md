---
title: "screen go out of range"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by allorder on 2007-10-21
This problem only happen when I run some game: black screen with error: out of range

Benq T705 widescreen

Ive uploaded my xorg.conf if it can help..
 
any ideas ? :confused:

---

### Post by John.Michael.Kane on 2007-10-21
> **allorder said:**
> This problem only happen when I run some game: black screen with error: out of range

Benq T705 widescreen

Ive uploaded my xorg.conf it it can help..
 
any ideas ? :confused:

First thing I see missing from your xorg is the screen resolution.

You could try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and reset your config.

The other option is the thread below.
[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)

---

### Post by allorder on 2007-10-21
thx

---

