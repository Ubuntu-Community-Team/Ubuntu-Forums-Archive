---
title: "Can OpenGL 3.2 run DirectX11 games like Overwatch?"
date: 2017-06-15
forum: Wine
---

### Post by Zeikcied on 2017-06-15
I know this is more suited for the Wine forum, but I need more of a gamer opinion on this.

I'm trying to run Overwatch in Wine.  I installed it using a program called Lutris, which pulls from the "wine-overwatch" repository.  It uses wine-staging, plus some extra patches to help run Overwatch.  Many have reported success running it.  I have not.

Now, Overwatch will run on Windows on the same exact machine.  My GPU is a Geforce GT 240, which is below the minimum specs, but Overwatch runs at a good 60FPS, albeit somewhat ugly.  But hey, looks aren't everything.  I just don't like having to reboot every time to play the game, so I tried to get it running in Linux.

In Linux, using the wine-overwatch code, it loads to the title screen, and that's about it.  The stage background doesn't load, the character models don't have any textures or hair, and the game will freeze completely when trying to load the practice range.

Which leads to the question I have in the subject line.  Can OpenGL 3.2 run DirectX 11 games?  I know the GPU itself can run Overwatch, but something isn't right when trying to translate the DirectX 11 code to OpenGL 3.2.  I just don't know if it's an issue with wine-overwatch code or an OpenGL vs DirectX issue.

---

### Post by howefield on 2017-06-15
Thread moved to the "*Wine*" forum.

---

### Post by sccman on 2017-07-08
Not sure if OpenGL can run DirectX directly, but I know Wine translates DirectX system calls to OpenGL/Linux system calls so you can run your Windows games on Linux. I don't think Wine supports DirectX11 when you install it, but you can install DirectX11 on Wine through Winetricks.

---

