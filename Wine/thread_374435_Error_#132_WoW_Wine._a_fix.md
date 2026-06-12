---
title: "Error #132 WoW Wine. a fix?"
date: 2007-03-02
forum: Wine
---

### Post by K3nto on 2007-03-02
I am attempting to run WoW with Wine. Each time i run it i get the following:
[IMG]http://img506.imageshack.us/img506/1154/screenshotlw6.png[/IMG]
I have OpenGL enabled with regedit.


The larger box reads:

==============================================================================
World of WarCraft (build 6383)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Mar  2, 2007  2:43:31.298 PM
User:     k3nt
Computer: k3nt-laptop
------------------------------------------------------------------------------


This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:0040F040

The instruction at "0x0040F040" referenced memory at "0x00000000".
The memory could not be "read".


WoWBuild: 6383
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000000  EBX=00000000  ECX=00000000  EDX=00000000  ESI=01117308
EDI=00000001  EBP=0034FD48  ESP=0034FD20  EIP=0040F040  FLG=00010246
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

0040F040 0034FD48 0001:0000E040 C:\Program Files\World of Warcraft\WoW.exe
004705E4 0034FD74 0001:0006F5E4 C:\Program Files\World of Warcraft\WoW.exe
0047066A 0034FD80 0001:0006F66A C:\Program Files\World of Warcraft\WoW.exe
0046FEF3 0034FDBC 0001:0006EEF3 C:\Program Files\World of Warcraft\WoW.exe
00402DFB 0034FDF8 0001:00001DFB C:\Program Files\World of Warcraft\WoW.exe
0042334A 0034FE60 0001:0002234A C:\Program Files\World of Warcraft\WoW.exe
004230F1 0034FE78 0001:000220F1 C:\Program Files\World of Warcraft\WoW.exe
00404B0E 0034FF08 0001:00003B0E C:\Program Files\World of Warcraft\WoW.exe
7B87011E 0034FFE8 0001:0004F11E c:\windows\system32\kernel32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

0040F040 WoW.exe      <unknown symbol>+0 (0x00000000,0x0086B258,0x0034FD68,0x0034FD73)
004705E4 WoW.exe      <unknown symbol>+0 (0x0034FD94,0x0034FDBC,0x0046FEF3,0x0111F9A8)
0047066A WoW.exe      <unknown symbol>+0 (0x0111F9A8,0x0034FDD8,0x0111F9A8,0x00866AB8)
0046FEF3 WoW.exe      <unknown symbol>+0 (0x00402CB8,0x00426BB0,0x00000102,0x0111FC08)
00402DFB WoW.exe      <unknown symbol>+0 (0x00000000,0x0111FC08,0x0042320A,0x7FFDF000)
0042334A WoW.exe      <unknown symbol>+0 (0x00000000,0x00402584,0x00000001,0x00000001)
004230F1 WoW.exe      <unknown symbol>+0 (0x0040A850,0x00400000,0x00000000,0x0011665C)
00404B0E WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B87011E kernel32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7EB15A7              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00350000 - 0x003E0000  C:\Program Files\World of Warcraft\fmod.dll
0x00400000 - 0x00D9C000  C:\Program Files\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B926000  c:\windows\system32\kernel32.dll
0x7BC10000 - 0x7BC94000  c:\windows\system32\ntdll.dll
0x7C8A0000 - 0x7C8AA000  c:\windows\system32\psapi.dll
0x7D030000 - 0x7D06A000  c:\windows\system32\dsound.dll
0x7D070000 - 0x7D0B2000  c:\windows\system32\dbghelp.dll
0x7D0C0000 - 0x7D0C6000  c:\windows\system32\mswsock.dll
0x7D470000 - 0x7D513000  c:\windows\system32\wined3d.dll
0x7D520000 - 0x7D53D000  c:\windows\system32\d3d9.dll
0x7D540000 - 0x7D552000  c:\windows\system32\midimap.dll
0x7D570000 - 0x7D5A6000  c:\windows\system32\wineoss.drv
0x7D5B0000 - 0x7D5D8000  c:\windows\system32\uxtheme.dll
0x7DA60000 - 0x7DADD000  c:\windows\system32\winex11.drv
0x7DBB0000 - 0x7DBC7000  c:\windows\system32\mpr.dll
0x7DBD0000 - 0x7DC0E000  c:\windows\system32\wininet.dll
0x7DC20000 - 0x7DC73000  c:\windows\system32\msvcrt.dll
0x7DC80000 - 0x7DC99000  c:\windows\system32\msacm32.drv
0x7DCA0000 - 0x7DCAD000  c:\windows\system32\lz32.dll
0x7DCB0000 - 0x7DCC6000  c:\windows\system32\version.dll
0x7DCD0000 - 0x7DD54000  c:\windows\system32\winmm.dll
0x7DD60000 - 0x7DD70000  c:\windows\system32\imm32.dll
0x7E7A0000 - 0x7E802000  c:\windows\system32\opengl32.dll
0x7E810000 - 0x7E82E000  c:\windows\system32\ws2_32.dll
0x7E830000 - 0x7E848000  c:\windows\system32\wsock32.dll
0x7E860000 - 0x7E879000  c:\windows\system32\iphlpapi.dll
0x7E890000 - 0x7E8CE000  c:\windows\system32\rpcrt4.dll
0x7E8E0000 - 0x7E967000  c:\windows\system32\ole32.dll
0x7E980000 - 0x7E9BF000  c:\windows\system32\shlwapi.dll
0x7E9D0000 - 0x7EAB3000  c:\windows\system32\shell32.dll
0x7EBB0000 - 0x7EC54000  c:\windows\system32\gdi32.dll
0x7EC70000 - 0x7ED8E000  c:\windows\system32\user32.dll
0x7EDA0000 - 0x7EE4D000  c:\windows\system32\comctl32.dll
0x7EE60000 - 0x7EE93000  c:\windows\system32\advapi32.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 0040F040)

