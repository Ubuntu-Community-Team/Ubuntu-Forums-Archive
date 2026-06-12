---
title: "Screen is not compositing"
date: 2009-09-27
forum: x86 64-bit Users
---

### Post by arashiko28 on 2009-09-27
I get an error message about > Screen is not compositing, run compiz (-fusion) or other compositing manager Randomly, I can reproduce the effect when I run compiz on terminal and get this result:

> ~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png


I already tried installing libgl1-mesa-glx and liblgl1-mesa-dri
No good...
Any ideas?

---

### Post by steveneddy on 2009-09-30
I don't think all Intel video chips are able to run in composite mode.

Did you look here first?

Look here - [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

and you may want to run compiz-check from here:

[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

