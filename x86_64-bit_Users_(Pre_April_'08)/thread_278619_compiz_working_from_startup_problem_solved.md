---
title: "compiz working from startup problem solved"
date: 2006-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2006-10-16
hi can anyone help please.

i managed to get compiz gl desktop working. a litte red dice appears in system tray and you have to tick to enable gl 3d desktop to turn on nice effects.

surely compiz can be started on boot and not have to be turned on each time? otherwise it's pointless having to turn it on as it's not an integrated part of the desktop.

if turned on it should stay on however much you reboot til you turn it off again.

is there anyway to achieve this? thanks.

---

### Post by John.Michael.Kane on 2006-10-16
you have to add the compiz start to your session list. 

System->Preferences->Sessions-Startup

---

### Post by jonah1980 on 2006-10-17
i tried that. it either crashes and says it failed to start or it starts up the little icon in system tray, which you then still have to click on to enable the 3d effects etc...

what am i doing wrong

tried adding compizstart and compiz-start to sessions dialog, but these didn't work either.

---

### Post by John.Michael.Kane on 2006-10-17
What guide did you use?

---

### Post by jonah1980 on 2006-10-17
i did this:

[http://ubuntuforums.org/showthread.php?t=263840](http://ubuntuforums.org/showthread.php?t=263840)

---

### Post by John.Michael.Kane on 2006-10-17
Are you using the 32bit version of dapper or 64bit?

Also that guide is for edgy not dapper.

---

### Post by jonah1980 on 2006-10-17
i'm using both. got 32 on laptop and 64 on workstation. but there is no options to enable 3d effects running from startup...

---

### Post by John.Michael.Kane on 2006-10-17
If your using dapper 32/64bit that was the wrong guide to use to setup xgl.

If your using Edgy 32/64bit then use this guide [http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl)


**Your other option is to post what issues your having in thread that has the guide you used.**

---

### Post by jonah1980 on 2006-10-17
ah i figured it out. it loads on boot if you keep the tray icon enabled. if you disable system tray icon, even though effects still work for that session they don't come back on when rebooted. i'll just have to keep the icon there

---

### Post by ach3ron on 2006-10-30
Hi, could you please tell me how you made the tray icon stay there? It vanishes every time I reboot :-(

Cheers

---

### Post by J-raff on 2006-11-18
after you activate compiz, go into system, prefernces, startup programs.
Type "compiz" Without quotes, save, and you should be good to go

---

