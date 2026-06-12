---
title: "Cannot install LOTRO on 64-bit"
date: 2011-08-18
forum: Wine
---

### Post by Jaxilian on 2011-08-18
I have tried to follow the wiki on how to install LOTRO through Wine, but I cannot start the installer for the game. Pando says I have an unknown operating system.

I am running Ubuntu 11.04 64-bit

Error:
[B]
err:seh:setup_exception_record stack overflow 100 bytes in thread 0020 eip 7bc72985 esp 00d512cc stack 0xd50000-0xd51000-0xf50000[/B]

---

### Post by thatguruguy on 2011-08-18
You may want to post a question here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=23486](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23486)

---

### Post by donkyhotay on 2011-08-18
You should probably try posting in [the right forum for wine issues](http://ubuntuforums.org/forumdisplay.php?f=313) if you want a relevant answer.

---

### Post by Jaxilian on 2011-08-18
> **thatguruguy said:**
> You may want to post a question here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=23486](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23486)

Says clearly:

Note to all x86_64  (64 bit) Linux users:

Ensure that your system have installed the OpenGL 32bit compatibility drivers, or else LOTRO will not start or work correcty. If you don't know if your system has the 32bit compatibility drivers, ask in your distribution forum or live support chat. (**_Questions about how this is done will be not answered here, due to the wide range of distributions existing_**). 

So no help there then...
I dunno how to get 32-bit on the drivers.

---

### Post by uRock on 2011-08-18
Moved to *Wine*.

---

### Post by wojox on 2011-08-18
Try installing the 32 bit libraries:

```
sudo apt-get update; sudo apt-get install ia32-libs
```

---

### Post by Jaxilian on 2011-08-19
> **wojox said:**
> Try installing the 32 bit libraries:

```
sudo apt-get update; sudo apt-get install ia32-libs
```

Doesn't work

[B]ia32-libs is already the newest version.
ia32-libs set to manually installed.[/B]

This is what it says

---

