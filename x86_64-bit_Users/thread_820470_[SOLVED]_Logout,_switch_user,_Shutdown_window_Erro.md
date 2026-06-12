---
title: "[SOLVED] Logout, switch user, Shutdown window Error"
date: 2008-06-06
forum: x86 64-bit Users
---

### Post by Plasma_NZ on 2008-06-06
Ok - when i goto the logout/shutdown/restart - nothing happens, it's like its become invisible but still there.. cant click on anything etc... I've tried it with and without compiz running, makes no difference... Any idea's.?

---

### Post by Thelasko on 2008-06-06
Open the system monitor and see if there is anything unusual.

---

### Post by Thelasko on 2008-06-06
you can also go into the terminal and type ```
shutdown now
```
See what that tells you.

---

### Post by Plasma_NZ on 2008-06-06
> **Thelasko said:**
> Open the system monitor and see if there is anything unusual.

That's the thing, nothing out of the normal, and "ps -ax" show's nothing either..

Why im so puzzled.. It just stopped workin after a update..

- Also i've been using 

```
 sudo shutdown -r now
``` to reboot... will write a script for shutdown till i find the fix..

Thanks for your help though :D

---

### Post by Plasma_NZ on 2008-06-09
Bump..

I have enabled "logoff/logon" in ccsm - still wen i it the logoff - nothing appears, and i cant click anywhere.. - am forced to do a ctrl + alt + backspace..

any ideas..?

---

### Post by Plasma_NZ on 2008-06-23
Bump!!

---

### Post by Plasma_NZ on 2008-06-24
Solved... i had disabled power-applet - which is a old bug yet to be fixed when compiz is running...

---

### Post by Thelasko on 2008-06-24
Glad to hear it.  Sorry I couldn't be more help.

---

### Post by Doc Hoss on 2008-12-15
I'm having the same problem.  How did you enable the power-applet?

---

