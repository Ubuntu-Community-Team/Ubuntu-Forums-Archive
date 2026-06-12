---
title: "x11 can not start"
date: 2006-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by zxc831 on 2006-06-09
Hi,
After reboot my system, I can not start my computer by graphicu user interface (GUI). Could anybody give some suggestion?
Thx

---

### Post by charlie. on 2006-06-09
Suggestion: Be more specific. "can not start" could be on of an incredible number of things.

---

### Post by zxc831 on 2006-06-09
Thanks, Charlie. The error messege is as-followed:
Failed to start X server(Ggraphics User interface).............

and further to check /var/log/Xorg.0.log and found the following warning messege in the log file:
failed to load /usr/share/x11/fonts/cyrillic
failed to load /usr/share/x11/fonts/CID
failed to load /usr/lib/Xorg/modules/extensions/libGLore.so
.
.
.
No screens found

however, I check all of these files and they are in the right place. 
Cheers!

---

### Post by bonzodog on 2006-06-10
could you be more specific with that output..the font errors are normal., so there is something in between that contains the actual problem. What graphics card do you have?
When X crashes, and it asks if you want to see the error output, hit 'OK'. Then also tell it you want to see the second error log screen. There should be an error along the lines, of 'Problems loading <driver name>'. It all looks *very* technical, but we here can interpret it and tell you what you need to do.

---

### Post by cat on 2006-06-19
The problem could be with the .IceAuthority file in your home. You could remove that file in the console mode and reboot again..(change the rights should do the same thing, never tried that though)

---

