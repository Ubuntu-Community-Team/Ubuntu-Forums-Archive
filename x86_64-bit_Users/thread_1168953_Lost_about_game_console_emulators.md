---
title: "Lost about game console emulators"
date: 2009-05-24
forum: x86 64-bit Users
---

### Post by bmhm on 2009-05-24
Well, if you take a look at which video game consoles can be emulated, you will find out that most engines will be available for Linux. But most GUIs are not. That's really bad.  It's even worse on x64.

Ever tried to install **znes**? It's only in i386-repos, and the i386-binary will give you 100 % CPU consumption. Finally, I found an amd64-build for intrepid today, which works fine:
[https://launchpad.net/ubuntu/intrepid/amd64/zsnes/1.510-2.1ubuntu1.1](https://launchpad.net/ubuntu/intrepid/amd64/zsnes/1.510-2.1ubuntu1.1)

If you try to start it as it is, consider having a segfault. On the first run, you need to start it from terminal with *-ad sdl* to set the correct sound engine.

snes9x on DOS was GREAT. Even on windows. But on ubuntu amd64 there is just snes9express, which won't allow me to set good options or load movies (.smv) etc. That's too bad, but still better than nothing, of cause. 

---

Well, zsnes is a good emu with a great gui. You can set everything you need. You are even free to set your favorite resolution! GREAT!

Now I tried to find an emulator for Game Boy / Game Boy Color (gb/gbc). I found **gngb** (Gnu GameBoy) and **vba** (VisualBoyAdvanced). But both are somewhat unsatisfactory. On both I didn't figure out how to set a bigger resolution (I got a stamp-sized window) and my gamepad just won't work: The D-Pad is being recognized as "hat" control and cannot be used.

Anyway, vba's GUI is good enough, but still complicated. Videomode: 1, 2, 3. Aha, ok. I know what will hapen. ](*,) It's as self-explanatory as source code written in brainfuck. Sigh.

---

So if anyone cares, what about an emulator like ZSNES for GB/GBA? Is there such a project or anything similar? Can somebody recommend a good alternative? There is some lack of good GUIs. Really looking forward to it. 

If no one has a good suggestion, mind if I open some bugs or so?
Or perhaps some of you (and perhaps me) could team up and try to code one ourselves. What do you think?

Regards

---

