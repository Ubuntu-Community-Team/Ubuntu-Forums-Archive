---
title: "wine __cannt remove"
date: 2011-08-29
forum: Wine
---

### Post by nushbi on 2011-08-29
installed wine but messed up well n wanna remove it...
tried all i know...
form terminal: removed, autoremoved, purge
searched and deleted from file system...
but still wine browser, hh, notepad, rundl32, winebrowser, wine internet explorer, winhelp32, wordpad... comes along when trying to open an application as other choices of opening...
need some help....:(

---

### Post by dino99 on 2011-08-29
sudo rm -rf .wine

---

### Post by howefield on 2011-08-29
Moved to the "*Wine*" forum.

---

### Post by _d_ on 2011-08-29
> **dino99 said:**
> sudo rm -rf .wine

This will only remove the wine configuration folder, not any links that wine has installed into menus/alternative opening programs (such as the user describes).

---

### Post by Tweak42 on 2011-08-29
I think all the relevant places to manually remove wine stuff is here:

[http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa](http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa)

There are commands for clearing the menus and file associations.

---

### Post by wineman on 2011-08-29
hi tweak42

from what you're describing, it sounds like you could have a broken installation of wine. If that is the case, then you'll have to upgrade your current version of wine  (and its dependancies) to a newer version and/or a newer distribution of wine, and then uninstall it. This is fairly simple:
1) in aptitude (or synaptic), search for wine. 
In aptitude, press '/' and then type wine and press 'n' until you find it. Then once you have found wine or wine1.2, wine1.3, etc press 'u' to upgrade. Then press 'g' twice to go through with the upgrade, and you should be sorted. 
In synaptic, search for wine and then right click on it and click 'mark for upgrade'. Then press apply and Click ok and you're upgraded.
2) Once the upgrade is done, go into terminal and execute the following:
$ sudo apt-get purge wine wine1.2 wine1.3
This will totally remove wine.
3) Once wine is totally removed, reinstall wine in whatever fashion you want from either the Wine repos ([http://www.winehq.org/download](http://www.winehq.org/download), choose the 'Ubuntu' option) or from the official ubuntu repositories (i usually use za.archive.ubuntu.com, but you should use archive.ubuntu.com or your countries archive, eg: br.archive.ubuntu.com for brazil or us.archive.ubuntucom for the US).

HTH

---

### Post by nushbi on 2011-10-10
thankx [wineman]("http://ubuntuforums.org/member.php?u=602104")...!!!

---

