---
title: "Playonlinux AoE2, install ok, won't play"
date: 2012-07-12
forum: Wine
---

### Post by oiio on 2012-07-12
Hello everybody 

I'm having some issues with a game here.
I'm trying to play Age of Empires II (both "age of kings" and "the conquerers" )

for this I installed Playonlinux 4.0.14
Installing worked just fine, without any complaints.
I used an official cd-version of the game.

Problems occur when I want to start up the game. The problem is the same for both "age of kings" as for "the conquererds"

I open playonlinux menu, I click the play-button and an AoE-loading screen comes up on a "wine desktop" (a windows-looking blue screen :p)
However, after loading for a while i get the message :

*Internal errors-Invalid parameters received*

in the logfile there is this:
```

[POL_Wine]Message:Running wine 1.4-rc1 empires2.exe
-nostartup
wine:cannont find
L"C://windows//system32//winemenubuilder/.exe"
err:wineboot:ProcessRunkeys Error running cmd
L:C"//windows//system32//winemenubuilder.exe-a-r" (2)
WARNING: gnome-keyring::couldn't connect to: 
/tmp/keyring-IdvFfA/pcks11:No such file or directory
wube: Unhandled illegal instruction at address 0x5fe3c1
(thread 002f), starting debugger...
Can attach process 002e:error 5
[POl_Wine] Message: Wine return 29)
```

...which i guess is the problem ?

Here is a topic with the same problem, however the final solution to the problem is:

[I]Try this:

Age Of Empire II -> Configure menu -> Wine -> winecfg -> Graphics (or Display)

Set a virtual Desktop
[/I]

I did this as well, however it did not give a sollution for me, nor when I made the virual desktop the same res as my own screen.

Additional info: running Ubuntu 12.04 with cinnamon here


Help would be very much appreciated :)

---

### Post by sffvba[e0rt on 2012-07-12
*Thread moved to **Wine**.*


404

---

### Post by Dlambert on 2012-07-12
Try running it just in WINE no PlayOnLinux.

---

### Post by oiio on 2012-07-12
Thx for responding

I went to the empires2.exe on the cd-rom. 
Doesn't go into Wine-desktop-thingy now
but same message of "invalid parameters"

I tried locating the game on the "C-drive" but couldn't find it there, is that normal ?

---

### Post by oiio on 2012-07-12
installed it with wine in stead of playonlinux
problem remains

---

### Post by Dlambert on 2012-07-13
GO into your home directory and there should be a link to playonlinux "drives" find the game there. and run it in WINE. not pol. Don't install with WINE just run it from the POL drive.

---

