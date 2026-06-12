---
title: "Wine is almost not Broken or the Fight With the PAINT SHOP PROS 8 Splash!?#@#¤!!?"
date: 2018-04-21
forum: Wine
---

### Post by armrek on 2018-04-21
[FONT=Ubuntu]I still want to move towards using Ubuntu *18.04LTS* and the only problem I have, is that wine is playing up again.[/FONT] 
 
 [FONT=Ubuntu]I use an old paint program called *Paint Shop Pro 8* for sketching stuff for games on the Android platform. This program worked on *16.04LTS* like silk. (wine-1.6.2)[/FONT]
 
 [FONT=Ubuntu]On the new Ubuntu I installed the stable Wine version from the Software App(wine-3-0). Then I called *winecfg* in a terminal causing all sorts of error printouts, but it opened and showed it was set for Windows 7, then I closed it again.[/FONT]
 
 [FONT=Ubuntu]To install Paint Shop Pro 8 I opened File Explorer and positioned it in the PSP8 folder where the installer *autorun.exe* is placed. The first thing I noticed was that the context menu to *Open with Wine* was missing. Well tough luck! Something must have gone missing in the development of the newer versions of Wine. So away I went to a terminal’ed into the folder and typed:[/FONT]
 
 [FONT=Ubuntu]*wine autorun.exe*[/FONT]
 
 [FONT=Ubuntu]This caused an error message:[/FONT]
 
 [FONT=Ubuntu]*ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.*[/FONT]
 
 [FONT=Ubuntu]But the Splash Window of the installer opened to my delight. The Splash Window has four check boxes:[/FONT]
 
 
[LIST=1]
[*]      [FONT=Ubuntu]*Install Paint Shop Pro 8*[/FONT] 
[*]      [FONT=Ubuntu]*Install Paint Shop Pro Photo Album Trial*[/FONT] 
[*]      [FONT=Ubuntu]*Browse the CD*[/FONT] 
[*]      [FONT=Ubuntu][I]Exit


[/I][/FONT][IMG]http://schwartzengine.com/temp/SplashWindow.png[/IMG] 
[/LIST]
  
 [FONT=Ubuntu]So happily I clicked on the first option, to my horror nothing happened and the same goes for option 2, option 3 browses the desktop of the user under the *.wine* folder and *Exit* exits as expected[/FONT]
 
 [FONT=Ubuntu]After a lot of googling, binging, searx.me or wharever you like I found that typing:[/FONT]
 
 [FONT=Ubuntu]*sudo apt-get install libgtk3-nocsd0:i386*[/FONT]
 
 [FONT=Ubuntu]Then the error message disappears , but the Splash Window is still unresponsive.[/FONT]
 
 [FONT=Ubuntu]So I removed Wine, Installed again an called *winecfg* now no error where printed and the configuration program showed Windows 7 again and I closed it. Then I called:[/FONT]
 
 [FONT=Ubuntu]wine autorun.exe[/FONT]
 
 [FONT=Ubuntu]Again and it turned out that the Splash Window still was unresponsive when I clicked the *Install Paint Shop Pro 8* check box…[/FONT]
 
 [FONT=Ubuntu]I noticed also that Wine complained that gecko and mono where missing when I tried to call a fractal program I had written a long time ago in C#. These where installed by calling:[/FONT]
 
 [FONT=Ubuntu]*wine uninstaller*[/FONT]
 
 [FONT=Ubuntu]And install some MSI files I found for these and then the program ran. [/FONT]
 
 [FONT=Ubuntu]But my main problem is that I cannot install Paint Shop Pro 8. Very annoying that you can see the splash window but not install by clicking it, the Splash Window comes up nicely with animation and all, so what gives?[/FONT]

---

### Post by deadflowr on 2018-04-21
I'd try playonlinux.
Playonlinux allows you to install multiple versions of wine, so if one version doesn't work as you want you can install another and try that.
wine is fickle sometimes.What works brilliantly in one version might be a total bust in another.

Playonlinux is in the Ubuntu software store.

---

