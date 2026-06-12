---
title: "my gnome doesn't work...?"
date: 2005-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by juhis on 2005-08-01
hi, 

a brand new problem occured while i was refreshing gnome-panel with ctrl+alt+backspace. there where couple of programs running, open office and firefox and i hadn't logged out: now i can't log in anymore. well i can, but the gnome won't start and throws me out to the logging screen. other users are able to use it normally and i can log in in the terminal mode. 

what to do? i suppose the problem lies in configuration files of gnome, but where to find them + i'm afraid of modifying wrong files.

juhis

---

### Post by Tamir on 2005-08-01
[QUOTE=juhis]hi, 

a brand new problem occured while i was refreshing gnome-panel with ctrl+alt+backspace. there where couple of programs running, open office and firefox and i hadn't logged out: now i can't log in anymore. well i can, but the gnome won't start and throws me out to the logging screen. other users are able to use it normally and i can log in in the terminal mode. 

what to do? i suppose the problem lies in configuration files of gnome, but where to find them + i'm afraid of modifying wrong files.

juhis[/QUOTE]
 I  have this too. actually I have too reboot to re-login.

---

### Post by tseliot on 2005-08-01
Have you tried CTRL+ALT+F1. Then login (if the system asks you). Type "startx".

Let me know if this works for you.

---

### Post by DancingSun on 2005-08-01
[QUOTE=Tamir]I  have this too. actually I have too reboot to re-login.[/QUOTE]
That's what I do too.

---

### Post by juhis on 2005-08-02
[QUOTE=tseliot]Have you tried CTRL+ALT+F1. Then login (if the system asks you). Type "startx".

Let me know if this works for you.[/QUOTE]

After doing this, the working user name wouldn't login either (I removed this .x0-lock -file as the program suggested).I had to reboot to re-login with working user name like Tamir. Startx said something like "authority lock timed out in .Xauthority-file".

---

