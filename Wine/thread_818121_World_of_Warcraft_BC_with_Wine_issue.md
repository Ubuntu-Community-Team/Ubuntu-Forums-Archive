---
title: "World of Warcraft BC with Wine issue"
date: 2008-06-04
forum: Wine
---

### Post by Mollsmolyneux on 2008-06-04
I am using Linux Ubuntu 8.04(Ha rdy Heron), I have installed WoW with wine and when I launch it using the following command in the terminal from my WoW directory: wine Launcher.exe -opengl and press play, it play through the opening video for BC and then stop on a Black Screen playing the WoW music for the log in screen. The screen flickers with the icons in my top bar every few seconds and I cannot see anything although I can still do things like entering my username as I can her the noises when I press enter.

My computer can run WoW as it has done before. Can anyone help me with this issue?

---

### Post by Mauler5858 on 2008-06-04
The following guide is very well done.  I had no problems following it, and i now have flawless performance.

[http://www.wowwiki.com/Linux/Wine]("http://www.wowwiki.com/Linux/Wine")

---

### Post by Mollsmolyneux on 2008-06-04
> **Mauler5858 said:**
> The following guide is very well done.  I had no problems following it, and i now have flawless performance.

[http://www.wowwiki.com/Linux/Wine]("http://www.wowwiki.com/Linux/Wine")

This is the guide I used :P, I had no problems following it either, but this problem occurred. I also looked at the troubleshooting and couldn't find anything similar to the issue I'm having.

---

### Post by Mauler5858 on 2008-06-04
> **Mollsmolyneux said:**
> I am using Linux Ubuntu 8.04(Ha rdy Heron), I have installed WoW with wine and when I launch it using the following command in the terminal from my WoW directory: wine Launcher.exe -opengl and press play, it play through the opening video for BC and then stop on a Black Screen playing the WoW music for the log in screen. The screen flickers with the icons in my top bar every few seconds and I cannot see anything although I can still do things like entering my username as I can her the noises when I press enter.

My computer can run WoW as it has done before. Can anyone help me with this issue?

Try using it without the -opengl switch, and execute it directly from the wow.exe.

---

### Post by Mollsmolyneux on 2008-06-04
> **Mauler5858 said:**
> Try using it without the -opengl switch, and execute it directly from the wow.exe.

Just tried that, the game launches and then quits, so does work as well as the -opengl switch.

---

### Post by Mauler5858 on 2008-06-04
Try removing the opengl arguement from the config.wtf file and try to run it in direct3d.  it sometimes works better for some cases.

---

