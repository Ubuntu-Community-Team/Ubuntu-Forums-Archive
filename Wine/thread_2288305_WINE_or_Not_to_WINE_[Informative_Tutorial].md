---
title: "WINE or Not to WINE? [Informative Tutorial]"
date: 2015-07-26
forum: Wine
---

### Post by Simon_Tomoko on 2015-07-26
You may have an old game or application that you loved running in Windows and now you love Linux and want to run this old program. Maybe you just couldn't pass up the bargain software bins at the local mall? Your first option, that many people think of is running a dual boot OS. This means keeping over 4GB of space just to boot Windows XP. Every time you want to run your program you have to restart the machine. I know, I was there, been there, and done that. 


Another option is to run your old XP through a VM (Virtual Machine). This is quicker than the reboot, but Linux is still running in the background and taking up resources. The VM has issues with 3D drivers and frankly it gets old and tiring having to boot Windows at all.


WINE is not an emulator. It is an overlay. It reroutes keyboard and channels graphic commands through fake dll calls. Think of WINE as a traffic cop. It redirects a command meant for DirectX to either the X server or OpenGL. All the while, WINE convinces the program it is running in a Windows OS. 


To try WINE on your system all you need to do is type; $ sudo apt-get install wine
or you can try a graphic front end; $ sudo apt-get install playonlinux


If you like to tinker about (as I do) you can [download several variations]("https://www.playonlinux.com/wine/binaries/") of the WINE program. Those can be extracted to just about any directory. What I do is download the WINE version I want to use. Then install only the sub folders bin, lib, and share to a hidden sub folder inside my home. There is a simple reason I do this in this manner. As I said, I like to tinker, and while I use 1.7.44 for the most part, this allows me the freedom and ease to change the version build.

For example; If I downloaded the linux-x86 binaries for WINE 1.7.44 I have to extract* it twice. And inside is a folder called 1.7.44 which I move to my home folder and rename .wine-1.7.44 (note the dot) the folder will vanish but it is only hidden from view. Now I am ready to run a game with it. 

I can do this by typing up a simple command script; which is designed to export needed variable information and run this new WINE version.
In any text editor I enter this code:
Code:
```
#!/bin/bash
export WINESERVER="$HOME/.wine-1.7.44/bin/wineserver"
export WINELOADER="$HOME/.wine-1.7.44/bin/wine"
export WINEDEBUG="-all"
export WINEDLLPATH="$HOME/.wine-1.7.44/lib/wine"
export WINEPREFIX="$HOME/.wine-custom"
cd $(dirname "$1")
$WINELOADER "$1"
```

Now I save this as something like "wine-run" and set its properties to executable. 
$ chmod a+x wine-run

Then I place this in my path.
$ sudo mv wine-run /usr/local/bin/wine-run


Now you should be able to run any exe from terminal or creating a desktop shortcut. For example my GTA San Andreas shortcut or terminal command would be;
$ wine-run "/media/drive/Rockstar Games/GTA San Andreas/gta_sa.exe"


There are tons of tweaks that can be done with WINE using winetricks. It again is not a "perfect" solution. It is much better to find the games you like written for Linux. This is why I have a subscription to Steam for Linux and have purchased a few games from them. However many of us can't pass up the bargain software at the local mall and I often find myself with a stack of old Windows games.

*See post three below for details.

---

### Post by leunam12 on 2015-07-27
Thank you, WINE rocks. I'm running Adobe Photoshop CS2, Microsoft Word, TheWord, e-Sword and Dragon NatSpeak 12 under WINE.

---

### Post by Simon_Tomoko on 2015-08-15
Thanks [COLOR=#000000]leunam12, personally I think Ubuntu and Linux rocks, WINE is just handy for working in the stuff that otherwise I would have to leave behind. [/COLOR]

[COLOR=#000000]Thanks again for your interest!

Recently it came to my attention that some may not comprehend what I mean above about "[/COLOR][COLOR=#000000] I have to extract it twice[/COLOR][COLOR=#000000]". So here are the visual aid with notes;

[/COLOR][[img]http://s5.postimg.org/x9vs1vjxv/snapshot1.jpg[/img]](http://postimg.org/image/x9vs1vjxv/)

1. Yes, these are compiled binaries of WINE from the Play on Linux webpage. If you are afraid of these, then download or compile them from a repository you trust. My Linux is 32 bit so I am going with Linux-x86 folder, only download from the others if you are certain they match your OS.

[[img]http://s5.postimg.org/ndup28e5v/snapshot2.jpg[/img]](http://postimg.org/image/ndup28e5v/)

2. I did a page search and found 11 versions of 1.7.44, why so many? Well if you look, some versions are application specific. Such as a few lines up I see "Guild Wars 2" and below my selection, is "Planet Side 2". These don't contain the application, they just have been compiled to run those applications better.
 
[[img]http://s5.postimg.org/xt5gow0qb/snapshot3.jpg[/img]](http://postimg.org/image/xt5gow0qb/)

3. Now go to where you downloaded, if your system doesn't see this as an archived file just rename it with a .bz2 or .tar extension.

[[img]http://s5.postimg.org/v7zw1dbcj/snapshot4.jpg[/img]](http://postimg.org/image/v7zw1dbcj/)

4. Oh look another compression file! Extract it.

[[img]http://s5.postimg.org/638vnybw3/snapshot5.jpg[/img]](http://postimg.org/image/638vnybw3/)

5. Inside the next file you find the WINE. I am not interest in installing the POL GUI, so I only extract these WINE folders.

[[img]http://s5.postimg.org/h440sz44z/snapshot6.jpg[/img]](http://postimg.org/image/h440sz44z/)

6. At this point you can delete the 2 compression files. Unless you lack company or need them to hold down the HDD as a paperweight. 

[[img]http://s5.postimg.org/m5beucblf/snapshot7.jpg[/img]](http://postimg.org/image/m5beucblf/)

7. Finally, I used dolphin to move this folder out to my home and rename it; .wine-1.7.44

The script I wrote above handles the rest. As long as you tell your OS, where to find the libraries, server, and binaries, nothing else on your system need be removed or added.

---

