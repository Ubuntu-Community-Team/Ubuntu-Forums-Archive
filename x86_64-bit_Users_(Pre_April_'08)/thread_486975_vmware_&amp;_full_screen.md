---
title: "vmware &amp; full screen"
date: 2007-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by carniolus on 2007-06-28
When I try to set my guest to full screen mode I get this message:
```
Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.

Failed to switch to full screen SVGA mode.
```

Any ideas what should I do?
Host is amd64 and guest Windows Xp.

---

### Post by jespdj on 2007-06-29
To what screen resolution is Windows XP set?
Is this resolution available in your xorg.conf?

Try changing the screen resolution in XP to something else.

---

### Post by carniolus on 2007-06-29
Windows Xp resolution is set to 1024*768 and my host to 1280*1024.
In my xorg.conf all resolutions are available, so what else could go wrong?

I replaced my graphic card recently, does this have anything with it?
It worked on my older card.

---

### Post by carniolus on 2007-06-30
any ideas?

---

### Post by praxis22 on 2007-06-30
Did you update your xorg.conf when you slotted your new card?
Are you using proprietary drivers?
Can you actually switch to 1024x768 on your host system?

---

### Post by carniolus on 2007-06-30
Actually I've run the reconfiguration of xorg, but then x didn't start at all.
So I just restored my old xorg.conf.
Maybe I'm doing something wrong here.... I'll try again and post the results.

---

### Post by carniolus on 2007-07-02
This doesn't save the problem.
I figured out that this is caused by Xgl.
Any ideas?

---

### Post by CyberAngel on 2007-07-05
Did you bought an "evil" ATI graphics card? :D

As I have read using XGL, has some problems with the applications using OpenGL, but ATI cards does not support the composite extension yet and they cannot run beryl or compiz using AIGLX (which is better).
VMware as I know, it does not use OpenGL for any reason though so this should not be an issue.

Have you tried AIGLX?
It is the default on feisty ;)

---

### Post by carniolus on 2007-07-05
Yes, I tried with AIGLX and it works....
Well I solved this issue by installing vmware player, which works perfectly for me (even with xgl).

---

