---
title: "StarCraft II: Heart of the Swarm"
date: 2013-03-16
forum: Wine
---

### Post by Ximaceo on 2013-03-16
Hi folks, yesterday I installed StarCraft II: Heart of the Swarm, I have some troubles:

- Audio is out, also If I'm listening music from Rhythmbox.
- I can't see videos, black screen, I can skip with ESC.
- System crashes sometimes.

My system:
OS: Ubuntu 12.10 i386
Kenel: 3.5.0-25
Wine: 1.5.25
CPU: Intel Core i7 950 @ 3.07 GHz
RAM: 3 x 2GB DDR3 @ 1066 MHz
GPU: HIS Radeon HD 5850 1GB
Driver: AMD Catalyst 13.1
SPK: Logitech Z-5500 5.1
SND: Sound Blaster X-Fi Titanium

With low settings I have 30fps, someone is playing SCII:HotS?

---

### Post by Ximaceo on 2013-03-19
Hi again, I upgraded system software and better now:

- Audio works! it's crispy. Before I play I must open System Configuration > Sound (no tryed on last post).
- Video works!
- System crashes sometimes.

My system:
OS:Ubuntu 12.10 64-bit
Kernel: 3.5.0-26-generic
Wine: 1.5.26

With low settings I have 30fps yet.

---

### Post by NimalNet on 2013-03-23
I just finished installing Starcraft 2 Heart of the swarm
Lubuntu 12.10 using PlayOnLinux 4.1.9 Wine 1.5.26

It runs pretty smooth, graphics are great, Kerrigan looks hot as always
Multiplayer works great, the compaign crashed on me a couple of times

The installer kept crashing when I used the installation DVD.
So step one is to download the windows installer from battle.net

Then start POL
Goto Tools > Manage Wine versions
Install wine 1.5.26 for x86

Select install
Select install a non-listed program
Create a new virtual drive (I didn't upgrade WOL because I didn't want to ruin my install.

Select use another version of Wine
Select 1.5.26
Choose the 32 bits windows installation
Select the installer

Relax and sit back
Installation took a while but it runs quite smooth. 
Play On Linux didn't create an Icon for me. (Just like WOL, just make one manually)


Enjoy!

Nimal13
ps Zerg Rules

---

### Post by Ximaceo on 2013-03-24
Hi NimalNet, this is how I do:

- Install Wine development release
> sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.5
- Download game client from: [https://us.battle.net/account/download/](https://us.battle.net/account/download/)
- Double click on .exe file and install

   
System crashes sometimes.
I have played 30 match VS I.A. and system crashed in 15 of them  ](*,)
StarCraft II is rated Platinum in Wine Application Database (AppDB) [http://appdb.winehq.org/](http://appdb.winehq.org/)
I did some wrong? Can PlayOnLinux improve stability? Which video card you have?


**For the Swarm!!!**
[http://eu.battle.net/sc2/es/profile/1511524/1/Ximaceo/](http://eu.battle.net/sc2/es/profile/1511524/1/Ximaceo/)

---

### Post by Carmageddon on 2013-04-10
I am having somewhat different problem:

I am (trying) to install from ISO release (8.4GB file), and the problem is, that once I mount the ISO, I only see one directory, and one file (StarCraft II Setup.exe) - running that file, gives me an error about missing archive files (after which I discovered the missing files inside the mounted ISO under linux) - however, using the SAME ISO on Windows 8 machine with Daemon Tools, it shows 11 items (while I have only the directory and that .exe file in linux, using ls -a!).

I've been mounting using mount -o loop  /home/username/Downloads/StarCraft_II_Heart_of_the_Swarm-FLT/flt-hots.iso
also tried -t udf

This was like a week ago, currently I get a different installer error:
Battle.net requires the Windows Secondary Logon service to be enabled.
Please click the error code...

ERror code leads to [https://us.battle.net/support/en/article/BLZBNTBTS0000K](https://us.battle.net/support/en/article/BLZBNTBTS0000K)


Please, can anyone help?
It would be great to have this run on Ubuntu as well!

PS: I am running Ubuntu Raring Ringtail (13.04, if that is significant).



Thanks!

---

### Post by CharlesT423 on 2013-07-20
I realizez this was from a while ago, but in case anyone else has this problem you have to mount the CD with the "unhide" option.  IE, "mount -o loop,unhide /path/to/Hots.iso"  You may also have to add uid=<your user id> which you can find by running the command "id"  IE, if you see "uid=1003(charles)" then the you would use "mount -o loop,unhide,uid=1003 /path/to/Hots.iso"  If you get an error from Wine about not being able to read or find the Installer.exe file, then it's the uid issue.


> **Carmageddon said:**
> I am having somewhat different problem:

I am (trying) to install from ISO release (8.4GB file), and the problem is, that once I mount the ISO, I only see one directory, and one file (StarCraft II Setup.exe) - running that file, gives me an error about missing archive files (after which I discovered the missing files inside the mounted ISO under linux) - however, using the SAME ISO on Windows 8 machine with Daemon Tools, it shows 11 items (while I have only the directory and that .exe file in linux, using ls -a!).

I've been mounting using mount -o loop  /home/username/Downloads/StarCraft_II_Heart_of_the_Swarm-FLT/flt-hots.iso
also tried -t udf

This was like a week ago, currently I get a different installer error:
Battle.net requires the Windows Secondary Logon service to be enabled.
Please click the error code...

ERror code leads to [https://us.battle.net/support/en/article/BLZBNTBTS0000K](https://us.battle.net/support/en/article/BLZBNTBTS0000K)


Please, can anyone help?
It would be great to have this run on Ubuntu as well!

PS: I am running Ubuntu Raring Ringtail (13.04, if that is significant).



Thanks!

---

### Post by Carmageddon on 2013-07-20
Thank you!! this solved my problem and allowed me to install!
Now I am able to run the game, but having another issue ("...Starter Edition does not support offline mode" or something like that) so not quite there yet... anyone managed to run the RELOADED release under wine?

---

### Post by gabriel-balint on 2014-05-31
So I have been playing Starcraft 2 for a while from Ubuntu, but starting yesterday I am receiving this error. Now it could be some ubuntu update, or SC2 update, not sure.
I have used the web installer to install the game, so there is no ISO that I have to mount. Any idea anybody?


> **CharlesT423 said:**
> I realizez this was from a while ago, but in case anyone else has this problem you have to mount the CD with the "unhide" option.  IE, "mount -o loop,unhide /path/to/Hots.iso"  You may also have to add uid=<your user id> which you can find by running the command "id"  IE, if you see "uid=1003(charles)" then the you would use "mount -o loop,unhide,uid=1003 /path/to/Hots.iso"  If you get an error from Wine about not being able to read or find the Installer.exe file, then it's the uid issue.

---

