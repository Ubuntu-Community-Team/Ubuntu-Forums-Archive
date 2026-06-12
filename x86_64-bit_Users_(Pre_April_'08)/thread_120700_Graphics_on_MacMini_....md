---
title: "Graphics on MacMini ..."
date: 2006-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by wannabelinuxconvert on 2006-01-23
Hi,

Can anyone tell me how to identify which graphics driver my MacMini is using, and if it's the correct one !?

The reason I ask is it sometimes becomes a bit sluggish and there's also a 'Cannot Allocate Resource' error everytime I boot up, and I know it's to do with my graphics card as it mentions the word 'Radeon' but the screen flashes too quickly for me to catch anymore of the message :mad: 

I have tried things like ```
fglrxinfo
``` in the terminal, but get a ```
bash: fglrxinfo: command not found
```error.

Any help would be greatly appreciated.

Cheers

Mic

---

### Post by dietrying on 2006-01-23
your mac mini uses the ati driver (radeon support included). you can look for it in /etc/X11/xorg.conf. As far as i know, there is no commercial ai driver for linux ppc, wich shouldn't be a big problem, unless you don't need the newest 3d games. For tuxracer it's enough with the ati drivers.

greetings, David

---

