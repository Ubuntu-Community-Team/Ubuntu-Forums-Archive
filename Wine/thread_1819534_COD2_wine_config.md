---
title: "COD2 wine config"
date: 2011-08-06
forum: Wine
---

### Post by Geezanansa on 2011-08-06
Hi Folks

I have been trying to install COD2 through wine on natty.

The DVD i have is Game of the year Call of Duty 2 (1.2)
The instruction manual that came with game does not list minimum system requirements.


My system is running AMD Phenom X4 2.2ghz, 2GB ram, nvidia Geforce 6800 ultra

(i)My research has led me to believe Call of duty is written for single core cpu. Is running on multi core system problematic if doable at all?

After using wine to manually install from DVD rom single player worked perfect multiplayer did not work at all.
Configured router and multiplayer loaded to main menu but when i joined game i would promptly get kicked for "windows api" error.
(ii)This because windows(wine) ip address different from natty ip addresss so get kicked from server. Is there dlls/libraries or windows updates to aid in the configuration of wine to help prevent this.?

My research then led me to believe wine tricks was the answer so i uninstalled COD2 and wine prefix and reinstalled COD2 using wine tricks which gave same result as previous attempts.
More research led me to believe PlayOnLinux was the answer so uninstalled COD2 and wine prefix and reinstalled COD2 using PlayOnLinux.  Multiplayer worked flawlessly and this was my first taste of online gaming using my own system.  I tried single player but got "please insert proper DVD" message.

Research led me to believe Patching up to COD2 1.3 would help fix this so i did using PlayOnLinux.

After clicking multi player shortcut on desktop I did not get any intro and had to wait 2-3minutes until the main menu appeared (just a black screen until this  happened)
When I tried to join game I would get "this server for 1.2" and could not find a server that was usable( if i did get to weapon menu etc the cursor was incontrollable so I would exit game anyway)
Punkbuster is supposed to work at its most efficient on COD2 1.3 which has proven inaccurate so far I just get kicked...
So after researching even more i found this guide [http://www.unixmen.com/linux-tutorials/1300-install-and-configure-wine-to-play-latest-windows-games-in-linux-ubuntu-linuxmint-fedora](http://www.unixmen.com/linux-tutorials/1300-install-and-configure-wine-to-play-latest-windows-games-in-linux-ubuntu-linuxmint-fedora) which is the only step by step guide i have found so far so that somebody without an IT degree or 30 years experience programming can follow.

In this guide the author uses terminal commands to update winecfg libraries  (installing  windows updates/files(fonts and ++C etc)
(iii)How do i verify which windows dlls/libraries are required to run COD2?
(iv)How do i install required dlls/libraries from winecfg gui?

After uninstalling COD2 then all wine apps(wine tricks, playonlinux) I then reinstalled everything following the guide mentioned above.

For whatever reason i am struggling to find tutorials relevant info regarding wine cfg.

So lots of probs trying to install COD2.

I have spent 100 hrs plus trying to achieve the installation and running of COD2 on my system.  I am not willing to give up yet.  Thought i would ask for guidance.

Everybody has to learn but any help really would be appreciated.

Thanks in advance.

---

### Post by Geezanansa on 2011-08-06
This thread has now been posted on wine forums.(save admins time n effort telling me)

---

### Post by Dlambert on 2011-08-06
I would love to seem this game running in Linux.

---

### Post by Geezanansa on 2011-10-16
For Diambert and anybody else CoD2 can and does work good in linux.
 Just upgraded to 11.10 oneiric and using PlayOnLinux..  PoL was still  installed after upgrade but was broken so updated by using these  instructions [http://www.youtube.com/watch?v=PPKPr2v3qi8.]("http://www.youtube.com/watch?v=PPKPr2v3qi8")

Go to here [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2609](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2609)  and note the wine version for the version of your game.  Using PoL I  installed CoD2 but at end of windows installer PoL went to sleep so  logged out then back in and changed the wine version to 1.0.1 by  installing the wine version through PoL options then because there was  not any PoL launchers I used the CoD2 launcher on desktop after closing  PoL.  The game is not running flawlessly on my system due to hardware  configuration but using game console and manual(in installed folder)  there are many tweaks and settings to adjust to improve gaming  experience.  

This has been my introduction to pc online gaming and it is proving well  worth the effort.  Just need to upgrade hardware for newer games...:lolflag:

---

### Post by Geezanansa on 2011-10-16
Not very good screenshots but CoD2 does work.  It's an old game now but still great fps.:popcorn::popcorn:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=204527&stc=1&d=1318770964[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=204526&stc=1&d=1318770964[/IMG]

---

