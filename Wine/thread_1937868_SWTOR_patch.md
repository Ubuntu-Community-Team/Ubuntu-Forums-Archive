---
title: "SWTOR patch"
date: 2012-03-08
forum: Wine
---

### Post by Nemesis2012 on 2012-03-08
NOTE WILL NOT WORK ON Ubuntu 12.04 LTS beta
i got it  working on ubunto 11.4** natty**  ikernel 3.2.11 i used gcc 4.5.2 and wine 1.4 i downloaded wine1.4 1st

```

sudo add-apt-repository ppa:ubuntu-wine/ppa 
sudo apt-get build-dep wine1.3
sudo apt-get build-dep wine
``````
 winetricks d3dx9
``````
 winecfg
```In winecfg, add swtor's launcher.exe to the list of applications.  Select it. In the "Windows Version" dropdown box, select Windows 7.                      Select the "Libraries" tab. In the "New override for library" dropdown box, select d3d9.  Click "Add". Click OK to exit winecfg.                     
       
```
*git clone git://source.winehq.org/git/wine.git ~/wine-git* 
``````
*cd  ~/wine-git*      
``````
*wget bugs.winehq.org/attachment.cgi?id=39208 -O proof_of_concept.patch* 
``````
 *cat proof_of_concept.patch |patch -p1*     
``````
*./configure                             * 
``````
*make*      
``````
 *cd ~/.wine/drive_c/Program\ Files/Electronic\ Arts/BioWare/Star\ Wars\ -\ The\ Old\ Republic/ *
``````
 *~/wine-git/wine explorer /desktop=4,1280x1024 launcher.exe *     
```

---

### Post by Nemesis2012 on 2012-03-15
forgot the link
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25022](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25022)

---

### Post by zythaera on 2012-03-15
Awesome!! Now i can finally destroy my windows partition without another fleeting thought.

---

### Post by Nemesis2012 on 2012-03-20
> **zythaera said:**
> Awesome!! Now i can finally destroy my windows partition without another fleeting thought.
lol i did the same here

---

### Post by DarthKreeaj on 2012-03-24
I've gotten past the launcher, but I seem to have an endless load screen.  What's the best way to remedy this?

---

### Post by Nemesis2012 on 2012-03-25
removed

---

### Post by DarthKreeaj on 2012-03-25
Well, after installing the patch, my launcher no longer works.

---

### Post by Nemesis2012 on 2012-03-26
removed

---

### Post by schtufbox on 2012-03-26
> **Nemesis2012 said:**
> you need to set it for windows 7 and intall dx9 
 winetricks d3dx9 go to the wine page [http://appdb.winehq.org/objectManager.php?sClass=version&iId=25022](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25022) it will show you how to fix the launcher

Interesting. I have mine set to windows XP and it works fine :)

---

### Post by Nemesis2012 on 2012-03-26
> **DarthKreeaj said:**
> Well, after installing the patch, my launcher no longer works.
you using Ubuntu LTS 12.04?

---

### Post by Nemesis2012 on 2012-03-27
> **DarthKreeaj said:**
> Well, after installing the patch, my launcher no longer works.

i found some info on ubuntu LTS beta the network manager has some bugs so you may try like Wicd i'm going to test it out soon as i reinstall 12.04 LTS Beta

---

### Post by cg40k on 2012-05-05
Im running Ubuntu 12.04 LTS and with Wine the Launcher is still hanging up after entering the login info.

---

### Post by zach1535 on 2013-01-27
I was able to get swtor working and patched with PlayOnLinux and I actually got into the game far enought to create a character. After i made my character i changed the resolution (from the desktop 1000x614 that I set in wine) to 1024x768 and then it froze. I can launch the game and log in just fine, then the blue wine desktop takes a few minutes, but eventually bring up the loading screen. It is in the 1024x768 size I set earlier, but is frozen. Any ideas how to get the whole game back to the 1000x614 I originally had it working in? Thanks:p

---

