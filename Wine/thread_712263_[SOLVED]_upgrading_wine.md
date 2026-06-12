---
title: "[SOLVED] upgrading wine"
date: 2008-03-01
forum: Wine
---

### Post by terry_gardener on 2008-03-01
I am currently using 9.55 and want to upgrade to 9.56.

how is this done i have been to the winehq website and copied and pasted the command for wine but when i go into synaptic it says that the only version is 9.55. how do you upgrade to 9.56. 

also i have a game installed via wine 9.55 will i have to reinstall it via 9.56 or will it just work. (game is cnc3) 

also i have used the reload button but still 9.55.

---

### Post by FrozenFox on 2008-03-01
The version on winehq is old, still 0.9.55. 

If you want 0.9.56, you will have to wait, compile it yourself (not recommended), or do a search in these forums for a .deb (simple exe-like installer) that is unofficial. Note that unofficial versions lack some features the official ones have (like start menu entry stuff), so you might want to just wait for an official one. You simply double click it to install it. There have been many postings of such here, not too far away from this post. I'm not sure if someone posted one for gutsy, but i know for sure someone posted one for hardy 32 bit and hardy 64 bit that -might- work or might not (probably not, itll probably nag about libc being old). If you can't find one here, google wine 0.9.56 deb and I think someone posted the .deb for it on the mepis forums that will work for gutsy.

No, you shouldnt have to reinstall your game. Wine is simply updated as opposed to the entire folder being deleted and then wine is reinstalled.

---

### Post by ahaslam on 2008-03-01
Assuming 32bit:
```
sudo apt-get build-dep wine
sudo apt-get install build-essential checkinstall
mkdir wine && cd wine
wget [http://easynews.dl.sourceforge.net/sourceforge/wine/wine-0.9.56.tar.bz2](http://easynews.dl.sourceforge.net/sourceforge/wine/wine-0.9.56.tar.bz2)
tar -xvjf wine-0.9.56.tar.bz2
./configure --prefix=/usr --sysconfdir=/etc --enable-opengl --with-x
make depend && make
sudo checkinstall
wineprefixcreate
```
;)

---

### Post by mc4man on 2008-03-01
@ahaslam
> --sysconfdir=/etc
what does this option do vs. not using it?

---

### Post by ahaslam on 2008-03-02
> **mc4man said:**
> what does this option do vs. not using it?
It installs configuration files into /etc instead of /usr/etc. Though this is just an empty directory for Wine, as all configurations are kept within the users home dir. Simply, it's keeps things tidy & can avoid future problems, it's a good practice to get into.

;)

---