### Post by armrek on 2018-04-21
> **deadflowr said:**
> I'd try playonlinux.
Playonlinux allows you to install multiple versions of wine, so if one version doesn't work as you want you can install another and try that.
wine is fickle sometimes.What works brilliantly in one version might be a total bust in another.

Playonlinux is in the Ubuntu software store.

Tried that, could create a virtual drive an call the installer from Wind 3.6, but again option 1 and 2 of the splash can be selected but does not start any installation.

Then I installed the Wine version I know works (wine-1.6.2) with PlayOnLinux, I got to where the virtual drive is being created, here I got stuck in the spokes hour glass running infinitely. Then I removed 1.6.2 and installed it again and it could show the Splash again, but it failed to do the installation when selecting that option. I have tried several versions but that same happens every time, even though I can see that the check mark for the option one is  selected when I have clicked on it, nothing happens...

So not exactly a success, the idea to have several versions to select from is good, but should not be necessary if wine was more stable. And it did not solve the problem, so what gives again?...

---

### Post by Holger_Gehrke on 2018-04-22
Autorun programs like the one you're having trouble with often don't do anything themselves beyond showing a splash screen and offering some choices, they just call other programs to do the real work. In your place I'd search the CD for another executable - probably in a subdirectory and named 'setup.exe'.

Holger

---

### Post by armrek on 2018-04-22
Some Progress!

I have tried to get this to work on an old Toshiba Satellite Pro L40  CLunker. Today I have boosted with a new SSD and reinstalled Ubuntu  18.04. All my stuff works only wine is giving me trouble.

But know at  least I can install wine from the software app and do this in the terminal: 

wine autorun.exe 

and then click on the Splash Window and make it install but then I  get this error when I start Paint Shop Pro 8:

