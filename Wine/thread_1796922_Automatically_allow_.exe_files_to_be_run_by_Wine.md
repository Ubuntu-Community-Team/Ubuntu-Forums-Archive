---
title: "Automatically allow .exe files to be run by Wine"
date: 2011-07-04
forum: Wine
---

### Post by CodeBunny19 on 2011-07-04
I'm new to Ubuntu, and I've been using Wine to run some Windows applications (GraphicsGale, Angelcode Bitmap Font Generator, etc.) but it's a bit annoying to have Ubuntu always tell me that .EXE files are not executable, and a bit nonsensical since, by definition, they are. 

Right now, every time I download an installer .EXE I have to first manually set the executable flag in the file's properties. This is a bit annoying. Is there some way I can set Ubuntu to automatically register .exe files as executables?

---

### Post by diesch on 2011-07-04
On Linux files are executable only if they have the executable bit set. Unlike Windows Linux doesn't care that much about file names or extensions.

---

### Post by CatKiller on 2011-07-04
> **CodeBunny19 said:**
> it's a bit annoying to have Ubuntu always tell me that .EXE files are not executable, and a bit nonsensical since, by definition, they are. 

They really aren't.

What you want to do is to set Wine as the default program to open .exe files (which generally happens automatically when you install Wine). Pick an .exe file, right-click on it and select Properties. Go to the Open With tab and either pick it from the list if it's there or click on the Add button and select "Wine Windows Program Loader" from that list. If it's not in that list either, select "Use a custom command" and put *wine* in the box, or browse to /usr/bin/wine.

---

### Post by Morbius1 on 2011-07-04
> Pick an .exe file, right-click on it and select Properties. Go to the  Open With tab and either pick it from the list if it's there or click on  the Add button and select "Wine Windows Program Loader" from that list
Close.

The default Wine file association has something called cautious-launcher attached to it. That's what's causing the problem with files not being executable. Wine doesn't care is it's executable. Wine only cares if it's an *.exe.

Right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine

In the "Open With" tab mark the "wine"[COLOR=Black] [COLOR=Blue]**you added**[/COLOR] [/COLOR]as   the default ( from the Wine that's already selected) and every time  you run an exe it should select the wine without the cautious  launcher  script.

---

### Post by jwbrase on 2011-07-04
> **CodeBunny19 said:**
> I'm new to Ubuntu, and I've been using Wine to run some Windows applications (GraphicsGale, Angelcode Bitmap Font Generator, etc.) but it's a bit annoying to have Ubuntu always tell me that .EXE files are not executable, and a bit nonsensical since, by definition, they are. 

Right now, every time I download an installer .EXE I have to first manually set the executable flag in the file's properties. This is a bit annoying. Is there some way I can set Ubuntu to automatically register .exe files as executables?

The file type itself is executable (at least on Windows or Wine-equipped Linux), but the executable flag (there are actually three of them, though Nautilus only has one checkbox for "executable" in the permissions tab) controls who has *permission* to use the executable. It's perfectly possible (though not very useful) to have a file that is executable, but which no user on the system has permission to execute. Windows doesn't use Unix file permissions, and Linux doesn't know about Windows file types (Wine is an application, not part of the OS), so when Windows files arrive on a Linux system they may not get the correct permissions set.

> **Morbius1 said:**
> Close.

The default Wine file association has something called cautious-launcher attached to it. That's what's causing the problem with files not being executable. Wine doesn't care is it's executable. Wine only cares if it's an *.exe.

Right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine

In the "Open With" tab mark the "wine"[COLOR=Black] [COLOR=Blue]**you added**[/COLOR] [/COLOR]as   the default ( from the Wine that's already selected) and every time  you run an exe it should select the wine without the cautious  launcher  script.

The one problem with this is that, while these instructions will allow you to run an *.exe without having the executable bit set, I have noticed that, at least for some programs, the executable bit affects the way the program runs (with the program I've observed this with, there is a significant drop in framerate if the executable bit is not set).

I've never encountered the error the OP is running into (my Lucid install is an upgrade from Jaunty, and so the default program to open *.exe files is already a version of the Wine loader that doesn't call cautious-launcher), but it seems it would help avoid the above program behavior / framerate issues, as it would give the user warning that the executable bit isn't set. However, if you're not running into any trouble of that sort, it makes sense to cut cautious-launcher out of the loop.

EDIT: My solution would probably be to rewrite the cautious-execute script to give an option to set the executable bit and run the program.

---

### Post by frtachi on 2013-04-09
My problem was that the "add" option from the method above was unclickable.

So what i did was edit file associations via terminal:
type
```
[FONT=arial][SIZE=2]gedit ~/.local/share/applications/mimeapps.list[/SIZE][/FONT]
```
then find 
*application/x-ms-dos-executable=*
and add *wine.desktop*

---

