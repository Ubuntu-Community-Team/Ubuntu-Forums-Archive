---
title: "Amarok skips tracks"
date: 2006-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by lonrot on 2006-07-10
I used Synaptic to install amarok an d everything related to it, but still I can't make it work, same for Totem-xine. 

I only want to run mp3s. The weird part is that every other music app works flawless.

Here's what I have tried so far:

Installed all totem and xine stuff.
All Gstreamer codecs

except
```
gstreamer0.10-plugins-ugly-multiverse:
 Depends: liblame0 (>=3.96.1-1) but it is not installable
```

Totem does not play any video file too.

---

### Post by RAOF on 2006-07-10
It seems you don't have the Multiverse repository enabled.  gstreamer0.10-plugins-ugly-multiverse is in *Universe* for some reason, but liblame0 is only in Multiverse.

---

### Post by lonrot on 2006-07-11
Thank you but I think that doesn't help me alot.

Can you please tell me what can I do?

---

### Post by bluenova on 2006-07-11
Go to 'Synaptic package manager' in one of the menu options at the top you will find 'Repositories' go in there and enable the multiverse repository (it's disabled by default cause it contains non-free software) then go back to the main synaptic windows and click 'reload' then try to install gstreamer again.

---

