---
title: "Flash Install"
date: 2008-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by larainzlo07 on 2008-01-03
i found and was trying this 
Download the Flash tarball ([http://www.adobe.com/shockwave/download/download](http://www.adobe.com/shockwave/download/download). cgi?P1_Prod_Version=ShockwaveFlash).

wget [http://fpdownload.macromedia.com/get/flashplayer/c](http://fpdownload.macromedia.com/get/flashplayer/c) urrent/install_flash_player_9_linux.tar.gz

Extract it and move the necessary to the plugins directory:
tar -zxf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux/
mv *flashplayer* ~/.mozilla/plugins

Install nspluginwrapper:


sudo aptitude install nspluginwrapper


Install a wrapper version of the Flash plugin for your 64-bit browser:


nspluginwrapper -i ~/.mozilla/plugins/libflashplayer.so

but when i get to the last command i get this problem
nspluginwrapper: /home/user/.mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin

---

### Post by Kilz on 2008-01-03
[Take a look here.]("http://ubuntuforums.org/showthread.php?t=476924")

---

### Post by MrKlean on 2008-01-04
this worked for me..thanks to another Ubuntu'er LOL!

cd ~/ && wget [http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz](http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz) && tar xzvf nsplugin*.tar.gz && cd nsplugin*install && sudo ./GetFlash

---

### Post by ~LoKe on 2008-01-04
> **MrKlean said:**
> this worked for me..thanks to another Ubuntu'er LOL!

cd ~/ && wget [http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz](http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz) && tar xzvf nsplugin*.tar.gz && cd nsplugin*install && sudo ./GetFlash

I wrote that based off of Kilz's guide, all it does it combine the steps.  So all credit still goes to him. =]

---

### Post by larainzlo07 on 2008-01-04
thanx kilz that worked

---

