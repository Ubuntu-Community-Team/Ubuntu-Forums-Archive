---
title: "[SOLVED] WoW Installation woes leading to opengl failure"
date: 2008-06-08
forum: Wine
---

### Post by sendHalp on 2008-06-08
Did a fresh install this morning on my AMD64 X2 machine, with a 7600GT graphics card.  Everything went ok, and when I first logged in, I clicked the little icon that asks if you want to install restricted Nvidia modules.

Then I installed Wine and installed world of warcraft, everything was looking good, and the game was patched and everything.  Now I have big problems.

While trying to run the game, system crashes and I have to reboot.  While logging in I get a message about linux running in low-graphics mode.  I fixed that (i think) by doing a dpkg-reconfigure xserver-zorg with a few other flags, and now I have full screen resolution.

My problem is, I think OpenGL is corrupted or missing.  When trying to load warcraft, i get an error:

err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": /usr/lib32/libGLcore.so.1: undefined symbol: _nv000037gl
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135

I also ran glxinfo | grep rendering, and I get:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I have no idea what to do now.  I installed nvidia-glx via aptitude on the command line, tried nvidia-glx-new, still the same problem.

I *really* dont want to completely wipe this system, or reinstall warcraft because they both took me a lot of time and effort.  Any ideas on what I should do?

---

### Post by sendHalp on 2008-06-08
On another note: tried reinstalling nvidia-settings and linux-restricted modules.

Running the following:

```
sudo nvidia-xconfig
```

Gives errors that the Device section has no driver line.  Also, doing this puts me right back at the low-graphics mode problem i had earlier.  When loading the xwindow system the machine fails to run at 1440x900 mode, then all the other modes until 80x600 or something smaller makes it run.

It's important to note that when I installed from the beginning, direct rendering was enabled on glxinfo.  For some reason wine or WoW crashed opengl or my drivers, or both (?)

---

### Post by thisismalhotra on 2008-06-09
These wiered errors have happened to me b4r. What I would do is uninstall the driver etc etc and installs evrything back using Envy-GTk. That seems to work better for me all the time, plus threads may help(specially the troubleshooting one);

[http://ubuntuforums.org/showthread.php?t=743945&page=2](http://ubuntuforums.org/showthread.php?t=743945&page=2)

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

---

### Post by sendHalp on 2008-06-09
Problem turned out to not be a wine or WoW issue, but a nvidia driver / Xorg issue.

After much wrangling, I got the nvidia drivers to work after purging nvidia-glx-new and a few other packages, along with running the driver package provided by nvidia on their site.

---

