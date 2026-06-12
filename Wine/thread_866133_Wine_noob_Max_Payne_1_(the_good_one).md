---
title: "Wine noob: Max Payne 1 (the good one)"
date: 2008-07-21
forum: Wine
---

### Post by itix on 2008-07-21
Hi!

I've just installed wine and in wine I have after some Google-ing and how-to's installed max payne 1 without any problems. I have on various sites that it runs almost flawless in wine, so I thought I'd give my max payne a go.

The installation and startup process went too smooth for me to feel comfortable, and my male intuition was right.

Everything works perfectly except for the game itself. I can reach all menus, change all options etc, but when I choose new game and fugitive (the easiest level), it switches to loading screen and freeze there.

I tried a .deb of wine 1.1.1, but it didn't run at all in 1.1.1. It just terminated without any error code so I downgraded back to the Synaptics version.

Help... It seams to me as it should be able to run.

---

### Post by happyhamster on 2008-07-21
I tried running it under wine 1.1.1, and it works out of the box for me. (Ubuntu Hardy Heron 64 bits, Nvidia driver 173.14.09).

- Which ubuntu version are you running?
- Which video card and driver are you using?

- How do you start the program? From a shortcut or from the wine menu? If so, try running it from a terminal: advantage is that you'll get a lot of feedback about what's going on. The program will be in a hidden folder in your home dir. In my case, it's in:

$HOME/.wine/drive_c/Program Files/Max Payne

- So, open a terminal, and navigate to that folder with the command:

cd "$HOME/.wine/drive_c/Program Files/Max Payne"

- Then run the program:

wine MaxPayne.exe

- Or, to get rid of the less important error messages:

WINEDEBUG=fixme-all wine MaxPayne.exe


- BTW, when the game loads, I have to click a mouse button to proceed. But that's even before the ingame menu shows up. Weird.

---

### Post by itix on 2008-07-21
The Max Payne problems were actually solved last night, right before I went to bed. I'm sorry that I didn't notify the forum.

I switched to this ultra old wine version which actually is meant for gutsy (9.5 or something) and it actually ran.

I was trying (and is still trying) to install Morrowind and accidentially solved the Payne problems.

Sorry once again for the late update.

---

