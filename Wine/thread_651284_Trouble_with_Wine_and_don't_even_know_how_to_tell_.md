---
title: "Trouble with Wine and don't even know how to tell you what my Wine settings are..."
date: 2007-12-27
forum: Wine
---

### Post by Palu on 2007-12-27
Problem: I type "wine programname" with the program name being the program I'm trying to run. Instantly the system freezes, and I am forced to click the reset button. It's a game that can run on OpenGL OR DirectX and it's simply 2D, needing no hardware accelleration. It probably was written for XP... though I'm not sure because I think I've seen it played on Win98. It uses internet too, btw. :) It's called Tibia, and tibia.com gives a pdf reference on wine that hasn't especially helped me. There are 30+ threads on Tibia, but all those users got further than Wine crashing during / before launch. I don't know how to find/change Wine settings, open wine as a cute little desktop without opening a program yet, or anything else. I can, however, follow simple instructions to help me learn where to find settings in Wine, how to launch the virtual desktop (if that's the correct term), and fiddle with graphic modes, hehe... And they can't be in the form of "then check for waffleconfig and revamp the widget". They need to be, for instance: "$ sudo apt-get wine"... THANK YOU!

System specs: I run gOS. From my reading, I believe that means Gutsy with Enlightenment and x11... Also, I think I have 1.5 BP of RAM though in the bios only 950-some MB seems to be recognized. I'll save that problem for later because it's pretty weird and I'm pretty noobish. :)

Personal tech background: I know nothing about Linux. I've been running it for 7 years, learning (and forgetting) basic terminal commands, reinstalling from scratch when I ruin something that's probably simple to fix, and generally acomplishing nothing... except learning that gOS sounded pretty cool to try. I know terminology in general. I'm a Windows IT person, specializing in C++, Javascript, CSS, PHP etc etc... I can install something from a repository, can't figure out how to compile things, and can sometimes do the installs that are somewhere in between (ie sometimes I download something and it works but sometimes I decide I have no idea what to do with the resulting files.

Wine version: I have Wine installed (I think) from selecting it in my package manager yesterday, so it should be new. I have not figured out how to launch it. I opened a terminal and typed wine. It told me to include a program to launch. I typed "which wine" and all I got was a file path.

---

### Post by markharding557 on 2007-12-27
y

---

### Post by hikaricore on 2007-12-27
> **markharding557 said:**
> you cant' run programs in wine that way
simplest way is type"winefile"in a terminal,this will load wines file manager,you use this to install apps and find executables

Errmmm... I'm going to have to disagree with the "can't' statement.

```
wine *programname.exe*
```

Is very much a way that can be used and is suggested to run programs.
Winefile may be an alternative, but you should misinform new users like this.

The OP had many issues and concerns, I don't believe your post actually even responded to any of them.

---

### Post by Beren Camlost on 2007-12-27
It sounds like you have Wine succesfully installed already, however that it freezes your system sounds very odd. Usually Wine terminates itself pretty fast if stuff is not as it should be.

Anyway, the first thing you should do after installing (or updating) Wine is to run winecfg.

```
$ winecfg
```That will bring up the Wine configuration :) Also, since it will be the first time you run it it will set up the base directories you need and detect devices. If Wine, for some strange reason, still locks up after this then I would suggest uninstalling Wine (preferably with the purge option), and then reinstall it.

```
$ sudo apt-get remove wine --purge
$ sudo apt-get install wine
```
Now you can follow hikaricore's example, given you are currently in the same directory as the .exe file you are trying to run.

cogadh also wrote a nice [Howto: Wine]("http://ubuntuforums.org/showthread.php?t=497332")

---

### Post by markharding557 on 2007-12-28
> **hikaricore said:**
> Errmmm... I'm going to have to disagree with the "can't' statement.

```
wine *programname.exe*
```

Is very much a way that can be used and is suggested to run programs.
Winefile may be an alternative, but you should misinform new users like this.

The OP had many issues and concerns, I don't believe your post actually even responded to any of them.

AS IVE ALREADY SAID I QUIT NIT PICKING person

---

### Post by hikaricore on 2007-12-28
Lol I saw what it said before.  ^_^

But no worries, just simmer down there buddy.  I think we just got off on the wrong foot.

---

