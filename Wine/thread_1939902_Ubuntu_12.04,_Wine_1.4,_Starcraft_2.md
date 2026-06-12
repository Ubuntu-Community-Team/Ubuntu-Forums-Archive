---
title: "Ubuntu 12.04, Wine 1.4, Starcraft 2"
date: 2012-03-12
forum: Wine
---

### Post by Vegasq on 2012-03-12
Hello there (:

I have small issue with my Ubuntu Desktop. I tried update to current beta relise (12.04 32bit). After upgrade stopped work Wine&&Starcraft II with follow message:

> 
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:imm:ImmReleaseContext (0x40030, 0x1552b0): stub
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x39ccaac,0x39ccab0): stub
fixme:dbghelp:EnumerateLoadedModulesW64 If this happens, bump the number in mod
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x39cc738,0x39cc73c): stub
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:dbghelp:EnumerateLoadedModulesW64 If this happens, bump the number in mod
err:ntdll:RtlpWaitForCriticalSection section 0x16bfa74 "?" wait timed out in thread 002d, blocked by 0032, retrying (60 sec)


Last line repeat every minute.

Wine 1.4
Ubuntu 12.04 32bit
Nvidia proprietary driver

Can someone help me with this?

Best regards,
Niko

P.S.

Join Date: Aug 2007... My first message for a long long time...

---

### Post by 8Kuula on 2012-03-14
Have you tested launching game using default prefix?

For me it launches, but crashes when I try to login, and crashes at login screen right away after that first login try. Using default prefix again, launches at login screen again.

Wine 1.4
Ubuntu 12.04 64bit
nvidia: 295.20

---

### Post by dino99 on 2012-03-14
start with a cleaned new .wine
so, rename the actual .wine to .wineold (or erase it), then reinstall wine1.4, log out/in

---

### Post by fredrik-fyksen on 2012-03-19
I got the same problem. Have anyone found a fix for it? My Starcraft 2 crashes right before the login screen.

Then I get a long and nasty error message from "ErrorReporter".

I installed Starcraft with PlayOnLinux, Wine version 1.4

---

### Post by 8Kuula on 2012-03-19
Not me, so far, but i am a noob.

---

### Post by schtufbox on 2012-03-19
While not starcraft, I did notice on my test machine with 12.04 that I cannot run Star Wars: The Old Republic under patched wine or the unsupported crossover build.  This is both under 32bit and 64bit versions.

The same PC running Ubuntu 11.10 runs the game flawlessly under 32 and 64bit versions.  Also runs fine under PCLinuxOS, and Sabayon.  Similar issues with a few other games too, such as COD Black Ops...

I'm guessing it's something to do with 12.04 :)

---

### Post by Vegasq on 2012-03-20
Install winbind and test again. Also, follow all the indications in the Starcraft II page.

Yore

---

### Post by Gnobody on 2012-04-01
I have Wine 1.4 & 1.5 installed from PPA on 12.04 AMD64 and StarCraft 2 crashes at the login screen w/ the following report:


ACCESS_VIOLATION (0xC0000005)
occurred at 0023:3CD0A616.  The memory at '0x38CF0D21' could not be read.


I've tried all the suggested regedit tweaks on the WineHQ DB for SC2, nothing will get it past the login screen.

EDIT; 
I also installed winbind

---

### Post by Gnobody on 2012-04-04
bump


Has anybody had any progress?

---

### Post by Nemesis2012 on 2012-04-04
Ubuntu 12.04 have a firewall?

---

### Post by saxin on 2012-04-05
> **Gnobody said:**
> bump


Has anybody had any progress?

Nope... still the same message as you got. It's strange actually, cuz' in earlier versions of Ubuntu there have been how-to's/guides how to fix it. Now, there is nothing :confused:

---

### Post by Nemesis2012 on 2012-04-06
> **Gnobody said:**
> bump


Has anybody had any progress?

did you try *nvidia*-*utils*

---

