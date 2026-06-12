---
title: "Warcraft 3 TFT"
date: 2008-05-12
forum: Wine
---

### Post by IzThatHawt7 on 2008-05-12
Well, I have finally got Wine to work, and decided to check out how wc3 will run. It successfully launched, however, I got only something around 3fps in the main screen, while in Windows I get about 30 ingame... Any ideas of how can that be solved?
PS I have an Intel 915GM Express Graphics Controller.

---

### Post by Exershio on 2008-05-12
Did you try running the game in opengl mode? That made the game incredibly fast for me (I had like 5fps in DirectX mode [default], and like 100fps in OpenGL mode)

You can run the program with -opengl or you can add the following registry key

Browse to "HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III"

Create new DWORD value called "Gfx OpenGL" with the value set to 1

---

### Post by IzThatHawt7 on 2008-05-12
Well, that is useful, fps increased to something about 15... I guess it's enough playable. (However, maybe can I somehow further increase it?)
And by the way, I get a strange thing every click: gamescreen disappears for a brief moment. Is that normal?

---

