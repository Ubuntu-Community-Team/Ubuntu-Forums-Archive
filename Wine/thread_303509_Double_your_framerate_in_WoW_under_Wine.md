---
title: "Double your framerate in WoW under Wine"
date: 2006-11-20
forum: Wine
---

### Post by z00s on 2006-11-20
I found some tweaks regarding, specifically, WoW under Wine from: [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

Tweak #1 has proven to work for me. Tweak #2 has proven NOT to work for me.
 

[SIZE=4]Tweak #1[/SIZE]
 
The following from [http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606) , a simple registry edit for Wine that dramatically increases the framerate in game for both ATi and nVidia users (reportedly, I have only verified with nVidia using Wine 0.9.22): 
 
```
regedit
```
 
Find HKEY_CURRENT_USER\Software\Wine\ 
 
Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder 
 
Click right on the wine folder and select [NEW] then [KEY] 
 
Replace the text "New Key #1" with OpenGL 
 
Click right in the right hand pane and select [NEW] then [String Value] 
 
Replace "New Value #1" with "DisabledExtensions" 
(Notice it's case sensitive) 
 
Then double click anywhere on the line, a dialog box will open. 
In the value field type "GL_ARB_vertex_buffer_object" (without the quotes). 
 
Here's what regedit should look like once you have finished adding this new key and it's value. 
 
[http://appdb.winehq.org/appimage.php?iId=4640](http://appdb.winehq.org/appimage.php?iId=4640)


[SIZE=4]Tweak #2[/SIZE]
 
Another tweak you can use from [http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606) , the idea is to create a script which will allow you to launch WoW on a dedicated X server, and will give you a little boost of FPS. 
 
```
nano -w ~/launch-wow.sh
``` 
 
Put this content in your newly created file: ~/launch-wow.sh
 
```
#!/bin/sh
 
 X :3 -ac &   # Launches a new X session on display 3 
 cd "~/.wine/drive_c/Program Files/World of Warcraft"   # Goto WoW dir 
 sleep 2   # Forces the system to have a break for 2 seconds 
 DISPLAY=:3 /usr/X11R6/bin/wine WoW.exe -opengl   # Launches WoW
```
 
 
Press Ctrl+o then Ctrl+w in order to save your file & quit nano. 
 
Don't forget to make your script executable : 
 
```
chmod +x ~/launch-wow.sh
``` 
 
Using a nVidia GeForce4 420 Go 32MB on a Toshiba Laptop, I managed to get a performance boost of about 10-15 FPS (I had 10-15 before doing this and now I have about 25-30 FPS, 15-20 in Orgrimmar).

---

### Post by z00s on 2006-11-20
Updated.

---

### Post by chadk on 2006-11-20
I think the boost from both of these is simply that they turn on opengl... which I didn't even think was a problem in wine 9.25?

---

### Post by z00s on 2006-11-20
The first tweak appears on Wine's site: [http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)
for version 0.9.25. If it wasn't for version 0.9.25 then I might agree, but until I can test them myself tonight I won't know for sure.

The second tweak should work regardless of what version of Wine you're running.

- Z

---

### Post by reiki on 2006-11-20
Tweak #1 works under at LEAST wine 0.9.22, 0.9.24, and 0.9.25. The LOCATION of the registry edit has changed for 0.9.25 and that is reflected on that link you posted 
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

I have used that one personally and even though it was originally intended to help solve a corrupted text issue with ATI cards, it was apparently discovered that it also significantly improves the frame rates on nVidia cards as well. I have an nVidia card and I can confirm that it does in fact just about double your frame rate in WoW. Depending on where you are in the game it can go more than double or a little less than double. I have seen 80fps while standing at the Great Forge in Ironforge at the flight path there. Outside with more stuff to draw I am typically at around 55-60fps. I have an nVidia 7300GT with 512MB so it's not as fast as some of the newer cards, but it does fine in WoW for me.

That Tweak #2 I had not seen. I may try that one later tonight.

---

### Post by scotty2hott2k on 2006-11-20
worked a treat, thank you, fps has gone up loads :)

---

### Post by z00s on 2006-11-20
Confirmed: Tweak #1 works - truly did double my framerate.

Tweak #2 does NOT work, for me anyway.

- Z

---

### Post by Drezliok on 2006-11-20
Tweak 1 worked for me, I can not have my shaders on with out it going all wacked.

As for tweak 2, I won't try that one. I found one like it on the internet.

---

### Post by erythro on 2006-11-21
Hmm. I tried both tweaks with a fresh install of Ubuntu 6.10 and the latest Wine. Tweak #1 did improve my FPS by quite a bit. Tweak #2 did nothing for FPS, but it did seem to fix a glitch I was having with autorun. I have MOUSE4 bound to Autorun. Before tweak #2, any further keyboard input (such as direction changes) while autorunning would cancel the autorun. That got mighty annoying let me tell you. Now it seems to be fixed. So yay, thanks a lot.

---

### Post by Drezliok on 2006-11-21
```

drezliok@TuxEater:~$ wow
X: user not authorized to run the X server, aborting.
cd: 5: can't cd to ~/.wine/drive_c/Program Files/World of Warcraft
wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found

```

Maybe whit link would help but I don't understand it.

[http://www.winehq.com/pipermail/wine-users/2006-July/022814.html](http://www.winehq.com/pipermail/wine-users/2006-July/022814.html)

---

### Post by z00s on 2006-11-21
> **Drezliok said:**
> ```

drezliok@TuxEater:~$ wow
X: user not authorized to run the X server, aborting.
cd: 5: can't cd to ~/.wine/drive_c/Program Files/World of Warcraft
wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found

```

Maybe whit link would help but I don't understand it.

[http://www.winehq.com/pipermail/wine-users/2006-July/022814.html](http://www.winehq.com/pipermail/wine-users/2006-July/022814.html)

Change the tilde to /home/"yourusername"/drive_c/Program Files/World of Warcraft

Then run the script with sudo.

- Z

---

### Post by Drezliok on 2006-11-21
could sudo be added to the script?

And now I get a blank Xserver.
I can switch back with crtl+alt+f keys.

Also```

drezliok@TuxEater:~$ wow
X: user not authorized to run the X server, aborting.
cd: 5: can't cd to /home/drezliok/.wine/drive_c/Program Files/World Of Warcraft
wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found

```
I ran the script with out the sudo to make sure I got a error that I could get to.

---

### Post by Drezliok on 2006-11-21
Ok I got it to work for me but I have to use crtl+alt+f7 keystroke to get back into my other Xserver. the game ends up on f9.

Here is my script edited to work for me.
```

#!/bin/sh

 X :3 -ac &   # Launches a new X session on display 3 
 sleep 2   # Forces the system to have a break for 2 seconds 
 DISPLAY=:3 /usr/X11R6/bin/wine ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft/WoW.exe -opengl   # Launches WoW

```

I took out the change of directory and told it where to go at the display line.

ALSO
this fixes a resolution issue I have with wine and games. Wine would all ways throw me into 1600X1200. And I hate that.

Now I would like to know how to add sudo to the script.
Anyone know how I can kill the Xserver when I'm done playing?

---

### Post by lckeeper1 on 2006-11-21
Hey guys,

I tried the first tweak, yet I haven't seen any increase in framerate. In fact, I have about 18-22 fps. I have a pretty decent rig:

AMD Athon64 3800
NVIDIA 6600 
1GB RAM
250 GB harddrive

So I feel like I have decent enough hardware to run at a better speed than what I get.

I'm currently using Wine 0.9.22, and have no problems what so ever. 

Just wondering if my framerate should be where it's at, or maybe higher.

EDIT: Sorry, I'm running Dapper, as well.

---

### Post by scotty2hott2k on 2006-11-22
try using the latest wine 0.9.25 (not sure but it may help)

---

### Post by z00s on 2006-11-22
1. Make sure you're using 0.9.25.
2. Make sure you're using OpenGL (simplest method is to open wow with: wine WoW.exe -opengl)
3. Make sure you're using tweak #1.
4. Make sure your color depth is set to 24 bits.
5. Try tweak #2.

I've got roughly the same setup as you and I'm getting between 40-100 FPS with the exception of 25 in Grom'gol.

- Z

---

### Post by lckeeper1 on 2006-11-22
Thanks Z!

Really seemed to help. Now when I'm indoors, I get around 70fps! Much better!

---

### Post by Drezliok on 2006-11-22
A work around for the sudo problem is making a launcher to the script.
You will need the launcher to run it in a terminal, so it can prompt for the password.

---

### Post by erythro on 2006-11-23
> **Drezliok said:**
> A work around for the sudo problem is making a launcher to the script.
You will need the launcher to run it in a terminal, so it can prompt for the password.

Or, you can allow users to run commands through sudo without asking for a password.

```
$ sudo visudo
```

add the following line to the file:
```
username ALL=NOPASSWD: /usr/bin/X
```

Where "username" is your username. Duh. This line allows "username" to run /usr/bin/X (which is the command that requires root privileges in the wow launcher script) without a password. This will allow you to run the launcher without opening a terminal.

Now, I'm no expert. For all I know, this is a major security hole. So use at your own risk. :P

---

### Post by Drezliok on 2006-11-23
I think I'll leave it as it is.

---

### Post by Ferrat on 2006-11-24
> **chadk said:**
> I think the boost from both of these is simply that they turn on opengl... which I didn't even think was a problem in wine 9.25?

Now the RegEdit tweak (tweak 1) is to tell the program not to even try running with that extention reducing the load and the leaks and garbage that pulls down the FPS

---

### Post by BitTorrentBuddha on 2006-11-24
> **z00s said:**
> 1. Make sure you're using 0.9.25.
2. Make sure you're using OpenGL (simplest method is to open wow with: wine WoW.exe -opengl)
3. Make sure you're using tweak #1.
4. Make sure your color depth is set to 24 bits.
5. Try tweak #2.

I've got roughly the same setup as you and I'm getting between 40-100 FPS with the exception of 25 in Grom'gol.

- Z

I followed all these steps (not sure on #4, but I think I did) and I'm only getting ~20fps indoors, is that low or am I just asking for performance my PC doesn't have: Celeron (2 ghz), GeForce 6200, and a gig of ram.

---

### Post by kragen on 2006-12-06
Your best bet is to try it on windows and see. Your CPU does seem a little slow - I was running wow with a Athlon XP 1900+ a while back (under windows) and had issues. 

BTW, the above works well, it seems to give a significant FPS boost, before it was unplayable, now I almost have better performance than I had with windows! (perhaps there was another problem with my configuration that I fixed at the same time or something).

I had to change the script slightly, the "cd" command in mine reads:

```
cd ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft   # Goto WoW dir 
```

The other one gave me an error, so I removed the quotes and used backslashes to sort out the spaces.

Also, if I run the script once, it works fine, but after closing wow, re-running the script doesn't work properly - this is probably just me not understanding how x servers work... It gives me a message about the server already running, comes up with some stuff which indicates that wow is probably starting up, but switching (with <Ctr><Alt><F9>) just gives a blank screen.

---

### Post by chadk on 2006-12-07
Tweak #2 didn't do anything for me.  But I'm not sure I'd notice anyway, I run full graphics options and it's smooth either way, in it's own X or in my default X.

---

### Post by Drezliok on 2006-12-07
> **chadk said:**
> Tweak #2 didn't do anything for me.  But I'm not sure I'd notice anyway, I run full graphics options and it's smooth either way, in it's own X or in my default X.

I hope to be able to do the same. I think I am getting a new video card for Christmas. If I don't I am buying one afterwards.

---

### Post by hsoj on 2006-12-15
Thank you VERY much for the guide.. This helped me immensely. I've just started really but I'm having a positivie experience with WoW on Linux so far :D 

Now if I can figure out why changing video settings crashes WoW every time :-/

---

### Post by Afteraffekt on 2006-12-29
When i go to launch Wow it crashes after 2 black screens and gives me this error:



```
==============================================================================
World of WarCraft (build 6180)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Dec 29, 2006  4:26:49.707 AM
User:     travis
Computer: Travis-Ubuntu
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7E010A03

The instruction at "0x7E010A03" referenced memory at "0x00007548".
The memory could not be "read".


WoWBuild: 6180
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=000010C5  EBX=7E1E14A0  ECX=00007548  EDX=00000000  ESI=7C8659D0
EDI=7D8F5710  EBP=0033C6A4  ESP=0033C62C  EIP=7E010A03  FLG=00010246
CS =0073      DS =007B      ES =007B      SS =007B      FS =003B      GS =0033


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

7E010A03 0033C6A4 0000:00000000 <unknown>
7E0A283D 0033C6D4 0000:00000000 <unknown>
7E5E0CBD 0033C704 0000:00000000 <unknown>
7E744070 0033C744 0001:00033070 c:\windows\system32\opengl32.dll
005D8A73 0033C770 0001:001D7A73 C:\Program Files\World of Warcraft\WoW.exe
005C3308 0033C78C 0001:001C2308 C:\Program Files\World of Warcraft\WoW.exe
005C331B 0033C7B8 0001:001C231B C:\Program Files\World of Warcraft\WoW.exe
007473EC 0033C84C 0001:003463EC C:\Program Files\World of Warcraft\WoW.exe
007446DC 0033FBC8 0001:003436DC C:\Program Files\World of Warcraft\WoW.exe
007BF22E 0033FCA0 0001:003BE22E C:\Program Files\World of Warcraft\WoW.exe
004734EF 0033FCC4 0001:000724EF C:\Program Files\World of Warcraft\WoW.exe
007B5A57 0033FCE8 0001:003B4A57 C:\Program Files\World of Warcraft\WoW.exe
007B430C 0033FCF4 0001:003B330C C:\Program Files\World of Warcraft\WoW.exe
0044306E 0033FDBC 0001:0004206E C:\Program Files\World of Warcraft\WoW.exe
004250A0 0033FDF0 0001:000240A0 C:\Program Files\World of Warcraft\WoW.exe
00421A5F 0033FE60 0001:00020A5F C:\Program Files\World of Warcraft\WoW.exe
004215E1 0033FE78 0001:000205E1 C:\Program Files\World of Warcraft\WoW.exe
0040448E 0033FF08 0001:0000348E C:\Program Files\World of Warcraft\WoW.exe
7EE99EDE 0033FFE8 0001:00058EDE c:\windows\system32\kernel32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

7E010A03              <unknown symbol>+0 (0x00000004,0x000010C5,0x000010CA,0x0000000C)
7E0A283D              <unknown symbol>+0 (0x00000004,0x000010C5,0x000010CA,0x0000000C)
7E5E0CBD              glDrawRangeElementsEXT+77 (0x00000004,0x000010C5,0x000010CA,0x0000000C)
7E744070 opengl32.dll <unknown symbol>+0 (0x00000004,0x000010C5,0x000010CA,0x0000000C)
005D8A73 WoW.exe      <unknown symbol>+0 (0x0033C7A8,0x00000001,0x00000001,0xFFFFFFFF)
005C3308 WoW.exe      <unknown symbol>+0 (0x00000001,0x00748D1C,0x00000000,0x0033C86C)
005C331B WoW.exe      <unknown symbol>+0 (0x00000000,0x05F90E08,0x06D518A8,0xBE6F409A)
007473EC WoW.exe      <unknown symbol>+0 (0x00000000,0x06759008,0x06746088,0x0000000D)
007446DC WoW.exe      <unknown symbol>+0 (0x00000000,0x06114008,0x3F800000,0x00000000)
007BF22E WoW.exe      <unknown symbol>+0 (0x00000000,0x007BF781,0x00000001,0x06426A08)
004734EF WoW.exe      <unknown symbol>+0 (0x012CD608,0x063D4008,0x0638FC88,0x00000000)
007B5A57 WoW.exe      <unknown symbol>+0 (0x0638FCA0,0x0033FDBC,0x0044306E,0x0638FCA0)
007B430C WoW.exe      <unknown symbol>+0 (0x0638FCA0,0x401F6C8C,0x0033FDD0,0x010F27C8)
0044306E WoW.exe      <unknown symbol>+0 (0x010F2818,0x010F2808,0x00000000,0x010F27C8)
004250A0 WoW.exe      <unknown symbol>+0 (0x00000000,0x00000102,0x010F2808,0x00000000)
00421A5F WoW.exe      <unknown symbol>+0 (0x00000000,0x00402489,0x00000001,0x00000001)
004215E1 WoW.exe      <unknown symbol>+0 (0x0040A390,0x00400000,0x00000000,0x001166F4)
0040448E WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7EE99EDE kernel32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7E8A567              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00340000 - 0x003D0000  C:\Program Files\World of Warcraft\fmod.dll
0x00400000 - 0x00D8D000  C:\Program Files\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x72980000 - 0x729B3000  c:\windows\system32\dbghelp.dll
0x7D220000 - 0x7D22B000  c:\windows\system32\psapi.dll
0x7D240000 - 0x7D250000  c:\windows\system32\mswsock.dll
0x7D6C0000 - 0x7D6CD000  c:\windows\system32\midimap.dll
0x7D6F0000 - 0x7D721000  c:\windows\system32\wineoss.drv
0x7D890000 - 0x7D8BA000  c:\windows\system32\uxtheme.dll
0x7E210000 - 0x7E288000  c:\windows\system32\winex11.drv
0x7E360000 - 0x7E372000  c:\windows\system32\mpr.dll
0x7E380000 - 0x7E3B9000  c:\windows\system32\wininet.dll
0x7E3D0000 - 0x7E41D000  c:\windows\system32\msvcrt.dll
0x7E420000 - 0x7E443000  c:\windows\system32\msacm32.drv
0x7E450000 - 0x7E457000  c:\windows\system32\lz32.dll
0x7E460000 - 0x7E470000  c:\windows\system32\version.dll
0x7E480000 - 0x7E4F9000  c:\windows\system32\winmm.dll
0x7E500000 - 0x7E515000  c:\windows\system32\imm32.dll
0x7E710000 - 0x7E774000  c:\windows\system32\opengl32.dll
0x7E780000 - 0x7E79F000  c:\windows\system32\ws2_32.dll
0x7E7B0000 - 0x7E7B9000  c:\windows\system32\wsock32.dll
0x7E7D0000 - 0x7E7EA000  c:\windows\system32\iphlpapi.dll
0x7E800000 - 0x7E83B000  c:\windows\system32\rpcrt4.dll
0x7E850000 - 0x7E8CF000  c:\windows\system32\ole32.dll
0x7E8E0000 - 0x7E927000  c:\windows\system32\shlwapi.dll
0x7E940000 - 0x7EA11000  c:\windows\system32\shell32.dll
0x7EB20000 - 0x7EBBB000  c:\windows\system32\gdi32.dll
0x7EBE0000 - 0x7ECF1000  c:\windows\system32\user32.dll
0x7ED00000 - 0x7EDB1000  c:\windows\system32\comctl32.dll
0x7EDC0000 - 0x7EDF7000  c:\windows\system32\advapi32.dll
0x7EE40000 - 0x7EF2F000  c:\windows\system32\kernel32.dll
0x7EF90000 - 0x7F000000  c:\windows\system32\ntdll.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 7E010A03)

7E010A03: 0F B7 04 51  66 2B 45 B2  66 89 04 57  83 C2 01 39  ...Qf+E.f..W...9


Stack: 1024 bytes starting at (ESP = 0033C62C)

* = addr                                         **                       *   
0033C620: 8C C6 33 00  A4 C6 33 00  E3 09 01 7E  C8 BA 85 7C  ..3...3....~...|
0033C630: 10 57 8F 7D  18 00 00 00  02 00 00 00  0C 00 00 00  .W.}............
0033C640: 03 14 00 00  48 75 00 00  A0 14 1E 7E  D0 59 86 7C  ....Hu.....~.Y.|
0033C650: 04 00 00 00  94 C6 C5 10  68 C6 33 00  C8 BA 85 7C  ........h.3....|
0033C660: 5E FB 09 7E  48 75 00 00  C0 3C 89 7C  00 40 8F 7D  ^..~Hu...<.|.@.}
0033C670: 10 17 00 00  28 17 00 00  10 17 00 00  10 47 30 E0  ....(........G0.
0033C680: 00 00 00 00  00 00 00 00  00 00 00 00  94 F3 27 7E  ..............'~
0033C690: 00 6B 5D 7E  2B 06 01 7E  A0 14 1E 7E  D0 59 86 7C  .k]~+..~...~.Y.|
0033C6A0: 48 75 00 00  D4 C6 33 00  3D 28 0A 7E  04 00 00 00  Hu....3.=(.~....
0033C6B0: C5 10 00 00  CA 10 00 00  0C 00 00 00  03 14 00 00  ................
0033C6C0: 48 75 00 00  04 C7 33 00  AA 27 0A 7E  10 75 60 7E  Hu....3..'.~.u`~
0033C6D0: 70 0C 5E 7E  04 C7 33 00  BD 0C 5E 7E  04 00 00 00  p.^~..3...^~....
0033C6E0: C5 10 00 00  CA 10 00 00  0C 00 00 00  03 14 00 00  ................
0033C6F0: 48 75 00 00  00 00 00 00  E2 4A 5D 00  79 0C 5E 7E  Hu.......J].y.^~
0033C700: 98 F4 76 7E  44 C7 33 00  70 40 74 7E  04 00 00 00  ..v~D.3.p@t~....
0033C710: C5 10 00 00  CA 10 00 00  0C 00 00 00  03 14 00 00  ................
0033C720: 48 75 00 00  00 00 00 00  08 40 0C 01  00 00 00 00  Hu.......@......
0033C730: 08 40 0C 01  08 40 0C 01  08 40 0C 01  B0 C7 33 00  .@...@...@....3.
0033C740: 60 5B 75 7E  70 C7 33 00  73 8A 5D 00  04 00 00 00  `[u~p.3.s.].....
0033C750: C5 10 00 00  CA 10 00 00  0C 00 00 00  03 14 00 00  ................
0033C760: 48 75 00 00  01 00 00 00  A0 ED 87 00  00 00 00 00  Hu..............
0033C770: 8C C7 33 00  08 33 5C 00  A8 C7 33 00  01 00 00 00  ..3..3\...3.....
0033C780: 01 00 00 00  FF FF FF FF  CA 10 00 00  B8 C7 33 00  ..............3.
0033C790: 1B 33 5C 00  01 00 00 00  1C 8D 74 00  00 00 00 00  .3\.......t.....
0033C7A0: 6C C8 33 00  00 00 00 00  03 00 00 00  A4 3A 00 00  l.3..........:..
0033C7B0: 0C 00 C5 10  CA 10 74 00  4C C8 33 00  EC 73 74 00  ......t.L.3..st.
0033C7C0: 00 00 00 00  08 0E F9 05  A8 18 D5 06  9A 40 6F BE  .............@o.
0033C7D0: 77 44 AA 3E  2F E7 69 BF  00 00 00 00  18 EA 78 3F  wD.>/.i.......x?
0033C7E0: 7F A8 A3 3D  DC D2 60 BE  00 00 00 00  00 00 00 00  ...=..`.........
0033C7F0: B3 8F 70 3F  3F 1D AF 3E  00 00 00 00  00 00 00 00  ..p??..>........
0033C800: 00 00 00 00  00 00 00 00  00 00 80 3F  E6 95 C6 3F  ...........?...?
0033C810: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C820: F0 63 04 40  00 00 00 00  00 00 00 00  00 00 00 00  .c.@............
0033C830: 00 00 00 00  31 08 80 3F  00 00 80 3F  00 00 00 00  ....1..?...?....
0033C840: 00 00 00 00  81 95 E3 BE  00 00 00 00  C8 FB 33 00  ..............3.
0033C850: DC 46 74 00  00 00 00 00  08 90 75 06  88 60 74 06  .Ft.......u..`t.
0033C860: 0D 00 00 00  84 6A 42 06  08 40 11 06  C9 01 25 3F  .....jB..@....%?
0033C870: 00 00 00 80  00 00 00 00  00 00 00 80  00 00 00 80  ................
0033C880: AB 82 F7 3E  00 00 00 80  00 00 00 00  00 00 00 00  ...>............
0033C890: 00 00 00 80  00 00 00 00  FF FF 7F 3F  00 00 00 80  ...........?....
0033C8A0: 00 00 00 00  64 FB 0F C0  9B 04 10 40  08 0E F9 05  ....d......@....
0033C8B0: 18 54 D7 00  10 00 64 06  00 00 00 00  00 00 00 00  .T....d.........
0033C8C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C8D0: 00 00 00 00  00 00 00 00  00 00 00 00  E6 95 C6 3F  ...............?
0033C8E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C8F0: F0 63 04 40  00 00 00 00  00 00 00 00  00 00 00 00  .c.@............
0033C900: 00 00 00 00  31 08 80 3F  81 95 E3 BE  00 00 00 00  ....1..?........
0033C910: 00 00 00 00  00 00 80 3F  00 00 00 00  00 00 80 3F  .......?.......?
0033C920: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C930: 00 00 80 3F  00 00 00 00  00 00 00 00  00 00 00 00  ...?............
0033C940: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C950: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C960: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C970: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C980: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C990: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................


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
Processor Revision:     9985

Percent memory used:    7
Total physical memory:  1060536320
Free Memory:            790089728
Page file:              2147483647
Total virtual memory:   2147352575

```


and when i close that i get

Error #132 0x851000084

exception: 0xc0000005 (ACCESS_VIOLATION) at 0073:7E010A03

Instruction at 0x7E010A03 referenced memory at 0x00007548
the memory could not be "read"



WTF do i do? whats wrong?

---

### Post by Sammi on 2006-12-29
Has the game worked before? If so, what has changed?

This could probably be an error with your grafics card drivers or xgl/aiglx/compiz/beryl.

Try reinstalling your grafics card drivers and removing the compositions effects if you have installed any.

---

### Post by nikki on 2006-12-30
Very nice. I hit to up 130 fps in Ogrimmar on Blade's Edge today. I even have FULL detail on. Very Hawt. This is 4x what I got in windows. Just have to fix the sound in WoW now.

---

### Post by hikaricore on 2006-12-31
A little offtopic here, but did anyone else's minimap suddenly start working everywhere properly or is it just me?  ^.^

---

### Post by nikki on 2006-12-31
From what I've experienced, it has been. Though, I've been experiencing random crashes.

---

### Post by hetzz on 2007-04-22
Had about constantly lower than 20fps earlier today.  Surfed in here and found this thread :D
Tweak #1 was already done(found it in another thread)

At first i couldnt get tweak #2 working, nothing happend. Then i tried with sudo(even though i really dont feel safe runing wow as root) i was finding myself with a black screen.  This got me a little bit worried, but i thought it would happend something in a minute or two. When nothing happend i tried ctrl+alt+f*, nothing happend. I slammed my fingers at ctrl+alt+backspace, again nothing happened.  

I always play wow in windowed so i thought maybe i should deactivate that option. No difference though :(

i'll give you some info and configs, i hope you'll get that "ohh theres your problem"-thingy, cuz im getting tired of this.


At first the script:
[HTML]#!/bin/sh
 
 X :3 -ac &   # Launches a new X session on display 3 
 cd "/media/hdb5/World\ of\ Warcraft/"   # Goto WoW dir 
 sleep 2   # Forces the system to have a break for 2 seconds 
 DISPLAY=:3 /usr/X11R6/bin/wine WoW.exe -opengl   # Launches WoW[/HTML]

Then maybe you'll want a look at my wtf.config
[HTML]SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "32"
SET farclip "477"
SET specular "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET realmList "eu.logon.worldofwarcraft.com"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET gxMultisampleQuality "0.000000"
SET accountName "hetzz"
SET locale "enGB"
SET realmName "Twisting Nether"
SET gxWindow "1"
SET mouseSpeed "1"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET lastCharacterIndex "1"
SET profanityFilter "0"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET gameTip "20"
SET AmbienceVolume "0.60000002384186"
SET statusBarText "1"
SET uiScale "1"
SET UnitNameNPC "1"
SET autoSelfCast "1"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET timingTestError "0"
SET checkAddonVersion "0"
SET MasterSoundEffects "0"
SET EnableMusic "0"
SET EmoteSounds "0"
SET SoundListenerAtCharacter "0"
SET gxCursor "0"
SET M2UseShaders "0"
SET useWeatherShaders "0"
SET ffx "0"[/HTML]

xorg.conf may be at help (got rid of those parts i didnt think would affect the gfx)

[HTML]Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1152x921" "1152x900" "1024x768" "960x720" "832x624" "800x600" "720x400" "640x480"
	EndSubSection


Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


[/HTML]


fglrxinfo:
[HTML]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6400 (8.35.5)
[/HTML]

as what i can see i shouldnt have these problems :( 
a lot of people are posting error messages, where do you find these? for me wow is working then suddently the computer freezes and hardboot is the only solution.(this can happen after a couple of minutes up to an hour or so) Thought this "another server"-thingy atleast would solve the problem with whole computer freeze, if only wow would freeze i atleast could kill it and start it up again.

Greatfull for all help possible :)

---

### Post by sitheris on 2007-04-23
off topic - I am getting about 70-80 fps in WoW under Ubuntu but it still seems so choppy, lots of tearing (even with vsync on)...and gives me a headache.

In windows it runs very smoothly.  Am i not doing something right?

---

### Post by Qwerty) on 2007-04-24
> **sitheris said:**
> off topic - I am getting about 70-80 fps in WoW under Ubuntu but it still seems so choppy, lots of tearing (even with vsync on)...and gives me a headache.

In windows it runs very smoothly.  Am i not doing something right?


I had the same problem.  Turned off full screen glow effect and the tearing went away.  I dont miss the glowing either :)

---

### Post by sitheris on 2007-04-24
pretty sure i turned that off as well. the game just doesn't feel the same as it does in windows

---

### Post by foug on 2007-04-25
Any other tricks to increase FPS?

---

### Post by phatalbert on 2007-04-25
My minimap is still not working. From what I've seen this is a problem with an older version of Wine, but I have it updated to the latest version and it still will not show while indoors or in cities.

---

### Post by foug on 2007-04-26
I'm not sure if the second tweak is working. I run the command ~,/launch.sh or whatever it was and I get invalid command.

---

### Post by wormite on 2007-05-24
After the recently update to 2.10, while quitting wow I always get a crash.
The screen gets a freeze. The followings are displayed in console:
Any idea?
> 
fixme:reg:GetNativeSystemInfo (0x37400f40) using GetSystemInfo()
fixme: process:IsWow64Process (0xffffffff 0x7bbfe4b4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

---

### Post by hikaricore on 2007-05-24
> **wormite said:**
> After the recently update to 2.10, while quitting wow I always get a crash.
The screen gets a freeze. The followings are displayed in console:
Any idea?

everyone's is having this issue:
[http://ubuntuforums.org/showthread.php?t=451505](http://ubuntuforums.org/showthread.php?t=451505)

this probably won't be fixed for a couple wine releases or until the next wow patch.
until then, try my kill script for WoW: [http://ubuntuforums.org/showpost.php?p=2708504&postcount=42](http://ubuntuforums.org/showpost.php?p=2708504&postcount=42)

also, don't post the same thing in more than one thread.

---

### Post by sammael666 on 2007-07-19
both worked like charm, getting 3x to 4x the performance i got under Wincrap even with beryl running on my primary X display. thanks a lot!!

---

### Post by tehgimpeh on 2007-07-19
i tried tweak 1 and it didnt seem to help that much... still getting about 14fps.. any other suggestions?

---

### Post by Lostthoughts54 on 2007-08-08
ok i am decently new to linux and very new to X servers

i ran tweak #2 hoping it would help but all i get is a black or checkered screen with a X cursor. I can here a very distorted wow in the background but no video display. When i ctrl+alt+f7 i get back and this is the message in my terminal

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==)

 default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Wed Aug  8 12:09:31 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7d740000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d740000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f584,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wave:DSD_CreateSecondaryBuffer (0x172d60,0x33fcd0,180e8,0,0x1a3e10,0x172e94,0x1a3df0): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374026c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7cc9f494) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
^[[19~^[[19~^[[20~fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub
adam@ubuntu:~$ ~~~FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!


i am thinking i have a wrong path in my script. WoW dir is /media/host/World of Warcraft

and my X server script is 

#!/bin/sh

 X :3 -ac &   # Launches a new X session on display 3
 cd "/media/host/World of Warcraft"   # Goto WoW dir
 sleep 2   # Forces the system to have a break for 2 seconds
 DISPLAY=:3 /usr/X11R6/bin/wine WoW.exe -opengl   # Launches WoW



anyone got any idea where i am going wrong?

edit: i am running the script with the sudo command if that makes a difference.

---

### Post by Pikestaff on 2007-08-09
Just tried Tweak #1 for Kubuntu Dapper with Wine 0.9.42.  Previously my framerate was a steady 17-20 FPS, which is certainly playable but also left something to be desired.  After doing Tweak #1, my framerate is kinda all over the place but it's now almost always 30 FPS or above so I'll call it successful :)  (Middle of Stormwind on a busy day kind of lags the FPS down to where it was previously, or close to it, but other than that it's an improvement.)

I haven't tried Tweak #2 but I think I'm good with where my FPS is right now, it doesn't have to be super smooth for me, it just has to be playable and it definitely is.  Thanks to the OP for posting these!

---

### Post by andraxion on 2007-09-27
I hope no one is complaining about 14fps =P

I bought the best graphics card sold for my computer (ATI Radeon X1300 because my computer only supports the basic PCI) and the card isn't too bad really. 256mb with 2.0 shaders. So I put it in my computer (was running Windows at the time) and got it all set up. I jammed open WoW as fast as I could and turned the settings all the way up and what do ya know? 4fps. So even after dishing out $150, I have to play with 10-14fps with everything turned down.

I am not sure if it will improve in Linux, but I hope I can still attend raids haha.

---

### Post by juggalojesus87 on 2007-09-27
ok i am running in d3d because when running in open gl it takes forever to just get to char selection. the frame rate seems really really low. but running in d3d its smooth up to the actual game and then im only running 1-14 fps... i try to change video settings but if i click ok it hard locks and have to reset comp. any ideas what i can do???:confused:

---

### Post by 99bluefoxx on 2007-10-08
neither of these worked for mee, in fact the first screwed me over and crashed my computer as soon as the logon loader was finished, the second actually decreased preformance, and i cant figure out how to undo it :( i am not happy, i was only getting 7 fps before and now it has dropped to 3.

---

### Post by imtheguru on 2007-10-24
This weekend i replaced my Fedora core with Ubuntu 7.10. On a whim i tried to get World of Warcraft running using wine... i try it with each Wine release, but, results are usually not promising. Install was far too trivial... so i tried to go a step further and optimise the graphics. The results are as below:

Basic launcher:
[http://i73.photobucket.com/albums/i216/ibguru/wow-linux/Wow-launcher.png](http://i73.photobucket.com/albums/i216/ibguru/wow-linux/Wow-launcher.png)

Running in windowed mode, using DirectX API
(hardware cursor very responsive, but ugly)
[http://i73.photobucket.com/albums/i216/ibguru/wow-linux/Directx-windowed-mode.png](http://i73.photobucket.com/albums/i216/ibguru/wow-linux/Directx-windowed-mode.png)

Running in windowed mode, maximized, using OpenGL
[http://i73.photobucket.com/albums/i216/ibguru/wow-linux/Opengl-maxwindow-secondaryXserver-m.jpg](http://i73.photobucket.com/albums/i216/ibguru/wow-linux/Opengl-maxwindow-secondaryXserver-m.jpg)

Running in full screen mode, using OpenGL on a secondary Xserver.
[http://i73.photobucket.com/albums/i216/ibguru/wow-linux/Opengl-fullscreen-secondaryXserver-.jpg](http://i73.photobucket.com/albums/i216/ibguru/wow-linux/Opengl-fullscreen-secondaryXserver-.jpg)

Average FPS ~50, max seems to be around 100. That's about double the numbers from XP home.

Upgraded system memory from 1GB to 2GB and gained about 35fps.
[http://i73.photobucket.com/albums/i216/ibguru/wow-linux/Opengl-fullscreen-secondaryXserv-1.jpg](http://i73.photobucket.com/albums/i216/ibguru/wow-linux/Opengl-fullscreen-secondaryXserv-1.jpg)

New average numbers are ~60fps outdoors and about 40-45 in arenas. Max fps is ~140...

Cheers and thanks for the great write-up.

---

### Post by hikaricore on 2007-10-24
In an effort to clean up the Gaming and Leisure section of our forums and
reduce the number of World of Warcraft threads, I have stickied this thread
for you all to use: [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

Please consider posting there instead.

I'm moving new posts but leaving existing threads such as this alone with only the suggestion.

Thanks,

--Aaron

---

### Post by asnd16 on 2008-01-16
why after like 10 minutes of playing does things get really slow?

---

### Post by angryforumreader on 2008-01-30
do you have a swap partition on your HD? WoW will use up lots of system memory for sure, virtual memory is probably used.

---

### Post by myname on 2008-02-09
> **z00s said:**
> I found some tweaks regarding, specifically, WoW under Wine from: [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

Tweak #1 has proven to work for me. Tweak #2 has proven NOT to work for me.
 

[SIZE=4]Tweak #1[/SIZE]
 
The following from [http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606) , a simple registry edit for Wine that dramatically increases the framerate in game for both ATi and nVidia users (reportedly, I have only verified with nVidia using Wine 0.9.22): 
 
```
regedit
```
 
Find HKEY_CURRENT_USER\Software\Wine\ 
 
Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder 
 
Click right on the wine folder and select [NEW] then [KEY] 
 
Replace the text "New Key #1" with OpenGL 
 
Click right in the right hand pane and select [NEW] then [String Value] 
 
Replace "New Value #1" with "DisabledExtensions" 
(Notice it's case sensitive) 
 
Then double click anywhere on the line, a dialog box will open. 
In the value field type "GL_ARB_vertex_buffer_object" (without the quotes). 
 
Here's what regedit should look like once you have finished adding this new key and it's value. 
 
[http://appdb.winehq.org/appimage.php?iId=4640](http://appdb.winehq.org/appimage.php?iId=4640)


[SIZE=4]Tweak #2[/SIZE]
 
Another tweak you can use from [http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606) , the idea is to create a script which will allow you to launch WoW on a dedicated X server, and will give you a little boost of FPS. 
 
```
nano -w ~/launch-wow.sh
``` 
 
Put this content in your newly created file: ~/launch-wow.sh
 
```
#!/bin/sh
 
 X :3 -ac &   # Launches a new X session on display 3 
 cd "~/.wine/drive_c/Program Files/World of Warcraft"   # Goto WoW dir 
 sleep 2   # Forces the system to have a break for 2 seconds 
 DISPLAY=:3 /usr/X11R6/bin/wine WoW.exe -opengl   # Launches WoW
```
 
 
Press Ctrl+o then Ctrl+w in order to save your file & quit nano. 
 
Don't forget to make your script executable : 
 
```
chmod +x ~/launch-wow.sh
``` 

when I try the bash script above, I receive the following:

> X: user not authorized to run the X server, aborting.
cd: 4: can't cd to ~/games/WoW
wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found
kevinp@dugr:~$ fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!

I then have to hit CTRL+C.

Any idea?

--Kevin

---

### Post by Linux Gabe on 2008-02-09
Sorry, Im just getting reaquanted with Linux. With that said, Im having trouble getting method2 to work.

tried pasting this into a terminal:

#!/bin/sh
 
 X :3 -ac &   # Launches a new X session on display 3 
 cd "~/.wine/drive_c/Program Files/World of Warcraft"   # Goto WoW dir 
 sleep 2   # Forces the system to have a break for 2 seconds 
 DISPLAY=:3 /usr/X11R6/bin/wine WoW.exe -opengl   # Launches WoW

I get this message back:

gabriel@BLACKP4-UBUNTU:~$ #!/bin/sh
gabriel@BLACKP4-UBUNTU:~$  
gabriel@BLACKP4-UBUNTU:~$  X :3 -ac &   # Launches a new X session on display 3 
[1] 10113
gabriel@BLACKP4-UBUNTU:~$  cd "~/.wine/drive_c/Program FileX: user not authorized to run the X server, aborting.
  # Goto WoW dir ft"  
bash: cd: ~/.wine/drive_c/Program Files/World of Warcraft: No such file or directory
[1]+  Exit 1                  X :3 -ac
gabriel@BLACKP4-UBUNTU:~$  sleep 2   # Forces the system to have a break for 2 seconds 
gabriel@BLACKP4-UBUNTU:~$  DISPLAY=:3 /usr/X11R6/bin/wine WoW.exe -opengl   # Launches WoW
wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found

Rember now, Ima newb so be gentle

---

### Post by Linux Gabe on 2008-02-09
also tried this and got a X server created on f9, but it was just grey with the X mouse icon

gabriel@BLACKP4-UBUNTU:~$ sudo ~/launch-wow.sh
cd: 4: can't cd to ~/.wine/drive_c/Program Files/World of Warcraft

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux BLACKP4-UBUNTU 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686
Build Date: 18 January 2008
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Sat Feb  9 14:57:21 2008
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
wine: /home/gabriel/.wine is not owned by you
gabriel@BLACKP4-UBUNTU:~$ (II) Module already built-in
(II) Module already built-in
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

---

### Post by Trevo_Teh_Nerd on 2008-02-22
How do i allow my user to create an X server without being root? thats my only problem.. otherwise the code would work i believe > X: user not authorized to run the X server, aborting.
cd: 4: can't cd to ~/games/WoW
wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found
kevinp@dugr:~$ fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0 count = 0! 
Its because the script can't find WoW, goto that directory and copy the address and drop that in after the "cd" command, so it would look something like 
> cd "/home/--user--/.wine/drive_c/Program Files/World of Warcraft/"


edit: i realized there was a post on the sudo fix, (cant get it to work) and the 2nd quote was more of an answer, i just realized how confusing my post was

---

### Post by Shne on 2008-03-11
I tried the script making a dedicated X server for WoW and it worked, well, technically.
There were a few problems.
I didn't get any fps boost from it (at least none that I noticed) and the full screen AA from my nvidia-settings was gone. My mouse moved faster (not less lag, but with a higher sensitivity) and the play/pause/etc. button I have on my keyboard didn't work with Rhythmbox (which was running on the other X server).
Using Ctrl-Alt-F7 and Ctrl-Alt-F9 switched me back and forth original X Server and new X Server fine. But when I exited WoW, I had to go back to original X Server and end the extra X Server using the System Monitor before I could start it again. 
Could it perhaps be added to the script that the extra X Server should be killed when WoW is exited?

One extraordinary thing I did discover, however, was that the multisampling option in WoW now worked! I could choose up to 4x multisampling and it worked and looked like it should.

All in all, I'm gonna stick with what I have now (ie. not use the script).

---

### Post by Scarletfire on 2008-04-24
First of all... BUMP. I have used this script listed as tweak #2 since it was released and have loved it. However, i have run into a problem since the release of 8.04. I have been away from ubuntu for a few months now due to windows software restraints. However when i try to execute the script i keep getting an error from wine. It seems they have changed permissions requirements in wine to fit to the ubuntu style of "security". I have tried going in and changing permissions to all the folders that lead to wine and have had no luck. If anyone could point me in the right direction it would be much appreciated.

here's the error i get when wine tries to invoke the last part of the script. 

wine: /home/me/.wine is not owned by you

---

### Post by JustinAlf on 2008-07-28
Is there a way to do this Registry Edit with Direct3d?  My Wow under ubuntu only works through Direct 3d, so its really slow right now.

---

### Post by hotballz87 on 2008-11-03
i have done the tweak #1 since i have started using ubuntu.

since patch 3.0 i have been having framerate problems, so i tried #2, but the run script would not work. 
i decided to run it in sudo, here is my output:

```
steve@steve-desktop:~$ sudo '/home/steve/launch-wow.sh' 
[sudo] password for steve: 
cd: 4: can't cd to ~/.wine/drive_c/Program Files/World of Warcraft

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux steve-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Mon Nov  3 17:53:59 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
wine: /home/steve/.wine is not owned by you
steve@steve-desktop:~$ FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


```

---

### Post by kyr on 2008-11-20
Is it possible to run multiple instances of WoW on separate X servers simultaneously?

I am currently using the following script to launch WoW:
$ cat start_wow.sh
#!/bin/sh
sudo X $1 -ac -terminate &
sleep 5
DISPLAY=$1 /usr/bin/wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe &

I then launch WoW on display 3:
$ ./start_wow.sh :3

WoW comes up fine on display 3 (Ctrl+Alt+F9). I then attempt to launch WoW on display 4:
$ ./start_wow.sh :4

WoW now comes up fine on display 4 (Ctrl+Alt+F10) but the WoW instance on display 3 locks up and shows only a static black screen.

Any thoughts on how I can get multiple instances of WoW to run simultaneously?

---

### Post by JoePits on 2008-12-07
I had the crazy polygon issue as well when going indoors to outdoors.

The registry hack fixed that.

Heres how I have it working:

latest ATI driver installed via envyg -t

took out Disable "dri2" in the xorg.conf so that amdcccle would work

turned everything in there to performance.

gxAPI "OpenGL"

wine 1.1.10

---

### Post by Miles_Prower on 2008-12-29
I know this thread's really old, but I came here for help, and that screwed me, so I thought maybe I could help the next poor ******* out.

1st, wine has been updated since this guide (which means the writer of this guide had no way of knowing it wouldn't work a couple years later.)

 It seems to me that you're no longer allowed to run wine with sudo. (it will produce an error). This would not be a problem, except that hack #2 involves you setting up wow on it's own X server (which you can ONLY do as root or with sudo).  Hack #2, then, is completely broken unless you find a way to put wow on it's own x server without using root. I suggest a schrodinger's cat kind of thing, where the computer doesn't know if you're logged in as root or not until it looks at the terminal. Maybe that will give you enough time to set up the separate x server?


ugh....

---

### Post by Miles_Prower on 2008-12-29
oh, also, the friendly folks at wineHQ suggest that you delete the ~/.wine directory should you ever accidentally try to run wine as root. NO ONE TELLS YOU, maybe it's supposed to be common sense, BUT DOING SO WILL DESTROY ANY AND ALL PROGRAMS YOU'VE INSTALLED VIA WINE.

thanks, guys.

---

### Post by Greyed on 2008-12-29
> **Miles_Prower said:**
> It seems to me that you're no longer allowed to run wine with sudo. (it will produce an error). This would not be a problem, except that hack #2 involves you setting up wow on it's own X server (which you can ONLY do as root or with sudo).  Hack #2, then, is completely broken unless you find a way to put wow on it's own x server without using root.

Uhm, put it on its own server.  Only X needs root to start.  So put sudo in front of the X line inside the shell script.

---

### Post by Miles_Prower on 2008-12-30
i've tried putting sudo into the script there, but there was some trouble with the terminal turning around and asking for my password, but then the script would continue with the next command. Is there any way to get around that kind of problem without typing my password into the script?

---

### Post by Greyed on 2008-12-30
That is not a problem, that's the point of sudo.  Here's what I have for mine:

```

#!/bin/sh

kdesudo -- X :3 -ac &   # Launches a new X session on display 3
#nvidia-settings --load-config-only
cd .wine/drive_c/games/World\ of\ Warcraft/
sleep 10   # Forces the system to have a break for 2 seconds
DISPLAY=:3 wine WoW.exe -opengl &  # Launches WoW

```

This brings up a GUI dialog for the password.

---

### Post by lucasta on 2010-10-18
> **z00s said:**
> 
```
#!/bin/sh
 
 X :3 -ac &   # Launches a new X session on display 3 
 cd "~/.wine/drive_c/Program Files/World of Warcraft"   # Goto WoW dir 
 sleep 2   # Forces the system to have a break for 2 seconds 
 DISPLAY=:3 /usr/X11R6/bin/wine WoW.exe -opengl   # Launches WoW
```


i tried using this code to launch a game in a dedicated x server and upon restart tty1-6 have no text interfaces. just a buggy X display. do you know how i can recover my text consoles?

---

### Post by Sammi on 2010-10-19
Holy Necromancy!

---

