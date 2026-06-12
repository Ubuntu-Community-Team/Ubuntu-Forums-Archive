---
title: "[SOLVED] Setting up new Programs Menu entry"
date: 2008-11-03
forum: Wine
---

### Post by sjbaugh on 2008-11-03
I have successfully installed some programs in Wine (Version 1.0.1 on 8.10) using their install programs. These have successfully set up entries in the Wine>Programs menu.

I have just set up a program (in Program Files) that did not come with an install program. It has a number of configuration files in sub directories.

If I use Wine>Browse C:\ Drive I can double click on the .exe file and it runs up and all is well.

I wanted to set up a Programs Menu entry for this program and, seeing how the other programs were set up in the menu, I created a Applications Menu entry with the command entry:

```
env WINEPREFIX="/home/shack/.wine" wine "C:\Program Files\Minos\MinosLogger.exe
```" 

This starts the application but it gives errors that it cannot find its configuration files.

My guess is that it is expecting Windows to have set the default directory to the location of the .exe file.

Have I set the menu entry up correctly? Is there a way to do it so that the program can locate its files?

Thanks,

Steve

---

### Post by david_kt on 2008-11-04
> **sjbaugh said:**
> 

If I use Wine>Browse C:\ Drive I can double click on the .exe file and it runs up and all is well.

I wanted to set up a Programs Menu entry for this program and, seeing how the other programs were set up in the menu, I created a Applications Menu entry with the command entry:

```
env WINEPREFIX="/home/shack/.wine" wine "C:\Program Files\Minos\MinosLogger.exe
```" 

This starts the application but it gives errors that it cannot find its configuration files.

Change your command to (just copy and paste below command):

```
sh -c 'cd ~/.wine/drive_c/Program\ Files/Minos && wine MinosLogger.exe'
```

DK

---

### Post by sjbaugh on 2008-11-04
David,

Thanks. It did, of course, work perfectly. I have also been able to set a launcher "shortcut" using the same command.

Now you have pointed it out I can see what it does!

Thanks again,

Steve

---

