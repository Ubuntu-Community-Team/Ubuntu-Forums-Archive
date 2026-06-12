---
title: "Anyone able to play Fifa 2007 with cedega or wine?"
date: 2006-10-15
forum: Wine
---

### Post by rickympl on 2006-10-15
Hi,
I was just wondering if anyone was able to get fifa 2007 to play using either wine or cedega, and if so, if you coulp post how you got it to work.

Thanks.

Ricardo

---

### Post by plugitin on 2006-11-14
Yes, I am interested if anyone has gotten this game to work? Also, getting a logitech wingman cordless gamepad to work has been a major problem for me.

Thanks

---

### Post by [maxx] on 2006-11-24
i got fifa 07 running BUT....the graphics in the actual game are running far too slow, but this is how i got it going, maybe one of you can get it right:

1.i created an iso file of the original dvd
2.i mounted the iso: sudo mount -o loop -t iso9660 fifa07.iso /media/cdrom0
3.at one point the program freezes on ereg.exe, so kill ereg.exe and the       install will continue. do not install the online options.
4.i copied a cracked fifa.exe to .wine/drive_c/program files/EA sports/fifa 07
5.i typed wineboot and a fifa icon appeared on my desktop.

good luck

---

### Post by hikaricore on 2006-11-24
Remember everyone, if you have any success getting windows games working under wine, be kinda and add your info to: [The Wine App Database]("http://appdb.winehq.org/")

Currently there isn't a page for FIFA 2007, so anyone with the game and enough interest can make one.  :)  This has done wonders for compatibility improvements via the development team as well and fan modifications of wine and it's many libraries (world of warcraft for example has come a long way).

You may also want to try running games in virtual wine desktops (example):

*fifa07.sh*
```

#! /bin/bash
cd /locationoffifa
WINEDEBUG=fixme-all,err-all,warn+cursor,-all wine explorer /desktop=nameofwinedesktop,1024x768 fifa.exe

```

This forces the game to run in a box on your desktop that's 1024x768 and removes almost all of the winedebug spam you would normally see in a terminal (this can improve your framerate slightly depending on your hardware, but it's not the end all solution, it's helpful to me anyway).  This will also (mostly) prevent any chance of the game stealing your mouse and keyboard essentially locking up your system (like worms4 did to me for about a week lol).

Good luck.



--Aaron

---

### Post by [maxx] on 2006-11-25
btw, dont forget to set the drive as cdrom drive in winecfg.

---

### Post by guyvdb on 2006-12-10
i managed to install and run fifa 07 but the game speed is too fast. is anyone else having this problem? there are also minor problems with rendering.
it's basically unplayable

---

### Post by 3zero2 on 2007-01-16
i installed FIFA07 on both wine and cedega.

on cedega it just didn't work but on wine it works quite ok. see comments on winehq database.

---

### Post by herdez on 2007-01-27
how do i kill the ereg.exe?

---

### Post by Louis XVI with a gun on 2007-07-31
Hello

> **guyvdb said:**
> i managed to install and run fifa 07 but the game speed is too fast. is anyone else having this problem? there are also minor problems with rendering.
it's basically unplayable

same problem here

In addition, the game crash in strartup with wine 0.9.41 and 0.9.42 :'(

Edit : I fixed the speed problem using "vista emulation" in winecfg and setting the CPU speed on "performance"
Edit 2 : I use now wine 0.9.40 

hoping it helps ;)

---

### Post by El_Matthews on 2007-08-07
Hello,


I would love to play Fifa 07 on my Linux. Could you post your wine settings because whatever I do it always crashes.

I tried with wine 9.33 or with 9.42 and both completely freezes my PC as soon as the game starts. This happens with the cracked exe. If I don't apply a nocd patch it always complains about the cd.

Please help, I really love that game.

---

### Post by El_Matthews on 2007-08-09
Gents,

Fifa07 is working when I enable the option "emulate virtual desktop". Did somebody made it work in Fullscreen?

Greetings

Matthieu

---

### Post by Louis XVI with a gun on 2007-08-14
yes it works in fullscreen for me, but , I must run the game in a wine virtual desktop because when I quit the game my desktop résolution is changed in 1024x768  whereas my screen resolution is 1440x900 :(

---

### Post by Louis XVI with a gun on 2008-05-17
works out of the box with the latest version of Wine.

Can somebody tell me if fifa 08 works too ?

---

### Post by El_Matthews on 2008-05-19
have a look on the wine app db ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=9476](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9476)). 

I personally play the game with Cedega and that works fine without any problems.

---

