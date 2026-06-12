---
title: "new to wine and not understanding it all the way"
date: 2007-12-08
forum: Wine
---

### Post by hotroddude on 2007-12-08
Hi again everybody, I downloaded wine last night and have been reading how to's for downloading games since, but i keep getting errors. I'm using ubuntu feisty fawn the latest wine and am trying to download NoLimits coaster sim.this game is put as an .exe downloaded from the internet i brought the exe from my windows hard drive and placed the exe in my /home/steven/GAMES folder, is that ok? from what i know you can put it anywhere? so then i open it in a terminal window then type wine Installer.exe right after and i get this error


wine: could not load L"c:\\windows\\system32\\Installer.exe": Module not found
steven@ubuntu:~$ wineserver: could not save registry branch to /home/steven/.wine/system.reg : No space left on device
wineserver: could not save registry branch to /home/steven/.wine/userdef.reg : No space left on device
wineserver: could not save registry branch to /home/steven/.wine/user.reg : No space left on device


can someone help me here im not quite sure what im doing wrong and im not sure if im doing anything right :-k  and is there supposed to be a place to open wine like an icon or something, there was one when i installed it from the add/remove thing last night before i found the sticky on how to install the latest version.
thanks in advance,
steven.

---

### Post by atomkarinca on 2007-12-08
To run the .exe file just right-click the file and select "Open with 'Wine Windows Emulator'". But I guess you will come across some problems, [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7056") you can find some workarounds.

---

### Post by hotroddude on 2007-12-08
> **atomkarinca said:**
> To run the .exe file just right-click the file and select "Open with 'Wine Windows Emulator'". But I guess you will come across some problems, [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7056") you can find some workarounds.

when i try doing that i get  a
Could not add application to the application database
pop up i tried  wine

and when i tried wine windows emulator i  get
cannot find wine

i installed everything correclty and it all worked, i didnt get any errors when i installed it.
any ideas?

and thanks for the quick reply!

---

### Post by atomkarinca on 2007-12-08
> **hotroddude said:**
> and when i tried wine windows emulator i  get
cannot find wine

In a terminal type

```
whereis wine
```

If it returns /usr/bin/wine then it means you installed wine correctly and it shouldn't say "cannot find wine". You can also try this: right-click the .exe file, select properties, under open with tab if you can see Wine Windows Emulator select it, if not click on Add, if you can see Wine listed select it, if not click on "Use a custom command", click browse and browse through /usr/bin and select wine.

Does the .exe start now?

---

### Post by cogadh on 2007-12-08
Wine applications should be run from the terminal until you get them completely installed and running properly. That way, any errors that Wine encounters are output to the terminal and can be used for troubleshooting purposes. Once you have your application installed and running properly, then you can use the right-click, double-click or menu shortcut methods to launch the application.

To install an application using Wine, simply open a terminal, change directories to where you placed the installer executable, then run it like this:
```
wine <executable name>.exe
```
If you are running an install from a CD, then all you have to do is open a terminal and run it like this:
```
wine /media/cdrom/<executable name>.exe
```

If you run into problems with the installation, then post the terminal output here, the error messages produced are usually very helpful.

However, the error messages you already got are a little disturbing. It looks like you no longer have any space left in your home directory. You might want to verify that before continuing.

---

### Post by hotroddude on 2007-12-08
> **atomkarinca said:**
> In a terminal type

```
whereis wine
```

If it returns /usr/bin/wine then it means you installed wine correctly and it shouldn't say "cannot find wine". You can also try this: right-click the .exe file, select properties, under open with tab if you can see Wine Windows Emulator select it, if not click on Add, if you can see Wine listed select it, if not click on "Use a custom command", click browse and browse through /usr/bin and select wine.

Does the .exe start now?

ok i did that and it did installed correctly, i think this is what i got.

wine: /usr/bin/wine /usr/lib/wine /usr/X11R6/bin/wine /usr/bin/X11/wine /usr/share/wine /usr/share/man/man1/wine.1.gz


 i followed your instructions, and i got to the usr/bin/wine hit add and i got the 
Could not add application to the application database
error again. :-k

---

### Post by hotroddude on 2007-12-08
> **cogadh said:**
> Wine applications should be run from the terminal until you get them completely installed and running properly. That way, any errors that Wine encounters are output to the terminal and can be used for troubleshooting purposes. Once you have your application installed and running properly, then you can use the right-click, double-click or menu shortcut methods to launch the application.

To install an application using Wine, simply open a terminal, change directories to where you placed the installer executable, then run it like this:
```
wine <executable name>.exe
```
If you are running an install from a CD, then all you have to do is open a terminal and run it like this:
```
wine /media/cdrom/<executable name>.exe
```

If you run into problems with the installation, then post the terminal output here, the error messages produced are usually very helpful.

However, the error messages you already got are a little disturbing. It looks like you no longer have any space left in your home directory. You might want to verify that before continuing.

heres what i typed in

 wine /home/steven/Desktop/desktop folders/GAMES NLSetup16.exe

and heres what came out

wine: cannot find '/home/steven/Desktop/desktop'
steven@ubuntu:~$ wineserver: could not save registry branch to /home/steven/.wine/system.reg : No space left on device
wineserver: could not save registry branch to /home/steven/.wine/userdef.reg : No space left on device
wineserver: could not save registry branch to /home/steven/.wine/user.reg : No space left on device

if its refering to my hard drive memory ive got plenty left.

---

### Post by cogadh on 2007-12-08
Try this:
```
wine /home/steven/Desktop/desktop\ folders/GAMES\ NLSetup16.exe
```
Linux doesn't understand the spaces in file and directory names by default. The "\" escape character avoids that problem.

---

### Post by hotroddude on 2007-12-08
> **cogadh said:**
> Try this:
```
wine /home/steven/Desktop/desktop\ folders/GAMES\ NLSetup16.exe
```
Linux doesn't understand the spaces in file and directory names by default. The "\" escape character avoids that problem.

alright thanks for the help. unfortunatly my system restartd out of nowhere and linux refuses to start its saying "cant find whatever file" this is the third time thats happened. if i can get it running again i'll try it.

---

### Post by hotroddude on 2007-12-08
> **cogadh said:**
> Try this:
```
wine /home/steven/Desktop/desktop\ folders/GAMES\ NLSetup16.exe
```
Linux doesn't understand the spaces in file and directory names by default. The "\" escape character avoids that problem.

ok so i fixed my computer, i did this and heres what my terminal said.
```
steven@steven-desktop:~$ wine /home/steven/Desktop/desktop\ folders/GAMES\ NLSetup16.exe
wine: cannot find '/home/steven/Desktop/desktop folders/GAMES NLSetup16.exe'
```
what a pain lol

---

### Post by cogadh on 2007-12-08
You must have the path or file name wrong. Copy the install executable into your home folder then run it from there. That way, all you have to do is open the terminal and type "wine <executable name>.exe".

---

### Post by hotroddude on 2007-12-08
> **cogadh said:**
> You must have the path or file name wrong. Copy the install executable into your home folder then run it from there. That way, all you have to do is open the terminal and type "wine <executable name>.exe".

got it, thanks a ton for your help!

---

