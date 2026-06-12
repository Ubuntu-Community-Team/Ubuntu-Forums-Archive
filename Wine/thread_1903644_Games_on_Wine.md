---
title: "Games on Wine"
date: 2012-01-03
forum: Wine
---

### Post by layers on 2012-01-03
I am trying to run Age of Empires II on wine 1.3.28 (apparently it does work properlyhttp://appdb.winehq.org/objectManager.php?sClass=application&iId=99 ), but when I try to run it from terminal
i get only this, with no other terminal output.[ATTACH]210165[/ATTACH]```
ibo@ibo-vaio:~$ ~/.wine/drive_c/Program\ Files/Age\ of\ Empires\ II\ Gold\ Expansion/age2_x1.exe
ibo@ibo-vaio:~$
```

If I try to run it from nautilus, it loads up, and when I'm about to actually start the game, it crashes with [ATTACH]210164[/ATTACH] Can someone help me fix this?

or how can I upgrade my Wine to 1.3.35, without braking Office 2007 which runs perfectly now?

---

### Post by Elfy on 2012-01-03
Thread moved to Wine.

---

### Post by Toz on 2012-01-03
Try using PlayOnLinux ([http://www.playonlinux.com]("http://www.playonlinux.com")). AOEII is supported ([http://www.playonlinux.com/repository/?cat=1]("http://www.playonlinux.com/repository/?cat=1")).

It would be best to install the latest version of POL - see the "Ubuntu" section at: [http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html") for instructions on how to install.

POL will create a separate set of prefixes and won't interfere with your existing install of Office. POL will also manage different versions of wine.

---

### Post by layers on 2012-01-03
> **Toz said:**
> Try using PlayOnLinux ([http://www.playonlinux.com]("http://www.playonlinux.com")). AOEII is supported ([http://www.playonlinux.com/repository/?cat=1]("http://www.playonlinux.com/repository/?cat=1")).

It would be best to install the latest version of POL - see the "Ubuntu" section at: [http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html") for instructions on how to install.

POL will create a separate set of prefixes and won't interfere with your existing install of Office. POL will also manage different versions of wine.

yeah... the thing is, I only have a copy of the AOE2 folder from Program Files over from the other my old Windows computer - so no disk with an installation executable. On previous Ubuntu systems, I just ran the empires2.exe to play the game, when I had Wine only. Would that be possible with POL? Don't I actually need the disk with POL?

---

### Post by dioxholster on 2012-01-04
I would like to know how POL works with games as well.

---

### Post by Toz on 2012-01-04
> **layers said:**
> yeah... the thing is, I only have a copy of the AOE2 folder from Program Files over from the other my old Windows computer - so no disk with an installation executable. On previous Ubuntu systems, I just ran the empires2.exe to play the game, when I had Wine only. Would that be possible with POL? Don't I actually need the disk with POL?

POL will require the installation disks. In fact, any wine install would, unless you can somehow recreate the necessary environment for a copy to work (directx, windows dlls, etc). I don't know enough about AOE to comment on how its installed and what components it requires.

---

### Post by Toz on 2012-01-04
> **dioxholster said:**
> I would like to know how POL works with games as well.

Not sure what exactly you're asking about. Have a look at [www.playonlinux.com]("http://www.playonlinux.com") for information about the product.

---

### Post by layers on 2012-01-06
i got hold of an iso of the game.
there - my exact clicks: install,apply,forward, wtf


i need the game first, then the expansion

---

### Post by Toz on 2012-01-07
There seems to be a bug in the installation script for that file. Looks like the prefix isn't being created properly. Might be worth posting on the PlayOnLinux Forums or creating a bug report. 

As a workaround, manually create the prefix before running the startup script. From a terminal window, execute the following command:
```
WINEPREFIX=~/.PlayOnLinux/wineprefix/AgeOfEmpire2 winecfg
```
...and when the wine configuration dialog box opens up, just close it and then start the POL installation script.

Note: I don't have this game so am unable to continue further with the script. Hopefully it will install.

---

