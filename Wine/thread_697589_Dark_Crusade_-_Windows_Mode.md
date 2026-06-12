---
title: "Dark Crusade - Windows Mode"
date: 2008-02-15
forum: Wine
---

### Post by Sugi on 2008-02-15
I am running Dark Crusade under PlayOnLinux with wine (i think 0.9.35).  It's working fine, except that the mouse can't stay locked within Dark Crusade within windows mode.  I finally got the mouse to stay locked within full screen mode.  Is there a way to lock the mouse within window mode.

My settings: winecfg > Graphics Tab > Allow DirectX apps to stop the mouse leaving their window.

What should I do?


I am also unable to run the game under PlayOnLinux but I can run it through my menu launcher.

My terminal output:
> Running wineversion menu
Running Dawn of War : Dark Crusade
Dawn of War : Dark Crusade: line 5: cd: /home/midori/.PlayOnLinux/wineprefix/DawnOfWar_DarkCrusade/drive_c/Program Files/THQ/Dawn of War - Dark Crusade/: No such file or directory
wine: could not load L"c:\\windows\\system32\\DarkCrusade.exe": Module not found


Sugi

---

### Post by Sugi on 2008-02-16
Bump

---

### Post by Sugi on 2008-02-23
Bump

---

### Post by Sugi on 2008-02-25
Bump

---

### Post by Sugi on 2008-02-27
Bump

---

### Post by Sugi on 2008-02-27
Bump

---

### Post by Sugi on 2008-03-19
Bump

---

### Post by Sugi on 2008-03-20
Bump

---

### Post by Sugi on 2008-03-24
Bump

---

### Post by naz37 on 2008-03-26
Iv had similar problems with Dark Crusade. I use this launch script to get it to run;

```
X :3 -ac & 

cd ~/".wine/drive_c/Program Files/THQ/Dawn of War - Dark Crusade"

sleep 2

DISPLAY=:3 /usr/bin/wine DarkCrusade.exe
```

Copy this into a file and call it something like launch-dark-crusade.sh

Run it with;
```
sh launch-dark-crusade.sh
```

After exiting the game you will have to ctrl-alt-backslash to get back to your normal desktop.

See [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6051&iTestingId=11620") for more details.

---

