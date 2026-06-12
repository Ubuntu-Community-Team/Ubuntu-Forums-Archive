---
title: "Warcraft 3 help"
date: 2008-01-01
forum: Wine
---

### Post by SLNR on 2008-01-01
I've been running Warcraft 3 in Wine for about 6 months or so, but it's gotten really  slow in the past few days. I keep reading about running it with -opengl, but whenever I do that, it doesn't work.

$ wine Warcraft3.exe -opengl
wine: could not load L"c:\\windows\\system32\\Warcraft3.exe": Module not found

Any idas?

-SLNR

---

### Post by shad0w_walker on 2008-01-01
Are you trying to run the command from the folder warcraft is actually in? Because it looks like wine can't find the file because you are in a different folder.

---

### Post by SLNR on 2008-01-01
I tried it typing the exact location of the .exe, and I get this:

$ /home/slipman/.wine/drive_c/Program Files/Warcraft III/Warcraft III.exe -opengl
bash: /home/slipman/.wine/drive_c/Program: No such file or directory

Or this:

$ wine /home/slipman/.wine/drive_c/Program Files/Warcraft III/Warcraft III.exe -opengl
wine: cannot find '/home/slipman/.wine/drive_c/Program'

Edit: I just got something working. I'll try it out. If you're interested, I copied the location of the launcher I have and did this:

$ env WINEPREFIX="/home/slipman/.wine" wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl

---