### Post by 8Kuula on 2012-04-08
[http://www.codeweavers.com/support/tickets/browse/?ticket_id=883964;list=6;ticket_level=0](http://www.codeweavers.com/support/tickets/browse/?ticket_id=883964;list=6;ticket_level=0)

There is something, not helping, but maybe a reason why 12.04+SC2 do not play ball.

Other that I noticed, if you do not save your login then SC2 won't crash until you try to login (not helping? ;)).

---

### Post by Nemesis2012 on 2012-04-09
> **8Kuula said:**
> [http://www.codeweavers.com/support/tickets/browse/?ticket_id=883964;list=6;ticket_level=0](http://www.codeweavers.com/support/tickets/browse/?ticket_id=883964;list=6;ticket_level=0)

There is something, not helping, but maybe a reason why 12.04+SC2 do not play ball.

Other that I noticed, if you do not save your login then SC2 won't crash until you try to login (not helping? ;)).

you can write bugs for wine in ubuntu? i just downgraded to 11.10 :mad:

---

### Post by hellcatv on 2012-04-13
typing

echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope

before running starcraft 2 avoids the issue for me

Given the workaround, it could be related to this bug
[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/632206](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/632206)
or this one
[http://bugs.winehq.org/show_bug.cgi?id=24193](http://bugs.winehq.org/show_bug.cgi?id=24193)
Thanks to Shadows_Friend for pointing these out here
[https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/978678](https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/978678)

---

### Post by 8Kuula on 2012-04-13
\o/ so it does. Now I can get beaten again! :D

---

### Post by saxin on 2012-04-13
Great! Thanks for the work-around! Works great :) Finally possible to get SC2 working again!! :popcorn:

---

### Post by TAWoody on 2012-04-28
AHHHH!! After spending the last 12 hours trying to get RIFT to work with 12.04 I FINALLY found this thread and that command fixed it! Thank God I thought I was going crazy. The game is working perfect now under Wine 1.3. I tried winetricks, crossover games, and playonlinux, and nothing worked until I ran that command. I wonder how I can get it to auto run everytime I start the game...

echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope

---

### Post by fonsopr on 2012-06-19
Hi I just tried that command and the game did log in for me, but after a while it the graphics got all weird, and as soon as I tried to play on bnet, the game crashed. Does anybody know of any developments regarding this problem?

Thanks

---

### Post by Caluca on 2012-07-29
Hey guys,

I am running on Kubuntu 12.04 64 bit (and using Bumblebee 3.0), with Wine 1.5.9 and PlayOnLinux 1.4.1. I have used the built-int StarCraft 2 script (which installs Wine 1.3.27) to install the game from the DVD. The game installs perfectly however I am unable to run the updates. And as such I cannot start playing.

I get to see the StarCraft 2 update window. However it never starts with the updates and a Wine window pops-up stating: "The application couldn't be executed for some reason. Please close all applications and try again".

I have tried the work-around mentioned in this thread. Unfortunately it does not work for me. I have done the following:

echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope
optirun playonlinux

This does not work. On another site: 

[http://www.retrohive.com/2010/08/20/play-starcraft-ii-linux/](http://www.retrohive.com/2010/08/20/play-starcraft-ii-linux/)

they suggest a library override: add and disable mmdevapi in the library tab of WineCFG. However this also did not work for me. Can someone suggest me to try new things that might help my case?

Thanks in advance.

---

### Post by Caluca on 2012-07-29
Maybe this output from the command-line will help:

carlos@nuitari:~$ echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope
[sudo] password for carlos: 
0
carlos@nuitari:~$ optirun playonlinux
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
[main] Message: PlayOnLinux (4.1.3) is starting
[clean_tmp] Message: Cleaning temp directory
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
[install_plugins] Message: Checking plugin: Offline PlayOnLinux...
[Check_OpenGL] Message: 32bits direct rendering is enabled
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
[install_plugins] Message: Checking plugin: Capture...
[install_plugins] Message: Checking plugin: Transgaming Cedega...
[Check_OpenGL] Message: 64bits direct rendering is enabled
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
[install_plugins] Message: Checking plugin: WineImport...
[main] Message: Filesystem is compatible
[install_plugins] Message: Checking plugin: Wine Look...
[install_plugins] Message: Checking plugin: ScreenCap...
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
[install_plugins] Message: Checking plugin: PlayOnLinux Vault...
[maj_check] Message: List is up to date

And after I select StarCraft 2 and press run I get the following output from the command-line:

ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
[POL_System_CheckFS] Message: Checking filesystem for StarCraft II.exe
[POL_Wine] Message: Running wine-1.3.27 StarCraft II.exe (Working directory : /home/carlos/.PlayOnLinux/wineprefix/SC2_WoL/drive_c/Program Files (x86)/StarCraft II)
[POL_Wine] Message: Notice: PlayOnLinux deliberately disables winemenubuilder. See [http://www.playonlinux.com/fr/page-26-Winemenubuilder.html](http://www.playonlinux.com/fr/page-26-Winemenubuilder.html)
[POL_Wine] Message: Wine return: 0
[POL_LoadVar_Device] Message: Gettings GPU informations
[POL_LoadVar_Device] Message: VendorID : 8086
[POL_LoadVar_Device] Message: DeviceID : 0116
[POL_Website_GET] Message: GET [http://www.playonlinux.com/api/s.php?data=ODA4Nn4wMTE2fjB%2BU3RhcmNyYWZ0IElJIFdpbmdzIG9mIExpYmVydHl%2BMH4xfjF%2BfjB%2BVWJ1bnR1%0AIDEyLjA0IExUU34yMDQ4fjEwMDk0MDMxNDg5MzcwODl%2BMX5TdGFyQ3JhZnQgSUkgV2luZ3Mgb2Yg%0ATGliZXJ0eX40LjEuM34xMg%3D%3D](http://www.playonlinux.com/api/s.php?data=ODA4Nn4wMTE2fjB%2BU3RhcmNyYWZ0IElJIFdpbmdzIG9mIExpYmVydHl%2BMH4xfjF%2BfjB%2BVWJ1bnR1%0AIDEyLjA0IExUU34yMDQ4fjEwMDk0MDMxNDg5MzcwODl%2BMX5TdGFyQ3JhZnQgSUkgV2luZ3Mgb2Yg%0ATGliZXJ0eX40LjEuM34xMg%3D%3D)

I hope this helps figuring stuff out.

---

### Post by vexorian on 2012-07-29
Maybe this helps isolate the issue. I got WINE 1.5 from the WineHQ ppa, proprietary nvidia drivers and SC2 works all right, with decent but slightly worse performance. The main difference I can see from other posts is that I copied the SC2 install from a windows partition instead of installing with WINE (Installation is a drag).

Edit: I also run the game from a terminal sesion to make sure no compositing managers or other things use resources. (Top answer from here explains how to do it: [http://askubuntu.com/questions/132285/add-terminal-session-with-network-to-login-in-screen](http://askubuntu.com/questions/132285/add-terminal-session-with-network-to-login-in-screen))

---

### Post by Caluca on 2012-07-30
Thank you for you reply!

It did not occur to me to just copy the StarCraft install from my Windows partition (I am dual-booting Kubuntu 12.04 and Windows 7). I actually managed to run StarCraft this way. However a lot of graphical backgrounds are gone (Jimmy during loading, my avatar, backgrounds when a mission is loading, cinematic only partially shown). The biggest issue is that a mission starts to load, but never finish loading (or it just takes for ever).

---

### Post by vexorian on 2012-07-30
That's quite strange. I can honestly never ran into that issue when just copying the SC2 install. Well, the avatar always happens (It has to redownload BNET cache, and your avatars come from there).

It is possible to copy BNET ache as well, but unless your connection is slow, it is probably not needed. But I guess if your connection was not slow, then you should be able to see the avatars already. My connection is 192kbps and I need some minutes before the portraits and achievements finish downloading. Of course, a WINE bug may be making it download slower.

Jimmy's background though, should really appear and also cinematics. Only explanation i can think of this is that your ubuntu's NTFS compatibility is not working very well and is making an incomplete install. But if your install was incomplete, SC2 would not even load...

Maybe it is a WINE bug making those large backgrounds not appear. Try using winecfg to make SC2 run not on full screen but on a 'virtual' desktop. It tends to remove a couple of graphics glitches in some games.

---