```
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x7f545c76).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:006b GS:0063
 EIP:7f545c76 ESP:003387f0 EBP:00338818 EFLAGS:00010293(  R- --  I S -A- -C)
 EAX:0012fb48 EBX:7f5bddb8 ECX:00338830 EDX:0012fb48
 ESI:00000000 EDI:00338958
Stack dump:
0x003387f0:  00338f00 0012fb48 5f403844 00338814
0x00338800:  00339ea0 7f545c46 00338830 7f5bddb8
0x00338810:  00338958 0012fb48 00338868 7f545f76
0x00338820:  00000000 02e1a460 7f58358b 7f545f76
0x00338830:  00338958 7f5bddb8 00338868 7f545f5c
0x00338840:  01286c3a 0012fb48 00339ea0 00000000
Backtrace:
=>0 0x7f545c76 (0x00338818)
  1 0x7f545f76 (0x00338868)
  2 0x7f547268 (0x00338a38)
  3 0x7f54601a (0x00338a98)
  4 0x7bc7dfab (0x00338ab8)
  5 0x7bc80993 (0x00338b28)
  6 0x7bc7ded2 (0x00338e18)
  7 0x7b43ce2c in kernel32 (+0x1ce2b) (0x00338ea8)
  8 0x7f53d461 (0x00338ee8)
  9 0x0034394f in jascerrorcodes (+0x394e) (0x00339ec0)
  10 0x004901f6 in paint shop pro (+0x901f5) (0x0033a160)
  11 0x00f04015 in jascfileutil (+0x4014) (0x0033a444)
  12 0x00f03b19 in jascfileutil (+0x3b18) (0x0033a570)
  13 0x00f063cd in jascfileutil (+0x63cc) (0x0033a814)
  14 0x00494034 in paint shop pro (+0x94033) (0x0033a998)
  15 0x0049124d in paint shop pro (+0x9124c) (0x0033a9e0)
  16 0x004744af in paint shop pro (+0x744ae) (0x0033fe00)
  17 0x5f40b4f3 in mfc42 (+0xb4f2) (0x0033fec0)
  18 0x7b46255c in kernel32 (+0x4255b) (0x0033fed8)
  19 0x7b463f8e in kernel32 (+0x43f8d) (0x0033ffd8)
  20 0x7b46256a in kernel32 (+0x42569) (0x0033ffec)
0x7f545c76: movl    0x4(%esi),%eax
Modules:
Module    Address            Debug info    Name (100 modules)
PE      340000-  351000    Export          jascerrorcodes
PE      360000-  36e000    Deferred        jasclanguage
PE      370000-  37b000    Deferred        jascmemory
PE      380000-  3a8000    Deferred        jasccolormgr
PE      3b0000-  3bb000    Deferred        jascsingletonmgr
PE      3c0000-  3f1000    Deferred        jascdebugtools
PE      400000-  876000    Export          paint shop pro
PE      880000-  95f000    Deferred        sxlrt308
PE      960000-  ad5000    Deferred        jascrender
PE      ae0000-  d93000    Deferred        jascfileformats
PE      da0000-  deb000    Deferred        pcdlib32
PE      df0000-  ef5000    Deferred        jasccontrols
PE      f00000-  ff4000    Export          jascfileutil
PE     1000000- 103c000    Deferred        jascimagegear
PE     1040000- 11fe000    Deferred        gear12d
PE     1200000- 138c000    Deferred        jasccommandbase
PE     1390000- 13ee000    Deferred        jasccmdproc
PE     13f0000- 1450000    Deferred        jascmip
PE     1450000- 146b000    Deferred        jasccmyk
PE     1470000- 14fa000    Deferred        jascmaterialpalette
PE     1500000- 1522000    Deferred        jascbrowserutil
PE     1530000- 15b2000    Deferred        jascbrowser
PE     15c0000- 1603000    Deferred        cmydb
PE     1610000- 1623000    Deferred        jasclearningcenter
PE     1630000- 1639000    Deferred        jasccapture
PE     1640000- 1685000    Deferred        jasclayerpalette
PE     1690000- 16b0000    Deferred        jascpreferences
PE     16b0000- 1773000    Deferred        jasctoolbase
PE     2360000- 2433000    Deferred        igcad
PE     2550000- 2559000    Deferred        igdgn
PE     2560000- 2580000    Deferred        igfpx
PE     2580000- 25d2000    Deferred        fpxig
PE     25e0000- 25f5000    Deferred        jpegacc
PE     2820000- 2837000    Deferred        ighpgl
PE     2950000- 298d000    Deferred        igjpeg2k
PE     2990000- 29db000    Deferred        kdu_v32r
PE     2af0000- 2b0c000    Deferred        iglzw
PE     3920000- 3aaa000    Deferred        jasccmdartistic
PE     3ab0000- 3b09000    Deferred        jasccmdbevels
PE     3b10000- 3b40000    Deferred        jasccmdbrowse
PE     3b40000- 3bdd000    Deferred        jasccmdclipboard
PE     3be0000- 3d0a000    Deferred        jasccmdcolor
PE     3d10000- 3d2b000    Deferred        jasccmdexternal
PE     3d30000- 3f19000    Deferred        jasccmdfile
PE     3f20000- 4004000    Deferred        jasccmdgeometry
PE     4010000- 4038000    Deferred        jasccmdjgl
PE     4040000- 41c9000    Deferred        jasccmdlayers
PE     41d0000- 4215000    Deferred        jasccmdlighting
PE     4220000- 4522000    Deferred        jasccmdnongraphic
PE     4530000- 47af000    Deferred        jasccmdphoto
PE     47b0000- 4806000    Deferred        jasccmdpluginhost
PE     4810000- 484e000    Deferred        jasccmdprint
PE     4850000- 48c8000    Deferred        jasccmdpyscript
PE     48d0000- 49f8000    Deferred        jasccmdselections
PE     4a00000- 4b2b000    Deferred        jasccmdstandard
PE     4b30000- 4bd1000    Deferred        jasccmdtexture
PE     4be0000- 4bea000    Deferred        jasccmdui
PE     4bf0000- 4c86000    Deferred        jasccmdvector
PE     4c90000- 4d2d000    Deferred        jasccmdweb
PE     4d30000- 4f1c000    Deferred        jasctoolobject
PE     4f20000- 51e6000    Deferred        jasctoolpaint
PE     51f0000- 5278000    Deferred        jasctoolselect
PE     5280000- 5367000    Deferred        jasctoolstandard
PE     5370000- 5401000    Deferred        jasctooltext
PE     5410000- 54f3000    Deferred        jasctoolwarp
PE    10000000-1012d000    Deferred        jascworkspace
PE    1e000000-1e0cf000    Deferred        python22
PE    5f400000-5f4f2000    Export          mfc42
PE    780a0000-780b2000    Deferred        msvcirt
PE    780c0000-78121000    Deferred        msvcp60
PE    7ac10000-7ac23000    Deferred        riched20
PE    7b420000-7b5c6000    Export          kernel32
PE    7bc10000-7bc14000    Deferred        ntdll
PE    7d470000-7d473000    Deferred        wintab32
PE    7d490000-7d494000    Deferred        sti
PE    7d8a0000-7d8a4000    Deferred        ws2_32
PE    7d8d0000-7d8e8000    Deferred        wininet
PE    7dde0000-7ddea000    Deferred        actxprxy
PE    7df10000-7df1a000    Deferred        mpr
PE    7df30000-7df35000    Deferred        atl
PE    7df70000-7df74000    Deferred        uxtheme
PE    7e9a0000-7e9a4000    Deferred        riched32
PE    7ec20000-7ec24000    Deferred        winex11
PE    7eec0000-7ef60000    Deferred        comdlg32
PE    7efc0000-7efc8000    Deferred        oleaut32
PE    7f0f0000-7f0f4000    Deferred        imm32
PE    7f110000-7f113000    Deferred        usp10
PE    7f150000-7f1a0000    Deferred        comctl32
PE    7f290000-7f3f3000    Deferred        shell32
PE    7f4e0000-7f4ea000    Deferred        winspool
PE    7f530000-7f534000    Deferred        msvcrt
PE    7f5d0000-7f5d9000    Deferred        msacm32
PE    7f600000-7f604000    Deferred        rpcrt4
PE    7f690000-7f6b8000    Deferred        ole32
PE    7f7e0000-7f858000    Deferred        winmm
PE    7f890000-7f894000    Deferred        advapi32
PE    7f910000-7f917000    Deferred        gdi32
PE    7fa40000-7fb06000    Deferred        user32
PE    7fc20000-7fc28000    Deferred        shlwapi
PE    7ffd0000-7ffd4000    Deferred        version
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000037    0
    00000026    0
    00000023    0
    0000001e    0
    00000018    0
    00000013    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    0000001b    0
    00000017    0
    00000016    0
    00000012    0
0000001c plugplay.exe
    00000020    0
    0000001f    0
    0000001d    0
00000021 winedevice.exe
    0000002b    0
    00000025    0
    00000024    0
    00000022    0
00000029 explorer.exe
    0000002e    0
    0000002d    0
    0000002c    0
    0000002a    0
0000002f (D) C:\Program Files (x86)\Jasc Software Inc\Paint Shop Pro 8\Paint Shop Pro.exe
    0000003f    0
    0000003e    0
    00000033    0
    00000032    0
    00000031    0
    00000030    0 <==
00000035 svchost.exe
    00000043    0
    00000042    0
    00000041    0
    00000040    0
    0000003d    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000039    0
    00000036    0
System information:
    Wine build: wine-3.5 (Ubuntu 3.5-1)
    Platform: i386 (WOW64)
    Version: Windows 7
    Host system: Linux
    Host version: 4.15.0-15-generic
```


