---
title: "Steam Crashes half way through downloading Skyrim"
date: 2013-04-06
forum: Wine
---

### Post by JacRichardson on 2013-04-06
I am running ubuntu 12.04 and have downloaded Wine from the ubuntu software center. I installed Steam with no problem from valves website. After I installed Steam, I went to download Skyrim. I gave it a few hours to download, and it downloaded to about 50 percent. Then steam Crashes. Not only does steam crash, but Wine will not open up, configuration or anything. I tried to open up firefox, but it said it was already open. I restarted the computer and it gave me some errors relating to the tmp folder not being set up. Luckily, the system fixed itself, but when I tried to run steam again, it downloaded to about 56 percent, only to happen again. I do not know why this is happenning. 

I have downloaded steam and skyrim completely through playonlinux, but I deleted it because the performance was terrible. i beleived it was from improper 3d drivers, but I could not test using wines suggested method because play on linux put skyrim in a strange place. I have a relatively new computer with an amd FX-6300 CPU, a radeon 7770 GPU, and 8 gb of RAM. I have the newest radeon drivers and have downloaded the d3d9 for skyrim along with .net, but I do not think that would be the problem because skyrim is not done downloading.

I fear it is some sort of memory leak, or wines steam directory running out of space, but I am way out of my comfort area and have no idea on how to test my theory.

I used a disk for play on linux, but opted to download this time.

I am an ubuntu noob, if that was not obvious. In fact, my primary computer is still windows 7. At least until linux gets some more native support.

---

### Post by ppjdee on 2013-04-06
are you using wine to run steam?

---

### Post by xREDEMPTIONx on 2013-04-07
Hi, a couple things I want to point out are that Playonlinux uses (by default) the regular wine you have installed on your system. So if performance was terrible with Playonlinux, using plain wine won't make a difference. Also, don't expect to get the same performance with wine as you do with windows 7. I lose around 10 fps in wine compared to windows7. I also have to turn down all graphical effects to low and antialaising off. 
 You said something about improper 3d drivers,this is very important if you want to play games in linux. Make sure you are using the fglrx propietery drivers if you want to make full use of your graphics card. The radeon driver is the open source driver, and while it is a decent driver with great 2d performance the fglrx drivers will give you a massive performance gain in 3d graphics performance.
 The location of the Playonlinux installs will reside in /home/your-name/.PlayOnLinux/wineprefix/name of game. (.Playonlinux is a hidden folder, press ctrl+h to see hidden files and folders) There is also an option to open the games folder directly from playonlinux. Configure/select game/Miscellaneous/open programs directory.

---

### Post by JacRichardson on 2013-04-07
I can switch my driver back to the proprietary drivers, but steam will not finish downloading skyrim. Should I try to use a Disk to download skyrim. And I know I wont get windows level performance, but I do not even get 10 fps on lowest setting. Should I just redownload it through play on Linux, try a Disk, what? Steam, through wine, will not stay open and it crashes the rest of wine and bugs out the rest of My computer. Sorry for spelling, my Android Does not like this text Box.

---

### Post by JacRichardson on 2013-04-07
I am trying to download again, but this time as windows 7.

---

### Post by JacRichardson on 2013-04-07
Download under windows 7 version of wine seams to work, windows xp version crashed.

---

### Post by ppjdee on 2013-04-08
grtz on getting it fixed. if you feel this topic is solved then you might want to mark it as solved.

---

### Post by JacRichardson on 2013-04-08
My computer takes along time to download and I'm at school. I will marked as solved when I know it works. It's done downloading, but I haven't played it yet.

---

### Post by JacRichardson on 2013-04-08
Okay, I need to download dotnet3.5, but appearently I am running win64 bit data. I have a seperate config file for wine32, but I am haveing trouble running wine tricks with it.

---

### Post by JacRichardson on 2013-04-09
Okay, I am marking this as closed because my current problem is no longer with downloading Skyrim. All I had to do to finish downloading Skyrim was switch wine to windows 7 mode, but I cannot install dotnet to play skyrim with 64 bit Wine, so I will have to delete Wine and redownload wine 32 bit to get Skyrim to work, unless I missed something. But I only needed the windows 7 preset to finish the download.

---

