---
title: "cant install wow at ubuntu !!!"
date: 2008-04-17
forum: Wine
---

### Post by m4t30 on 2008-04-17
hello ... i m new user and i hear about wine and cedega... so i was try with both but still cant install wow... i try to use wow from my windows but then i dont see any window... it is all black. So if someone can help me that woud be nice.:confused:

---

### Post by Vadi on 2008-04-17
Give this guide a try: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Faud on 2008-04-17
If its all black make sure that you have your video card set up correctly.

---

### Post by synapse13 on 2008-04-18
I second Vadi's comment above, I found that page's instructions very helpful.  Also, you might try configuring your video driver with Envy.  It helped me to get better performance once I had WoW installed and running (rather slow) under regular Ubuntu vid drivers.  Here's the link:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by m4t30 on 2008-04-21
GUYS THANKS U HELP ME A LOT....i like ubuntu :P

---

### Post by m4t30 on 2008-04-21
there is one more question ... can i get banned for playing on linux? i dont wanna be banned...

---

### Post by Vadi on 2008-04-21
Nope, don't worry. Lots of people play WoW on Linux, and there's nothing illegal in that either.

---

### Post by m4t30 on 2008-04-21
ok , Thanks !!!

---

### Post by Rohen on 2008-04-21
I'm about to install it myself.  It just finished downloading and it's already installing.

---

### Post by ferod on 2008-04-21
made a backup of my wow folder before i deleted my old windows partition, wow in wine using opengl = sharper graphics, higher framerate an generally sexier than on windows. Fixed my mouse buttons so one activates autorun and all set.

anyway yeh no problems at all for me, only thing i changed was the desktop type from 2000 to xp >.<

---

### Post by funguy on 2008-04-21
I play WOW in WINE all the time and this is what I noticed:

In windows,
    300-700ms latency
    20-30fps

In Linux,
    23-30 latency
    60-100fps

Also if you have a ATI card, toss it. It has troubles with the cave and city mini maps. I went with a Nvidia 8600gts SWEET! I just wish all window games played this well.:lolflag:

---

### Post by rickggreen on 2008-04-21
I would echo all the comments so far, latency and FPS, big improvement. About those comments on the net about linux and WOW, more to it than what was reported. I even have a G15 keyboard, supposed to be the other part of the myth, and have been online for about 6 months. No problems. 
I would add one thing though, ver 59 of Wine has a small bug that that prevents the use of the shift key with some other keys, I reverted back to ver 58.

---

### Post by funguy on 2008-04-22
Ya that shift key sure was annoying. I thought I was doing something wrong.. ](*,)

---

### Post by m4t30 on 2008-04-24
btw how i can fix my mouse keys and shift key?

---

### Post by Alkaif on 2008-04-28
hey guys,

finally got my linux installed properly (yay).

so this is what i've done :)

sudo apt-get install update
sudo apt-get install wine

then mounted the iso to /media/iso

then did cd /media/iso and then wine installer.exe

but then it spits out this error:
```

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
wine: could not load L"C:\\windows\\system32\\installer.exe": Module not found
alkaif@takian:/media/iso$ preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

```

is there anyway i can fix this please?

---

### Post by situz on 2008-04-28
yes, check this page:
[http://ubuntuforums.org/showthread.php?t=770262](http://ubuntuforums.org/showthread.php?t=770262)

---

