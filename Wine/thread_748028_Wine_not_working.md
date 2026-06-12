---
title: "Wine not working?"
date: 2008-04-07
forum: Wine
---

### Post by Stabilityonitsown on 2008-04-07
Okay so I decided to re-install Debian 4.0 Etch(it was personal problems). And the way I reinstalled it was I install windows xp, load all drivers, then I run Debian Win32 Loader, and reboot and select the "Guided - Use Entire Disk" option. And now I am back up and running, so I go to reinstall all my previous apps and stuff. Well I installed my app into wine, I had done this before the reinstallation with success, and I go to terminal and do "winefile" but it doesn't work[It says "Command Not Found"], I even tried "wine root/.wine/programfolder/morefolders/myprogram.exe" and it came up with "Could Not Find". And also the only ONLY way I can install wine is through pk management. I have tried "wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -" and all it does is go to the second line(without the ""username:/home/username/#" and it just sits there, I have waited 15 minutes with it on the blank line waiting for something to happen). And also ANOTHER thing(yes I know sorry lol) is that I noticed wine was different, it almost seemed like a completely new version after the reinstallation, there was black dialog boxes after anything I have done in wine, with a few options on the bottom. Perhaps I got a wrong installation, I am not sure. Plz help.

---

### Post by gsmanners on 2008-04-07
First of all, I think that site may be down. I haven't been able to pull up [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) so I assume a wget is probably out of the question.

Secondly, I don't think you would use sudo in a default Debian install (unless you have edited sudoers in which case never mind).

---

