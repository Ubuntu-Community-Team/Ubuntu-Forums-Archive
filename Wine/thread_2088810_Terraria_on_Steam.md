---
title: "Terraria on Steam"
date: 2012-11-27
forum: Wine
---

### Post by LilLZ on 2012-11-27
Hello. I have a working steam via playonlinux. I currently just have one game, dungeons of dredmor. It works. I just bought Terraria, and tried to install it. the XNA(?) install went fine. I installed xinput and xact as well as .net40 and the full .net and copied the files from .net into the Terraria folder. Whenever I try to start it, it says something about getthread failed.... any ideas? I'm on Ubuntu 12.10 and using wine 1.5.7 I believe.
I've tried following guides like this: [http://tom-geiger.de/?p=163](http://tom-geiger.de/?p=163)
but it still doesn't work... I posted on the wine forums but no one will ever respond there.

---

### Post by LilLZ on 2012-11-28
I tried running this: echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope
because I read this error is caused by this and now when I run the game, the error doesn't pop up but the game doesn't start either. Oh and also, when doing it without this command, after I get the error I can go into 'System Manager' and see the game running, but of course it doesn't show up.

---

