---
title: "Delete all prefixes"
date: 2016-02-13
forum: Wine
---

### Post by edouardvallet on 2016-02-13
Hello,

I want to delete all prefixes that I created but they are re-created every time I launch some applications.
How can I delete them and go back to normal ?
How can I stop wine from re-creating prefixes ?

Thanks,

---

### Post by montag dp on 2016-02-20
Which applications are recreating the wineprefixes when launched? Can you be more specific about what the problem is? Give an example of the application being launched and the wineprefix being created. Otherwise, all we can do is guess about what's happening.

---

### Post by edouardvallet on 2016-02-20
> **montag dp said:**
> Which applications are recreating the wineprefixes when launched? Can you be more specific about what the problem is? Give an example of the application being launched and the wineprefix being created. Otherwise, all we can do is guess about what's happening.

The application I want to use is *Morghs M&B WB-WFAS Editor.exe*, it is a save game editor for the video game *Mount and Blade Warband*.
This application require *MS visual basic 6* in order to work so my intention was to create a separate prefix in which I would install *MS visual basic 6*.
I could install it on the default prefix but I remembered that installing random packages often make all my other applications unstable.

So I typed this command :
```
env WINEPREFIX=~/.mnbeditor WINEARCH=mnbeditor /home/xxx/Downloads/Morghs_MB_WB-WFAS_Editor_v1_40/Morghs M&B WB-WFAS Editor.exe
```

The prefix *mnbeditor* was created and I succesfully installed the required package with *winetricks*.
The application could launch but crashed for an other reason so I decided to delete the prefix *mnbeditor*.

The problem is that every time I launch the application *Morghs M&B WB-WFAS Editor.exe* to do an other test, the prefix *mnbeditor* is re-created.

I would like to understand why and have some advices on how to manage those prefixes. This is new for me and it is hard to find tutorial for beginner.

---

### Post by montag dp on 2016-02-20
The reason the prefix is being created again is because you typed it in the first part of your command: 

```
env WINEPREFIX=~/.mnbeditor ... 
```

When you specify the WINEPREFIX variable and run wine, it will first look for the prefix and create it if it doesn't already exist.  If you don't want that prefix to be created, type something else after WINEPREFIX= in your command.  You can also omit WINEPREFIX=<directory> altogether, in which case the program will be installed in ~/.wine.

Just so you know, "mnbeditor" is not a valid WINEARCH.  WINEARCH should either be win32 or win64, for 32-bit or 64-bit.  For most programs, 32-bit is recommended unless they are 64-bit only.

Hopefully this sheds some light on your situation.

---

### Post by edouardvallet on 2016-02-22
So I learned a bit more about those prefixes and I think that I get it now.

I specify the environment every time that way : 
```
env WINEPREFIX=~/.wine32 WINEARCH=win32
```
followed by the action, for example :
```
env WINEPREFIX=~/.wine32 WINEARCH=win32 wine /home/xxx/Downloads/Folder/Application.exe 
```

I am not sure though if I have to write it the same way every time.

---

### Post by montag dp on 2016-02-22
Well, you only need to specify WINEARCH when the prefix is created, and you don't need to type "env," at least if your shell is BASH.  And also, most applications get installed by Wine in <prefix>/drive_c/Program\ Files/<program directory>/<program>.exe. If you are used to Windows, this should make sense to you, because each Wine prefix is a fake Windows installation with the same system files and directory structure. So, a typical launch command would normally look something like:

```
WINEPREFIX=<prefix> wine <prefix>/drive_c/Program\ Files/<program directory>/<program>.exe
```

where things in <> get replaced by their actual names.  For most programs, Wine will also create a launcher (.desktop file, aka "shortcut" in Windows) which gets installed in ~/.local/share/applications/wine/<program directory>/<program>.desktop.  The launcher should also appear in your applications menu or Dash search, depending on what desktop environment you are using.  That way you don't have to launch it by typing the command from the terminal every time.  Of course, there may be exceptions to this if Wine can't create a launcher for a particular program for whatever reason.

---

### Post by yoshii on 2016-02-22
You may want to be careful of any folders that have spaces in their names (such as "C:\Program Files\")
I think you'd want to use quotes.  I haven't tested this to be sure though.  

```
env WINEPREFIX=~/.wine32 WINEARCH=win32 wine "/home/xxx/Documents/Folder With Spaces In The Name/Application.exe" 
```

That's pretty clever how you specified the bit architecture within each launcher code though.

---

