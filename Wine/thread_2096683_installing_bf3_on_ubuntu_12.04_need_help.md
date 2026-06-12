---
title: "installing bf3 on ubuntu 12.04 need help"
date: 2012-12-20
forum: Wine
---

### Post by Larsm1980 on 2012-12-20
i installed origin and can get the disk install to run ... but when it tells me to insert disk 2 and i pull disk 1 out the dvd wont mount...

So i tried to compile them to iso files .. but the same resault.. almost

in Acetoneiso disk 1 only runs up to 22 % before asking for disk 2

in furius Iso mount disk 1 runs all 58 % but the i cant mount disk 2

So now i want to try to combine the 2 iso files.

Do anybody know a program?

I have written the proceture down to.. have far ive come. under here

**************************************************************************************

*Download latest wine
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.5

*Download Origin WINDOWS ver.
[http://www.origin.com/dk/download](http://www.origin.com/dk/download)

*Enter wineconfig
*exit wineconfig (OK)

*Enter winetricks
Select the default wineprefix
install a windows dll 
wininit
exit winetricks (Cancel)

*install origin
Run originthinsetup.exe (Rightclick - open with wine)
unclick (run on startup)(Share hardware) 
Move the - accept licence - window to the side and click NO. to restart
Accept the licence
Enter your origin id and password
Press (TOP BAR MENU --> origin -->Close)

*Wineconfig
Enter wineconfig
change to windows 7
enter libraies
change wininit to builtin

*Copy Battlefield disks to iso files and place on desktop in 2 folders
Enter disk 1 BattleField 3
enter filesystem click dvd battlefield 3 click arrow on top bar to go one libraie back
right click bf3 disk
copy disk
choose iso file nr 2 line (Drive)
make isofile
do the same for disk 2

File is normaly saved in home folder

make 2 folders on the desktop name bf3-1 - bf3-2
Move the iso file from disk 1. to bf3-1 
iso file disk 2 to bf3-2

---

### Post by dino99 on 2012-12-21
maybe you should do an other choice

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=26175](http://appdb.winehq.org/objectManager.php?sClass=version&iId=26175)

---

