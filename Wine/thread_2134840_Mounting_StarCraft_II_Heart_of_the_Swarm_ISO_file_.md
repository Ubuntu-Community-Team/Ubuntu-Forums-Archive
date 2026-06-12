---
title: "Mounting StarCraft II Heart of the Swarm ISO file in Ubuntu"
date: 2013-04-12
forum: Wine
---

### Post by Carmageddon on 2013-04-12
I am having a problem:

I am (trying) to install from ISO release (8.4GB file), and the problem is, that once I mount the ISO, I only see one directory, and one file (StarCraft II Setup.exe) - running that file, gives me an error about missing archive files (after which I discovered the missing files inside the mounted ISO under linux) - however, using the SAME ISO on Windows 8 machine with Daemon Tools, it shows 11 items (while I have only the directory and that .exe file in linux, using ls -a!).

I've been mounting using mount -o loop /home/username/Downloads/StarCraft_II_Heart_of_the_Swarm-FLT/flt-hots.iso
also tried -t udf

This was like a week ago, currently I get a different installer error:
Battle.net requires the Windows Secondary Logon service to be enabled.
Please click the error code...

ERror code leads to [https://us.battle.net/support/en/article/BLZBNTBTS0000K](https://us.battle.net/support/en/article/BLZBNTBTS0000K)


Please, can anyone help?
It would be great to have this run on Ubuntu as well!

PS: I am running Ubuntu Raring Ringtail (13.04, if that is significant).

---

### Post by spacesamurai on 2013-05-28
Hello,

I had the same issue tonight. To work around, I performed the following two steps.

1. I updated wine to beta version 1.5

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

2. I did not install from the CD, but selected to run the installer as downloaded from Battle.net. When you download the link and it asks you what program you want to run it with, select wine (it will be found under /usr/bin/wine).

Good luck!

---

### Post by Carmageddon on 2013-05-28
Well, what you are describing is an entirely different product type :)
I cant install from Battle.net for well... obvious reasons :)

However I found out something interesting:
All image files are mounting properly, its just that to MOST of the files, only ROOT has read access!! so far I am unable to overcome this issue (without running wine as root).

---

