---
title: "i scr**d up my KDE :D"
date: 2009-03-16
forum: x86 64-bit Users
---

### Post by Bellatox on 2009-03-16
hai! i am using kde 64bit 8.10 and i changed sum graphic settings while i was bored and now it blocks in loging in my account after typing password.

i was wondering if there's any way to set default settings in kde from recovery mode?

thanks for your answers ^_^ cheers

---

### Post by HavocXphere on 2009-03-16
> it blocks in loging in my account
Could you be a bit more specific on this part? Does the desktop not load or does it give a wrong password message or what?

---

### Post by Bellatox on 2009-03-16
it accepts password and starts loading KDE and after few seconds it crash and gets me back on login screen

i can normally log into recovery mode but i dont know how to reset all settings to defoult i do think this would help :O

---

### Post by mhgsys on 2009-03-16
Hey,

My thought is that it isn't the code that's not working, it's your last graphic settings.

in recovery mode.

```

sudo dpkg-reconfigure xserver-xorg

```

This will reset the conf file completely , so maybe it would be wise if you make a backup. to do this:

```

sudo nano /etc/X11/xorg.conf

```
and save it like xorgback.conf or something like that.

---

### Post by Bellatox on 2009-03-16
thanks for answers, i solved it blindly in console mode... it wqas black screen on my console login but apparently worked... i type something like ```
ms .kde tkde
``` to reset it and worked... not sure tho was is ms mt m'sumtin'

anyhowz problem solved :) thankz ppls and cya arround!

---

