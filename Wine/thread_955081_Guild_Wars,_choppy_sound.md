---
title: "Guild Wars, choppy sound"
date: 2008-10-21
forum: Wine
---

### Post by c/Kr3t on 2008-10-21
I just installed Guild Wars and the sound is very bad. It's slow and very choppy. I've searched all over for a solution but i couldn't find one.
the flags don't work, (-dsound, -nosound) and aoss doesn't work either.
Any solutions?

---

### Post by Shaythong on 2008-10-21
Everything works fine over here. Maybe try setting your winecfg audio settings to OSS?

---

### Post by c/Kr3t on 2008-10-21
ya, i tried that, it sort of worked. it's less choppy but it's out of sync\

any other thoughts?

---

### Post by Shaythong on 2008-10-21
You could try changing some of the PulseAudio settings around ([http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)) and then set WINE back to ALSA. :)

I use Hardy (with latest updates) and WINE 1.1.6 and Guild Wars worked fine using the normal audio settings.

---

### Post by c/Kr3t on 2008-10-22
nice, that worked only a little bit.  now it's just got this scratchy static sound aswell as the actual audio
anything to fix that?

---

### Post by Shaythong on 2008-10-22
Try setting the Hardware Acceleration setting to Emulation in winecfg with OSS on.

---

