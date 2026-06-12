---
title: "Wine"
date: 2007-05-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2007-05-20
Ok well I installed wine, now I've got steaminstall.exe on my desktop and I opened up a terminal and I type

dagger@dagger-desktop:~$ wine Steaminstall.exe
wine: could not load L"c:\\windows\\system32\\Steaminstall.exe": Module not found

so I don't know whats going on.  did I stype something in wrong?

---

### Post by Kilz on 2007-05-20
> **DaGGer said:**
> Ok well I installed wine, now I've got steaminstall.exe on my desktop and I opened up a terminal and I type

dagger@dagger-desktop:~$ wine Steaminstall.exe
wine: could not load L"c:\\windows\\system32\\Steaminstall.exe": Module not found

so I don't know whats going on.  did I stype something in wrong?

You could right click on the exe. Select open with other Application. The list of applications will come up. Click "Use a custom command" at the bottom. Type in wine in the space that opens. Click ok.

---

### Post by King_Critter on 2007-05-20
It looks like Wine is searching for the .exe file in the system32 folder. So just stick the installer in the system32 folder and try again.

---

### Post by Enverex on 2007-05-20
> **King_Critter said:**
> It looks like Wine is searching for the .exe file in the system32 folder. So just stick the installer in the system32 folder and try again.

Don't do this... ever.

> **Kilz said:**
> You could right click on the exe. Select open with other Application. The list of applications will come up. Click "Use a custom command" at the bottom. Type in wine in the space that opens. Click ok.

