---
title: "Cant load WoW / Wine"
date: 2008-04-04
forum: Wine
---

### Post by jayla on 2008-04-04
Hey Guys

I've been able to game thru wine successfully for quite some time now, but have recently run into some issues

I have a dual boot, XP and ubuntu 7.10 machine

World of warcraft was originally installed on the XP side, but I can successfully run it through wine when in windows, from the C:\ drive (I run it from there rather than ~/.wine so whatever OS i boot into I'm using the same game files)

Anyway, this was working perfectly fine until a recent update of the game from Blizzard, being patch 2.4

Now, I can no longer get wine to emulate the game, but strangely enough it still works flawlessly in XP, yet I am using the same files?

Right, the screenshot and wine-error code are below

Screenshot: [http://junk.teamstag.co.uk/wow/wowerrors.jpg](http://junk.teamstag.co.uk/wow/wowerrors.jpg)

Errors:

```
World of WarCraft (build 8125)

Exe:      C:\Program Files\WoW\Wow.exe
Time:     Apr  4, 2008 11:46:00.117 PM
User:     jimmy
Computer: nevada
------------------------------------------------------------------------------

This application has encountered a critical error:

File not found

Program:	C:\Program Files\WoW\Wow.exe
File:	.\Client.cpp
Line:	2840

file: signaturefile


WoWBuild: 8125
------------------------------------------------------------------------------

----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 1/1 threads...

--- Thread ID: 9 [Current Thread] ---
00552830 0033F6D4 0001:00151830 C:\Program Files\WoW\Wow.exe
00552854 0033F6E8 0001:00151854 C:\Program Files\WoW\Wow.exe
00402388 0033F7A4 0001:00001388 C:\Program Files\WoW\Wow.exe
004054F8 0033FC14 0001:000044F8 C:\Program Files\WoW\Wow.exe
00405EC3 0033FE5C 0001:00004EC3 C:\Program Files\WoW\Wow.exe
004061D6 0033FE6C 0001:000051D6 C:\Program Files\WoW\Wow.exe
00406228 0033FF08 0001:00005228 C:\Program Files\WoW\Wow.exe
7B86F7F9 0033FFE8 0001:0004E7F9 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 1/1 threads...

--- Thread ID: 9 [Current Thread] ---
00552830 Wow.exe      <unknown symbol>+0 (0x00000002,0x0088A030,0x0033F6F8,0x0033F7A4)
00552854 Wow.exe      <unknown symbol>+0 (0x00000002,0x0088A030,0x0088A04C,0x00000000)
00402388 Wow.exe      <unknown symbol>+0 (0x014D7F68,0x014D8988,0x00000A28,0x014D8408)
004054F8 Wow.exe      <unknown symbol>+0 (0x00000A28,0x00000002,0x00000001,0x74726574)
00405EC3 Wow.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x0033FF08,0x00406228)
004061D6 Wow.exe      <unknown symbol>+0 (0x00409E09,0x00400000,0x00000000,0x00111A25)
00406228 Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B86F7F9 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7E3B1CF              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00EB9000  C:\Program Files\WoW\Wow.exe
0x10000000 - 0x10069000  C:\Program Files\WoW\DivxDecoder.dll
0x7B820000 - 0x7B926000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA2000  C:\windows\system32\ntdll.dll
0x7CB70000 - 0x7CBA9000  C:\windows\system32\dbghelp.dll
0x7CF80000 - 0x7CF87000  C:\windows\system32\psapi.dll
0x7CFB0000 - 0x7CFDD000  C:\windows\system32\uxtheme.dll
0x7D550000 - 0x7D557000  C:\windows\system32\midimap.dll
0x7D560000 - 0x7D56E000  C:\windows\system32\msacm32.drv
0x7D650000 - 0x7D679000  C:\windows\system32\winealsa.drv
0x7D6C0000 - 0x7D736000  C:\windows\system32\winex11.drv
0x7D880000 - 0x7D88A000  C:\windows\system32\lz32.dll
0x7D890000 - 0x7D8A3000  C:\windows\system32\version.dll
0x7D8B0000 - 0x7D901000  C:\windows\system32\rpcrt4.dll
0x7D910000 - 0x7D9A1000  C:\windows\system32\ole32.dll
0x7D9D0000 - 0x7D9E2000  C:\windows\system32\iphlpapi.dll
0x7D9F0000 - 0x7DA0D000  C:\windows\system32\ws2_32.dll
0x7DA10000 - 0x7DA33000  C:\windows\system32\msacm32.dll
0x7DA40000 - 0x7DAF2000  C:\windows\system32\comctl32.dll
0x7DB00000 - 0x7DBF8000  C:\windows\system32\shell32.dll
0x7DC00000 - 0x7DC4E000  C:\windows\system32\shlwapi.dll
0x7DC50000 - 0x7DC6F000  C:\windows\system32\mpr.dll
0x7DC80000 - 0x7DCBB000  C:\windows\system32\wininet.dll
0x7DCC0000 - 0x7DCD8000  C:\windows\system32\imm32.dll
0x7DCF0000 - 0x7DDCF000  C:\windows\system32\wined3d.dll
0x7DDE0000 - 0x7DDFF000  C:\windows\system32\d3d9.dll
0x7EB50000 - 0x7EBC0000  C:\windows\system32\opengl32.dll
0x7EBD0000 - 0x7EC0A000  C:\windows\system32\advapi32.dll
0x7EC20000 - 0x7ECA2000  C:\windows\system32\gdi32.dll
0x7ECC0000 - 0x7EDDE000  C:\windows\system32\user32.dll
0x7EDF0000 - 0x7EE6A000  C:\windows\system32\winmm.dll


----------------------------------------
    Memory Dump
----------------------------------------

Stack: 1024 bytes starting at (ESP = 0033E0DC)

* = addr                                         **                       *   
0033E0D0: 01 00 6E 00  BC A5 55 00  DC E0 33 00  C0 20 00 00  ..n...U...3.. ..
0033E0E0: 00 00 00 00  BC A5 55 00  DC E0 33 00  F0 E0 33 00  ......U...3...3.
0033E0F0: 8C EE 33 00  32 14 55 00  01 00 6E 00  D0 10 55 00  ..3.2.U...n...U.
0033E100: C0 20 00 00  03 00 00 00  00 00 00 00  F4 20 55 00  . ........... U.
0033E110: 3C A0 88 00  01 01 00 00  18 0B 00 00  D8 07 04 00  <...............
0033E120: 05 00 04 00  17 00 2E 00  00 00 75 00  00 00 00 00  ..........u.....
0033E130: AC EE 33 00  3C A0 88 00  00 00 00 00  88 0B 8A 00  ..3.<...........
0033E140: 20 00 00 00  00 67 66 E1  E7 94 C8 01  00 97 11 A6   ....gf.........
0033E150: A5 96 C8 01  00 67 66 E1  E7 94 C8 01  00 00 00 00  .....gf.........
0033E160: 90 12 7E 00  00 00 00 00  00 00 00 00  57 6F 77 2E  ..~.........Wow.
0033E170: 65 78 65 00  00 00 00 00  00 00 00 00  00 00 00 00  exe.............
0033E180: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E190: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E1A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E1B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E1C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E1D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E1E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E1F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E200: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E210: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E220: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E230: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E240: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E250: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E260: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E270: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E280: 20 E3 33 00  82 9B C5 7B  48 E3 33 00  01 00 00 00   .3....{H.3.....
0033E290: 00 00 00 00  C8 E2 33 00  02 00 00 00  00 00 00 00  ......3.........
0033E2A0: 00 00 00 00  F4 6F E0 B7  00 00 00 00  40 81 E0 B7  .....o......@...
0033E2B0: C1 A6 D2 B7  C8 E2 33 00  C0 E2 33 00  1C 10 00 00  ......3...3.....
0033E2C0: 02 00 40 00  C8 E2 33 00  68 00 11 00  58 01 00 00  ..@...3.h...X...
0033E2D0: 20 E3 33 00  EF 12 C4 7B  01 00 00 00  5C 45 D0 00   .3....{....\E..
0033E2E0: 00 81 4D 01  00 E3 33 00  38 99 01 00  C8 66 13 00  ..M...3.8....f..
0033E2F0: B8 66 13 00  FC 6A C8 7B  58 65 13 00  14 00 11 00  .f...j.{Xe......
0033E300: 20 E3 33 00  E3 00 C4 7B  48 99 0E 00  C8 66 13 00   .3....{H....f..
0033E310: 57 C7 C3 7B  A0 C8 8A 7B  B4 E3 33 00  B4 E3 33 00  W..{...{..3...3.
0033E320: 80 E3 33 00  D8 30 84 7B  BC 20 00 00  00 00 00 00  ..3..0.{. ......
0033E330: 00 00 00 00  B4 E3 33 00  B4 E3 33 00  F4 E4 33 00  ......3...3...3.
0033E340: 00 10 00 00  60 E3 33 00  00 00 00 00  06 00 00 00  ....`.3.........
0033E350: 70 E3 33 00  B4 E3 33 00  00 00 00 00  60 E3 33 00  p.3...3.....`.3.
0033E360: 00 00 00 00  D0 44 D0 00  A0 82 4D 01  05 00 00 00  .....D....M.....
0033E370: 98 E3 33 00  B1 E6 54 00  A0 82 4D 01  05 00 00 00  ..3...T...M.....
0033E380: 54 68 69 73  20 61 70 70  6C 69 63 61  74 69 6F 6E  This application
0033E390: 20 68 61 73  20 65 6E 63  6F 75 6E 74  65 72 65 64   has encountered
0033E3A0: 20 61 20 63  72 69 74 69  63 61 6C 20  65 72 72 6F   a critical erro
0033E3B0: 72 3A 0A 0A  46 69 6C 65  20 6E 6F 74  20 66 6F 75  r:..File not fou
0033E3C0: 6E 64 0D 0A  0A 50 72 6F  67 72 61 6D  3A 09 43 3A  nd...Program:.C:
0033E3D0: 5C 50 72 6F  67 72 61 6D  20 46 69 6C  65 73 5C 57  \Program Files\W
0033E3E0: 6F 57 5C 57  6F 77 2E 65  78 65 0A 46  69 6C 65 3A  oW\Wow.exe.File:
0033E3F0: 09 2E 5C 43  6C 69 65 6E  74 2E 63 70  70 0A 4C 69  ..\Client.cpp.Li
0033E400: 6E 65 3A 09  32 38 34 30  0A 0A 66 69  6C 65 3A 20  ne:.2840..file: 
0033E410: 73 69 67 6E  61 74 75 72  65 66 69 6C  65 0A 0A 00  signaturefile...
0033E420: 30 70 4D 01  00 00 00 00  CC 71 4D 01  00 00 00 00  0pM......qM.....
0033E430: 78 82 4D 01  00 E4 33 00  20 E4 33 00  F8 F4 33 00  x.M...3. .3...3.
0033E440: 10 55 87 00  00 00 00 00  CC 71 4D 01  B3 6B 57 00  .U.......qM..kW.
0033E450: CC 71 4D 01  30 0C D1 00  30 0C D1 00  C8 E4 33 00  .qM.0...0.....3.
0033E460: 63 09 57 00  C8 E4 33 00  08 1C 30 01  30 0C D1 00  c.W...3...0.0...
0033E470: 3C 0C D1 00  00 00 00 00  30 0C D1 00  08 7E 4D 01  <.......0....~M.
0033E480: EF 2E C3 7B  08 1C 30 01  3C 0C D1 00  46 3A 58 00  ...{..0.<...F:X.
0033E490: 3C 0C D1 00  CB 06 CA A6  00 00 00 00  08 1C 30 01  <.............0.
0033E4A0: 08 1C 30 01  E8 EA 33 00  30 0C D1 00  08 7E 4D 01  ..0...3.0....~M.
0033E4B0: 4A 3F 58 00  28 01 30 01  38 E9 33 00  C8 65 87 00  J?X.(.0.8.3..e..
0033E4C0: 38 E9 33 00  9B 65 87 00  FF FF FF FF  8D 52 58 00  8.3..e.......RX.
0033E4D0: 87 06 CA A6  00 00 00 00  08 1C 30 01  08 1C 30 01  ..........0...0.


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x1
Number of Processors:   1
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     12034

Percent memory used:    28
Total physical memory:  1592107008
Free Memory:            1130594304
Page file:              2595516416
Total virtual memory:   2147352575

```

I understand this isn't the Blizzard tech support, and I'm most likely shouting out to a rather small community in regards to this situation, but I'd really appreciate any advice you can give me

For the record, I'm using a fully up to date ubuntu 7.10 and the latest version of wine, i believe its .58

I have changed nothing to XP/linux around the time of failure, I have not installed/removed any software or altered any settings, the only thing that has changed is getting the latest world of warcraft patch, but like I say it works fine when I boot to XP

Please help, booting into windows hurts more each time i do it... :P

Thanks

EDIT: also, from googling I have seen this issue can occur in windows (luckily it hasnt for me, otherwise me=cold turkey!)

Its rumoured the cause is due to a system restore, yet I havent done one of those? I've also been advised to have wine simulate a windows boot, but I have no idea how to achieve that, and google hasn't helped much either. :S

---

### Post by jayla on 2008-04-05
I have tried absolutely everything I can think of, bar a complete ubuntu reinstall, and its now getting to that stage where I'm tempted to just scrap ubuntu an head back to an OS where everything just works out of the box

but no...I've gruelled a 6 month period of linux usage, and I want to stay


I have reinstalled WoW completely, 

I have tried the last 10 versions of wine

I have tried running it from C:\, and copying to /.wine, but neither work

I have run wineboot to simulate a boot

I have tried every environment on winecfg

I have posted on about 4 forums, not had a single post with advice

I have spent several nights trawling google, no results


someone please help, I want to solve this, and write up a good solution so it helps people in the future

Regards

---

### Post by rigol on 2008-04-06
Well... in your first post, it says in the output:
```
File not found

Program:	C:\Program Files\WoW\Wow.exe
File:	.\Client.cpp
```

Did you check that? Seems like the Client.cpp file is missing?

In your case, I would try deisntalling wine completely, then reinstalling the current version, doing a clean install of WoW with all the patches in Win, copying the WoW folder into the appropriate wine directory (eg WoW was installed in C.\Program Files\World of Warcraft, you would copy it to /home/yourusername/.wine/drive_c/Program\ FIles/World\ of\ Warcraft), setting "windows 2000" in winecfg.

I know you already did that. But without making sure you are working with a clean wine and WoW it's difficult to give good advice.

I'm sure we will get your WoW to run, it can't be that difficult. :)

---

### Post by jayla on 2008-04-06
Hi Rigol

First off, thanks for taking the time to reply

I appreciate your advice. I have done a total fresh reinstall of both WoW and Wine recently, it took well over a day so I'd rather not have to do that again!

in regards to that client.cpp file, I've done a search on ubuntu and on my XP boots, and neither can find that file, yet I can load the game fine if I boot into windows? And considering I'm trying to wine the same files as what windows is using, it seems rather odd that I'm having this issue on ubuntu boot

Is there anything else you can recommend?

Kind Regards

---

### Post by Worf on 2008-04-06
Well, i can tell i get the exactely same error, and i still could not find a solution.
I think it started with patch 2.4, only that i first had the error eaven in Windows, but it dissapeared after reinstalling WoW (something i don't want do do again)

i also [posted on the Blizzard Forums](http://forums.wow-europe.com/thread.html?topicId=3405053227&postId=34047073885&sid=1#0), but we all know how much that usually helps.

---

### Post by inborrable on 2008-04-06
Hi! I have the same problem dunno how to fix it, it runs for me in Windows but not in linux

---

### Post by jayla on 2008-04-06
seems like we got a right little crowd starting to form!

/begs for help :P

---

### Post by Trilian-NE on 2008-04-06
hey

i having the same problem with wine and couldnt find the solution.
but i got the idea wine is not the only "winemulator" so i made a serarch if cedega users got the same problem with newsest wow
it turns out they got it too but they have a solution

[http://www.cedega.com/forum/viewtopic.php?p=53753&sid=07fe17831c25cd3d06d8399c93945a86]("http://www.cedega.com/forum/viewtopic.php?p=53753&sid=07fe17831c25cd3d06d8399c93945a86")

if i understand right this problem is related to GLSL so they advice to turn it off
maybe if thats possible in wine that could help...

ps.:
i dont realy know whats the diffrence between wine and cedega so sry if i said something totaly unrelevant :)

---

### Post by Jovec on 2008-04-06
You could try forcing WoW to repatch/repair (see below).  However, since it works in Windows and not in Linux, my guess would be that you obviously ran the 2.4 patch in one OS and that patch made some changes outside of the WoW directory (registry perhaps) that the other OS can't recognize. You might try comparing the Blizzard/WoW registry entries in both OSes for differences.  You might also try downloading the 2.4 complete patch and running it from Linux.

```
1. Open your World of Warcraft directory (This is commonly located at C:\Program files\World of Warcraft)
2. Open the folder called "Data"
3. Delete the Patch.MPQ file
4. Run the repair.exe utility found in the World of Warcraft directory
5. Click the button "Reset and Check Files"
6. The repair utility will say, "World of Warcraft is seriously damaged and will need to be reverted to an earlier version. After it has been reverted you may need to patch up to continue playing."
7. Once the repair utility has completed, you will need to reapply the patch to enter the game. Patch Mirrors can be found at:
http://us.blizzard.com/support/article.xml?articleId=21079
```

---

### Post by jayla on 2008-04-07
> **Jovec said:**
> my guess would be that you obviously ran the 2.4 patch in one OS and that patch made some changes outside of the WoW directory (registry perhaps) that the other OS can't recognize. 

Thanks Jovec

I will give that a shot tonight

If so, it would make sense that the registries are different, and my assumption is that there are no easy ways to track this down? ie where in windows these wow entries could be?

---

### Post by russ18uk on 2008-04-07
From my experience of keeping WoW up-to-date on 12 PCs you shouldn't have to manually patch each system, so registry settings *shouldn't* be an issue; however, I did once have an issue updating to 2.01 I think. The patch just before BC launched with the additional talents etc when I had to patch on each machine. If you use an MSI repackager, or a program that will tell you differences between the system before and after an install, you could then locate any changed registry settings and export them and reimport to Wine after some changes (if not HKLM f.x).

---

### Post by jayla on 2008-04-07
> **russ18uk said:**
> From my experience of keeping WoW up-to-date on 12 PCs you shouldn't have to manually patch each system, so registry settings *shouldn't* be an issue; however, I did once have an issue updating to 2.01 I think. The patch just before BC launched with the additional talents etc when I had to patch on each machine. If you use an MSI repackager, or a program that will tell you differences between the system before and after an install, you could then locate any changed registry settings and export them and reimport to Wine after some changes (if not HKLM f.x).

Hi Russ

Is there any chance you can elaborate on this? or at least some guidance as to how to check

Regards

---

### Post by Trilian-NE on 2008-04-07
Russ is this means you got a working wow under wine?
that case would gief me new hope :P

btw jayla i gess Jovecs solution didnt work?

---

### Post by russ18uk on 2008-04-07
Umm, I'm referring how I used to do it with Windows Apps to redeploy via GPOs on a server. What I was meaning was that you could use a snapshot program which compares the system before and after an installation and tells you what has changed. I used ezMSI so if you could completely uninstall, snapshot, install WoW fully in Windows, find any changes to the Registry, export those changes, and import them into WINE's registry and that should remove any possibility of it being a registry issue. Should say you do this in Windows if possible obviously :P

I'm still quite new to Linux and particularly Wine but I have a 2.3 install at home that I haven't played since January and will download the 2.4 patch on Gutsy and see if I can get it working :)

Just don't want to get hooked again just yet :lolflag:

---

### Post by Jovec on 2008-04-07
I would suggest forcing a repatch as described in my code block from my previous post or try downloading the complete 2.4 wow patch from a mirror and manually rerunning it from one OS then the other if needed.  If you have any sort of broadband the download isn't that bad (500-600MB?).

---

### Post by jayla on 2008-04-07
> **Trilian-NE said:**
> 
btw jayla i gess Jovecs solution didnt work?

Its quite a large download and I have 1meg connection :P

I'll set it up overnight an report back sometime tomorrow :D

cheers

---

### Post by jayla on 2008-04-07
Well I like to say any progress is good progress

I followed what Jovec suggested 

firstly make sure u have the wow installation under ~/.wine.....

delete patch.mpq

then try to wine the game

surprise surprise, it loads up and u get the log screen, no more wow error cant find client.cpp

although, by deleting that mpq, it takes you back to version 2.0 of the game, aka october 2006.

currently patching over 1.2 gig of updates

My hope are high!

---

### Post by Trilian-NE on 2008-04-07
yea i got the same results so far
hope its not only loads up because its a previus game version.. got baad feelings about it..
i searched the registry in windoz for Blizzard and there are some entries there. i copied the stuff to wines regedit but its nothing better...
lets hope repatch will help..

---

### Post by rickggreen on 2008-04-07
I am running the 2.4 patch of WOW with Ubuntu 8.04 (beta) and Wine 58. I had the same problem until I tweaked the dpi setting in Wine. Now runs flawlessly again, and I can change screen setting in WOW without crashing.

---

### Post by jayla on 2008-04-08
well, good news I must admit! :D

Heres what I did, for anyones future reference

Firstly, get WoW working in windows fine.

next, copy those files, basically everything under C:\Program Files\World of Warcraft\ 

into your wine directory, ~/.wine/drive_c/program files/WoW

(this way we keep a working copy for safety :P)

try to wine the copy, it will most likely fail and give the same error that this post is based on

go into the ~/.wine and delete the "Patch.mpq" file from WoW\Data

wine wow.exe

Hey presto it loads the login screen, but your back to version 2.0(october 2006) of the game so you need to patch it to 2.4

(Its not all bad tho, as the 2.0 > 2.4 is all one download, so u can leave it unnattended overnight, its 1.1gb)

Once your patched up, it will load as normal

Good Luck!

---

### Post by Trilian-NE on 2008-04-09
tnx for the soulutin jayla and Jovec
i still working on it because my system always crasses after 20mins download but its a local problem i gess (wifi card dieing)

i thinkin about upgrading to Hardy so rickggreen could u tell more about that dpi tweak?

---

### Post by Worf on 2008-04-09
I now reinstalled the game (again), this time in Linux, and i got different md5sums for the game files. And the error went away.

I assume that something is broken with the blizzard updater and one has to reinstall until things work.

---

### Post by Trilian-NE on 2008-04-09
finally i made it!

i upgraded to hardy with latest wine, copied the files from windows partition to wines drive_c and it worked without any errors (even in directx mode but there was some problems with multitexturing) i didnt need any repatch or repair or dpi tweak (?) just the files from windows... (ofc i done the opengl registry tweak but it was ok without that too)
still i dont know what made the errors. its just strange...

Hardy Heron ubercool btw :guitar:

---

### Post by ReapingOne on 2008-08-04
ok this is my first time posting here but i see alot of people are having this problem and there is a much faster fix for it. linux is case sensitive and after copying wow from my windows partition to my linux partition i had the same problem, all you have to do is rename all the .mpq files so that .mpq is all capitals (ie. rename patch.mpq to patch.MPQ). this has worked for me everytime, hope this helps

---

### Post by boglio on 2008-09-18
> **ReapingOne said:**
> ok this is my first time posting here but i see alot of people are having this problem and there is a much faster fix for it. linux is case sensitive and after copying wow from my windows partition to my linux partition i had the same problem, all you have to do is rename all the .mpq files so that .mpq is all capitals (ie. rename patch.mpq to patch.MPQ). this has worked for me everytime, hope this helps


Works like a charm, thank you very much!

---

