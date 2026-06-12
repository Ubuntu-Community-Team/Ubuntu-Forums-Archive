---
title: "Unable to get Office 2010 to Work under Wine in 12.10"
date: 2012-12-04
forum: Wine
---

### Post by kevinr1 on 2012-12-04
So I have a new computer build (ASRock FM285X Extreme-M | AMD A10 5800K 3.9 GHz Quad-core | 8GB RAM | Ubuntu 12.10 64bit) that I cannot get Office 2010 to run.   Wine version is 1.5.18.
 
1. I've attempted to follow the instructions on [WineHQ ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17336")for installation with limited success.  I am able to install Office 2010, but the programs do not run.  I.e., when I attempt to run Word 2010, the splash screen comes up and says that Word suffered a serious error, yada yada yada.
 
2. I attempted the instructions [here ]("http://ubuntuforums.org/showthread.php?t=1885051&highlight=office+2010+install+problems;bcsi-ac-f883d00464788be6=1EB2F0E6000000027dbdChLbBShxDk3b3rvdiourVK87SwAAAgAAAIzCIwGEAwAAmgAAAFblDgA=") and included ia32-libs, wine-mono, etc and all said that they were installed and current.
 
3. I found an extensive PDF instruction that included selecting about 15 .dlls from winetricks, some of which were included some of which were not, and that did not even install... the installer started then quit.
 
4. I've also attempted to install Office 2010 in a fresh 32bit prefix, but was unable to enter the product key at the opening of the installation.
 
Any assistance would be appreciated.  And for those that may wish to ask, I do use LibreOffice, just (1) need the functionality of Word and Excel for some legacy documents that don't convert well and (2) the online school I go to requires Word-specific functionality for papers.
 
Thanks!

---

### Post by kevinr1 on 2012-12-05
For those who have more expertise with Wine than myself, would it be worth trying to install Office and Wine in chroot since I have 64bit system and Office is a 32 bit program.  I am specifically refering to [this article on WineHQ.]("http://wiki.winehq.org/WineOn64bit")  With supporting documentation [here]("https://help.ubuntu.com/community/BasicChroot"), [here]("https://help.ubuntu.com/community/DebootstrapChroot"), and [here]("http://ubuntuforums.org/showthread.php?t=24575").
 
Any thoughts if this is advisable or not?  "Could" it solve the Office 2010 install/run problem I am having?
 
Thanks!

---

