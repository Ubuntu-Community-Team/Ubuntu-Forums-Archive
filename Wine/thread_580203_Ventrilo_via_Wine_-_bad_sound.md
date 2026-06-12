---
title: "Ventrilo via Wine - bad sound?"
date: 2007-10-18
forum: Wine
---

### Post by dakoth on 2007-10-18
I've got Ventrilo working through wine with the guide shown here; [http://ubuntuforums.org/showthread.php?t=41737](http://ubuntuforums.org/showthread.php?t=41737)

However, others hear my voice as if it's stuttering, or chopping up. Just alot of static noise interfering with the signal.

Is there some way to get rid of this? (sound works fine in Teamspeak, but I'd prefer not to force everyone I know to use that).

edit: Played around a bit and the noise went away when I tested at 8khz instead of 44khz. Strange, since winecfg says I'm using 44khz and all. Played around with winecfg some more and eventually lost all sound from mic altogether :P Gonna try a reboot in a bit.

edit2: Made a workaround by downgrading the codec on the server from 44khz to 22khz. Would be nice to have 44khz working though.

---

