---
title: "Diablo 2 Lord of Destruction Install Problems"
date: 2007-02-12
forum: Wine
---

### Post by MicroChris on 2007-02-12
Hello all,

I'm trying to install Diablo II: Lord of Destruction via Wine. 

I have installed Diablo II correctly and it runs, however when I try and install LoD, it says "Please install Diablo II before installing this".... well, its already installed.. lol

Any workaround for this?

Thanks,
Chris

---

### Post by Muiske on 2007-02-13
Usually when you have installed D2 fine and put the LOD cd in, it automatically detects that D2 is installed. From there, you can choose to upgrade to LOD. Have you tried this already?

If not, I'd try to search where D2 was installed (usually in ~/c/Program Files/Diablo II) and see if everything is correct.

I wouldn't know if there is any workaround should everything be installed fine. You could try to see if the Wine settings (winecfg) are messed up.....

---

### Post by amusicalsoul on 2009-06-16
I have this same problem as we speak. Have you found anything out?

---

### Post by Azuu on 2009-06-16
Diablo 2 and LoD are old enough you can just extract them direct from the CD and install. If that doesn't work, try a mount command in the terminal.

---

### Post by amusicalsoul on 2009-06-17
yo slick i got it to work using wine. make sure that D2 *and *the expansion LOD are installed with wine. it will work. tell it to put a desktop shortcut and then bam, you're set. game runs fine with wine! ;)

---

### Post by efikkan on 2009-06-17
The latest patch is able to run without the CD, but otherwise use d2loader.

You can also try installing using [PlayOnLinux]("http://playonlinux.com/en/")

---

### Post by del_diablo on 2009-06-17
> **MicroChris said:**
> I'm trying to install Diablo II: Lord of Destruction via Wine. 

Thats just odd. Last time i checked it was just to install, and its a go go.
Diablo 2 LOD reads a register file, which means there got to be some clutter there. Did you install on Windows then move it to Wine? Because thats fail, just in case.

PS: did you check it on appdb before you attempted to install=

---

### Post by ELD on 2009-06-17
This would be better suited in the WINE forum, it was created for a reason buddy.

As already noted add in all the patches and follow instructions on the WINE website for the game.

---

