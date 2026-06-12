---
title: "MoBo ASUS K8V-MX and screen fluttering issue"
date: 2005-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by chinaski on 2005-12-21
I have just installed Ubuntu AMD64 on a brand new PC with the MoBo in object (and 64bit AMD CPU of course), which has Video and Sound card integrated.

the problem is with the screen, I have non-stop fluttering. i made a search before I open this thread but with no results.

so, any help would be very appreciate :)

---

### Post by Ribs on 2005-12-21
'fluttering'? Could you elobrate on this? Does it happen from power-on, or only when Ubuntu is running?

Have you tried using a lower resoultion (Crtl + Alt + Keypad Minus)? It sounds like your monitor can't cope.

---

### Post by chinaski on 2005-12-21
it happens all the time when Ubuntu is running.

yes, I tried all possible resolutions and edited  xorg.conf according to monitor (philiphs 107E6 CRT) specs but situation won't change :(

---

### Post by Ribs on 2005-12-21
Tried the vesa driver instead of whatever you're currently using?

---

### Post by chinaski on 2005-12-21
I think Vesa drivers are already in use. I did not make any change in that way.

attached's my xorg.conf file, and many thanks for your help :)

---

### Post by Ribs on 2005-12-21
I can't see anything obvious in your xorg.conf file. Can you try a LiveCD like knoppix? Or maybe another monitor?

I'm still not sure what you mean by 'fluttering'...

---

### Post by chinaski on 2005-12-22
first of all thank you Ribs ;)

it seems the problem it's due to defective hardware, as I got same problem with Kubuntu, Ubuntu, and (yes, I know...) WinXP.

just brought the machine back to the shop, tonite will be ready at no cost.

thank you again

---

### Post by FluffyElmo on 2005-12-22
Another thought might be power issues? In an old apartment I had a monitor flutter but connecting it to a UPS solved the issue. But if they can repeat the problem in the shop then that isn't it.

---

### Post by chinaski on 2005-12-22
[QUOTE=FluffyElmo]But if they can repeat the problem in the shop then that isn't it.[/QUOTE]
yes, that's what they did at the shop. but it's a good tip anyway ;)

---

