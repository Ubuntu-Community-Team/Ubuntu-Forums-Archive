---
title: "Wine installation failing, cannot reinstall either"
date: 2018-12-31
forum: Wine
---

### Post by dysprosium-1218-x on 2018-12-31
Hi, forgive me my ignorance as I'm completely new to Linux.

I'm trying to install Wine on Xubuntu 18.10. Through the Software Center it worked, but I could not start the program (nothing happend + no icon etc)
Then I tried to install it directly through WineHQ 'packages', but that install failed aswell, giving me errors in the terminal that I have unmet dependencies and "holding broken packages".
Now, I can't even try to install it through Software Center either because now it gives me errors saying I have unmet dependencies.

Did I corrupt my packages/dependencies? How do I repair this and start back from scratch? And if that's solved, how do I get Wine to work?

---

### Post by Timothy Taylor on 2019-01-07
I am having the same problem on MATE 18.04.1:  Software says it is installed, but no sign of it on the menu anywhere.  Clicking "Launch" from the Software window doesn't do anything.  I tried Synaptic = won't install it either.
??

---

### Post by CatKiller on 2019-01-07
You seem to misunderstand what Wine does and how it works. It doesn't *do* anything on its own. It translates other things. No other thing: nothing to translate. Simply launching it would be meaningless, so of course there's no launcher to do that.

If you've installed it properly, Windows executables will get the option to be launched through Wine.

If you want something to click on to help you to manage your Wine prefixes there are tools like Play on Linux or Lutris.

---

### Post by Timothy Taylor on 2019-01-07
Er, no.

I've used Wine before.  There is a definite "Wine" menu entry where I can set up or select Windows apps to run.
Except this time, installed by the new software center..

---

### Post by CatKiller on 2019-01-07
Er, yes.

When you've installed things with Wine you'll get menu entries to launch those things, because that is meaningful.

---

### Post by Timothy Taylor on 2019-01-08
I tried *Play On Linux* which I gather is a new front end for WINE.
I got my apps running with that.

Still no WINE menu entry like I had before..

---

### Post by mastablasta on 2019-01-10
menu entry is not necessary. you launch windows stuff by 
wine application.exe

so you could just create the launcher for app.

also PlayonLinux is not new. though lutris is. i didn't know Lutris can also setup stuff in wine i though it's just a launcher. well look like i have to look into it. 
Otherwise playonlinux is much easier for people like me who can handle a GUI, but don't have time to learn the commands :P

---

### Post by Timothy Taylor on 2019-01-10
> **mastablasta said:**
> Otherwise playonlinux is much easier for people like me who can handle a GUI, but don't have time to learn the commands :P

Me too.
:-)

---

