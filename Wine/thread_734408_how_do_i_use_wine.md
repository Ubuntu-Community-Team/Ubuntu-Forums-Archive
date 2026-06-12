---
title: "how do i use wine?"
date: 2008-03-24
forum: Wine
---

### Post by T2manner on 2008-03-24
all i really know about it is that it can run windows programs?

---

### Post by gsmanners on 2008-03-24
I suppose you should read the FAQ:

[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

---

### Post by Fjatle on 2008-03-24
You can right-click .exe files, and hit "open with wine".... Not sure if this is the smartest way to go...

The way I use it is this:
download a setup file etc, and put it in my home folder.
Then i open my terminal and type sudo wine /home/myuser/filename.exe

Now, if everything work as you hope (wine cannot handle every single windows software out there), you should start the installer. 

After finished installation, you program should be listed in Application-Wine

(wine creates a hidden folder in you home folder, called .wine). There it creates typical windows folders (c: Program files - Windows etc.) 
So if you wonder where wine actually installed it, this is the folder)

---

### Post by T2manner on 2008-03-24
thanks!!
btw
what does the sudo mean?
i've used it alot before, but what does it mean?

---

### Post by Tyke91 on 2008-03-24
sudo gives a normal user elevated rights as described in it's config file. the config file that comes default in ubuntu will give the user total administrative rights for a short amount of time.

---

### Post by gsmanners on 2008-03-24
Please make a special note of this (from the FAQ):

> NEVER run Wine as root!

[http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014](http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014)

---

### Post by Fjatle on 2008-03-26
Yeah, sorry about that sudo thingy.
It slipped my head that wine only touched the home folder...

You may call it a typo :)

---

### Post by Sockerdrickan on 2008-03-26
Seriously running wine with sudo is as stupid as running Windows
What if the windows exe wants to remove everything it can find, and has superuser power? I tell you it's the POWER of the DARK SIDE we have to be careful about.

---

