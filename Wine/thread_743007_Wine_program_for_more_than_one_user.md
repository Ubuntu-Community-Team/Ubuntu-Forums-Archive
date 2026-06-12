---
title: "Wine program for more than one user"
date: 2008-04-02
forum: Wine
---

### Post by tuberculo on 2008-04-02
Is it possible to share a windows program to all the users that use the computer? Or do I need to install the program for each user?

---

### Post by MemoryDump on 2008-04-03
I was wondering about this the other day.. I'm sure it can be somehow.. hopefully somebody with more experience can answer this question :)

---

### Post by FrozenFox on 2008-04-03
Take this with a grain of salt and caution, as I've not tried to do what you're asking and I'm particularly sleepy, but I have an obvious idea that might work.

I think a simple sudo chmod 777 -R on the appropriate wine folder or files would do the trick. Try chmod 777 -R on the program folder of the program you want to share in wine or perhaps the wine folder itself (BACK IT UP FIRST!).

I think Cedega didn't like when I tried to do this once, but I'm not sure if normal wine will behave the same way. If your wine folder is currently small, back up the entire wine folder and try sudo chmod 777 -R /home/YOURNAME/.wine  perhaps. If it messes anything up, just restore the old one. If all of your programs still work fine on your account, try running them from another account and ignore the rest of this message.

If that fails and you want to try to fine-grain share stuff, it might take a little effort, I'm not sure. For instance, to share warcraft 3, it would be something like

sudo chmod 777 -R "/home/YOURNAME/.wine/drive_c/Program Files/Warcraft III"

You may need to also chmod some other stuff (or just clone it to your new user's wine folder), like the 3 registry files in /home/YOURNAME/.wine and perhaps other stuff if it installs dll's or other such things.

---

### Post by johnl on 2008-04-03
Assuming that you set the permissions on all the files correctly, you can use the WINEPREFIX variable to set where you want wine to create all the files.  This will let you create more than one wine environment.

On my machine I have a folder /home/shared that is readable/writable by all users on the machine.  

First, create the wine environment:
```

wineprefixcreate --prefix /home/shared/.wine

```

Then, install your software into this environment:

```

WINEPREFIX=/home/shared/.wine wine InstallSomething.exe

```

Any user with the correct permissions should hopefully now be able to run any program in this wine environment just by setting the 'WINEPREFIX=' variable when running a program with wine.

Hope this helps!

---

### Post by MemoryDump on 2008-04-04
thanks John! 
You'd think this would be done easier. Wine should have an option to install itself for single user or multiple user setups. Still somewhat of a pain since shortcuts have to be created manualy for each use who wishes to use this shared wine setup.. but I guess it'll work ;)

---

### Post by YokoZar on 2008-04-04
> **MemoryDump said:**
> thanks John! 
You'd think this would be done easier. Wine should have an option to install itself for single user or multiple user setups. Still somewhat of a pain since shortcuts have to be created manualy for each use who wishes to use this shared wine setup.. but I guess it'll work ;)
Making this easier has been on my todo list for a while, however there are some difficulties.  Wine itself would need to support building its registry from multiple sources (the system-wide prefix and the user one).

On the other hand, Windows itself isn't particularly friendly to multiuser setups either.

---

### Post by MemoryDump on 2008-04-07
> **YokoZar said:**
> Making this easier has been on my todo list for a while, however there are some difficulties.  Wine itself would need to support building its registry from multiple sources (the system-wide prefix and the user one).

On the other hand, Windows itself isn't particularly friendly to multiuser setups either.

ahhh sweet! It would be nice to see this feature eventually! Keep up the great work ;)

---

