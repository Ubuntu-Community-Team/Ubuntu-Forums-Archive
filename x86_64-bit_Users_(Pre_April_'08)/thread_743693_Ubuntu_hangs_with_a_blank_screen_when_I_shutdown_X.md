---
title: "Ubuntu hangs with a blank screen when I shutdown X Server."
date: 2008-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by JudasReanimated on 2008-04-02
Attempting to install some new Nvidia Drivers, and I discovered that when I,

> sudo init 1

or any similar command.

---

### Post by PmDematagoda on 2008-04-03
Do you mean that you are trying to shutdown the X-Server by switching to a different run-level? If so, then it is unnecessary, all you need is:-
```
sudo /etc/init.d/gdm stop
```
and that will stop the X-Server.

---

### Post by JudasReanimated on 2008-04-03
Well really any command that shuts down the X server leaves me with a blank screen and it never does anything until I have to Ctrl-Alt-Del a few times and it will beep at me, then restart.

I've used ```
sudo /etc/init.d/gdm stop
```

Still the same.

---

### Post by PmDematagoda on 2008-04-03
After you use that command I mentioned, try moving to a tty by pressing Ctrl+Alt+F1(any other number would work) and then see if you can get to a terminal.

---

### Post by JudasReanimated on 2008-04-03
No that doesn´t work either, but I fixed it!!!

Apparently it was the restricted drivers. I disabled the Nvidia restricted driver and then, 
```
sudo /etc/init.d/gdm stop
```

worked fine, and after I updated the drivers to 169.12; Everything is golden.

Thanks for the support though; Glad to have it fixed.

---

