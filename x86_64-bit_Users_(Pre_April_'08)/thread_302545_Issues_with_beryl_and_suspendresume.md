---
title: "Issues with beryl and suspend/resume"
date: 2006-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by fenomenoxp on 2006-11-18
Hi everyone! I've got a quite specific question:
I got Beryl/AIGLX to work under edgy/amd64, with the latest Nvidia driver. Everything works just fine, except when I suspend. On resume, all I get is the mouse cursor, but nothing else. I even can't switch to a console to kill X. On the other hand, I've got suspend/resume to work flawlessly with metacity, so I know it is a problem of Beryl. Anyway, anyone knows a workaround for this?
By the way, have you tried the metacity compositor? I enabled the option in Gconf-Editor, but I find no differences. 
Thanks in advance

---

### Post by janbockaert on 2006-11-18
same problem here. the problem is the (still beta?) Nvidia-driver i guess

---

### Post by Azakus on 2006-11-19
That might be an AIGLX problem. I run an XGL/Beryl setup with the Nvidia drivers and it doesn't do that for me.

---

### Post by PRGUY85 on 2006-11-20
I have the same problem using AIGLX, beryl and nvidia drivers on edgy.

---

### Post by fenomenoxp on 2006-11-20
Well, I tried XGL, and yes, it seems to work fine with suspend/resume. But it behaves terribly with totem. CPU usage gets up to 60% and everything is very slow and unstable (blinking window decorations, etc)

---

### Post by bmhm on 2006-12-29
[FONT="Verdana"]So will there be a workaround with AIGLX?

Btw: I think AIGLX doesn't support windows-transparency, XGL does - am I right? I am using AIGLX and when I right-klick a window, i don't have a menu entry like "opacity".[/FONT]

---

