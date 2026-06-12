---
title: "sound problems - sounds AWFUL"
date: 2005-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by fidlet on 2005-11-21
I run Ubuntu Breezy on my g3 IBook.  I recently noticed some sound problems - when I play mp3s, and when I play some movies (but not all), the sound is absolutely terrible (sort of like when you turn up cheap speakers too loud).  A few things:

 - I have speakers plugged into my laptop.  I intitially thought they were the problem, but they don't always sound so badly, and when it DOES sound bad, it does so even if I use earphones.
- Using mpg123 has all of a sudden proven more difficult: I have to play files with the command mpg123 -o alsa file.mp3. (I'm not sure what that does - I found it online on a discussion board.)
- I've recently upgraded to Breezy.  I don't know if the problems happened with the upgrade or not.  I've JUST noticed it (and I'm not sure if I've tried playing mp3s and such since the upgrade).
- The problem always occurs when I play mp3's, and only sometime occurs when I play avi's.  I don't know what accounts for the difference.

Any ideas?

---

### Post by ssam on 2005-11-21
if you right click (f12) on the volume control in the gnome panel and choose open volume control then you should get a bunch of sliders. in edit -> preferences, you can select some more sliders.

now have a good play with them all. a couple of them will probably have an effect, and you will need to ballance the gain between both of them.

---

### Post by fidlet on 2005-11-21
That seemed to do the trick!  Thanks!

---

### Post by er-ku on 2005-11-22
[QUOTE=ssam]if you right click (f12) on the volume control in the gnome panel and choose open volume control then you should get a bunch of sliders. in edit -> preferences, you can select some more sliders.

now have a good play with them all. a couple of them will probably have an effect, and you will need to ballance the gain between both of them.[/QUOTE]

I have a similar laptop, and it seems like you should maximize the DRC Range channel, and uncheck the DRC checkbox to get best results. You can hide and forget those controls afterwards.

good luck!

---

