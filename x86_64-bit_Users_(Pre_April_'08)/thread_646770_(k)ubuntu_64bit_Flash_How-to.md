---
title: "(k)ubuntu 64bit Flash How-to"
date: 2007-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by banko on 2007-12-21
**This tutorial assumes you have Firefox installed.**

Step 1 - Get to a terminal:
----------------------------------------------------
Ubuntu:  Alt + F2, type "gnome-terminal"
Kubuntu: Alt + F2, type "konsole"

Step 2 - First try the repo installer:
----------------------------------------------------
> 
At the time of this writing, do to an upgrade at macromedia, the checksum is failing, resulting in flash not installing.  This is fine still perform this step, as it  installs many other needed packages like our wrapper


```
sudo apt-get install flashplugin-nonfree
```

case(1): If no errors you are done! Congrats
case(2): You received the error "md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.".  Welcome to the club, continue with Step 3.
case(3): You received a different error then the above.  Well there is always a black-sheep in the family.  Copy and paist the terminal session in here for us, and we will try and help.

Step 3 - Download the tar.gz from Macromedia
```

wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz

```
Step 4 - Install Flash
```

tar xf install_flash_player_9_linux.tar.gz; cp install_flash_player_9_linux/libflashplayer.so /usr/lib/flashplugin-nonfree/

```
Step 5 - Put it through a wrapper for 64bit Firefox
```
nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so
```

Step 6 - Link our plugin into firefox
```

sudo ln -s ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so

```

Firefox is done just restart it and browse to a site with flash.  Kubuntu users can you verify that it also works in Konqueror by Clicking Settings --> Configure Konqueror --> Plugins --> Scan for new plugins --> Yes, Then restart Konqueror and visit a flash site.

---

### Post by flamelab on 2007-12-21
Very good .

I haven't exactly followed these instructions though , check :

(```
sudo -s -H
```)

```
apt-get install nspluginwrapper
```

```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```

```
tar -zxf install_flash_player_9_linux.tar.gz
```

```
mkdir ~/.mozilla/plugins/
```

```
mv install_flash_player_9_linux/flashplayer.xpt install_flash_player_9_linux/libflashplayer.so ~/.mozilla/plugins/

```
```
nspluginwrapper -i ~/.mozilla/plugins/libflashplayer.so
```

---

### Post by utUtu on 2007-12-21
I find it hard to believe this has not been fixed yet in gutsy though it was in hardy.  The md5sum check was hardcoded for r48 which does not work for r115(latest).  It should have issued a warning instead, and went on it's merry way.  Besides it's getting it from Adobe web site.
:confused:

---

### Post by Kilz on 2007-12-21
Even easier
1. [Go here]("http://ubuntuforums.org/showthread.php?t=476924")
2. Get Script
3. Click on script and choose "run in terminal"
4. Answer easy questions.
5. Flash works.

---

