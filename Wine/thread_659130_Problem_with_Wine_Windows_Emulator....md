---
title: "Problem with Wine Windows Emulator..."
date: 2008-01-05
forum: Wine
---

### Post by Vita_Edo on 2008-01-05
I'm trying to run an .exe file by opening it with WWE. The problem is that it goes to a screen that asks what application to use, and of course I select WWE and okay...And nothing happens, the screen just closes and the .exe doesn't open.
The program in question is Burning Sand, and I'm positive that it should run fine, because right on the official website for it there's a picture of it running with Ubuntu and Wine.
 I'm sure there's probably just something I'm missing..

---

### Post by agtownz on 2008-01-05
I didn't find Burning Sand in winehq, but some simple things you can try is to enable a virtual desktop and if that doesn't work, then try changing the OS systems.  Those two usually do the trick for me in most applications that work.

---

### Post by Sam on 2008-01-05
Run the program from a teminal to get any error output:
```
cd /path/to/your/program.exe
wine ./program.exe
```

Then paste the output.

---

### Post by happyhamster on 2008-01-06
Just tried it and it appears to work fine (although I have no idea how this game works :))

Download here:
[http://siebn.de/index.php?page=burningsand/game](http://siebn.de/index.php?page=burningsand/game)

Unzip the downloaded file, open a terminal, navigate to the folder, and type:

wine BurningSand.exe

(I used wine 0.9.52 and Burning Sand 0.99b beta 7)

---

