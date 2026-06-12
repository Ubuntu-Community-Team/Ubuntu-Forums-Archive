---
title: "Steam games"
date: 2008-05-28
forum: Wine
---

### Post by Kayos02 on 2008-05-28
I'm running them under a virtual desktop with pixel shader disabled, and when I start them it works fine (to like the menu and stuff), but when I start the actual game play it crashes.

This is all under xubuntu hardy heron with compiz disabled.

---

### Post by Kayos02 on 2008-05-28
Bump? :/

---

### Post by cogadh on 2008-05-28
Why did you diable the pixel shader? What do you have for video hardware? Have you tried running the games with specific DirectX levels (add "-dxlevel 80", "-dxlevel 90", etc. to the games launch options)? What games are you trying to run?

---

### Post by Kayos02 on 2008-05-28
I disabled the pixel shader from some information after googling, plus the game didn't start up without it disabled.

I have an Nvidia Geforce 5200 overclocked.
The original clocks were 250 for memory and GPU, it is clocked at 320 for memory and 300 for GPU.

I tried launching it with DirectX 8.1, but not 8.0 and other modes, let me try that.

EDIT: I am trying to run Garrys Mod and CS:S

EDIT2: Changing the Dxlevel did not work.

---

### Post by cogadh on 2008-05-28
Run the game from the terminal and post the error output, there is likely some informative message in there that will lead to a cause and possibly a solution.

---

### Post by schtufbox on 2008-05-28
> **Kayos02 said:**
> I disabled the pixel shader from some information after googling, plus the game didn't start up without it disabled.

I have an Nvidia Geforce 5200 overclocked.
The original clocks were 250 for memory and GPU, it is clocked at 320 for memory and 300 for GPU.

I tried launching it with DirectX 8.1, but not 8.0 and other modes, let me try that.

EDIT: I am trying to run Garrys Mod and CS:S

EDIT2: Changing the Dxlevel did not work.

tried -dxlevel 70 ?

---

### Post by Kayos02 on 2008-05-28
Oh! -dxlevel 70 worked! Are there any disadvantages to running it at Dx7.0?

Also: Sorry for not trying 7.0 originally.

---

### Post by cogadh on 2008-05-28
It won't look quite as nice as it would if it could run at the higher DX levels. With a FX 5200, the highest it can actually run is DX 8.1 (the hardware only supports up to that level, DX 9 support is present in the Windows drivers), so you wouldn't be able to get full graphical performance out of it anyway.

---

### Post by strongboww on 2008-05-29
actually he can run it in -opengl too ;)

---

### Post by cogadh on 2008-05-29
That is not a legitimate launch option for Source-based games, which are currently only DirectX. You can set Wine to use OpenGL as the DirectDraw renderer, but the game itself will still use DirectX.

---

### Post by jaithehulk on 2008-05-30
hey guys ... the game CS 1.6 starts normally under wine... but as i press the new game button nothing happens...no new game.no muliplayer..
what todo??

---

### Post by Kayos02 on 2008-05-31
My games are working now but are incredibly unstable, have lots of errors, and crash frequently. I guess I'm gonna dual boot XP.

---

