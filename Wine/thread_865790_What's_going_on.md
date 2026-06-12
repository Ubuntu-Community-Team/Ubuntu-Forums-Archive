---
title: "What's going on?"
date: 2008-07-21
forum: Wine
---

### Post by qe2eqe on 2008-07-21
When I use thunar to load tribes.exe, how can I know what command is being sent to wine?

Did I post this in the right section?

-------non-questions below this line-----

I'm using xubuntu 8.04, and I'm using wine to play Tribes. 
I when I point thunar file manager  at an .exe, it works. When I try from console "wine foo.exe", it doesn't work.

I like my desktop at 1024x768, but I like tribes at 800x600. I'm sure there's a command somewhere to switch X's resolution on the fly, which is something I'd like to include in a tribes startup script (of which step one is starting tribes from a bash script...). Any advice here would be awesome.

---

### Post by aoanla on 2008-07-21
I suspect that Thunar is just picking up the association of Wine as a handler for exe files. Therefore, it is probably just doing

wine file.exe

The difference between when you do it and when Thunar is doing it might depend on the directory you're in - wine likes you to invoke it from the directory the exe file is located it, so you have to cd to that directory in the terminal before invoking it.

xrandr is the command you want to change screen resolution from a terminal.

---

