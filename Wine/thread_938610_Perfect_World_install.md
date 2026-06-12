---
title: "Perfect World install"
date: 2008-10-05
forum: Wine
---

### Post by ilikeroflcopters on 2008-10-05
I just downloaded the Perfect World International client, but i dont know what to do next to install it. Trying to open by double clicking does nothing, and when i try to run it on the command line i just get 
```
 Desktop > Perfect_World_International.exe 
bash: ./Perfect_World_International.exe: Value too large for defined data type

``` Does anyone know what to do, or redirect me to where i can see what to do?Im running Ubuntu 8.04 Hardy

---

### Post by Nostrafus on 2008-10-05
Looks like a windows binary... .exe files don't work in linux without wine being installed, if there is no version of this software available in synaptic (Under System-> Administration) try finding a open source version through sourceforge, if there isn't anything there... try using Wine to run it...

```
sudo apt-get install wine
```

---

### Post by ilikeroflcopters on 2008-10-05
Aw crap, sorry. I shouldve elaborated more.
I already have wine installed and working fine, since i was able to get Steam to work on my computer.

---

### Post by StooJ on 2008-10-05
Try
```
wine Perfect_World_International.exe
```

Also, have a look through the appdb on wineHQ, the Perfect World page is here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923)

---

### Post by ilikeroflcopters on 2008-10-05
Ah, that worked like a charm.Thanks StooJ!i also looked on the appdb page for perfect world;it didnt have so much on installing the game as it did on the Directx9 install,but i didnt look around to much. The directx9 install wouldve given me trouble too, but i found a how-to on it.
:D

---

### Post by dbrotzman on 2011-05-20
I am using ubuntu 11.04 (natty) Wine version 1.3.  I am trying to get Perfect World to run on my comp i can get the updater loaded and update but when i click start it darkens like it should and disapears but nothing else happens I am very new to this os so please any help needs to be very specific i know i will have to get to some window to put in some code but i dun know where to pull it up from or what to enter in any and all help is greatly appreciated

[email]Dbrotzman69@gmail.com[/email]

---

### Post by Hex0x75 on 2011-06-15
I too am having this problem. I am running 11.04 natty and have tried copying over the folders/files from a windows computer to mine and have tried downloading and installing. Both give me the same results where the launcher will load but when you click start, nothing happens and then the launcher closes down. I know I had PWI running perfectly on 10.04 and 10.10, but now nothing.
Some more info is that I am running the Ubuntu Classic (thinking it might have been the Unity desktop. I am running a quad core 3.2ghz intel cpu, 4gb ram, and 1gb Nvidia vid card, the same specs from running fine on 10.04 and 10.10. 
I have even done a full wipe of Ubuntu and reinstall thinking there might have been something there. No change in results. I have tried using both Wine 1.3 and 1.2, still same results.
If there is anyone that can help in this area, it is much appreciated. Thank you in advance.

---

### Post by Pirate.king on 2011-07-31
If you are having troubles getting Perfect World to run on Natty (Launcher loads and updates but clicking start does nothing and the launcher shuts down) it is because it now needs VCrun6. If you use the command:

```
winetricks vcrun6
```

It will connect MS update the necessary files and you will then be able to run Perfect World again.

---