0040F040: 8B 01 BA FF  FE FE 7E 03  D0 83 F0 FF  33 C2 83 C1  ......~.....3...


Stack: 1024 bytes starting at (ESP = 0034FD20)

* = addr  **                                                  *               
0034FD20: D9 35 7A 00  00 00 00 00  00 00 00 00  48 6A 11 01  .5z.........Hj..
0034FD30: 00 00 00 00  49 00 00 00  60 B2 86 00  7A DE 98 76  ....I...`...z..v
0034FD40: 74 FD 34 00  8C 2E 69 00  74 FD 34 00  E4 05 47 00  t.4...i.t.4...G.
0034FD50: 00 00 00 00  58 B2 86 00  68 FD 34 00  73 FD 34 00  ....X...h.4.s.4.
0034FD60: 6C FD 34 00  00 04 00 00  04 00 00 00  03 00 00 00  l.4.............
0034FD70: 00 00 00 00  80 FD 34 00  6A 06 47 00  94 FD 34 00  ......4.j.G...4.
0034FD80: BC FD 34 00  F3 FE 46 00  A8 F9 11 01  D8 FD 34 00  ..4...F.......4.
0034FD90: A8 F9 11 01  B8 6A 86 00  00 00 00 00  FF FF FF FF  .....j..........
0034FDA0: 00 00 00 00  00 04 00 00  00 03 00 00  00 00 00 00  ................
0034FDB0: 00 00 00 00  00 00 40 44  00 00 80 44  F8 FD 34 00  ......@D...D..4.
0034FDC0: FB 2D 40 00  B8 2C 40 00  B0 6B 42 00  02 01 00 00  .-@..,@..kB.....
0034FDD0: 08 FC 11 01  00 00 00 00  A8 F9 11 01  BD FC 11 01  ................
0034FDE0: 00 00 00 00  7F 0E 7F 02  FC FD 34 00  01 00 00 00  ..........4.....
0034FDF0: 07 00 00 00  B8 FC 11 01  60 FE 34 00  4A 33 42 00  ........`.4.J3B.
0034FE00: 00 00 00 00  08 FC 11 01  0A 32 42 00  00 F0 FD 7F  .........2B.....
0034FE10: 00 00 00 00  00 B5 8A 7B  45 6E 67 69  6E 65 20 31  .......{Engine 1
0034FE20: 62 00 11 00  D8 CD 16 00  65 6E 00 00  A1 8B C2 7B  b.......en.....{
0034FE30: A1 8B C2 7B  00 B5 8A 7B  00 F0 FD 7F  5C FE 34 00  ...{...{....\.4.
0034FE40: EA 4B 88 7B  80 20 00 00  00 00 00 00  0B 00 00 00  .K.{. ..........
0034FE50: A4 02 00 00  00 B5 8A 7B  16 25 00 00  78 FE 34 00  .......{.%..x.4.
0034FE60: 78 FE 34 00  F1 30 42 00  00 00 00 00  84 25 40 00  x.4..0B......%@.
0034FE70: 01 00 00 00  01 00 00 00  08 FF 34 00  0E 4B 40 00  ..........4..K@.
0034FE80: 50 A8 40 00  00 00 40 00  00 00 00 00  5C 66 11 00  P.@...@.....\f..
0034FE90: 01 00 00 00  00 F0 FD 7F  00 10 40 00  00 B5 8A 7B  ..........@....{
0034FEA0: 05 00 00 C0  5C 66 11 00  08 FF 34 00  44 00 00 00  ....\f....4.D...
0034FEB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FEC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FED0: 00 00 00 00  00 00 00 00  01 00 00 00  01 00 00 00  ................
0034FEE0: 00 00 00 00  0C 00 00 00  10 00 00 00  14 00 00 00  ................
0034FEF0: 94 FE 34 00  94 F8 34 00  2C FF 34 00  90 C1 40 00  ..4...4.,.4...@.
0034FF00: 88 51 86 00  00 00 00 00  E8 FF 34 00  1E 01 87 7B  .Q........4....{
0034FF10: 00 F0 FD 7F  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FF20: 00 00 00 00  00 00 00 00  00 00 00 00  FF FF FF FF  ................
0034FF30: 00 BF 82 7B  10 06 84 7B  00 B5 8A 7B  00 C0 FD 7F  ...{...{...{....
0034FF40: 00 10 00 00  E8 FF 34 00  10 FF 3E FF  90 00 8D 84  ......4...>.....
0034FF50: 01 00 00 00  03 2A 01 10  00 00 00 00  00 00 00 00  .....*..........
0034FF60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FF70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FF80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FF90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FFA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FFB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FFC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0034FFD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 B5 8A 7B  ...............{
0034FFE0: 00 C0 FD 7F  00 10 00 00  00 00 00 00  A7 15 EB B7  ................
0034FFF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
00350000: 4D 5A 90 00  03 00 00 00  04 00 00 00  FF FF 00 00  MZ..............
00350010: B8 00 00 00  00 00 00 00  40 00 00 00  00 00 00 00  ........@.......
00350020: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
00350030: 00 00 00 00  00 00 00 00  00 00 00 00  F0 00 00 00  ................
00350040: 0E 1F BA 0E  00 B4 09 CD  21 B8 01 4C  CD 21 54 68  ........!..L.!Th
00350050: 69 73 20 70  72 6F 67 72  61 6D 20 63  61 6E 6E 6F  is program canno
00350060: 74 20 62 65  20 72 75 6E  20 69 6E 20  44 4F 53 20  t be run in DOS 
00350070: 6D 6F 64 65  2E 0D 0D 0A  24 00 00 00  00 00 00 00  mode....$.......
00350080: 46 47 7A 03  02 26 14 50  02 26 14 50  02 26 14 50  FGz..&.P.&.P.&.P
00350090: 81 3A 1A 50  05 26 14 50  6D 39 1E 50  07 26 14 50  .:.P.&.Pm9.P.&.P
003500A0: 6D 39 10 50  00 26 14 50  02 26 15 50  9F 26 14 50  m9.P.&.P.&.P.&.P
003500B0: 60 39 07 50  0D 26 14 50  56 05 25 50  04 26 14 50  `9.P.&.PV.%P.&.P
003500C0: 56 05 24 50  52 26 14 50  C5 20 12 50  03 26 14 50  V.$PR&.P. .P.&.P
003500D0: 02 26 14 50  08 26 14 50  FD 06 10 50  03 26 14 50  .&.P.&.P...P.&.P
003500E0: 52 69 63 68  02 26 14 50  00 00 00 00  00 00 00 00  Rich.&.P........
003500F0: 50 45 00 00  4C 01 05 00  2E 18 B2 43  00 00 00 00  PE..L......C....
00350100: 00 00 00 00  E0 00 0E 21  0B 01 06 00  00 C0 03 00  .......!........
00350110: 00 30 05 00  00 00 00 00  05 CD 03 00  00 10 00 00  .0..............


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x1
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3846

Percent memory used:    7
Total physical memory:  2124378112
Free Memory:            1753423872
Page file:              2147483647
Total virtual memory:   2147352575

---

### Post by disturbedite on 2007-03-02
after some reading, i think this may be a warden thing; where it can detect cedega/wine.  so there isn't really a way around it i guess.  here is a link with the same problem you appear to be having:
[http://appdb.winehq.org/commentview.php?iAppId=1922&iVersionId=5109&iThreadId=13989](http://appdb.winehq.org/commentview.php?iAppId=1922&iVersionId=5109&iThreadId=13989)
(the wineappdb is the first place i would have looked).

---

### Post by K3nto on 2007-03-02
Other people seem to be problem free, and WoW is always automatically up-to-date so..

---

### Post by Sammi on 2007-03-02
What on earth makes you think it's warden that's acting up??

---

### Post by hikaricore on 2007-03-02
> **Sammi said:**
> What on earth makes you think it's warden that's acting up??

I don't think that thinking had anything to do with the comment related to warden. :lolflag:

---

### Post by K3nto on 2007-03-02
bump

---

### Post by K3nto on 2007-03-03
I got crossover office pro; should i continue with this or try crossover? If i should swith to crossover, how do i do it?

---

### Post by Sammi on 2007-03-03
To my knowledge "Crossover Office Pro" was version 5 from last year, while the new version 6 from january  this year was renamed to only "CrossOver". There have been many improvements in Wine the last half year so a new version if CrossOver should also be much better.

If you look at this page on the official site, you can see that WoW just became a officially supported game in version 6:
[http://www.codeweavers.com/products/cxoffice/change_log/](http://www.codeweavers.com/products/cxoffice/change_log/)

---

### Post by K3nto on 2007-03-03
ok im getting rid of crossover office pro. in the meantime, do you think i could get some help with wine? i prefer it to crossover.

---

### Post by Sammi on 2007-03-03
I've been posting this link to the community WoW/Wine Howto in about every tread in here that's got something to do with WoW: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

You must have noticed it already.

---

### Post by Ferrat on 2007-04-16
Have you installed WoW as Root?

Is your WoW installation on a NTFS disk or write protected?

Have you tried reinstalling?

---

### Post by khaije1 on 2008-05-26
i was getting the same errors but was able to get it worked out. Im not exactly sure what i did that fixed it, but i ran the installer in fluxbox and it updated like a million times. Once it was fully up to date it worked ok under my normal desktop KDE. 

Lemme know if you are still having troubles and I can check summo stuff. cheers!

---

### Post by LazyEngineer on 2008-06-02
I'm get the same crash as described by the original poster.

I've followed the instructions in the prior link:

OpenGL registry fix
Install the 4 .dll files (that might be from another link - but in any event, that didn't work)

I haven't been able to modify my Config.wtf file as per instructions, because such a file does not yet exist on my machine.  I think you have to successfully run WoW for it to create it first - before you can edit it.

---

### Post by LazyEngineer on 2008-06-05
Problem solved - runs great now.  

The trouble was with my video drivers.  I have a Ubunty 8.04 install on a TX1308nr laptop.  

I then used EnvyNG to update and install my video drivers.  Big mistake.  

I eventually uninstalled EnvyNG, Installed, and then uninstalled the 3rd party drivers thing ( the built in version supported by Ubuntu via add/remove programs).  Rebooted, reinstalled the 3rd party drivers addin thngy - and now WoW runs like a champ.  

I did make the config.wtf changes suggested as well.

---

### Post by Andymeows on 2008-10-11
I got this error and seem to have fixed it.

It was working fine for weeks, and all the sudden it started to crash and gave me this error.
I was going to double check that the permissions of the Config.wtf were correct. Looking in the 'World of Warcraft/WTF' directory, I noticed a file called 'RunOnce.wtf.temp' that wasn't there before. I moved it to 'RunOnce.wtf.temp.backup', and then WOW started again perfectly. I'm guessing that just removing the file would work too, but a move works just as well.

I hope this helps out.

Thanks,
Andy

---

### Post by grimboj on 2008-10-12
I got this error running crossover pro thinking it was better for games. Checked out the latest wine and moved my wow directory from the cxoffice to wine directories & BAM! Works with great fps. I did have to incorporate every other fix on this web site except the sound ones.

---

### Post by theo1000 on 2008-10-18
can some1 plz tell me what to do with this error??? i use the latest drivers for my ati graphic card...and i got 2gb ram...and 200gb hard drive with amd opteron....

i was playing fine until i updated to patvh 3.02 plz help me !!!

---

### Post by harvodan on 2008-12-07
If anyone's still watching this thread...I added a line to /world of warcraft folder/WTF/Config.wtf. This line is as follows. SET gxApi "opengl". Add this to the end of the file, save and rerun WOW. This line sets the video mode to opengl instead of direct3d...Using the command line option --opengl did not work for me, but this file edit did.

---

### Post by Rinnon on 2009-01-03
Another "I don't know if anyone is still following this thread" but if I found my way here... maybe someone else will.

To anyone who has just installed WoW and does not yet HAVE a Config.wtf file, what I did was email my config file from a working copy of WoW on Windows, and place it in the WTF folder. At that point, the game opened up just fine without any crashes. It should also be noted, that I followed the advise of another poster and removed the "Run Once" files that happened to be there as well. Hope that helps someone!

---

### Post by andr3w on 2009-02-02
> **harvodan said:**
> If anyone's still watching this thread...I added a line to /world of warcraft folder/WTF/Config.wtf. This line is as follows. SET gxApi "opengl". Add this to the end of the file, save and rerun WOW. This line sets the video mode to opengl instead of direct3d...Using the command line option --opengl did not work for me, but this file edit did.

I'll be sure to configure that /WTF/Config.wtf to make it work,
when I get it to work, so it makes one. ;)

*wink 
*wink
El O El...

---

### Post by OrbJinzo on 2009-02-03
necro posting? s/

---

### Post by Ferrat on 2009-02-03
if anyone still have this problem try switching WINE between WinXP, Win2000 and Win98/WinME and see it helps

---

### Post by Napoleon85 on 2009-04-29
I just spent two days beating my head against the wall on this same problem and tried all the fixes above but what ended up working for me is as follows:

-Install WINE and WoW as instructed in the common threads
-Launch wow from terminal ```
wine /home/<user>/.wine/c_drive/Program\ Files/World\ of\ Warcraft/wow.exe -opengl
``` replacing <user> with your username
-exit wow
-add ```
SET gxApi "opengl"
```  to your config.wtf file

You should now be able to play WoW without having to launch from terminal without the -opengl switch.

---

### Post by Lawngnome on 2009-06-12
I've tried everything in this thread and a few other things I've found on other sites.  I also tried updating to the nvidia driver version 185 but I'm still unable to get wow to launch successfully for the 1st time.  I'm running 9.04 64bit with an nvidia 9800gt.  Any tips would be appreciated.

---

