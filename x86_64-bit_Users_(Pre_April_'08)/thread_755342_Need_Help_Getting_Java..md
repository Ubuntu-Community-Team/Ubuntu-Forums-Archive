---
title: "Need Help Getting Java."
date: 2008-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by IGanjaI on 2008-04-14
Ok. So I want to get Java for my Comp( I got Gutsy Gibbon On it) so that i can play some java game's and i dont know how to download it or how to install it. Also I want To get adoby flash player.

---

### Post by Pumalite on 2008-04-14
Check Synaptic

---

### Post by ibutho on 2008-04-14
For flash, do
```
sudo aptitude install ubuntu-restricted-extras
```
For java you need to make sure that the universe software repository is enabled and do
```
sudo aptitude install icedtea-java7-plugin
```
You can use the Add/Remove software program or Synaptic if you prefer working in a GUI.

---

### Post by IGanjaI on 2008-04-14
Ok when i try and open synaptic i get this error.> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


---

### Post by Pumalite on 2008-04-14
Run:
sudo dpkg --configure -a 
sudo apt-get update
sudo apt-get upgrade

---

### Post by IGanjaI on 2008-04-14
Ok So i did what u said pumalite then i did what ibutho said and on the first one for flash i got this message at the end.> E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


---

### Post by ibutho on 2008-04-14
The permission denied error can happen if you did not prefix your commands with sudo e.g. "sudo dpkg --configure -a" or you are not in the admin group.

---

### Post by IGanjaI on 2008-04-14
I am Set as admin But Ill try andmake sure then re-try.

---

### Post by nnamdi on 2008-04-14
hey you go to synaptics and install the compiler i.e the jsdk that will help ok

---

### Post by Pumalite on 2008-04-14
Make sure you close Synaptic too.

---

### Post by IGanjaI on 2008-04-14
Ok so i Checked and re-set myself as administrator and then re did the flash and the it started to go thru the steps then this popped up.

> Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)

---

### Post by Pumalite on 2008-04-14
Run:
sudo apt-get -f install

---

### Post by IGanjaI on 2008-04-14
Tryed and got this> .Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  binfmt-support sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  sun-java6-jre
The following packages will be upgraded:
  sun-java6-bin
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/32.7MB of archives.
After unpacking 93.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package sun-java6-jre.
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
88511 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-03-0ubuntu2_all.deb) ...
Selecting previously deselected package sun-java6-bin.
Preparing to replace sun-java6-bin 6-03-0ubuntu2 (using .../sun-java6-bin_6-03-0ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
Setting up sun-java6-jre (6-03-0ubuntu2) ...

Setting up sun-java6-bin (6-03-0ubuntu2) ...
No theme index file in '/usr/share/icons/sun-java6.png'.
If you really want to create an icon cache here, use --ignore-theme-index.

---

### Post by jpeddicord on 2008-04-14
Moved from Installation & Upgrades to x86 64, since this appears to be a 64-bit problem.

---

### Post by nnamdi on 2008-04-14
yes that is a strong point too u cant use to package managers at the same time
i.e either you use the synaptics or you are goin through the command line ok

---

### Post by brento73 on 2008-04-15
I used Synaptic to install the plugin, but I still have no java according to Firefox, is there something I need to do so it recognizes the plugin?

Update: I copied the file /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so to the plugin folder, and now Firefox crashes when it encounters java on a page.

---

### Post by IGanjaI on 2008-04-15
Ok i know that i can only run one at a time.... Not A total moron....lol..... But i have been browsing around my comp and it says that my java thing is broken. But i also want to know should i download all my package's from synaptic? from the look's of it i have like well over 500.

---

