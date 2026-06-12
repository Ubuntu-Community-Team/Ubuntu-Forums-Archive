---
title: "Handling multiple patched wine versions"
date: 2012-05-16
forum: Wine
---

### Post by phYnc on 2012-05-16
I need to be able to run multiple patched version of wine for different programs. I've tried playonlinux but that doesnt support _custom patched_ versions of wine.
 
I know that I could make a shell script similar to
 
```
 
cd ~/Downloads/wine-game1
sudo make install
WINEPREFIX=$HOME/.wine-game1/ wine "C:\Program Files\game1.exe" 

```
 
```
 
cd ~/Downloads/wine-game2
sudo make install
WINEPREFIX=$HOME/.wine-game2/ wine "C:\Program Files\game2.exe" 

```
 
But that wouldnt be ideal because of the time taken reinstall each time and I couldn't run 2 wine programs at once. Is there a way I can just point to the wine folder and the exe without having to re-install every time I switch?

---

### Post by thatguruguy on 2012-05-16
You might want to take a look at [Swine]("http://www.swine-tool.de/").

I don't use it personally, so I can't guarantee it will help. Feel free to report back here your experience with it.

---

### Post by phYnc on 2012-05-16
> **thatguruguy said:**
> You might want to take a look at [Swine]("http://www.swine-tool.de/").

I don't use it personally, so I can't guarantee it will help. Feel free to report back here your experience with it.

I can't even get Swine to run. I've installed it from the repo and it just does nothing.

Terminal
```
adam@phYnc-PC:~$ swine
Loading winetricks entries...
Command failed: None
```

Running from the menu shortcut in Unity also does nothing

edit: Compiled it from source and still does nothing :D

---

### Post by cogadh on 2012-05-16
> **phYnc said:**
> I need to be able to run multiple patched version of wine for different programs. I've tried playonlinux but that doesnt support _custom patched_ versions of wine.
 
I know that I could make a shell script similar to
 
```
 
cd ~/Downloads/wine-game1
sudo make install
WINEPREFIX=$HOME/.wine-game1/ wine "C:\Program Files\game1.exe" 

```
 
```
 
cd ~/Downloads/wine-game2
sudo make install
WINEPREFIX=$HOME/.wine-game2/ wine "C:\Program Files\game2.exe" 

```
 
But that wouldnt be ideal because of the time taken reinstall each time and I couldn't run 2 wine programs at once. Is there a way I can just point to the wine folder and the exe without having to re-install every time I switch?
Don't install your patched Wine in its default location and specify which Wine executable to run by its path. I don't remember the default install path, but let's assume it's /usr/bin/wine, just change that to /usr/bin/wine-patch or something, then when you run that Wine, specify that path. That way you can have multiple patched versions of Wine installed and still run apps simultaneously.

---

