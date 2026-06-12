---
title: "nvidia 9500 kills sound and will not recover from screensaver"
date: 2009-10-05
forum: x86 64-bit Users
---

### Post by vbtemp on 2009-10-05
The other day I installed an nvidia 9500 GT graphics card.  Since then my sound has been completely knocked out (Nothing in the forums so far seems to help) and -- more urgently -- the computer does not recover after the screensaver turns on.

I noticed that in recent days it has been taking bizarrely long for the computer to resume from the screensaver (like 30 seconds to 1 minute, and the mouse and keyboard would even lag).  Just a few minutes ago I had to do a hard reboot because it just wouldn't come back altogether!


Has anyone seen similar issues??  Thanks!

---

### Post by grege on 2009-10-05
My guess is that the Nvidia driver has installed an unconnected HDMI sound driver and made it device zero.

Have a look at System Preferences Sound and see if it has switched sound cards. You may be able to just switch back to your preferred device as the default.

OR

Open a terminal and run aplay -l and aplay -L and see what is listed

It could also be that a volume (other than the main one) has been set to zero or muted, which can happen in an update. Use Synaptic to install Gnome Alsamixer as it will give you more control than the normal sound applet.

Just a few ideas to get you started.

---

