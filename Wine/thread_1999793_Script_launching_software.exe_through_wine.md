---
title: "Script launching software.exe through wine"
date: 2012-06-08
forum: Wine
---

### Post by Dinero on 2012-06-08
Every time I launch diablo 3 I have to type a command in a terminal before launching diablo 3.

I wrote a script to remember the command for me, so all I have to do is run the script. I would like to know how to make diablo 3 launch before the script terminates and closes the terminal.

Basically I would like to set up the script, saved on the desktop, to become the new desktop icon for launching d3, rather than running the script, then launching diablo 3.

Just to be clear, diablo 3 is run through wine, for people who may be unfamiliar with diablo 3

---

### Post by hwttdz on 2012-06-08
I'd look at the launcher for diablo, it should contain a command like, "wine /path/to/diablo.exe" so in your script (bash?), just add that command before the end of the script.

bash: wine /path/to/diablo
perl: system("wine /path/to/diablo");
... it might be something else, but these seem the most likely to me.

---

### Post by Dinero on 2012-06-08
Thanks for the input. I am trying that now but getting bad format error. I will try to get it working with some wine/playonlinux research and get the format correct.

Currently, the line in my bash script is as follows
```
wine /user/defaultlocation/playonlinux/playonlinux --run "Diablo III"
```With the exception of adding the keyword 'wine', this is basically a copy paste from the 'Command' line, in the 'Basic' tab of the desktop icon for diablo 3.

Thank you for a push in the right direction, and I will post again if I fail or succeed in making it run.

---

### Post by oldos2er on 2012-06-08
Moved to Wine.

---

### Post by Dinero on 2012-06-08
Ok I changed the bash script line to:
```
 playonlinux --run "Diablo III"
```and diablo 3 launches as expected.  It turns out the format error was my mistake in thinking wine started playonlinux, now it seems playonlinux launches wine.  However the background operates, the script is doing its job in saving me effort. Thank you very much for your assistance.

---

### Post by Dinero on 2012-06-08
@oldos2er  I understand your assumption in moving this thread, but as this was a general question about a bash script, which just happens to include wine, it is still a bash script question and not a wine specific question.

---

