---
title: "&quot;enable Sound server startup&quot; killed user"
date: 2006-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by diablozx9 on 2006-02-21
I turned off "enable Sound server startup" and I can no longer login to my user.
Gives me an error for logging in for less than 10 seconds,,,HELP... other users work BUT this was my "first" user that SUDO works from.

---

### Post by RAOF on 2006-02-21
While it won't really help the initial problem, you can let other users use "sudo" by adding them to the "admin" group: "adduser *username* admin".  Of course, you need root privs to do this, so you'd need to either sudo adduser ... or enter recovery mode.

As to the actual problem, if you log in using "failsafe terminal", you should be able to move your existing KDE configuration out of the way - then you should be able to start KDE again, but you will lose some of your customisation settings.

To do that, try ```
cd ~
mv .kde .kde-backup
```
from the terminal.

---

### Post by diablozx9 on 2006-02-22
Thanks for the help.
However, I am running gnome.

Does something like this still apply ?

---

### Post by diablozx9 on 2006-02-22
I just tried this with ".gnome" file (su command still works in other users).
It had no effect.

Should I have restarted ?

I changed the file back

---

### Post by alan.mckinnon on 2006-02-22
[QUOTE=diablozx9]I turned off "enable Sound server startup" and I can no longer login to my user.
Gives me an error for logging in for less than 10 seconds,,,HELP... other users work BUT this was my "first" user that SUDO works from.[/QUOTE]

That error means that the X server (which displays the GUI and gnome on top of that)is failing to start. The system picks up several retires in short succession and knows that there must be a problem.

You need to find out why X is not starting, and the answer will be in /var/log/Xorg.0.log. Press Ctrl-Alt-F1 to get a non-X terminal, log in as yourself (it will work) and type this command:
sudo less /var/log/Xorg.0.log
pay close attention to lines near the end starting with (!!) AND (WW) at the left margin.

The reason might not be related to the sound server

---

### Post by diablozx9 on 2006-02-22
Thanks for the info,,, I was feeling a little (OK a LOT) stressed over this one.

I will try this tonight.

---

### Post by louis_nichols on 2006-03-27
I experienced thos once on my laptop. the solution for me was to remove a .lock file from home folder. I don't remember the exact name, but I believe it's safe to remove all .lock files from ~ . they are created to protect against more than one instance of certain apps/processes and, in case of a crash or hardware reboot, if they don't get deleted, it can be a reason why some apps won't start.

hope this helps.

---

