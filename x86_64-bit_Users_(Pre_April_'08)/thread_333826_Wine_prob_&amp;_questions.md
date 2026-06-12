---
title: "Wine prob &amp; questions"
date: 2007-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by blu3sman on 2007-01-08
ok i seem to have Wine installed on Edgy 64bit but am having probs running it.
When i run winecfg the config window opens but it/ freezes/locks up ( i click buttons but nothing happens ). any idea why this might be??

And a few questions:
1: when running Wine is it ok to run it while XGL/Beryl is running or should i just run it in Gnome?
2:I want to try and run some Windows games. Must i reinstall these games in Ubuntu or can i run them straight from the HDD's where they are already installed in Windows?

---

### Post by xopher on 2007-01-08
1. If you run beryl with XGL, then you'd have to login to a session without XGL before being able to run OpenGL accelerated games. (3d games) If you run Beryl with the texture from pixmap extension, which the newest nvidia drivers support, you can run 3d-games even with beryl enabled, but Id close Beryl before either way, because it really decreases performance of the games when running.

2. Yes, I believe you do. (Not sure though, so it's always worth a try I guess) Wine installs the games into a directory that will act as a 'windows partition', it will create 'Program Files' etc. depending on what and 'where' you install the games.

Hope this helps, at least to some extent.. :)

---

