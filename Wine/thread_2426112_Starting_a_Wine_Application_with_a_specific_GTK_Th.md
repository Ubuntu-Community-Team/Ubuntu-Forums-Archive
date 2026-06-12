---
title: "Starting a Wine Application with a specific GTK Theme"
date: 2019-09-04
forum: Wine
---

### Post by nate-eastman on 2019-09-04
[FONT=arial]I know what you're thinking: we all know how to make an application (like Scrivener) use a specific GTK theme on launch by starting it with:
```
GTK_THEME=Adwaita:light Scrivener %F
```[/FONT]
But how do you do this for an application running in WINE? Obviously, windows themes aren't sensible to GTK variables, but in this case I have a windows application, configured to run in dark mode, that gets a light-mode window decoration. It kills the mood.
Here's what I've figured out doesn't work:

[LIST=1]
[*]Running the full command like so: ```
GTK_THEME=Adwaita:light Playonlinux "Scrivener" %F
``` 
[*]Launching ```
env GTK_THEME=Adwaita:light Playonlinux "Scrivener" %F
``` from the exec line of a .desktop file. 
[*]Creating a shell script that launches the WINE application (so that the terminal command is **GTK_THEME=Adwaita:light Scrivener**) and the "Scrivener" executable is a shell script that's just ```
Playonlinux "Scriverner" %F
``` 
[/LIST]
 In all these cases, Scrivener launches successfully with whichever theme GNOME is using, and not with the theme specified by GTK_THEME. I can get Scrivener to run with a dark titlebar if I switch my entire desktop to Adwaita-dark. Other applications, like Firefox, launch using whichever theme I specify with GTK_THEME, so my working theory is that something in the way the Playonlinux scripts that launch Scrivener are configured keeps GTK_THEME from being passed all the way down to whatever the executable is.

---

### Post by howefield on 2019-09-04
Thread moved to the "*Wine*" forum.

---

