---
title: "shortcuts do not work , program does...?"
date: 2008-11-25
forum: Wine
---

### Post by westywesty on 2008-11-25
I just installed wine on ubuntu 8.04 and it works fine for several programs.
Except for one, Euroglot, to me a very handy translator E-D-F-G, I downloaded (for free) quite some time ago on Windows, but which isn't free anymore.... This program works (via wine) in Ubuntu when I click on the exe file on the virtual c disk, but the installer didn't place a shortcut to Applications/Wine/Programs (in the past, the program didn't place shortcuts under windows either, I created these myself), but in Ubuntu, I don't know how to do this, or it does not work ... When I create a new item under Edit Menus/new item, and when I use as command-line the path to this exe-file (/home/geert/.wine/drive_c/EUROGLOT/EUROGLOT.EXE), then, when I use the 'link', the program does start, but crashes after a while. (Which it NEVER does when I just click on the exe file on the virtual c-disk...)
On the other hand, I can start the program everytime without crashing via the command terminal, by these 2 sparate command lines:
$ cd /home/geert/.wine/drive_c/EUROGLOT  ,and:
$ ./EUROGLOT.EXE
Can somebody help me to find a way to place a shortcut in Ubuntu, somewhere on the desktop, or near to it, so I can start up this program (via wine) easily:
-without having to go each time to the exe file on the virtual c-disk (Am I typing something wrong in the path to the exe file in the Edit Menu window?),
-or without having to type the 2 command lines in the command-terminal? ( a small executable script based on these command lines or so ?)
Thanks
Westy

---

### Post by cogadh on 2008-11-25
If you want to just create a menu shortcut, you need to specify certain variables and the path for it to work:[LIST=1]
[*]Execute command: env WINEPREFIX="/home/geert/.wine" wine "C:\\EUROGLOT\\EUROGLOT.EXE"
[*]Path: /home/geert/.wine/dosdevices/c:/EUROGLOT
[/LIST]

You could also easily do it with a simple script. Copy this into a plain text editor (not OpenOffice):
```
#!/bin/sh

cd ~/.wine/drive_c/EUROGLOT
wine EUROGLOT.EXE
```
Save the file and name it something like "EUROGLOT_Launcher.sh". Then make the script executable:
```
chmod +x EUROGLOT_Launcher.sh
```
Then create a desktop or menu shortcut to the script using "./EUROGLOT_Launcher.sh" as the command.

---

### Post by westywesty on 2008-11-25
Hello Cogadh,
It works (the executable script) and the programs runs without troubles.
Thanks
Just 1 more question: can I change a menu shortcut icon into any icon of my choice (the logo of the program, eg), I mean can I convert an image of a specific size into an icon (.svg file)? (I know to change the icon via the properties menu)

---

### Post by cogadh on 2008-11-25
I don't really mess with GUI customization stuff like that, but I see no reason you couldn't do that using Gimp.

---

### Post by westywesty on 2008-11-25
Thanks
Westy

---

