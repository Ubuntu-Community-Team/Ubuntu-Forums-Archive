---
title: "tf2 lags on new gaming desktop."
date: 2012-02-27
forum: Wine
---

### Post by ploxkid on 2012-02-27
Hello. I just built my own desktop one week ago. The specifications are:

Intel 2nd gen core i7 2600k @ 3.4ghz
8gb ddr3 ram
1000 gb SATA harddrive
EVGA gtc 560 ti sd 1024 mb
Ubuntu 11.10 64 bit

After testing out minecraft, I knew the cpu was good(1000+ fps). Shortly after, I downloaded Wine, Play on Linux, Steam, and finally Team Fortress 2. I thought it was going to run very fast, but unfortunately it didn't. On the lowest settings, I would say it peaked around 35 fps. On "high" settings, it dropped to a max of 15. By the way, all the settings were not even turned to the max(antialiasing etc.) Before playing, I did go into system settings and look for additional drivers. 2 proprietry drivers showed up from NVIDIA, and I chose the won that said "recommended." I also checked speedtest.net, and it said my download speed was 1.1 mb/s. It also said I had an F rating in the US. Is this the problem? All help would be greatly appreciated.

---

### Post by ploxkid on 2012-02-27
sorry i meant to say gtx not gtc for the GPU.

---