Ideas any one?

---

### Post by armrek on 2018-04-22
I have also gotten some leeway with PlayOnLinux but there the installer is minimized, after I have selected Install Paint Shop Pro 8, and you can only move the title around in the screen?

[IMG]http://schwartzengine.com/temp/MinimizedInstallerPSP8.png[/IMG]

I can move this little window around on the screen but not maximize it, and I can sort of see how it should have looked in the launcher bar. There is an OK and Cancel button to go ahead and install and some other options in this first window, but whit is it locked?

Any ideas are welcome!

But I am carrying on, this has to work! 

But it is beginning to feel a little uphill...

Help! :-)

---

### Post by armrek on 2018-05-01
I have a confession, there is no Splash Window problem!

I have fooled myself since I had copied the files from the PSP CD folder and then stopped during the copy leaving a half finished copy to install from. Hence the unresponsive Splash, it simply could not find the programs I was ordering it to install ;-)

What a classic mistake I'd a maker'. 

I have however still to problem that PSP crashes once it has started as shown below, so... Help! :-)

```
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x7f545c76).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:006b GS:0063
 EIP:7f545c76 ESP:003387f0 EBP:00338818 EFLAGS:00010293(  R- --  I S -A- -C)
 EAX:0012fb48 EBX:7f5bddb8 ECX:00338830 EDX:0012fb48
 ESI:00000000 EDI:00338958
Stack dump:
0x003387f0:  00338f00 0012fb48 5f403844 00338814
0x00338800:  00339ea0 7f545c46 00338830 7f5bddb8
0x00338810:  00338958 0012fb48 00338868 7f545f76
0x00338820:  00000000 02e1a460 7f58358b 7f545f76
0x00338830:  00338958 7f5bddb8 00338868 7f545f5c
0x00338840:  01286c3a 0012fb48 00339ea0 00000000
Backtrace:
=>0 0x7f545c76 (0x00338818)
  1 0x7f545f76 (0x00338868)
  2 0x7f547268 (0x00338a38)
  3 0x7f54601a (0x00338a98)
  4 0x7bc7dfab (0x00338ab8)
  5 0x7bc80993 (0x00338b28)
  6 0x7bc7ded2 (0x00338e18)
  7 0x7b43ce2c in kernel32 (+0x1ce2b) (0x00338ea8)
  8 0x7f53d461 (0x00338ee8)
  9 0x0034394f in jascerrorcodes (+0x394e) (0x00339ec0)
  10 0x004901f6 in paint shop pro (+0x901f5) (0x0033a160)
  11 0x00f04015 in jascfileutil (+0x4014) (0x0033a444)
  12 0x00f03b19 in jascfileutil (+0x3b18) (0x0033a570)
  13 0x00f063cd in jascfileutil (+0x63cc) (0x0033a814)
  14 0x00494034 in paint shop pro (+0x94033) (0x0033a998)
  15 0x0049124d in paint shop pro (+0x9124c) (0x0033a9e0)
  16 0x004744af in paint shop pro (+0x744ae) (0x0033fe00)
  17 0x5f40b4f3 in mfc42 (+0xb4f2) (0x0033fec0)
  18 0x7b46255c in kernel32 (+0x4255b) (0x0033fed8)
  19 0x7b463f8e in kernel32 (+0x43f8d) (0x0033ffd8)
  20 0x7b46256a in kernel32 (+0x42569) (0x0033ffec)
0x7f545c76: movl    0x4(%esi),%eax
Modules:
Module    Address            Debug info    Name (100 modules)
PE      340000-  351000    Export          jascerrorcodes
PE      360000-  36e000    Deferred        jasclanguage
PE      370000-  37b000    Deferred        jascmemory
PE      380000-  3a8000    Deferred        jasccolormgr
PE      3b0000-  3bb000    Deferred        jascsingletonmgr
PE      3c0000-  3f1000    Deferred        jascdebugtools
PE      400000-  876000    Export          paint shop pro
PE      880000-  95f000    Deferred        sxlrt308
PE      960000-  ad5000    Deferred        jascrender
PE      ae0000-  d93000    Deferred        jascfileformats
PE      da0000-  deb000    Deferred        pcdlib32
PE      df0000-  ef5000    Deferred        jasccontrols
PE      f00000-  ff4000    Export          jascfileutil
PE     1000000- 103c000    Deferred        jascimagegear
PE     1040000- 11fe000    Deferred        gear12d
PE     1200000- 138c000    Deferred        jasccommandbase
PE     1390000- 13ee000    Deferred        jasccmdproc
PE     13f0000- 1450000    Deferred        jascmip
PE     1450000- 146b000    Deferred        jasccmyk
PE     1470000- 14fa000    Deferred        jascmaterialpalette
PE     1500000- 1522000    Deferred        jascbrowserutil
PE     1530000- 15b2000    Deferred        jascbrowser
PE     15c0000- 1603000    Deferred        cmydb
PE     1610000- 1623000    Deferred        jasclearningcenter
PE     1630000- 1639000    Deferred        jasccapture
PE     1640000- 1685000    Deferred        jasclayerpalette
PE     1690000- 16b0000    Deferred        jascpreferences
PE     16b0000- 1773000    Deferred        jasctoolbase
PE     2360000- 2433000    Deferred        igcad
PE     2550000- 2559000    Deferred        igdgn
PE     2560000- 2580000    Deferred        igfpx
PE     2580000- 25d2000    Deferred        fpxig
PE     25e0000- 25f5000    Deferred        jpegacc
PE     2820000- 2837000    Deferred        ighpgl
PE     2950000- 298d000    Deferred        igjpeg2k
PE     2990000- 29db000    Deferred        kdu_v32r
PE     2af0000- 2b0c000    Deferred        iglzw
PE     3920000- 3aaa000    Deferred        jasccmdartistic
PE     3ab0000- 3b09000    Deferred        jasccmdbevels
PE     3b10000- 3b40000    Deferred        jasccmdbrowse
PE     3b40000- 3bdd000    Deferred        jasccmdclipboard
PE     3be0000- 3d0a000    Deferred        jasccmdcolor
PE     3d10000- 3d2b000    Deferred        jasccmdexternal
PE     3d30000- 3f19000    Deferred        jasccmdfile
PE     3f20000- 4004000    Deferred        jasccmdgeometry
PE     4010000- 4038000    Deferred        jasccmdjgl
PE     4040000- 41c9000    Deferred        jasccmdlayers
PE     41d0000- 4215000    Deferred        jasccmdlighting
PE     4220000- 4522000    Deferred        jasccmdnongraphic
PE     4530000- 47af000    Deferred        jasccmdphoto
PE     47b0000- 4806000    Deferred        jasccmdpluginhost
PE     4810000- 484e000    Deferred        jasccmdprint
PE     4850000- 48c8000    Deferred        jasccmdpyscript
PE     48d0000- 49f8000    Deferred        jasccmdselections
PE     4a00000- 4b2b000    Deferred        jasccmdstandard
PE     4b30000- 4bd1000    Deferred        jasccmdtexture
PE     4be0000- 4bea000    Deferred        jasccmdui
PE     4bf0000- 4c86000    Deferred        jasccmdvector
PE     4c90000- 4d2d000    Deferred        jasccmdweb
PE     4d30000- 4f1c000    Deferred        jasctoolobject
PE     4f20000- 51e6000    Deferred        jasctoolpaint
PE     51f0000- 5278000    Deferred        jasctoolselect
PE     5280000- 5367000    Deferred        jasctoolstandard
PE     5370000- 5401000    Deferred        jasctooltext
PE     5410000- 54f3000    Deferred        jasctoolwarp
PE    10000000-1012d000    Deferred        jascworkspace
PE    1e000000-1e0cf000    Deferred        python22
PE    5f400000-5f4f2000    Export          mfc42
PE    780a0000-780b2000    Deferred        msvcirt
PE    780c0000-78121000    Deferred        msvcp60
PE    7ac10000-7ac23000    Deferred        riched20
PE    7b420000-7b5c6000    Export          kernel32
PE    7bc10000-7bc14000    Deferred        ntdll
PE    7d470000-7d473000    Deferred        wintab32
PE    7d490000-7d494000    Deferred        sti
PE    7d8a0000-7d8a4000    Deferred        ws2_32
PE    7d8d0000-7d8e8000    Deferred        wininet
PE    7dde0000-7ddea000    Deferred        actxprxy
PE    7df10000-7df1a000    Deferred        mpr
PE    7df30000-7df35000    Deferred        atl
PE    7df70000-7df74000    Deferred        uxtheme
PE    7e9a0000-7e9a4000    Deferred        riched32
PE    7ec20000-7ec24000    Deferred        winex11
PE    7eec0000-7ef60000    Deferred        comdlg32
PE    7efc0000-7efc8000    Deferred        oleaut32
PE    7f0f0000-7f0f4000    Deferred        imm32
PE    7f110000-7f113000    Deferred        usp10
PE    7f150000-7f1a0000    Deferred        comctl32
PE    7f290000-7f3f3000    Deferred        shell32
PE    7f4e0000-7f4ea000    Deferred        winspool
PE    7f530000-7f534000    Deferred        msvcrt
PE    7f5d0000-7f5d9000    Deferred        msacm32
PE    7f600000-7f604000    Deferred        rpcrt4
PE    7f690000-7f6b8000    Deferred        ole32
PE    7f7e0000-7f858000    Deferred        winmm
PE    7f890000-7f894000    Deferred        advapi32
PE    7f910000-7f917000    Deferred        gdi32
PE    7fa40000-7fb06000    Deferred        user32
PE    7fc20000-7fc28000    Deferred        shlwapi
PE    7ffd0000-7ffd4000    Deferred        version
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000037    0
    00000026    0
    00000023    0
    0000001e    0
    00000018    0
    00000013    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    0000001b    0
    00000017    0
    00000016    0
    00000012    0
0000001c plugplay.exe
    00000020    0
    0000001f    0
    0000001d    0
00000021 winedevice.exe
    0000002b    0
    00000025    0
    00000024    0
    00000022    0
00000029 explorer.exe
    0000002e    0
    0000002d    0
    0000002c    0
    0000002a    0
0000002f (D) C:\Program Files (x86)\Jasc Software Inc\Paint Shop Pro 8\Paint Shop Pro.exe
    0000003f    0
    0000003e    0
    00000033    0
    00000032    0
    00000031    0
    00000030    0 <==
00000035 svchost.exe
    00000043    0
    00000042    0
    00000041    0
    00000040    0
    0000003d    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000039    0
    00000036    0
System information:
    Wine build: wine-3.5 (Ubuntu 3.5-1)
    Platform: i386 (WOW64)
    Version: Windows 7
    Host system: Linux
    Host version: 4.15.0-15-generic
```

