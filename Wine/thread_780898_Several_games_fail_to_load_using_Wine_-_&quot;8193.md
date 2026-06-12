---
title: "Several games fail to load using Wine - &quot;8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)&quot;"
date: 2008-05-03
forum: Wine
---

### Post by tghe-retford on 2008-05-03
I keep getting this error message on several games which should according to the Wine AppDB work on my computer:

```
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
```

After which the games fail to load.

It affects GTA III (won't work at all), GTA Vice City (it worked once tonight, now it doesn't want to play ball) and sometimes GTA San Andreas (though that works for now)

I have followed the instructions to install and get the game to work, I reinstalled Wine from the repositories, reinstalled the games and restarted the computer to no avail. I don't want to remove the ~/.wine directory if I can help it because I have a number of working games, but I fear that is the next step I would have to take, because nothing is making these games work.

I'm tearing my hair out (not literally of course!), I have tried to get these games to work tonight to no avail.

Any help would be appreciated. Thanks in advance.

---

### Post by cogadh on 2008-05-03
I wouldn't remove the existing .wine directory, but rather create a separate one and install the GTA games there:
```
wineprefixcreate ~/.gtagames
```
Then when you want to run them, just make sure you tell Wine to use the new directory:
```
env WINEPREFIX=~/.gtagames wine gtavc.exe
```
Then if you continue to have problems, at least you don't have to mess up your existing good installs.

---

### Post by tghe-retford on 2008-05-04
I tried your suggestion and the same problem occurs. Thanks anyway.

I reinstalled the games and at least they work as in I can now launch the games, but I can only do so if I navigate to the exe files and launch the game from the exe file. Creating a launcher shortcut to the exe file on the desktop doesn't work and launching the game from a terminal gives the above message.

Very strange. :-k

---

### Post by Pitel on 2008-08-23
Same problem here, but only with SA. VC is ok. It started to behave like this since Wine 1.1.2

---

### Post by roaldz on 2008-08-28
I´ve got the same problem when trying to run San Andreas. I´ve patched it to 1.01 EURO, i´ve tried several no-cd cracks, but still no luck. Hardware:

Intel C2D T7200
2G RAM
Nvidia 7600Go
Ubuntu 8.04.1 64bit

What could it be?

---

### Post by naniekso2 on 2008-11-15
omg i have the same problem

---

