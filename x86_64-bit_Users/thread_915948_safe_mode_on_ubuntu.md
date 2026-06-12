---
title: "safe mode on ubuntu"
date: 2008-09-10
forum: x86 64-bit Users
---

### Post by x_error on 2008-09-10
hey everyone is there a way to safe boot ubuntu like i do on windows to modify the  user's properties because i need to remove a theme that is causing ubuntu to freeze after logging in  and how can i login as administarator to remove the user's current theme

---

### Post by tuxxy on 2008-09-10
Yes certainly, at login select the sessions menu, from here you would select **failsafe GNOME** or if no luck with that **failsafe terminal ** then proceed to log in, the second option will require you to remove the theme from the CLI.

---

### Post by x_error on 2008-09-10
ya i opened the terminal but i dont know the code to change the current theme to another or default theme so please can you give me a code to change the current theme !!

---

### Post by markbuntu on 2008-09-10
An easier way might be this:

At the login screen click on the little icon on the bottom left corner and you will find an option to change session. Change it to Gnome Safe mode. Then login. This will give you the default theme. You can then change your session theme from there.

---

### Post by x_error on 2008-09-11
i tried that way but it is still freezing at the startup !!

---

### Post by bford16 on 2008-09-11
Is this the Window Manager theme (changes look and feel of windows), or Emerald Theme (changes window borders), or GDM Theme (changes login screen) that is giving you fits?  (There are different configuration files or commands to run, depending on which you are using.)

---

### Post by x_error on 2008-09-12
it is gtk 2 theme

---

### Post by jdong on 2008-09-12
Try logging into a failsafe terminal, then

```

mv ~/.gtkrc-2.0 ~/.gtkrc-2.0.broken

```

---

