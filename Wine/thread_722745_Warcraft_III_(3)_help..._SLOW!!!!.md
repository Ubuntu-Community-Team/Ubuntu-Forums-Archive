---
title: "Warcraft III (3) help... SLOW!!!!"
date: 2008-03-12
forum: Wine
---

### Post by DarkZyzx on 2008-03-12
I already tried turning off compiz-fusion and changing speed to fastest not best looking. What do i do to make it not run so slow and choppy... even the sound is all chop chop chop!:confused:

---

### Post by FrozenFox on 2008-03-12
Did you run it with the -opengl flag? You should.

---

### Post by DarkZyzx on 2008-03-12
> **FrozenFox said:**
> Did you run it with the -opengl flag? You should.
I tried, but I don't think I did it right... whats the code for the opengl thing??

---

### Post by Diabolis on 2008-03-12
This issue has been discussed before in many threads. Check if you got direct rendering.

```
glxinfo | grep rendering
```

[http://ubuntuforums.org/showthread.php?t=45407&highlight=warcraft+III](http://ubuntuforums.org/showthread.php?t=45407&highlight=warcraft+III)

[http://ubuntuforums.org/showthread.php?t=502355](http://ubuntuforums.org/showthread.php?t=502355)

---

### Post by DarkZyzx on 2008-03-12
> **Diabolis said:**
> This issue has been discussed before in many threads. Check if you got direct rendering.

```
glxinfo | grep rendering
```

[http://ubuntuforums.org/showthread.php?t=45407&highlight=warcraft+III](http://ubuntuforums.org/showthread.php?t=45407&highlight=warcraft+III)

[http://ubuntuforums.org/showthread.php?t=502355](http://ubuntuforums.org/showthread.php?t=502355)

thanx for the links... I don't have direct rendering.

---

### Post by Diabolis on 2008-03-12
Then you need to install the correct drivers for your video card.

---

### Post by DarkZyzx on 2008-03-12
> **Diabolis said:**
> Then you need to install the correct drivers for your video card.

on my restricted drivers it says it is installed correctly.

---

### Post by DarkZyzx on 2008-03-12
NVM!!! The opengl thing works great!!!! Thanks!!!

---

