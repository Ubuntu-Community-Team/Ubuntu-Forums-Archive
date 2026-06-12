---
title: "Need help installing WoW"
date: 2008-05-12
forum: Wine
---

### Post by TrezenChath on 2008-05-12
'm using Ubuntu 7.04 Feisty Fawn and the newest version of WINE for said Ubuntu version.

Ok so I have the files from the CD copied onto a directory on my desktop, but for some reason I cant get the path to work in terminal. If I type in the command

cd </home/jake/Desktop/wowinstall> wine Installer.exe

(jake being my username, and wowinstall being the directory on my desktop that i copied the files from the wow dvd into)

and i get this response "bash: cd: Installer.exe: No such file or directory"


Now if i use the command

cd /</home/jake/Desktop/wowinstall>/ wine Installer.exe

i get "bash: /: Is a directory". I used this command because thats how it was shown on [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft).

Am I doing something wrong here? Am I stupid? Any help would be greatly appreciated.

(i fail english lots)

---

### Post by Ren Höek on 2008-05-12
> **TrezenChath said:**
> 'm using Ubuntu 7.04 Feisty Fawn and the newest version of WINE for said Ubuntu version.

Ok so I have the files from the CD copied onto a directory on my desktop, but for some reason I cant get the path to work in terminal. If I type in the command

cd </home/jake/Desktop/wowinstall> wine Installer.exe

(jake being my username, and wowinstall being the directory on my desktop that i copied the files from the wow dvd into)

and i get this response "bash: cd: Installer.exe: No such file or directory"


Now if i use the command

cd /</home/jake/Desktop/wowinstall>/ wine Installer.exe

i get "bash: /: Is a directory". I used this command because thats how it was shown on [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft).

Am I doing something wrong here? Am I stupid? Any help would be greatly appreciated.

(i fail english lots)

Well the syntax of your commands is a little bit wrong...
...try first to get to the right place
```
$ cd /home/jake/Desktop/wowinstall
```. ($ shows only, that the command has to be typed in terminal...)
Then start the installer
```
$ wine Installer.exe
```. It can be, that the name of the installer is maybe different (case sensetive), so take the right one...

good luck
ren

---

### Post by TrezenChath on 2008-05-12
Alright I tried it your way, and it worked (haha oops..). Thanks for the tip ren. Now I have another problem. When I type in wine Installer.exe into my terminal I will get:

 " No installer data could be found. If this problem persists, please contact Blizzard Technical Support." in a popup after a few seconds of hangtime. 

Then in terminal I get the message:

"fixme:richedit:IRichEditOle_fnGetClientSite stub 0x14d3290
fixme:ole:OleCreateStaticFromData (not shown), stub!"

What'd I miss this time?

---

### Post by pedro_orange on 2008-05-12
You can install from the CD ya' know.
You just need to tell Wine to eject the CD when it asks you to change CDs.

```
wine eject d:
```

Where d: is the drive label for your CD/DVD drive.

Incidentally; which version of wine are you using?

```
winecfg
```

Choose the about tab.

---

### Post by TrezenChath on 2008-05-12
I'm using Wine version 0.9.59. And the reason I did the installation like this is that the help page said to do it like so. I'm new to wine and linux in general, so I didnt know any other way to do it. What command sequences would I need to install from the disc? Also, I only have one WoW   DVD. Don't have to change discs every 10 minutes like old retail versions ftw.

I really appreciate the help guys.

Edit: Alright, so I figured out the command to start from the DVD, but I still got the same error messages as before (no installer data etc). This is becoming super frustrating.

---

### Post by Faud on 2008-05-12
Like the pervious post make sure that you have wine set up correctly by typing in termial ```
winecfg
```
then just install from the dvd OR you can do it improperly and open your dvd folder and right click on the install button and choose open with wine.

---

### Post by Ren Höek on 2008-05-13
> **TrezenChath said:**
> I'm using Wine version 0.9.59. And the reason I did the installation like this is that the help page said to do it like so. I'm new to wine and linux in general, so I didnt know any other way to do it. What command sequences would I need to install from the disc? Also, I only have one WoW   DVD. Don't have to change discs every 10 minutes like old retail versions ftw.

I really appreciate the help guys.

Edit: Alright, so I figured out the command to start from the DVD, but I still got the same error messages as before (no installer data etc). This is becoming super frustrating.

I searched for this error, but actually found no solution...
...have you made some improvement?

If you have a fast internet connection, it would be the easiest way to download the entire game, I guess...

---

### Post by kc5hwb on 2008-05-13
I downloaded the version of the game that I installed on my Ubuntu box.  A friend of mine tried it the same way from purchased CDs and he had problems also.  I don't remember the errors now, but my install from the downloaded version worked much better.

---

