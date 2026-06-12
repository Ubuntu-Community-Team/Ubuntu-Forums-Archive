---
title: "delay before quit window appears"
date: 2008-05-11
forum: x86 64-bit Users
---

### Post by platius on 2008-05-11
Fresh 8.04 install, retaining /home with it's data.  When I select System > Quit  there is a one minute delay before the shutdown selection window appears.  I have searched all logs I think might help, but no answers. I think that if I had the command issued by selecting System > Quit to run from a console I might get a clue.  Of course ctrl+alt+backspace gets me right to the login window if I am in a hurry.
     platius

---

### Post by hermes0710 on 2008-05-12
I suggest you create a new user and then log him in and see if this happens again. If not, then something in your old home folder messes things up

---

### Post by platius on 2008-05-12
Thanks,  I had several users on /home, all with same problem.  A new user I just created does not have the delay.  I will add my user files one at a time on my new fresh install and see where the problem may lie.
  Thanks again

---

### Post by prshah on 2008-05-12
> **platius said:**
> Fresh 8.04 install, retaining /home with it's data.  When I select System > Quit  there is a one minute delay before the shutdown selection window appears.  

Probably gnome-power-manager is not running; press alt-f2, then type ```
gnome-power-manager
``` and press enter. There will be no visible feedback. Now try the quit button, it should respond instantly.

If it works, you can add gnome-power-manager to your 
System-Preferences-Sessions, to have it startup automatically everytime.

---

### Post by hermes0710 on 2008-05-12
Glad I helped :)

---

