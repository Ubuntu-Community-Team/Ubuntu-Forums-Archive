---
title: "OE-Cake, anyone got it working?"
date: 2008-04-26
forum: Wine
---

### Post by Muscar on 2008-04-26
[http://www.octaveengine.com/en/casual/trial.html](http://www.octaveengine.com/en/casual/trial.html)

This game is simply awesome and I played with it all the time, but now I have completely switched to Ubuntu, I tried running it under wine but nothing happens, not even an error message and I don't know how to run .exe files in the terminal

So, if anyone have used it in Ubuntu or could help on how to do so, please tell me

---

### Post by happyhamster on 2008-04-26
If you haven't worked with a terminal before, then an easy way of navigating it is installing the package "nautilus-open-terminal" which will allow you to right-click a folder and start a terminal from there.
(Only works when using regular Ubuntu, meaning the one with the nautilus file browser). To install:

sudo apt-get install nautilus-open-terminal

- And to let it take effect, you'll likely have to restart nautilus (close all nautilus windows). If that doesn't help, just issue:

killall nautilus

- When that's done, open your home folder (Places-->Home folder) and press ctrl-h to be able to see hidden files. The wine stuff is in the hidden .wine folder. Navigate to it and keep going until you find  your program's folder, and right-click it to start a terminal session from there. Then run your program like this (insert correct program name instead):

wine program_name.exe


- You'll probably get a lot of feedback which will help troubleshooting. In case you get zillions of fixme messages, try running it like this:

WINEDEBUG=fixme-all wine program_name.exe


- BTW, to take a look around from within a terminal, use:

ls

- and to navigate to a folder:

cd foldername

- or to go down one folder:

cd ..

- For more info see:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Good luck, and keep us informed.

---

### Post by ss2man44 on 2008-10-29
I haven't tried WINE yet, but it works nicely in CrossOver Games.

---

