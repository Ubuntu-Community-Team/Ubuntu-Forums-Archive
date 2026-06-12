---
title: "Truble running Old Old game"
date: 2007-11-30
forum: Wine
---

### Post by WierdKid on 2007-11-30
The game I am trying to run is an Old classic game called menzoberranzan. Its a really great D&D Game.

I'm running Wine version 0.9.49

I've tried running the program with all the different OS's. And I havn't changed any of the other settings.

Everytimes I try to run the game I get this output from the terminal.

```
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.

```

---

### Post by foolsh on 2007-11-30
Is that an old dos game? If so install dosbox it runs stuff like really great.
the dosbox package doesn't come with a default config file. just google  dosbox and find the wiki. Its full of everything you'll need to know

---

### Post by WierdKid on 2007-11-30
Ok. so I got DosBox runing. but when I try to install the game. it says I need an "install.nfo" and a "boot.nfo" to install the game. but i don't have either of those files

---

### Post by hikaricore on 2007-11-30
Files like .nfo files are generally just text, ithe installer is probably trying to read the documentation files so it can show them on screen.  Try making two blank text files of those names and see if the installer works.  ^_^

---

### Post by WierdKid on 2007-11-30
I did that. and I got the installer to run. but when it tried to install the game, it just created a blank directory. And then closed.

---

### Post by hikaricore on 2007-11-30
Then they may not be text files but some kind of data files.  O.o

---

### Post by FranMichaels on 2007-11-30
> **WierdKid said:**
> Ok. so I got DosBox runing. but when I try to install the game. it says I need an "install.nfo" and a "boot.nfo" to install the game. but i don't have either of those files

What were you trying to run before? Was it the installer or game.exe or .bat?

Either way, I suggest grabbing dosbox 0.72
[http://www.getdeb.net/app.php?name=Dosbox](http://www.getdeb.net/app.php?name=Dosbox)

With that, you can just right click whatever .exe, .bat, or .com (whatever!) and choose Open With dosbox. It will handle the mounting for you and everything (if you have a custom .dosboxrc or dosbox.conf, make sure it isn't mounting c)

---

### Post by WierdKid on 2007-12-01
Nah, the problem I think is with the files I have, not with dosbox, I found some old freeware dos games and got them going just fine, I think its the files I have.

---

### Post by foolsh on 2007-12-19
Who needs shareware when theres Abondonware
I love this site [Abandonia]("http://www.abandonia.com/")
It sratches every gaming itch I have exept for [Frets of Fire]("http://fretsonfire.sourceforge.net/")

---

