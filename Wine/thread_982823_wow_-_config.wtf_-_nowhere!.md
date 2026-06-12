---
title: "wow - config.wtf - nowhere!"
date: 2008-11-15
forum: Wine
---

### Post by Servet on 2008-11-15
So I uninstalled wow the 1st version thinking that it would solve a problem with installing burning crusade (which I later found out was because of some hidden files, like the installer.exe)

So after finding out I installed wow, piece of cake, then it asks me to reset the configs because of some configs that I'd made earlier (for example the config.wtf) I accidentally clicked yes, and now I've only the regedit config back (vertex_buffer thing*)

So I tried to find the config.wtf file, which I found out was being made when you log into wow. Starting wow .... commercial / play window comes up, I press play .. Wait ... crash, error, and I know it's because of the config.wtf not being edited with SET gxApi "opengl". 

Directly from [wowwiki.com]("http://www.wowwiki.com/Wine_(software)")

> WoW uses DirectX by default, but for most people it will not perform well in this mode (usually on nVidia hardware). If this is the case for you, then you should change it to run in OpenGL mode instead. To do this you need to find the file wtf/Config.wtf in your WoW directory. By default it is found in /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/, where <username> is you computer login name. If the file does not exist, run the game and log into a character. The game should then create the file. Open it using a text editor, and add the following line to it:

SET gxApi "opengl"

So what do I do, I can't open wow, ergo I can't make the file, ergo I can't EDIT THE FILE 8(

edit: I tried running 
gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/wtf/Config.wtf
Tried to save after putting these lines in SET gxApi "opengl"
> SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
can't save the file as it is not made.

help guys?

---

### Post by hikaricore on 2008-11-15
Config.wtf is created upon the first run of WoW unless the game crashes (in some cases).

You may make this file yourself as it is just a text file.

---

### Post by Servet on 2008-11-15
Tahnk you, it worked perfectly! :)

---

