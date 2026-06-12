---
title: "Another Starcraft II In WINE/Play On Linux problem thread"
date: 2013-08-25
forum: Wine
---

### Post by KELLOGGVOIDS on 2013-08-25
**Failed to run a required program (Blizzard Setup) Error code: BLZPTS0000J**
[B]DURING UPDATER
[/B]
I am so tired now.
I have been surfing forums for weeks, trying to solve this problem. I've  installed several versions of wine, including the recommended (for WOL)  1.5.10. x86, through playonlinux. 
This is the last website I looked at:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

I always receive this error. I have gone through playonlinux's game  list, and installed it from there, and also used the option to install a  file from another directory. I install the game from cd, and it goes  well until i'm ready to update, it goes to 100% and then shows this.  I've installed the ie6 package, the dotnet40 package, and i had 2  seperate virtual drives WITH AND WITHOUT the plugin mono.  
and the DLL overrides in winecfg (set to WIN XP): 
dnsapi (bullitin) 
mshtml (native) 

i had tested on one virtual drive where i manually browsed for the  cd's installation, and another drive where i went into the gametab on  playonlinux, and found starcraft. the manual way made sound problems for  me, and the video would skip too fast in the installation window. i'm  sure that can be fixed, but the other way did not create any  installation problems. both arrive at the problem in the subject of this  post. there's a link for the error code: 
(THIS IS THE ONE I RECEIVE: BLZPTS0000J) 
[us.battle.net/support/en/article/BLZBNTBTS0000J]("https://us.battle.net/support/en/article/BLZBNTBTS0000J") 

i've tried running S2Switcher from the support folder. I can't find  the agent.exe anywhere in the recommended locations in other forum  posts. ( wine .wine/drive_c/users/Public/Application\  Data/Battle.net/Agent/Agent.exe --nohttpauth ) 

i've tried installing it from the installation file available at  battle.net, and i receive a different error, before installation even  begins: 
"No installer data could be found. If this problem persists, please contact Blizzard Technical Support." 
i ignored the installer from battle.net method from here, because i  felt one step closer just using the cd, with a full installation. the  problem after i install with the cd, is the updater. 
I've also tried the echo 0 | sudo tee /proc/sys/kernel/yama/ptrace_scope command
I even upgraded from ubuntu 12.04 to 12.10.

I doubt my hardware is the problem:
Ubuntu x86_64 Linux, 3.5.0-39-generic, Ubuntu 12.10 quantal
AMD Phenom(tm) II X4 945 Processor 800.000 MHz
RAM 3953 MBytes
1024mb memory video card (PNY NVIDIA GEFORCE GTS 250)

Can anyone help me? Thanks for reading..appreciated.

---

