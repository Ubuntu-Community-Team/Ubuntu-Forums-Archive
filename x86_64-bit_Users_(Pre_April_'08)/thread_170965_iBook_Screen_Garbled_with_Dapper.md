---
title: "iBook Screen Garbled with Dapper"
date: 2006-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by malachakla on 2006-05-05
My iBook Indigo 366 won't get past login on Dapper Drake. The screen is very distorted and I can't see anything... like scrambled.

---

### Post by deathshadow on 2006-05-06
[QUOTE=malachakla]My iBook Indigo 366 won't get past login on Dapper Drake. The screen is very distorted and I can't see anything... like scrambled.[/QUOTE]

switch to a terminal session (control-function key, pick one) login as root, and edit your /etc/xorg.conf file to drop the color depth to 16 bit (It's probably currently set to 24 bit)

I had the same issue on my iBook toilet seat 333 , for some {censored} up reason all the linux installers default to a 24 bit color depth which half the legacy laptops don't support properly.

---

### Post by malachakla on 2006-05-06
Doesn't work... when I press control-function key, nothing happens.
Thanks for the help, though.

---

### Post by malachakla on 2006-05-06
Oops, I got the commands mixed up, and I got to the xorg.conf, and removed everything 24 bit, but for some reason it still won't work. Waah.

---

### Post by donovan1983 on 2006-05-06
deathshadow was referring to the function keys at the top of the keyboard, rather than the fn key. Try pressing something like Ctrl + Alt + F2. You should get a terminal screen. Dapper has root logins disabled (at least the mere couple times I tried) so login like you normally would and then use the command "sudo su" to login as root so you can edit the /etc/X11/xorg.conf file.

Edit: Guess you didn't need the above, I was typing it as you posted. Make sure that the default color depth setting is 16. Did you reboot or kill the X server to test it already?

---

