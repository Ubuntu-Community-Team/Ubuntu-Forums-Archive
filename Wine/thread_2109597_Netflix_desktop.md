---
title: "Netflix desktop"
date: 2013-01-28
forum: Wine
---

### Post by gn2tx on 2013-01-28
Netflix desktop crashed on me today(had it working for a week), I tried uninstalling and re-installing it but now I only get a blank screen when I go to play something. I tried uninstalling and re-installing wine still a blank screen. I'm new to ubuntu and I don't quite know what I'm doing can anyone point me in the right direction?

---

### Post by gn2tx on 2013-01-28
I think the issue is with wine? how can I remove all of wine and re-install it ?

---

### Post by oldos2er on 2013-01-28
Moved to Wine.

---

### Post by Tweak42 on 2013-01-29
You didn't state how you installed the Netflix Desktop, but I'm assuming you did it via [Erich Hoover's PPA]("http://www.compholio.com/netflix-desktop/").  The actual launchpad project site is [Netflix Desktop]("https://launchpad.net/netflix-desktop") if you want to check bugs and such.  For Netflix Desktop to work you must use "Wine - Compholio Edition" (it's in the same PPA), so make sure you are not using the Ubuntu Wine PPA.

Wine puts windows programs it installs into hidden directories called "wine prefixes", thus uninstalling/reinstalling just the wine package itself does not remove the prefixes.  The default wine prefix is in .wine but I'm not sure where the Netflix Desktop setup places itself.
 
A hint where to look, according to [https://launchpad.net/netflix-desktop/+announcement/11112](https://launchpad.net/netflix-desktop/+announcement/11112) the netflix desktop moved it's directory from "~/.netflix-desktop" to "~/.wine-browser".  I would try uninstalling Netflix Desktop, rename or remove those directories if they exist and then reinstall netflix desktop.

NOTE: If you have any other windows programs setup using wine be carefull what you delete or you may end up deleting those installs as well.

---

### Post by gn2tx on 2013-01-31
Thank you so much for the link I had it up and running in minutes! I was ready to give up, turns out my graphics card driver got uninstalled somehow.
thanks for the help!

---

