---
title: "League of Legends installtion"
date: 2013-08-26
forum: Wine
---

### Post by Julian_Kirsch on 2013-08-26
Hi,
today I've installed Ubuntu, was a Windows user for years so I am also stick to Windows Programms / Games.
I've heard that I can use Win Games via Wine. I tried this. 
E.g. running ( succesfully ) Urban Terror Windows Client. It's great.
But the installation of League of Legends gives me a headache.
I start it normally via Wine, I can klick on Continue. But then, when I click on Install the Installer crashes. I 
have no Idea how to fix this. I've searched the internet all I found were fix for problems with the patcher.

I hope you can help me with this.
My Wine is Wine 1.6, new installed also I'm using the newest LoL installer.
I'm a total noob so I hope you can help me.

Regards July

EDIT: WineDbg gives this:
fixme:winedbg:be_i386_is_jump unknown 89
Single stepping until exit from function,
which has no line number information.
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:advapi:LsaOpenPolicy ((null),0xb9e310,0x00000001,0xb9e328) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0xb9e310,0x00000001,0xb9e328) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0xb9e310,0x00000001,0xb9e328) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0xb9e310,0x00000001,0xb9e328) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0xb9e310,0x00000001,0xb9e328) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0xb9e310,0x00000001,0xb9e328) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:shell:SHGetKnownFolderPath flags 0x00004400 not supported
fixme:shell:SHGetKnownFolderPath flags 0x00004400 not supported
fixme:shell:SHGetKnownFolderPath flags 0x00004400 not supported
err:msi:ACTION_CallDllFunction Custom action (L"C:\\users\\julian\\Temp\\msid9c8.tmp":L"OnAiRemoveFilesUndoable") caused a page fault: c0000005
fixme:ntdll:server_ioctl_file Unsupported ioctl 110008 (device=11 access=0 func=2 method=0)

---

### Post by oldrocker99 on 2013-08-26
Have you thought about dual booting?

---

### Post by kschlichther on 2013-08-27
> **oldrocker99 said:**
> Have you thought about dual booting?

This is still the best decision for League of Legends right now, Ill get you an answer as to how to do this through wine later today when I get home. However, in-game you will not be able to see chat and the minimap will appear quite glitchy. I will also have to recommend running the game on the lowest settings to get a decent amount of frames. League  of Legends requires on of the longest install processes to get it working on wine, but its mostly a bunch of simple steps.

EDIT: After doing some experiments, the only way i could make the installer work for league of legends was through a virtual machine, loaded with a copy of windows, if you do that you may as well just duel boot. However, if you have a friend you can get the league of legends files from then you can follow this tutorial on the league of legends forums, it is pretty straight forward (mostly just copy and paste commands for wine into terminal) and will get the job done, however, as mentioned earlier it will be a less-then-perfect game to run. If you have any issue feel free to send me a PM and ill get back to you with detailed instructions on how to complete part of a tutorial. Remember to lock the thread if this solves your issue

[http://forums.na.leagueoflegends.com/board/showthread.php?t=2957372](http://forums.na.leagueoflegends.com/board/showthread.php?t=2957372)*

*You only need complete steps 1-5 to make the game playable, after that you can navigate to the launcher (/home/username/.wine/drive_c/Riot Games/League of Legends/) and right click either launcher and open with Wine windows emulator

---

### Post by Julian_Kirsch on 2013-08-27
Actually I decided to setup an Dual Boot System, but since Microsoft doesn't offer Windows 7 Home Basic for free Download I had to change my decision. 

But, well, I've asked in a another forum "spieleprogrammierer.net" ( german game programmer site ), there was one reply that heloed me.
I could install LoL via PlayOnLinux, the patcher is currently running.

Still I am thankfull for your replys.
Thank, July

P.S.: Sorry for my bad english.

---

### Post by fireflower on 2013-09-19
> **Julian_Kirsch said:**
> Sorry for my bad english. Be of good cheer. Your English is better than mine when I'm drunk, and better than JKF's German, or my German after I run my English through Google translate.

Seeing as you've already fixed the problem - or at least, the first problem you encountered - it might seem the thread is at an end. But it is not. Because a lot of things can go wrong after the install. Not just in theory, but for this particular program, League of Legends. How do I know this? Eschewing personal experience, there is a resource you must be aware of, since you intend to game on linux:

[The Wine application database]("http://appdb.winehq.org/"). The specific page for LoL is [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141"). The information is priceless. It tells you what editions of linux, and what versions of wine, work with what versions of games, with accounts of all the various patches and tricks you have to do, and lists of remaining bugs. Note this gives you the awareness of how much work it would take to run any given game; if it's too much work, or work that's beyond your present skills, you may choose to forego installing that particular game. If it's your favourite game, you can brace yourself for an uphill battle, so you won't be disappointed when it takes 3 hours.

Normal rules for the free market apply. The most support is for the most popular software, someone will try to sell you something free, beware trolls, caveat emptor, etc.

---

