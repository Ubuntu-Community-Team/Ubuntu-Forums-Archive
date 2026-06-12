---
title: "Problem with wine repository in sources.list"
date: 2017-11-28
forum: Wine
---

### Post by zohran on 2017-11-28
_**Hello, i have problem when i launch apt update after add last wine ppa:**_
```
fulgurance@MSI-GS73VR-6RF:~$ sudo apt update
[sudo] Mot de passe de fulgurance : 
Atteint:1 http://security.ubuntu.com/ubuntu artful-security InRelease
Atteint:2 http://fr.archive.ubuntu.com/ubuntu artful InRelease        
Atteint:3 http://archive.canonical.com/ubuntu artful InRelease                 
Atteint:4 http://fr.archive.ubuntu.com/ubuntu artful-updates InRelease         
Atteint:5 http://fr.archive.ubuntu.com/ubuntu artful-backports InRelease
Atteint:6 https://dl.winehq.org/wine-builds/ubuntu artful InRelease       
Lecture des listes de paquets... Fait                          
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Tous les paquets sont à jour.
W: Skipping acquire of configured file 'main/source/Sources' as repository 'https://dl.winehq.org/wine-builds/ubuntu artful InRelease' does not seem to provide it (sources.list entry misspelt?)
```
[U][B]
My sources.list file:

[/B][/U]```
fulgurance@MSI-GS73VR-6RF:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ artful universe restricted multiverse main
deb-src http://fr.archive.ubuntu.com/ubuntu/ artful universe restricted multiverse main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ artful-updates universe restricted multiverse main
deb-src http://fr.archive.ubuntu.com/ubuntu/ artful-updates universe restricted multiverse main

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ artful-backports universe restricted multiverse main
deb-src http://fr.archive.ubuntu.com/ubuntu/ artful-backports universe restricted multiverse main

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu artful partner
deb-src http://archive.canonical.com/ubuntu artful partner

deb http://security.ubuntu.com/ubuntu artful-security universe restricted multiverse main
deb-src http://security.ubuntu.com/ubuntu artful-security universe restricted multiverse main

deb https://dl.winehq.org/wine-builds/ubuntu/ artful main
deb-src https://dl.winehq.org/wine-builds/ubuntu/ artful main
```

Also i have second question, how on Ubuntu (based Debian distribution) is it possible to recompile wine ? It's for performance reason. I'm not an expert of compilation on Debian, i'm Gentoo regular... Is there a file where is it possible to add compilation paramaters for gcc before compiling packages ?

---