### Post by donkyhotay on 2012-02-27
wine issues should really be posted in [the wine sub-forum](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by sir.sargento on 2012-02-28
Hey mate.. Was having some of the same problems with bad frames and rainbow tiles... One thing to try is to go into Steam and goto Games > TF2 > Launch Options and use the **-dxlevel 80** flag.. This will make the game use DirectX 8 instead of DirectX 9.. This gave me a big improvement in fps. Hope this helps.

Tony

---

### Post by sffvba[e0rt on 2012-02-28
*Thread moved to **Wine**.*


404

---

### Post by Dlambert on 2012-02-28
> **Detailed Configuration for Team Fortress 2**

This section is **Optional** how ever it may greatly improve the stability and frame rate you achieve with TF2.
[LIST]
[*]Make sure sound is configured and working (test in winecfg).
[*]Add "-nointro" option to skip valve video. Some users report this helps to avoid initial crash.
[*]Run TF2 within a Virtual Desktop if you want consistent alt-tabbing. This is done via winecfg -> Graphics -> "Emulate a Virtual Desktop". This size should be the same as your screen resolution.
[*]If you are using a multi-screen setup and a Virtual Desktop you may need to enable the "Automatically capture the mouse in full-screen windows" if the mouse is escaping in your Wine version.
[*]Virtual Desktops can be defined on a per-application basis.
[/LIST]**Running Team Fortress 2**

Team Fortress 2 can be run from Steam or from the command line.
To start TF2 using the command line:
WINEDEBUG=-all wine ~/.wine/drive_c/Program\ Files/Steam/steam.exe -applaunch 440 -nointro**Troubleshooting**

See [Steam Official Troubleshooting]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444") and [Steam Classic Troubleshooting]("http://appdb.winehq.org/appview.php?iVersionId=1554") for any issues related to Steam itself.
**Team Fortress 2 crashes on scoreboard display.**

This bug was introduced in a TF2 update at the start of 2010. Another update ~May 2010 is believed to have fixed it. If you are still experiencing this bug, please comment on bug #21534. There are two potential solutions.
1) The bug can be worked around by playing TF2 at a resolution with less than 1024 pixels of height.
2) A minor edit to the theme of TF2 fixes the crash consistently.
[LIST]
[*]Download and install GCFExplorer from [this forum post]("http://cs.rin.ru/forum/viewtopic.php?t=44110"). (Works with Wine 1.1.43, use at your own risk.)
[*]Extract ClientScheme.res from team fortress 2 content.gcf located in the steamapps folder (~/.wine/drive_c/Program Files/Steam/steamapps). ClientScheme is located in /tf/resource/ within the gcf package.
[*]Place this file in ./steamapps/~youruser~/team fortress 2/tf/resource
[*]Using a text editor open ClientScheme.res and find the subsections "ScoreboardTeamScore" and "HudFontGiant" and change the font type from 'TF2' to 'Verdana' in sub-definitions '4' and '5' for both sections.
[/LIST]Thanks to rasmus.ry for posting this. More information is available in [bug #21534]("http://bugs.winehq.org/show_bug.cgi?id=21534").
**Team Fortress 2 doesn't start at all or crashes on start**

In the most cases, this bug is caused by the Steam In-Game Overlay, to solve Open your winecfg, go to Libraries, add a new Library called **gameoverlayrender.dll** and set to disabled, the Steam In-Game Overlay and screenshot will not work.
Also solved by properly compiled Wine with supported [gcc versions]("http://wiki.winehq.org/GccVersions"").
**Team Fortress 2 crashes after connecting to some servers**

If you can connect to some servers and not others consistently it is most likely caused by the MOTD displayed at the start of any match. This can disabled for all servers via the in-game options.
Options -> Multiplayer -> Advanced -> Disable MOTD (checkbox).
This also happens with some languages has some symbols that Wine can't handle and Team Fortress 2 is a game that is full translated, so, when you connect some servers the engine load this fonts and crash TF2, to solve-it just set language of Steam to english, all the games will be english. This bug happens with portuguese, but, can happen with other languages as well. 
**Team Fortress 2 randomly crashes during game**

Unfortunately there are many reasons for these crashes. Try reducing screen resolution, lover video settings (shadow, textures quality, etc). If the bug is consistent please consider reporting it or filing a bug report if one doesn't already exist.
**TF2 slows down immensely after playing for a short while**

See bug [#23578]("http://bugs.winehq.org/show_bug.cgi?id=23578"). Valve updated their anti-cheat code with the Engineer update and WINE did not handle this well. This bug also affected at least some other games launched from Steam. There is [a fix]("http://source.winehq.org/git/wine.git/?a=commitdiff;h=1a79912a10a6cded54d1f1de5f746bbffec3ffee") for this in git after 21 July 2010. All 1.3.x versions should contain this fix. 1.2 does NOT contain this fix, but the patch applies cleanly to the 1.2 source. 1.2.1 **does** contain this fix, so the most recent stable or the most recent development versions should just both work fine now.
**Mouse randomly jumps around menu or in game.**

This is caused by the new implementation of mouse input in wine, to solve-it, you need to run the game in Windowed mode or into a Virtual Desktop.
Thanks to Frozen Fox and others, this bug has another solution that is download and install a Wine version to before than 1.3.20 (because this is the version that was set the new mouse implementation).
Download [here]("http://sourceforge.net/projects/wine/files/Source/wine-1.3.20.tar.bz2/download") the Source for Wine 1.3.19.
**Team Fortress 2 is Dark and doesn't show the menu correctly.**

This bug is related with the last Team Fortress update and some nvidia video cards, you can solve it by adding **-nod3d9ex** at the launch option into the game, to do that, right click at the game on steam, go to **Proprieties** and click into **Set Launch Options**.
**General Bug Fixes.**
If Team Fortress 2 crash and you can't solve, you can try these steps:
[LIST]
[*]Add "-dxlevel 81" to the TF2's launch options. This option is need for the first run in some machines.
[*]Verify video drivers installed properly. Wine is 32-bit application and requires 32-bit display driver libraries.
[*]Install Steam into separate WINEPREFIX to avoid conflicts.
[*]Set TF2's main executable "hl2.exe" to "Windows 98" version. This is done via winecfg -> "Add application..." -> type hl2.exe in the filename box -> click open -> select hl2.exe in the "Application Settings" list and change "Windows Version" to "Windows 98".
[*]Close Steam, verify that Wine is not running. To force Wine to exit use 'wineserver -k' command. If this doesn't work manually kill all Wine processes **except wineserver**.
[*]Make sure sound is working properly in Wine.
[*]Run TF2 in full-screen mode, window mode might cause crashes. Use a virtual desktop if required.
[*]Check integrity of Steam data files. To really be sure no files are corrupt remove "Program Files/Steam/steamapps/team fortress 2" directory (save configs first) and let Steam rebuild it.
[/LIST][IMG]http://appdb.winehq.org/images/blank.gif[/IMG]

 
 
Just what the AppDB says

---