This may work in this case (it normally works for single exe files that don't rely on any other files) but it shouldn't be used for running things normally.

> **DaGGer said:**
> Ok well I installed wine, now I've got steaminstall.exe on my desktop and I opened up a terminal and I type

dagger@dagger-desktop:~$ wine Steaminstall.exe
wine: could not load L"c:\\windows\\system32\\Steaminstall.exe": Module not found

so I don't know whats going on.  did I stype something in wrong?

This is quite simple. The file isn't there. Either you're typing it wrong or it's not where you think it is. That is exactly what this error message means. Double check that the file is there, if it still doesn't work then triple check. Are you sure it's not an MSI file? That's what the new Steam installers are.

---

### Post by DaGGer on 2007-05-20
Ok well right clicking and then using custom command worked fo rme.  Now I have the file on my desktop and the terminal said i was on the desktop.  The file I have is an .EXE because i noticed that the steam file I did download was an .MSI file and it didn't work in the terminal and even when I changed the extension to .EXE it still didn't work.  Its hard to look through all the stuff that I've searched for but thats how I got wine installed on my 64 bit ubuntu and everything so I just needed a little help.  Thanks for the help.  If I run into any other problems I'll ask, but thanks for the quick responce.

---

### Post by Enverex on 2007-05-20
> **DaGGer said:**
> Ok well right clicking and then using custom command worked fo rme.  Now I have the file on my desktop and the terminal said i was on the desktop.  The file I have is an .EXE because i noticed that the steam file I did download was an .MSI file and it didn't work in the terminal and even when I changed the extension to .EXE it still didn't work.  Its hard to look through all the stuff that I've searched for but thats how I got wine installed on my 64 bit ubuntu and everything so I just needed a little help.  Thanks for the help.  If I run into any other problems I'll ask, but thanks for the quick responce.

Well of course it's not gonna work if you rename it. That's like saying if I rename a .jpg to .avi will it turn my picture into a movie?

Rename it to MSI (back to how it was initially) and follow the FAQ guide link in my Sig and go to the section on how to use/install MSI files.

---

### Post by DaGGer on 2007-05-20
well it worked, anyways but right now I can't fine the file where I'm suppose to install the font into. I renamed the files because I was able to do that to another files (I forget what, but it worked).

---

### Post by Cappy on 2007-05-20
> **DaGGer said:**
> Ok well I installed wine, now I've got steaminstall.exe on my desktop and I opened up a terminal and I type

dagger@dagger-desktop:~$ wine Steaminstall.exe
wine: could not load L"c:\\windows\\system32\\Steaminstall.exe": Module not found

so I don't know whats going on.  did I stype something in wrong?

he needed to "cd Desktop" first.
**dagger@dagger-desktop:~$** wine Steaminstall.exe
Notice the "-desktop" is just the name of the computer.

---

### Post by DaGGer on 2007-05-20
ah ok, you know thats what it was.  Thanks.  But right now I really need someone to show me where to put the font.  I don't for the life of me know where it is suppose to go.

---

### Post by Enverex on 2007-05-21
> **DaGGer said:**
> ah ok, you know thats what it was.  Thanks.  But right now I really need someone to show me where to put the font.  I don't for the life of me know where it is suppose to go.

It says in the FAQ... er, unless I forgot to transfer that bit to it... anyway, fonts go in ~/.wine/drive_c/windows/fonts

---

### Post by DaGGer on 2007-05-21
ummmm, yea still can't find it.  Did I do something different or wrong?

EDIT: ok well I found the folder.  I couldn't find it exactly like you where saying it but I did find the folder.

---

### Post by DaGGer on 2007-05-23
well I've been playing for a few days.  Everything works fine but you know how there is suppose to be a .wine folder in my home folder.  Is there something that I have to do in order to be able to see the folder or what because its not there?

---

### Post by Enverex on 2007-05-23
. means hidden, enable hidden folders.

---

### Post by SnoopDeVille on 2007-05-23
> **DaGGer said:**
> well I've been playing for a few days.  Everything works fine but you know how there is suppose to be a .wine folder in my home folder.  Is there something that I have to do in order to be able to see the folder or what because its not there?

The files as mentioned above are hidden, u can simply go into your home/dagger folder and press 

CTRL+H which is a shortcut for view hidden files, also at star u simply got the message because u werent in the Desktop folder .... ie command = cd ~/Desktop    and then wine Steaminstaller.exe....
but that doesnt matter anymore does it '? :>

---

### Post by DaGGer on 2007-05-23
ok thank you, I figured they were hidden but I didn't know how to get them unhidden.  I thought maybe there would be something in the properties but there wasn't.  Thanks for all your help everyone.

---

### Post by DUNC4N on 2007-05-23
So how's it playing for you?


We have similar specs, but I haven't got it installed due to the beryl mishap that I had.:(

---

### Post by stchman on 2007-05-23
> **DaGGer said:**
> Ok well I installed wine, now I've got steaminstall.exe on my desktop and I opened up a terminal and I type

dagger@dagger-desktop:~$ wine Steaminstall.exe
wine: could not load L"c:\\windows\\system32\\Steaminstall.exe": Module not found

so I don't know whats going on.  did I stype something in wrong?

try

wine ./steaminstall.exe

Remember Linux is case sensitive and the ./ means you are wanting the file in the path that pwd points to.

---

### Post by Enverex on 2007-05-23
> **stchman said:**
> try

wine ./steaminstall.exe

Remember Linux is case sensitive and the ./ means you are wanting the file in the path that pwd points to.

Please read the rest of the thread. It wasn't working because it's actually an MSI file that he had renamed. ./ isn't needed on Wine.

---

### Post by stchman on 2007-05-24
> **Enverex said:**
> Please read the rest of the thread. It wasn't working because it's actually an MSI file that he had renamed. ./ isn't needed on Wine.

I did read the thread, it was initially a .EXE file and the person renamed it to a .MSI file.

The user initially tried wine with the .EXE file and it did not work. (post #1)

The user then appeared to rename the file with a .MSI extension and then again tried to run wine (post #5)

It is good practice to include the path with arguments.  Since nearly every other app I use needs the path in an argument I have developed the habit.

I have never tried wine without including the path in the argument.

---

### Post by Enverex on 2007-05-24
> **stchman said:**
> I did read the thread, it was initially a .EXE file and the person renamed it to a .MSI file.

The user initially tried wine with the .EXE file and it did not work. (post #1)t.

No, they DIDN'T initially try with an EXE file. The EXE file he was referring to in the first post was the MSI file he downloaded and renamed to .EXE.

> i noticed that the steam file I did download was an .MSI file and it didn't work in the terminal and even when I changed the extension to .EXE it still didn't work.

> **stchman said:**
> It is good practice to include the path with arguments.  Since nearly every other app I use needs the path in an argument I have developed the habit.

I have never tried wine without including the path in the argument.

For Linux apps, sure. Don't do it for Wine.

---

### Post by DaGGer on 2007-05-24
Well after messing around with the computer for a while (which I love to just screw around and search through everything) I've got things working pretty well.  Only problem is that when I run CS or CS:S the screen isn't as big as my monitor. If I change the resolution inside of CS to the same as the resolution of my monitor then it works fine.

As for the game play its fine, my sound lags a little but I don't think there is anything I can do about that. I have UT2K4 and that works flawlessly now. i love it.

---

### Post by DUNC4N on 2007-05-25
Put the resolution you want in launch options of CSS.  games>right click on game>properties>launch options

Put 
```
-w 1280 -h 1024 -dxlevel 81 -refresh 75
```

For resolution, direct x level, and refresh rate, respectively.

---

### Post by Cappy on 2007-05-25
> **DaGGer said:**
> Well after messing around with the computer for a while (which I love to just screw around and search through everything) I've got things working pretty well.  Only problem is that when I run CS or CS:S the screen isn't as big as my monitor. If I change the resolution inside of CS to the same as the resolution of my monitor then it works fine.

As for the game play its fine, my sound lags a little but I don't think there is anything I can do about that. I have UT2K4 and that works flawlessly now. i love it.

Try running ut2004 with
```
aoss ut2004
```

I used to have a problem of the ut2004 sound lagging because it was using ARTS and not ALSA. Probably won't help =P

---

### Post by DaGGer on 2007-05-25
well now, I just was messing around with stuff. I got it so that the scren resolution in CS comes up as it should but when I exit the game my regular desktop is now stuck at the same resolution.

---

### Post by Enverex on 2007-05-25
> **DaGGer said:**
> well now, I just was messing around with stuff. I got it so that the scren resolution in CS comes up as it should but when I exit the game my regular desktop is now stuck at the same resolution.

Run "xrandr -s 0".

---

### Post by DaGGer on 2007-05-25
it didn't do anything but bring up more commands for it

---

### Post by Enverex on 2007-05-25
You mistyped it then. Try copy and pasting what I wrote.

---

### Post by DaGGer on 2007-05-25
ok well still nothing. I just put it in and this is what happened

xrandr -s 0"

That was it nothing happened.

---

### Post by Enverex on 2007-05-25
That means that that is your default resolution that you're now at then. Run "xrandr" and it should give you a list. Then run the other command again replacing the 0 with the number from the mode that you want to switch to.

---

### Post by DaGGer on 2007-05-25
ah ok, your right. Well then this isn't working out for me LOL.

---

