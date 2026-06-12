---
title: "red phone just errors"
date: 2006-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by shultzjr on 2006-01-05
hi all,

I installed 5.10/x64 on a Sempron 64 system with an external modem hooked to COM1.  In a terminal window I can configure ppp and use pon and poff just fine.  After I add the red phone to the task bar at the top to get it to activate/deactivate and I try to use it, it just gives me an error beep and never dials the modem.  The command line stuff works fine, the gui stuff just doesn't work, how do I make the gui stuff just as reliable as the pon/poff method?

thanks,
charles......

---

### Post by adwait on 2006-01-06
How about installing gnome-ppp, with
```
sudo apt-get install gnome-ppp
```

Alternatively, you could just make custom launchers in the gnome panel, which run "pon" and "poff" respectively.

---

### Post by shultzjr on 2006-01-06
how would I install "custom launchers" in the gnome panel for pon and poff?

real beginner, sorry.

charles......

---

### Post by adwait on 2006-01-06
Right click on the panel. Nw select Add to Panel, and then custom launcher. Check "Run in Terminal" and in the command line enter "gksudo poff" (repeat the procedure to add another icon for "gksudo pon")

---