It worked in wine-1.6.2, but here it crashes any suggestions are welcome :-)

---

### Post by armrek on 2018-05-12
Some more progress, see the Next Post...

But the questions Am I the only one using Good Old Paint Shop Pro 8.0?

---

### Post by armrek on 2018-05-12
Some more progress...

PSP8 CD files installs both the Paint Shop Pro 8 and the Animation Shop 3.

The Animation Shop runs like it used to with the exception that a small dialog saying:

[I]Electronic registration Register.exe program not
found. You may need to reinstall the product.[/I]

After clicking OK in this dialog Animation Shop 3 runs as normal, and the dialog will not reappear when starting Animation Shop 3 again.

But Paint Shop Pro 8 still has problems and crashes during start up:


[LIST]
[*]It shows the Splash loading DLLs 
[*]It shows the main window behind the splash 
[*]When the Splash reads*Initializing Color Swatches*, it Crashes as described above! 
[/LIST]
 
I have even succeeded in updating Paint Shop Pro 8.0 to 8.1 calling *wine psp810enp.exe  *in a terminal, this it not straight forward as a preparation you have to:


[LIST]
[*]cd to the installation directory of Paint Shop Pro (/home/username/.wine/drive_c/Program Files (x86)/Jasc Software Inc) 
[*]call *'chmod -R 777 .*', to give read/write/execute to all file in the folder, because the installed tries to overwrite dlls and script when updating and will fail if they are write protected 
[/LIST]

I learned this the hard way, but now I know. It was mi tiny tiny hope :-) that this wuold be an ailment for bug, but no. But at least I can now update on my main machine to 8.10...
 
I have filed this bug in WineHQ through their Bugzilla,  BUT ANY suggestions are welcome.

---

