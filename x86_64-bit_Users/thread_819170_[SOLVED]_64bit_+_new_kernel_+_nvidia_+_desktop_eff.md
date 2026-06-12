---
title: "[SOLVED] 64bit + new kernel + nvidia + desktop effects = 3/4 of screen missing"
date: 2008-06-05
forum: x86 64-bit Users
---

### Post by paradoxni on 2008-06-05
After the recent kernel update, when I enable desktop effects, 3/4 of my screen is black and I can only see the upper left 1/4. 

The desktop and windows span into the black area, so no resolution change is occurring and the screen is still displaying 1280x1024. I must turn off desktop effects to regain the other 3/4's of screen real estate.

To help convey the problem, imagine covering the screen with some black card and then cutting out the upper left hand quarter of the card so you can only see whats behind this section, but the rest of the desktop still seems to exist under the rest of it :p

Ubuntu 64bit, latest kernel fully updated.
Nvidia 7900gs, Nvidia drivers installed using the driver manager.

Note. when installing Ubuntu I only get 640x480 as a choice of resolution in the "screen resolution" utility in the preferences menu even after enabling nvidia drivers. I must run DisplayconfigGTK and select my monitor (or Generic 1280x1024) model to achieve the native res of my screen.


Sorry I cannot provide further info as I am not presently at the machine.

---

### Post by Youresorock on 2008-06-05
This happened to me (back when nvidia drivers were working, don't get me started).

To fix it, I went into Advanced Desktop Effects Settings thing, and in General Options, go to Display Settings.  If 640x480 is in the Outputs box get rid of it.  Put in 1280x1024+0+0  or whatever your resolution is.

Anyway, save that and restart X, it should work.  If not fiddle around in there with the detect displays, etc.

---

### Post by paradoxni on 2008-06-05
thanks!! that worked perfectly! :)

---

