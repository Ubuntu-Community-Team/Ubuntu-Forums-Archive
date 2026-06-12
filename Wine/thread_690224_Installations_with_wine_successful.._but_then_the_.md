---
title: "Installations with wine successful.. but then the progs disappear"
date: 2008-02-07
forum: Wine
---

### Post by savethewabbit on 2008-02-07
hi,
i'm having a problem with wine 0.9.54. 
i'm trying to install games (tried with Anarchy Online at first and thought it was the game's problem, now i'm with World of Warcraft and   nothing's changed), and thankfully both installations were successful, no errors reported. 
however, when i go and try to find the games, they're nowhere to be found. 
i already looked in the .wine/drive_c/ folder but there's nothing there except for 'internet explorer' and an empty 'common files' folder. 

am i doing something wrong? when i install programs i just have them installed at their default folder. 

thanks for the help.

---

### Post by Mze on 2008-02-07
Did you run command winecfg after installing Wine?

They should be usually installed under the directory "Program Files" in .wine folder

To refresh gnome-panel, issue this command in terminal or simply logout and then login again

killall gnome-panel

---

### Post by savethewabbit on 2008-02-07
yes, i did. i followed [this guide]("https://help.ubuntu.com/community/WorldofWarcraft") and it said to do it. 
there are no folders in 'program files' other than those 'common files' and 'internet explorer'. i also had to reboot between trying to install AO and WoW, so i guess the gnome-panel did refresh?

eta: i would like to add that WoW runs if i start the installer (the one you can download from the official website), as i think the files are cached now so it takes about 5 minutes to download the full 3gb of the game. then it just says 'play world of warcraft' and does not ask me to install it as it did the first time, so i guess it is installed somehow, even if it's not in the folder.
i have uninstalled wine and installed it again in the meanwhile, and nothing's changed, it says WoW is installed already. running a search on my system doesn't find any 'warcraft' file. it's very weird. now i'm letting the uploader download the patch, but i'm not hoping WoW turns up on my pc after it :\

eta2 : i tried unistalling and reinstalling the game as well. no changes. i wouldn't mind if only i didn't know how to start the game after exiting it!

---

### Post by savethewabbit on 2008-02-09
bump..

---

### Post by happyhamster on 2008-02-09
Well, there's every evidence it's on your system somewhere, so keep searching.

sudo updatedb

locate wow
locate "Program Files"
locate .exe

etc, etc. :)

---

### Post by savethewabbit on 2008-02-09
> **happyhamster said:**
> Well, there's every evidence it's on your system somewhere, so keep searching.

sudo updatedb

locate wow
locate "Program Files"
locate .exe

etc, etc. :)


woah! thanks!! i couldn't find it with the "search for file" function but with 'locate wow' i found a 
root/.wine/drive_c/Program Files/World of Warcraft/ folder!
i was looking in home/"username"/.wine and there's nothing there, in that root/.wine folder i also found anarchy online.
thank you!

---

### Post by happyhamster on 2008-02-09
Congrats on finding your games :)

> **savethewabbit said:**
> in that root/.wine folder
That's not where the .wine folder should be though: it should be in your home dir. Probable cause is that at some time wine (or winecfg) was run as root (by using 'sudo'). This should be avoided if at all possible.

- Should you run into trouble, then try removing wine completely from your system:

sudo apt-get remove --purge wine

- Re-install wine and when that's done, configure wine:

winecfg

- (without sudo). This should create a .wine folder in your home dir. Next re-install your games, etc. (again without using sudo). If all of that works, you can then safely delete the /root/.wine folder.

---

### Post by savethewabbit on 2008-02-09
ah, yes, i did use sudo. if i remember right, wine wouldn't load the blizzard installer without it, or something similar. if i copy the game folders and paste them in the wine folder after removing it and re-installing it correctly, will they work?
thanks a lot for your help!

---

### Post by happyhamster on 2008-02-09
> **savethewabbit said:**
> if i copy the game folders and paste them in the wine folder after removing it and re-installing it correctly, will they work?
I don't think so. You'll probably have to change permissions of all those files and folders, and even then it may still not work. (And messing with permissions can even hurt your system if not done right.)

---

