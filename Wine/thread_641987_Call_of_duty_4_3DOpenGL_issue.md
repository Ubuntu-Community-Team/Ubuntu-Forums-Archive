---
title: "Call of duty 4 3D/OpenGL issue"
date: 2007-12-16
forum: Wine
---

### Post by P.tritas on 2007-12-16
Hello all,
I have a Sony Vaio FE31H laptop. Is has 1GB of RAM and a 256 graphics card ( Nvidia GeForce Go 7400 ) which accepts TurboCharge up to 316MB ( haven't found a programm to use this feature, but anyway).
I have the Call of Duty 4 game, which says you need at least a 550 GeForce card. The problem is that although mine is a 7400, when I try to run the game (I installed it using Wine, not PlayOnLinux (yet) ) it says something about "alpha blend" and "glow" that "will be disabled".
I searched a little bit the .net and found that this message appears when one's graphic card isn't good enought.
Well, my laptop not only the "required hardware" but also the "recommended", meaning that it normally should be able to play on my computer!
Finally, I personally believe that the problem comes from the Graphic card's drivers. 
Has anyone any idea how to run the game?
Thanks a lot,
PhiL
P.S: I'll try to install COD4 using PlayOnLinux, it may work!
P.S2: It must be an OpenGL problem, because Counter-Strike:Source doesn't load either!

---

### Post by ahaslam on 2007-12-16
This guide looks good: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4&back=HOWTO+INDEX+Wine+Games)

Let us know how it goes, I'll be getting this game soon ;)

---

### Post by P.tritas on 2007-12-16
Thanks for the link :)
In the tutorial, it is written:

"   1. Get latest wine git tree (or cvs).
   2. Get patch for wine.
   3. Get a no cd patch for COD4.
   4. Make sure you have the latest DirectX 9.0c files in your system32 folder of your wine drive. You can copy d3dx9_24.dll...d3dx9_35.dll from an existing Windows installation. "

Can anybody detail these steps?
I have downloaded the wine git tree, but don't know how to install it.
Patch for Wine?
I don't need for the CD to run COD4, so I believe step 3 is ok.
Step 4 : I believe to have installed DirectX 9.0c, as I have run the .exe and is "installed succesfully". 

Sorry to be so noob :(
PhiL

---

### Post by cogadh on 2007-12-16
Don't actually install DirectX, it overwrites the Wine versions of Direct3D, DirectSound and DirectInput and prevents them from working. Just copy the listed DLLs from a Windows machine and override them in winecfg.

As for the steps, the patch is linked to in the how-to, you need to apply it to the extracted Wine git download. To apply it, change directories to where you have the git files extracted, then run this:
```
patch -p1 < /path/to/patchfile
```
Then you need to compile and install Wine:
```
./configure
make depend && make
su -c "make install"
```

---

### Post by ahaslam on 2007-12-16
> Step 4 : I believe to have installed DirectX 9.0c, as I have run the .exe and is "installed succesfully". 
[http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_34](http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_34) ;)

PS. More info: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9699&iTestingId=18036](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9699&iTestingId=18036)

---

### Post by P.tritas on 2007-12-26
Sorry guys, but the problem persists: 
I uninstalled COD4, and now when I try to run the installer I have a InstallShield error which says:
"1628: Failed to complete installation"
I have copy-pasted all the DirectX9 files into my windows>system32 folders.

---

### Post by ahaslam on 2007-12-30
Just tried it & it works quite well.
Just grab the source for wine 0.9.50 & apply the patch provided in my 1st link with ```
patch -p1 < path/to/3dmark.diff || return 1
```
You'll need a no-cd crack, which google will provide, the d3dx9_34.dll provided above & you'll need to turn off/reduce most of the special effects. What you're left with may not be graphically awe-inspiring, but it does run at a decent speed.

I had to jump through another hoop (chroot) as I run a 64-bit only os. Here's COD4 in action:

---

### Post by ahaslam on 2007-12-30
Update: This has got to be one of the best modern games for wine, it runs much better than Oblivion. ;)

---

### Post by ahaslam on 2007-12-31
& here's my current settings & their effects:

---

### Post by P.tritas on 2007-12-31
First of all, thanks A LOT for your help and interest :)

Should I run the patch for wine throught the COD4 folder (meaning the directory where it is installed) ?
Because it says "File to patch" (which I believe means that it didn't find some files it was searching for).
P.S: Stop posting photos, you're making me mad! I really want to play this game so bad! :P

---

### Post by ahaslam on 2007-12-31
I'll write a cut & paste guide later if you like... (do check it tho...) ;)

---

### Post by EXCiD3 on 2007-12-31
Whenever I try to install games with Wine i go to [http://www.linux-gamers.net](http://www.linux-gamers.net). They have a COD4 Tutorial here: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4)

Can't wait to try it myself...i need highspeed internet to download some stuff first so its going to be a few days before i can try it :( Parents are still running on dialdown...

---

### Post by ahaslam on 2007-12-31
This should be a straightforward way of installing a patched wine (which I assume is the problem here), just issue one line at a time:

[I]Amd64 users should look [here]("http://wiki.winehq.org/WineOn64bit#head-c47d9e53f952c5b6260467e0dc158321229216de") for a few additional steps. Basically, you'll need the extra dep's, links & ./configure options.
[/I]
Clean up & get some dep's :
```
sudo apt-get remove wine
rm -r ~/.wine
sudo apt-get build-dep wine
sudo apt-get install build-essential checkinstall
```
Get wine, patch it & install it:
```
mkdir wine && cd wine
wget http://easynews.dl.sourceforge.net/sourceforge/wine/wine-0.9.50.tar.bz2
tar -xvjf wine-0.9.50.tar.bz2
wget http://bugs.winehq.org/attachment.cgi?id=8548
cp attachment.cgi\?id\=8548 wine-0.9.50/3dmark.diff && cd wine-0.9.50
patch -p1 < 3dmark.diff
./configure --prefix=/usr --sysconfdir=/etc --enable-opengl --with-x
make depend && make
sudo checkinstall
```
*Accept the defaults, an option will come up to set a description, set one and enter, select the next default, job done - checkinstall created a .deb package, installed it and left a copy in the folder you're working in.*

Set up wine: 
```
wineprefixcreate
winecfg
```
Now you need to set the 'Windows Version' to XP. While you're here I recommend that you visit the drives tab and use the 'Autodetect' button, double checking your CDROM path & drive type with the 'Show Advanced' button. 

Get the required DX9 dll:
```
mkdir dx9 && cd dx9
wget http://www.m3fe.com/files/d3dx9_34.zip
unzip d3dx9_34.zip
mv d3dx9_34.dll ~/.wine/drive_c/windows/system32/

```

Now it's time to install COD4:
```
cd /path/to/cdrom/
wine setup.exe
```

No-dvd crack - needed to launch:
Go to [gamecopyworld]("http://www.gamecopyworld.com/") & get the appropriate no-dvd/fixed exe, eg:
> Call of Duty 4 v1.0 [ENGLISH] No-DVD/Fixed EXE #2
Make a backup of your original iw3sp.exe (location shown below) before replacing it with the fixed exe.

Launch the game:
```
cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare && wine iw3sp.exe
```

Once launched you'll need to reduce some graphics options to avoid glitches & improve performance. Some options don't work & some just don't look right, I recommend that you disable the following:

Anti-aliasing - *Doesn't work.*
Sync Every Frame
Shadows 
Specular Map
Depth of Field
Glow
Number of Dynamic Lights
**Soften Smoke Edges** - *Unplayable with this option enabled.*


Good luck. I hope it works for you, let us know.

;)

PS. There seems to be little success with ATi cards atm. If you don't have any other DX9 games working with Wine, you may wish to avoid this lengthy process. If you've got the experience & get it working, please post what GPU & driver you're running, along with any deviations from my guide.

---

### Post by ahaslam on 2008-01-01
Just completed it, not a single problem throughout. It's the best game I've played on Linux, not just under wine.
As an unexpected bonus I just found the multiplayer to work as well. The 1.4 update & punkbuster don't seem too essential. 

Just as I thought it was all over, it's only just begun.

;)

---

### Post by RyanKage on 2008-01-01
This is awesome stuff, I tried this game at my buddies on his Xbox 360 and I'm really thinking about getting the Dell M1330 for college. I would love to play this game (during class lol) and on campus. I'm a total noob with WINE so I'll hopefully be able to get a copy and test this install on my crappy desktop (with Ubuntu on it). The four games I hope to get on the laptop (whenever the hell I can get it...) will be: Team Fortress 2, World of Warcraft, Portal, and Call of Duty 4. :) If any body has had any luck with these games via WINE and the M1330, let me know please.

---

### Post by Jagfandaddy on 2008-01-02
I am building a pc that I will put Ubuntu on it. I am so glad to see COD4 will run on this. Are there a lot of these games that will run under Linux?

---

### Post by ahaslam on 2008-01-02
> **Jagfandaddy said:**
> Are there a lot of these games that will run under Linux?
I know that Half-Life 2 & STALKER also work well, though FEAR & Bioshock don't even install. There's no guarantee as to what's going to work, just check linux-gamers & the wine app db.

---

### Post by Radon on 2008-01-02
IMHO for games that run in Linux, Stalker was the best game for H107 and CoD4/UT3 for H207.  

And of course there are games that run natively:

-Unreal Tournament 3 (official release in a few weeks, check Phoronix)
-Doom 3
-Quake 3, 4
-Enemy Territory: Quake Wars
-Ballistics
-X3
-Civilisation: Call to power
-Disciples 2
-Neverwinter Nights

Here is a list of [200+ native]("http://linux.strangegamer.com/index.php?title=Category:Native_Linux_Games") games.  Have a look at [linux-gamers]("http://www.linux-gamers.net/") and [phoronix]("http://www.phoronix.com/scan.php?page=home") for updates. :)

---

### Post by Jagfandaddy on 2008-01-02
Thanks for the reply. To be honest the last time I build a PC and installed a game  was 1991. I just recieved the mobo,ps,cpu and graphics card. Boy this is going to be fun!!! The games you have mentioned will be great to start with.

---

### Post by ahaslam on 2008-01-09
Anyone think this screenshot looks familiar?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9699](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9699)

I don't mind people using anything I've posted (it's a public forum), but saying it's from Gutsy with Wine 0.9.52 will only mislead & frustrate people. It's from Arch64 using Wine 0.9.50, the only version I currently recommend (patched of course).

On a lighter note, the game also cleanly patches to v1.4. This is not terribly important unless you fancy yourself as a sniper ;)

*PS. Only run the 1.4 patch if sniping is important to you. There are few 1.4 servers at this time, you'll need to decide between long-range accuracy & servers.*

---

### Post by save2 on 2008-01-10
just small correction of this thread title.
Unlike Quake, COD4 has nothing to do with OpenGL. They  support only  DirectX  API.

---

### Post by echo6 on 2008-01-12
> **ahaslam said:**
> Good luck. I hope it works for you, let us know.An additional step some may have to do is to change the default settings from Window 2000 using winecfg otherwise wine setup.exe complains it has no support for Windows NT, 2000/98/ME etc.

---

### Post by ahaslam on 2008-01-12
> **echo6 said:**
> An additional step some may have to do is to change the default settings from Window 2000 using winecfg otherwise wine setup.exe complains it has no support for Windows NT, 2000/98/ME etc.

Thanks for that, guide updated.

Happy fragging ;)

---

### Post by algoe on 2008-01-15
And here comes the mandatory "i can't get it to work"-post :)
The COD4 installer runs, seemingly fine, but when it is done lot's of files are missing, including the .exe's. I copied the missing files from a installation on my windows drive, but it didn't work. The resolution changes to whatever is the game default (alot smaller than my standard 1920x1200 at least ;) ) and then everyting freezes.
I am using the compiz effects in ubuntu gutsy, and have also tried deactivating this.
The only thing i can think of is this: on what gfx card are you running this? I have an ATI FireGL V5200 with the 7.12-drivers.
Any suggestions? What gfx cards do you have?

```
pinky@pinky-laptop1:~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$ wine iw3sp.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33f91c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x11440208) : pBox=(nil) stub
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #1: "Fragment shader was successfully compiled to run on hardware.\nWARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported"
fixme:d3d:state_separateblend (WINED3DRS_SEPARATEALPHABLENDENABLE,1) not yet implemented
wine: Unhandled page fault on write access to 0x00000000 at address 0x7c02c5c8 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7c02c5c8).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7c02c5c8 ESP:0033f494 EBP:0033f4d4 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7eb86380 ECX:00187190 EDX:7eb86fa0
 ESI:00000000 EDI:00000000
Stack dump:
0x0033f494:  7c02c9fc 7eb1ef3c 00008775 0019160c
0x0033f4a4:  00000001 0033f4cc 7eb86380 00000006
0x0033f4b4:  0033f4d4 00000000 00000002 00000002
0x0033f4c4:  00000001 7eb86380 00000006 00000044
0x0033f4d4:  0033f544 7eac84ff 000000d8 00187190
0x0033f4e4:  0021c468 7eb86380 00194fc8 7eb809b8
Backtrace:
=>1 0x7c02c5c8 (0x0033f4d4)
  2 0x7eac84ff ActivateContext+0x3ff() in wined3d (0x0033f544)
  3 0x7eaf4d0b drawPrimitive+0x15b() in wined3d (0x0033f7e4)
  4 0x7ead3dbd in wined3d (+0x23dbd) (0x0033f854)
  5 0x7eb9ee4e in d3d9 (+0xee4e) (0x0033f884)
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 415f013a in module L"iw3sp"
  6 0x00602691 in iw3sp (+0x202691) (0x00000000)
0x7c02c5c8: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (92 modules)
PE        400000- 2100e7c       Export          iw3sp
PE       2110000- 247f000       Deferred        d3dx9_34
PE       c4b0000- c4b6000       Deferred        mssds3d.flt
PE      10000000-10016000       Deferred        mileseq.flt
PE      18000000-18033000       Deferred        binkw32
PE      21100000-21197000       Deferred        mss32
PE      22300000-22311000       Deferred        msseax.flt
PE      24100000-24112000       Deferred        mssdsp.flt
PE      26400000-2642a000       Deferred        mssvoice.asi
PE      26f00000-26f20000       Deferred        mssmp3.asi
ELF     7b800000-7b92b000       Deferred        kernel32<elf>
  \-PE  7b820000-7b92b000       \               kernel32
ELF     7bbb6000-7bc00000       Deferred        dsound<elf>
  \-PE  7bbc0000-7bc00000       \               dsound
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bd08000-7bd3a000       Deferred        uxtheme<elf>
  \-PE  7bd10000-7bd3a000       \               uxtheme
ELF     7bd3a000-7be00000       Deferred        libasound.so.2
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf3d000-7bf52000       Deferred        midimap<elf>
  \-PE  7bf40000-7bf52000       \               midimap
ELF     7bf52000-7bf79000       Deferred        msacm32<elf>
  \-PE  7bf60000-7bf79000       \               msacm32
ELF     7bf79000-7bf91000       Deferred        msacm32<elf>
  \-PE  7bf80000-7bf91000       \               msacm32
ELF     7bf91000-7bfc7000       Deferred        winealsa<elf>
  \-PE  7bfa0000-7bfc7000       \               winealsa
ELF     7bfc7000-7bfd0000       Deferred        libxcursor.so.1
ELF     7bfd0000-7bfed000       Deferred        imm32<elf>
  \-PE  7bfe0000-7bfed000       \               imm32
ELF     7bfed000-7bff2000       Deferred        libxfixes.so.3
ELF     7bff2000-7bff8000       Deferred        libxrandr.so.2
ELF     7bff8000-7c000000       Deferred        libxrender.so.1
ELF     7c30e000-7c311000       Deferred        libxinerama.so.1
ELF     7c972000-7c975000       Deferred        libxcomposite.so.1
ELF     7d0e8000-7d0f1000       Deferred        librt.so.1
ELF     7d0f1000-7e2fa000       Deferred        fglrx_dri.so
ELF     7e2fa000-7e305000       Deferred        libgcc_s.so.1
ELF     7e305000-7e381000       Deferred        libgl.so.1
ELF     7e381000-7e386000       Deferred        libxdmcp.so.6
ELF     7e386000-7e389000       Deferred        libxau.so.6
ELF     7e389000-7e47a000       Deferred        libx11.so.6
ELF     7e47a000-7e488000       Deferred        libxext.so.6
ELF     7e488000-7e48d000       Deferred        libxxf86vm.so.1
ELF     7e48d000-7e4a5000       Deferred        libice.so.6
ELF     7e4a5000-7e4ad000       Deferred        libsm.so.6
ELF     7e4c0000-7e553000       Deferred        winex11<elf>
  \-PE  7e4d0000-7e553000       \               winex11
ELF     7e5b1000-7e5d1000       Deferred        libexpat.so.1
ELF     7e5d1000-7e5fc000       Deferred        libfontconfig.so.1
ELF     7e5fc000-7e611000       Deferred        libz.so.1
ELF     7e611000-7e681000       Deferred        libfreetype.so.6
ELF     7e681000-7e694000       Deferred        libresolv.so.2
ELF     7e6a7000-7e6c5000       Deferred        iphlpapi<elf>
  \-PE  7e6b0000-7e6c5000       \               iphlpapi
ELF     7e6c5000-7e721000       Deferred        rpcrt4<elf>
  \-PE  7e6d0000-7e721000       \               rpcrt4
ELF     7e721000-7e7c3000       Deferred        ole32<elf>
  \-PE  7e730000-7e7c3000       \               ole32
ELF     7e7c3000-7e818000       Deferred        ddraw<elf>
  \-PE  7e7d0000-7e818000       \               ddraw
ELF     7e818000-7e8d7000       Deferred        comctl32<elf>
  \-PE  7e820000-7e8d7000       \               comctl32
ELF     7e8d7000-7e930000       Deferred        shlwapi<elf>
  \-PE  7e8f0000-7e930000       \               shlwapi
ELF     7e930000-7ea34000       Deferred        shell32<elf>
  \-PE  7e940000-7ea34000       \               shell32
ELF     7ea34000-7ea9c000       Deferred        msvcrt<elf>
  \-PE  7ea50000-7ea9c000       \               msvcrt
ELF     7ea9c000-7eb88000       Export          wined3d<elf>
  \-PE  7eab0000-7eb88000       \               wined3d
ELF     7eb88000-7ebb7000       Export          d3d9<elf>
  \-PE  7eb90000-7ebb7000       \               d3d9
ELF     7ebb7000-7ec03000       Deferred        advapi32<elf>
  \-PE  7ebc0000-7ec03000       \               advapi32
ELF     7ec03000-7ec9b000       Deferred        gdi32<elf>
  \-PE  7ec10000-7ec9b000       \               gdi32
ELF     7ec9b000-7edd8000       Deferred        user32<elf>
  \-PE  7ecc0000-7edd8000       \               user32
ELF     7edd8000-7ee66000       Deferred        winmm<elf>
  \-PE  7ede0000-7ee66000       \               winmm
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d32000-b7d36000       Deferred        libdl.so.2
ELF     b7d36000-b7e80000       Deferred        libc.so.6
ELF     b7e81000-b7e99000       Deferred        libpthread.so.0
ELF     b7eac000-b7fc0000       Deferred        libwine.so.1
ELF     b7fc2000-b7fde000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3sp.exe
        00000012    0
        00000011    0
        00000010   15
        0000000e   15
        0000000d   -1
        00000009    0 <==
Backtrace:
=>1 0x7c02c5c8 (0x0033f4d4)
  2 0x7eac84ff ActivateContext+0x3ff() in wined3d (0x0033f544)
  3 0x7eaf4d0b drawPrimitive+0x15b() in wined3d (0x0033f7e4)
  4 0x7ead3dbd in wined3d (+0x23dbd) (0x0033f854)
  5 0x7eb9ee4e in d3d9 (+0xee4e) (0x0033f884)
  6 0x00602691 in iw3sp (+0x202691) (0x00000000)
err:ntdll:RtlpWaitForCriticalSection section 0x7ebb6e90 "d3d9_main.c: d3d9_cs" wait timed out in thread 000d, blocked by 0009, retrying (60 sec)


```

---

### Post by ahaslam on 2008-01-15
> The COD4 installer runs, seemingly fine, but when it is done lot's of files are missingThat's strange, you don't even need to patch Wine for the installation. :-k
> The only thing i can think of is this: on what gfx card are you running this?BFG 7950GT 512MB OC here. I know little of the red team's cards, but I'm sure there *was* little support for many shader features. However newer drivers *may* have addressed this for some GPUs.

I recommend that you install the latest driver for your card & reboot. Then open a terminal and issue: 
```
regedit
```
Now try the following (borrowed from Mongoose to save my keyboard):

Navigate to HKEY_CURRENT_USER / Software / Wine / Direct3D
If the Direct3D key folder does not exist then you can create it yourself:

    * 1. Right-click on the Wine folder icon.
    * 2. Select New > Key from the pop-up menu.
    * 3. Name the new 'folder' key "Direct3D" without the quotes. 

Once you find or create the Direct3D key you can enable shaders in Wine:

    * 1. Select the Direct3D key folder icon.
    * 2. Right-click the mouse in the pane to the right to open the right-click menu.
    * 3. Use the right-click menu command New > String Value to create each of the following key pairs: 
```
OffscreenRenderingMode   fbo    [I](more stable than pbuffer)
[/I]VideoMemorySize          256    *(or whatever your card has)*
```

If it still fails, you could either try removing you Activision directory & reinstalling, or copying it over from your Windows install. 

That's all I can suggest atm, I hope it helps a little. ;)

PS. I see you're already running the latest driver, 1 less step for you then :rolleyes:

---

### Post by algoe on 2008-01-15
Now i get this output, same both from windows partition and the linux install: (with the regedit stuff done)

```
wine iw3sp.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33f91c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xfca0110) : pBox=(nil) stub
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #1: "Fragment shader was successfully compiled to run on hardware.\nWARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported"
fixme:d3d:state_separateblend (WINED3DRS_SEPARATEALPHABLENDENABLE,1) not yet implemented
wine: Unhandled page fault on write access to 0x00000000 at address 0x7c02c5c0 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7c02c5c0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7c02c5c0 ESP:0033f494 EBP:0033f4d4 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7eb86380 ECX:00186e98 EDX:7eb86fa0
 ESI:00000000 EDI:00000000
Stack dump:
0x0033f494:  7c02c9f4 7eb1ef3c 00008775 00191314
0x0033f4a4:  00000001 0033f4cc 7eb86380 00000006
0x0033f4b4:  0033f4d4 00000000 00000002 00000002
0x0033f4c4:  00000001 7eb86380 00000006 00000044
0x0033f4d4:  0033f544 7eac84ff 000000d8 00186e98
0x0033f4e4:  0021c638 7eb86380 00194cd0 7eb809b8
Backtrace:
=>1 0x7c02c5c0 (0x0033f4d4)
  2 0x7eac84ff ActivateContext+0x3ff() in wined3d (0x0033f544)
  3 0x7eaf4d0b drawPrimitive+0x15b() in wined3d (0x0033f7e4)
  4 0x7ead3dbd in wined3d (+0x23dbd) (0x0033f854)
  5 0x7eb9ee4e in d3d9 (+0xee4e) (0x0033f884)
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 415f013a in module L"iw3sp"
  6 0x00602691 in iw3sp (+0x202691) (0x00000000)
0x7c02c5c0: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (92 modules)
PE        400000- 2100e7c       Export          iw3sp
PE       2110000- 247f000       Deferred        d3dx9_34
PE       c4b0000- c4b6000       Deferred        mssds3d.flt
PE      10000000-10016000       Deferred        mileseq.flt
PE      18000000-18033000       Deferred        binkw32
PE      21100000-21197000       Deferred        mss32
PE      22300000-22311000       Deferred        msseax.flt
PE      24100000-24112000       Deferred        mssdsp.flt
PE      26400000-2642a000       Deferred        mssvoice.asi
PE      26f00000-26f20000       Deferred        mssmp3.asi
ELF     7b800000-7b92b000       Deferred        kernel32<elf>
  \-PE  7b820000-7b92b000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bcbf000-7bd09000       Deferred        dsound<elf>
  \-PE  7bcd0000-7bd09000       \               dsound
ELF     7bd3a000-7be00000       Deferred        libasound.so.2
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf03000-7bf35000       Deferred        uxtheme<elf>
  \-PE  7bf10000-7bf35000       \               uxtheme
ELF     7bf45000-7bf5a000       Deferred        midimap<elf>
  \-PE  7bf50000-7bf5a000       \               midimap
ELF     7bf5a000-7bf81000       Deferred        msacm32<elf>
  \-PE  7bf60000-7bf81000       \               msacm32
ELF     7bf81000-7bf99000       Deferred        msacm32<elf>
  \-PE  7bf90000-7bf99000       \               msacm32
ELF     7bf99000-7bfcf000       Deferred        winealsa<elf>
  \-PE  7bfa0000-7bfcf000       \               winealsa
ELF     7bfcf000-7bfd8000       Deferred        libxcursor.so.1
ELF     7bfd8000-7bff5000       Deferred        imm32<elf>
  \-PE  7bfe0000-7bff5000       \               imm32
ELF     7bff5000-7bffa000       Deferred        libxfixes.so.3
ELF     7bffa000-7c000000       Deferred        libxrandr.so.2
ELF     7c30f000-7c317000       Deferred        libxrender.so.1
ELF     7c317000-7c31a000       Deferred        libxinerama.so.1
ELF     7c97b000-7c97e000       Deferred        libxcomposite.so.1
ELF     7d0f1000-7d0fa000       Deferred        librt.so.1
ELF     7d0fa000-7e303000       Deferred        fglrx_dri.so
ELF     7e303000-7e30e000       Deferred        libgcc_s.so.1
ELF     7e30e000-7e38a000       Deferred        libgl.so.1
ELF     7e38a000-7e38f000       Deferred        libxdmcp.so.6
ELF     7e38f000-7e392000       Deferred        libxau.so.6
ELF     7e392000-7e483000       Deferred        libx11.so.6
ELF     7e483000-7e491000       Deferred        libxext.so.6
ELF     7e491000-7e496000       Deferred        libxxf86vm.so.1
ELF     7e496000-7e4ae000       Deferred        libice.so.6
ELF     7e4ae000-7e4b6000       Deferred        libsm.so.6
ELF     7e4c9000-7e55c000       Deferred        winex11<elf>
  \-PE  7e4e0000-7e55c000       \               winex11
ELF     7e5b1000-7e5d1000       Deferred        libexpat.so.1
ELF     7e5d1000-7e5fc000       Deferred        libfontconfig.so.1
ELF     7e5fc000-7e611000       Deferred        libz.so.1
ELF     7e611000-7e681000       Deferred        libfreetype.so.6
ELF     7e681000-7e694000       Deferred        libresolv.so.2
ELF     7e6a7000-7e6c5000       Deferred        iphlpapi<elf>
  \-PE  7e6b0000-7e6c5000       \               iphlpapi
ELF     7e6c5000-7e721000       Deferred        rpcrt4<elf>
  \-PE  7e6d0000-7e721000       \               rpcrt4
ELF     7e721000-7e7c3000       Deferred        ole32<elf>
  \-PE  7e730000-7e7c3000       \               ole32
ELF     7e7c3000-7e818000       Deferred        ddraw<elf>
  \-PE  7e7d0000-7e818000       \               ddraw
ELF     7e818000-7e8d7000       Deferred        comctl32<elf>
  \-PE  7e820000-7e8d7000       \               comctl32
ELF     7e8d7000-7e930000       Deferred        shlwapi<elf>
  \-PE  7e8f0000-7e930000       \               shlwapi
ELF     7e930000-7ea34000       Deferred        shell32<elf>
  \-PE  7e940000-7ea34000       \               shell32
ELF     7ea34000-7ea9c000       Deferred        msvcrt<elf>
  \-PE  7ea50000-7ea9c000       \               msvcrt
ELF     7ea9c000-7eb88000       Export          wined3d<elf>
  \-PE  7eab0000-7eb88000       \               wined3d
ELF     7eb88000-7ebb7000       Export          d3d9<elf>
  \-PE  7eb90000-7ebb7000       \               d3d9
ELF     7ebb7000-7ec03000       Deferred        advapi32<elf>
  \-PE  7ebc0000-7ec03000       \               advapi32
ELF     7ec03000-7ec9b000       Deferred        gdi32<elf>
  \-PE  7ec10000-7ec9b000       \               gdi32
ELF     7ec9b000-7edd8000       Deferred        user32<elf>
  \-PE  7ecc0000-7edd8000       \               user32
ELF     7edd8000-7ee66000       Deferred        winmm<elf>
  \-PE  7ede0000-7ee66000       \               winmm
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ca0000-b7ca9000       Deferred        libnss_compat.so.2
ELF     b7caa000-b7cae000       Deferred        libdl.so.2
ELF     b7cae000-b7df8000       Deferred        libc.so.6
ELF     b7df9000-b7e11000       Deferred        libpthread.so.0
ELF     b7e24000-b7f38000       Deferred        libwine.so.1
ELF     b7f3a000-b7f56000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\pinky\Spel\KRIG\iw3sp.exe
        00000012    0
        00000011    0
        00000010   15
        0000000e   15
        0000000d   -1
        00000009    0 <==
Backtrace:
=>1 0x7c02c5c0 (0x0033f4d4)
  2 0x7eac84ff ActivateContext+0x3ff() in wined3d (0x0033f544)
  3 0x7eaf4d0b drawPrimitive+0x15b() in wined3d (0x0033f7e4)
  4 0x7ead3dbd in wined3d (+0x23dbd) (0x0033f854)
  5 0x7eb9ee4e in d3d9 (+0xee4e) (0x0033f884)
  6 0x00602691 in iw3sp (+0x202691) (0x00000000)
err:ntdll:RtlpWaitForCriticalSection section 0x7ebb6e90 "d3d9_main.c: d3d9_cs" wait timed out in thread 000d, blocked by 0009, retrying (60 sec)
pinky@pinky-laptop1:~/Spel/KRIG$ regedit
pinky@pinky-laptop1:~/Spel/KRIG$ wine iw3sp.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33f91c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe5522a8) : pBox=(nil) stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0xc6077c8) Event query: Unimplemented, but pretending to be supported
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #1: "Fragment shader was successfully compiled to run on hardware.\nWARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported"
fixme:d3d:state_separateblend (WINED3DRS_SEPARATEALPHABLENDENABLE,1) not yet implemented
wine: Unhandled page fault on write access to 0x00000000 at address 0x7c02c637 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7c02c637).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7c02c637 ESP:0033f490 EBP:0033f4d5 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:7eb86380 ECX:001a90d8 EDX:7eb86fa0
 ESI:00000000 EDI:7c02ca65
Stack dump:
0x0033f490:  7eb86fa0 00000000 7eb1ef3c 00008775
0x0033f4a0:  001b3554 00000001 0033f4cc 7eb86380
0x0033f4b0:  00000006 0033f4d4 00000000 00000002
0x0033f4c0:  00000002 00000001 7eb86380 00000006
0x0033f4d0:  00000044 0033f544 7eac84ff 000000d8
0x0033f4e0:  001a90d8 0c9e0050 7eb86380 00186770
Backtrace:
=>1 0x7c02c637 (0x0033f4d5)
0x7c02c637: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (92 modules)
PE        400000- 2100e7c       Deferred        iw3sp
PE       2110000- 247f000       Deferred        d3dx9_34
PE       c4b0000- c4b6000       Deferred        mssds3d.flt
PE      10000000-10016000       Deferred        mileseq.flt
PE      18000000-18033000       Deferred        binkw32
PE      21100000-21197000       Deferred        mss32
PE      22300000-22311000       Deferred        msseax.flt
PE      24100000-24112000       Deferred        mssdsp.flt
PE      26400000-2642a000       Deferred        mssvoice.asi
PE      26f00000-26f20000       Deferred        mssmp3.asi
ELF     7b800000-7b92b000       Deferred        kernel32<elf>
  \-PE  7b820000-7b92b000       \               kernel32
ELF     7bbb6000-7bc00000       Deferred        dsound<elf>
  \-PE  7bbc0000-7bc00000       \               dsound
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bd08000-7bd3a000       Deferred        uxtheme<elf>
  \-PE  7bd10000-7bd3a000       \               uxtheme
ELF     7bd3a000-7be00000       Deferred        libasound.so.2
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf43000-7bf58000       Deferred        midimap<elf>
  \-PE  7bf50000-7bf58000       \               midimap
ELF     7bf58000-7bf7f000       Deferred        msacm32<elf>
  \-PE  7bf60000-7bf7f000       \               msacm32
ELF     7bf7f000-7bf97000       Deferred        msacm32<elf>
  \-PE  7bf90000-7bf97000       \               msacm32
ELF     7bf97000-7bfcd000       Deferred        winealsa<elf>
  \-PE  7bfa0000-7bfcd000       \               winealsa
ELF     7bfcd000-7bfd6000       Deferred        libxcursor.so.1
ELF     7bfd6000-7bff3000       Deferred        imm32<elf>
  \-PE  7bfe0000-7bff3000       \               imm32
ELF     7bff3000-7bff8000       Deferred        libxfixes.so.3
ELF     7bff8000-7c000000       Deferred        libxrender.so.1
ELF     7c30c000-7c312000       Deferred        libxrandr.so.2
ELF     7c312000-7c315000       Deferred        libxinerama.so.1
ELF     7c976000-7c979000       Deferred        libxcomposite.so.1
ELF     7d0ec000-7d0f5000       Deferred        librt.so.1
ELF     7d0f5000-7e2fe000       Deferred        fglrx_dri.so
ELF     7e2fe000-7e309000       Deferred        libgcc_s.so.1
ELF     7e309000-7e385000       Deferred        libgl.so.1
ELF     7e385000-7e38a000       Deferred        libxdmcp.so.6
ELF     7e38a000-7e38d000       Deferred        libxau.so.6
ELF     7e38d000-7e47e000       Deferred        libx11.so.6
ELF     7e47e000-7e48c000       Deferred        libxext.so.6
ELF     7e48c000-7e491000       Deferred        libxxf86vm.so.1
ELF     7e491000-7e4a9000       Deferred        libice.so.6
ELF     7e4a9000-7e4b1000       Deferred        libsm.so.6
ELF     7e4c4000-7e557000       Deferred        winex11<elf>
  \-PE  7e4d0000-7e557000       \               winex11
ELF     7e5b1000-7e5d1000       Deferred        libexpat.so.1
ELF     7e5d1000-7e5fc000       Deferred        libfontconfig.so.1
ELF     7e5fc000-7e611000       Deferred        libz.so.1
ELF     7e611000-7e681000       Deferred        libfreetype.so.6
ELF     7e681000-7e694000       Deferred        libresolv.so.2
ELF     7e6a7000-7e6c5000       Deferred        iphlpapi<elf>
  \-PE  7e6b0000-7e6c5000       \               iphlpapi
ELF     7e6c5000-7e721000       Deferred        rpcrt4<elf>
  \-PE  7e6d0000-7e721000       \               rpcrt4
ELF     7e721000-7e7c3000       Deferred        ole32<elf>
  \-PE  7e730000-7e7c3000       \               ole32
ELF     7e7c3000-7e818000       Deferred        ddraw<elf>
  \-PE  7e7d0000-7e818000       \               ddraw
ELF     7e818000-7e8d7000       Deferred        comctl32<elf>
  \-PE  7e820000-7e8d7000       \               comctl32
ELF     7e8d7000-7e930000       Deferred        shlwapi<elf>
  \-PE  7e8f0000-7e930000       \               shlwapi
ELF     7e930000-7ea34000       Deferred        shell32<elf>
  \-PE  7e940000-7ea34000       \               shell32
ELF     7ea34000-7ea9c000       Deferred        msvcrt<elf>
  \-PE  7ea50000-7ea9c000       \               msvcrt
ELF     7ea9c000-7eb88000       Deferred        wined3d<elf>
  \-PE  7eab0000-7eb88000       \               wined3d
ELF     7eb88000-7ebb7000       Deferred        d3d9<elf>
  \-PE  7eb90000-7ebb7000       \               d3d9
ELF     7ebb7000-7ec03000       Deferred        advapi32<elf>
  \-PE  7ebc0000-7ec03000       \               advapi32
ELF     7ec03000-7ec9b000       Deferred        gdi32<elf>
  \-PE  7ec10000-7ec9b000       \               gdi32
ELF     7ec9b000-7edd8000       Deferred        user32<elf>
  \-PE  7ecc0000-7edd8000       \               user32
ELF     7edd8000-7ee66000       Deferred        winmm<elf>
  \-PE  7ede0000-7ee66000       \               winmm
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ca5000-b7ca9000       Deferred        libdl.so.2
ELF     b7ca9000-b7df3000       Deferred        libc.so.6
ELF     b7df4000-b7e0c000       Deferred        libpthread.so.0
ELF     b7e1f000-b7f33000       Deferred        libwine.so.1
ELF     b7f35000-b7f51000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\pinky\Spel\KRIG\iw3sp.exe
        00000012    0
        00000011    0
        00000010   15
        0000000e   15
        0000000d   -1
        00000009    0 <==
Backtrace:
=>1 0x7c02c637 (0x0033f4d5)
err:ntdll:RtlpWaitForCriticalSection section 0x7ebb6e90 "d3d9_main.c: d3d9_cs" wait timed out in thread 000d, blocked by 0009, retrying (60 sec) 

```

I guess I'll have to wait until the january ati drivers come out :(

Thanks for the help anyway! And if you come up with something else that even has the slightest chance of working, I'll gladly try it :)

---

### Post by ahaslam on 2008-01-15
As I'm no Wine guru, you may want to visit the winehq IRC channel & ask them to look over that output. You never know, it may be something simple. ;)
> Thanks for the help anyway! And if you come up with something else that even has the slightest chance of working, I'll gladly try it 
No problem, just wanted to share what I experienced. And cheers, that's good to hear ;)

---

### Post by Sockerdrickan on 2008-02-07
New WINE release tomorrow! Please tell me if it works without the wine patch then!

---

### Post by ahaslam on 2008-02-07
Maybe you could test it & report your findings at [Wine AppDB]("http://appdb.winehq.org/site_outage.html") (when it's back up). I'll not be updating my Wine install for a while, 0.9.50 is everything I need atm.

If you're being put off because of the patching, don't. It's a perfectly safe diff & you should have no problems following my guide.

;)

---

### Post by algoe on 2008-02-08
I will defenitly try again with the new wine version! :)
I will report back as soon as i have tried it.

---

### Post by phasee on 2008-02-08
Does Cod4 run ok online? With punkbuster and the 1.5 patch etc?

---

### Post by ahaslam on 2008-02-08
It runs perfectly on line. Punkbuster doesn't run from within Wine, but there are *plenty* of servers that don't require it. All of the game patches apply cleanly & run well, though the newer the revision the fewer the servers. So just disable PB & make the choice between # of servers & updates. ;)

@ algoe: have you found success with a newer/alternate vga driver? If so share for others in the red team ;)

---

### Post by Sockerdrickan on 2008-02-08
It didn't work with 0.9.54 with or without the patch.

---

### Post by ahaslam on 2008-02-08
0.9.55 no? Thanks for testing it. It's not surprising that 5 releases down the line the patch no longer applies. However, they should have applied this by now. As it can't really be reported as a bug or a regression (unless the patch applied), please report your findings on the application database (it's back up now).

To get it running though, follow my guide. It took some time you know ;)

---

### Post by Milos_SD on 2008-02-08
I have made .deb package of wine 0.9.55 version with 3DMark patch. If someone need it, I can upload it on rapidshare. :)
I made it with checkinstall, so I hope it will work on other computers.

---

### Post by ahaslam on 2008-02-08
So .55 works well with COD4 for you?
PS. I wouldn't recommend sharing checkinstalls, personal use only IMO.

---

### Post by Milos_SD on 2008-02-08
Yes, it is working for me with .55. Why wouldn't you recommend sharing checkinstalls?

---

### Post by Sockerdrickan on 2008-02-08
I'd like instructions how to patch the vanilla 0.9.55 code Milos_SD

---

### Post by ahaslam on 2008-02-08
Standards, control & compatibility. 
[http://ubuntuforums.org/showthread.php?t=143885](http://ubuntuforums.org/showthread.php?t=143885)

---

### Post by Milos_SD on 2008-02-08
Download patch from here:
[http://bellegueulle.damien.neuf.fr/progs/3dmark.diff](http://bellegueulle.damien.neuf.fr/progs/3dmark.diff)

And copy that file to wine source folder. Then cd to wine source folder in terminal and do this:

patch -p1 < 3dmark.diff

Than just do ./configure
make depend && make
and sudo checkinstall (or sudo make install if you don't want to make .deb)

---

### Post by ahaslam on 2008-02-08
> **Milos_SD said:**
> 
Than just do ./configure

Please refer to my guide on page 2 for precise details.

---

### Post by Sockerdrickan on 2008-02-08
> **Milos_SD said:**
> Download patch from here:
[http://bellegueulle.damien.neuf.fr/progs/3dmark.diff](http://bellegueulle.damien.neuf.fr/progs/3dmark.diff)

And copy that file to wine source folder. Then cd to wine source folder in terminal and do this:

patch -p1 < 3dmark.diff

Than just do ./configure
make depend && make
and sudo checkinstall (or sudo make install if you don't want to make .deb)

But that's the same patch as [http://bugs.winehq.org/attachment.cgi?id=8548](http://bugs.winehq.org/attachment.cgi?id=8548) which I was using. When I boot CoD 4 it says it won't use blend and it doesn't start.

---

### Post by ahaslam on 2008-02-08
The patch resolves a 'glow' issue, not 'blend'. What graphics card & driver are you using?

PS, I see '8800gts' in your sig, from the AppDB:
> NVIDIA-Users *Update - 07.01.2008*:

The new NVIDIA-Beta Driver brokes down the COD4 support. Please use 100.xx until NVIDIA fixed the 169.xx.

If there is no other way then use the beta driver (8800GTS users?) please use this patch:

[http://bugs.winehq.org/attachment.cgi?id=9364](http://bugs.winehq.org/attachment.cgi?id=9364) 

---

### Post by Sockerdrickan on 2008-02-08
Okay I'll compile 0.9.50 with the nvidia and the glowfix  patches

---

### Post by Sockerdrickan on 2008-02-08
The nvidia patch didn't work, I get the error "Video card or driver doesn't support UBYTE4N vertex data."

---

### Post by ahaslam on 2008-02-08
I don't know what to suggest, other than trying the appdb or visiting winehq on freenode...

---

### Post by Sockerdrickan on 2008-02-08
It doesn't work with the old nVidia driver either apparently... how cute

---

### Post by Odin2347 on 2008-02-11
> **ahaslam said:**
> This should be a straightforward way of installing a patched wine (which I assume is the problem here), just issue one line at a time:

Clean up & get some dep's :
```
sudo apt-get remove wine
rm -r ~/.wine
sudo apt-get build-dep wine
sudo apt-get install build-essential checkinstall
```
Get wine, patch it & install it:
```
mkdir wine && cd wine
wget http://easynews.dl.sourceforge.net/sourceforge/wine/wine-0.9.50.tar.bz2
tar -xvjf wine-0.9.50.tar.bz2
wget http://bugs.winehq.org/attachment.cgi?id=8548
cp attachment.cgi\?id\=8548 wine-0.9.50/3dmark.diff && cd wine-0.9.50
patch -p1 < 3dmark.diff
./configure --prefix=/usr --sysconfdir=/etc --enable-opengl --with-x
make depend && make
sudo checkinstall
```
*Accept the defaults, an option will come up to set a description, set one and enter, select the next default, job done - checkinstall created a .deb package, installed it and left a copy in the folder you're working in.*

Set up wine: 
```
wineprefixcreate
winecfg
```
Now you need to set the 'Windows Version' to XP. While you're here I recommend that you visit the drives tab and use the 'Autodetect' button, double checking your CDROM path & drive type with the 'Show Advanced' button. 

Get the required DX9 dll:
```
mkdir dx9 && cd dx9
wget http://www.m3fe.com/files/d3dx9_34.zip
unzip d3dx9_34.zip
mv d3dx9_34.dll ~/.wine/drive_c/windows/system32/

```

Now it's time to install COD4:
```
cd /path/to/cdrom/
wine setup.exe
```

No-dvd crack - needed to launch:
Go to [gamecopyworld]("http://www.gamecopyworld.com/") & get the appropriate no-dvd/fixed exe, eg:

Make a backup of your original iw3sp.exe (location shown below) before replacing it with the fixed exe.

Launch the game:
```
cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare && wine iw3sp.exe
```

Once launched you'll need to reduce some graphics options to avoid glitches & improve performance. Some options don't work & some just don't look right, I recommend that you disable the following:

Anti-aliasing - *Doesn't work.*
Sync Every Frame
Shadows 
Specular Map
Depth of Field
Glow
Number of Dynamic Lights
**Soften Smoke Edges** - *Unplayable with this option enabled.*


Good luck. I hope it works for you, let us know.

;)

Hey this is an awesome guide..but I just tried using it (on 64bit Gutsy) and when I try "sudo apt-get install build dep wine"
I get "wine dependencies not satisfied"

---

### Post by ahaslam on 2008-02-11
This is because amd64 Ubuntu releases don't ship with Wine in the repo's. Try adding a repository to your system's list of APT sources: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb).
You will also need to take a few extra steps: [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit).
I hope that helps, I can't offer any cast iron advise on this as I don't run Ubuntu. On Arch I used a 32bit chroot environment to build Wine & 32bit-libs to run it.

PS. Let me know if this helps you compile & I'll update the guide ;)

---

### Post by Odin2347 on 2008-02-11
> **ahaslam said:**
> This is because amd64 Ubuntu releases don't ship with Wine in the repo's. Try adding a repository to your system's list of APT sources: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) ;)

Haha, sorry I'm a total linux noob here, I might need more detailed instructions than that ;) I tried to edit the sources with " sudo gedit /etc/apt/sources.list
"
and I added "deb http://winehq.org/site/download-deb"
and now I try "sudo apt-get update" and I get "E: Malformed line 43 in source list /etc/apt/sources.list (dist)"

---

### Post by Odin2347 on 2008-02-11
Ahh nevermind..I figured out you were sending me a link to a how-to to add the entry to my apt list:lolflag: However, the problem still persists "E: Build-dependencies for wine could not be satisfied."
:confused:

---

### Post by ahaslam on 2008-02-11
Sorry, I was too busy editing my [previous post]("http://ubuntuforums.org/showpost.php?p=4311306&postcount=49") to see your replys :-\"

Have a browse over this: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) just to make sure the repo's set up properly. Then read the' WineOn64bit' guide which was one of the things I added to my previous post.

;)

---

### Post by Odin2347 on 2008-02-11
Ah, thanks:)
Well I'm trying to compile it but I get an error when running ./configure

"configure: error: C compiler cannot create executables"
and also "odin@odin-desktop:~/wine-0.9.50$ make depend && make
make: *** No rule to make target `depend'.  Stop."

---

### Post by ahaslam on 2008-02-11
You've got the extra packages & made the appropriate links? It sounds like you've not got 'gcc-4.2-multilib' installed. 
> sudo apt-get build-dep wine
sudo apt-get install libxcomposite-dev gcc-4.2-multilib
After "*patch -p1 < 3dmark.diff*" in my guide, continue with "*mkdir -p `pwd`/lib32*" from the '[WineOn64bit]("http://wiki.winehq.org/WineOn64bit#head-c47d9e53f952c5b6260467e0dc158321229216de")' guide.

;)

---

### Post by Odin2347 on 2008-02-11
When I try that code I get :
$ sudo apt-get install libxcomposite-dev gcc-4.2-multilib 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxcomposite-dev is already the newest version.
libxcomposite-dev set to manual installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gcc-4.2-multilib: Depends: libc6-dev-i386 (>= 2.5) but it is not going to be installed
E: Broken packages

and I picked up on the guide where you said too and I get :
odin@odin-desktop:~/wine-0.9.50$ CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc-4.2 -m32
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
:confused:

---

### Post by ahaslam on 2008-02-11
You need to fix the 1st problem before you continue. You can't compile 32bit apps without a multilib compiler (not without a chroot). 

A quick forum search brought this up: [http://ubuntuforums.org/showthread.php?t=666132&highlight=Broken+packages](http://ubuntuforums.org/showthread.php?t=666132&highlight=Broken+packages)

Hope it helps ;)

---

### Post by jdlf on 2008-02-12
Hello, just follow the steps you gave us and installed CoD4 in my computer. I noticed that single player works for me (hurray!), but that multiplayer does not (crashes at startup). Currently using patched 0.9.50 v of wine and followed your instructions. Have you got any ideas? 

*using Ubuntu 7.10. 

I just want multiplayer to play on LAN (we don't use Punkbuster).

Thanks for all,

JDLF

---

### Post by ahaslam on 2008-02-12
Nice to hear you've got the SP up & running at least. There are a couple of things you can try:
[LIST]Is there any difference between accessing MP through the SP menu, or by launching the iw3mp.exe?[/LIST]
[LIST]Have you tried patching the game itself?[/LIST]
If this gets you nowhere, please post the last few dozen lines of the debugging for us to ponder over. 

:-k

---

### Post by jdlf on 2008-02-13
Well, [B]there doesn't seem to be any difference between running from single player and then switching to multiplayer and going straight into multiplayer. 
[/B]

Also, the lines of code that appear when I execute wine from terminal are similar, no matter if it's sp or mp. This is from mp:

fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat)
 @ state.c / 2503
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat)
 @ state.c / 2503
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat)
 @ state.c / 2503




 But I found **something I don't quite understand** (maybe cause I'm newbie :p)  

[email]jdjd@jdjd-laptop:~/.wine[/email]/drive_c/Archivos de programa/Activision/Call of Duty 4 - Modern Warfare$ ls

binkw32.dll  codlogo.bmp  iw3sp.exe         miles      players
cod4.ico     __iw3mp      localization.txt  Mods       zone
cod.bmp     [COLOR="Lime"] iw3mp.exe [/COLOR]   main              mss32.dll

iw3mp.exe is in green ¿? also why is there a _iw3mp?? 

iw3sp.exe and _iw3mp are normal colour

**I don't have to install any patch to run multiplayer do I?** (appart from the ones to update from 1.0)

Thanks for all,
JDLF

PD: Fed up with Sony MP3 players as well ;-) Mine NW-A1000 and software provided is crap

---

### Post by ahaslam on 2008-02-13
The green highlight means it's flagged as executable, it shouldn't matter either way though. It's strange that you've got a '__iw3mp' - you shouldn't, delete it if you wish. You don't need to patch the game for MP, though it may save you a full reinstall if were corrupted (which is possible).
Regarding that output, what graphics driver version are you running (100.14.19 here)? I'd feel inclined to [switch to FBO rendering]("http://ubuntuforums.org/showthread.php?p=4141273&highlight=fbo#post4141273"), it's often more stable & I've noticed no reduction in performance.

Should keep you busy for a while ;)

PS. Yeah, Sony produce some really nice kit, only to spoil it with crap software. They've realized the dissatisfaction now, finally releasing players supporting drag & drop. :)

---

### Post by jdlf on 2008-02-13
running 169.09 nvidia driver for linux & graphics is ASUS 8600MGT 256MB DDR3 (and sp does work well at 1440x900 low settings). By the way, I'm using this resolution cause I don't know how tow put wine fullscreen at less than native resolution. Know how? Also I have Cod4 demo installed? can this be a problem? Don't know how to uninstall it (there is a link at the deskbar in wine directory but it doesn't work).

thanks, 

jdlf

ps: did registry stuff

---

### Post by ahaslam on 2008-02-13
You should be able to set the resolution as normal under the graphics section :confused:

The demo could be causing some sort of conflict. To remove it, open a terminal & issue:
```
uninstaller
```
Then I'd grab the 1.4 patch & install that, there's no negative to this if you're just wanting to play over your LAN (other than time for updating all installs).

Don't forget to try the FBO registry entry ;)

Failing that, uninstall COD4, remove your Activision dir & reinstall... :(

---

### Post by jdlf on 2008-02-13
Could you check this???

It's about problems when trying CoD4 mp with RealTek audio cards in vista -mine is RealTek- however when i played it on vista which i don't have now -->    [worm :-( --> format C:/ ]   I had no problems (?)  


[http://forums.firingsquad.com/firingsquad/board/message?board.id=software&message.id=12139](http://forums.firingsquad.com/firingsquad/board/message?board.id=software&message.id=12139)


**Some people say this**

"deleted the file located in Programfiles/Activision/Call Of Duty 4/Miles and delete a file called mssmp3.asi... delete or rename... hope that helps... forgot to say this works for me!"

More stuff: can't uninstall CoD4 with installer command (though I could uninstall demo -lol) and I've deleted mssmp3.asi and can't install 1.5 patch cause it asks me to put a valid cd key in multiplayer menu (which I obviously can't access!!)

About resolution, if i put it at less than native res, either the game or wine virtual desktop, the window resizes and i cannot set it fullscreen

ps: demo uninstalled w/o result & already tried FBO

thanks
jdlf

---

### Post by ahaslam on 2008-02-13
As MP isn't working for you atm it can't hurt too much:
```

cd ~/.wine/drive_c/Archivos\ de\ programa/Activision/Call\ of\ Duty 4\ -\ Modern\ Warfare/miles && mv mssmp3.asi mssmp3.bak
```
I doubt it'll make much difference & it certainly has nothing to do with your Wine output. If there is an issue with your sound card, I'd recommend  selecting a different sound driver (& maybe Win ver) within '*winecfg*'. 

Is the required resolution listed in your xorg.conf & more importantly, does it work on the desktop? Is 1440x900 your native resolution? If it works well there & you just want a few extra fps, you can invoke nvidia-settings within a launch script, a quick example:
```
#! /bin/bash
nvidia-settings -a OpenGLImageSettings=3 
cd ~/.wine/drive_c/Archivos\ de\ programa/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare && WINEDEBUG=-all wine iw3sp.exe
nvidia-settings --load-config-only && nvidia-settings -a OpenGLImageSettings=1

```

;)

---

### Post by jdlf on 2008-02-13
problem solved (or i think so) I'll tell you if it is definetely fixed

---

### Post by ahaslam on 2008-02-13
Fingers crossed ;)

---

### Post by jdlf on 2008-02-13
Yes. native res is 1440x900 Could you please explain they instructions you gave in your last post in an easier way? 

yep, the problem was that i was using alsa mixer instead of realtek drivers

thanks, 

jdlf

---

### Post by ahaslam on 2008-02-13
Glad it's sorted ;)

For the launch script simply create a new file called something like codlaunch (or whatever you want). Then paste the code from my previous post into it. Once saved, open a terminal, navigate to the directory where you made it & issue:
```
chmod +x codlaunch   # this makes it executable
```
To launch it, either click it or point a desktop/menu launcher toward it.
The nvidia-settings line sets OpenGL for maximum performance, typically gaining about 10%. 'WINEDEBUG=-all' prevents Wine from spurting out its endless debug info, gaing you an additional 1 or 2 fps. The last line reverts the OpenGL settings to default for your next app. For many more tweaks, read the nvidia-settings man page.

;)

PS. Did you also create the 'VideoMemorySize' registry entry?

---

### Post by jdlf on 2008-02-14
Ok, I'll test the settings you've suggested. 

But, isn't there any way in Wine to emulate a graphic environment at less than native res that is still showed as fullscreen?? You know what I mean? Thanks for all, 

jdlf

---

### Post by ahaslam on 2008-02-14
With Wine on default settings, your application should be able to set the resoloution. The other option is a virtual desktop which is set within winecfg, though from your posts I assumed you'd tried this. If you've not, here's an example:
```
winecfg
```
Go to the graphics tab & select/enter:
```
[x] Emulate a virtual desktop 
Desktop size: 1280  x  800   # or whatever
```
;)

---

### Post by msjones on 2008-02-17
Hi guys,

I have come to install CoD4. I follwed as was told in the tut patched and installed wine git, and then installed CoD4. I made sure the d3d files were in system 32.

When I come to execute CoD I get the splash screen and this error:

> ----- Initializing Renderer ----
----- Client Initialization Complete -----
Attempting 44 kHz 16 bit [Windows default] sound
----- R_Init -----
Getting Direct3D 9 interface...
Pixel shader version is 0.0
Vertex shader version is 0.0
Video card or driver doesn't accelerate dynamic textures.
Video card or driver doesn't support the required stencil operations.
Video card or driver doesn't support UBYTE4N vertex data.


Error during initialization:
Video card or driver doesn't support UBYTE4N vertex data.

Can anybody help me get this working?

Thanks

---

### Post by ahaslam on 2008-02-17
> Radeon X1650 PRO
You need better driver support for your grahics card. Take a look in the hardware section, maybe there's an alternative. I don't know much about ATi cards, sorry.

:(

---

### Post by msjones on 2008-02-17
Damn it lol. It was a struggle getting my X1650 to work in ubuntu. Ive moved completely over to linux now, this was the only thing i was moving over lol.

Thanks for the quick reply!

---

### Post by Private_Bug on 2008-02-24
specs: cpu:AMD Turion, videocard:ATI X700, Ubuntu 7.10 Gnome

My videocard works good, I can play 3d games etc. (Tremulous, ...)
I've downloaded d3dx9_24.dll...d3dx9_35.dll and placed them in my system32 folder.

When I get the splash screen, I keep getting an error message in a window when trying to play in Singleplayer:

```
Runtime Error!
Program: C:\Program...
R6002
-floating point support not loaded
```

and in the terminal I get:

```
root@Spot:~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare# cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare && wine iw3sp.exe
fixme:mixer:ALSA_MixerInit No master control found on ATI IXP Modem, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33f91c,0x00000000), stub!
wine: Unhandled exception 0x406d1388 at address 0x7b8448e0 (thread 0009), starting debugger...
Thread ID=000c renamed using MS VC6 extension (name=="Database")
Thread ID=000c renamed using MS VC6 extension (name=="Database")
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'

```


When I try to play Multiplayer I get the splash screen and this in my terminal (the splash screen freezes):

```
root@Spot:~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare# wine iw3mp.exe 
fixme:mixer:ALSA_MixerInit No master control found on ATI IXP Modem, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33f91c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
err:ntdll:RtlpWaitForCriticalSection section 0x110048 "heap.c: main process heap section" wait timed out in thread 000d, blocked by 0009, retrying (60 sec)
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x19aa23c8) : pBox=(nil) stub
err:ntdll:RtlpWaitForCriticalSection section 0x110048 "heap.c: main process heap section" wait timed out in thread 000d, blocked by 0009, retrying (60 sec)
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x17e4aef0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x17e4aef0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x17e4aef0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x17e4aef0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x17e4aef0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x17e4aef0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x17e4aef0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x17e4aef0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x17e4aef0) Event query: Unimplemented, but pretending to be supported
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #1: "Fragment shader was successfully compiled to run on hardware.\nWARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported"
fixme:d3d:state_separateblend (WINED3DRS_SEPARATEALPHABLENDENABLE,1) not yet implemented
wine: Unhandled page fault on write access to 0xffffffff at address 0x7c04bff2 (thread 0009), starting debugger...
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8208
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8224
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8232
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8232
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8240
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8240
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8240
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8248
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8248
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8256
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8256
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8256
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8264
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8264
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8272
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8272
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8272
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8280
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8280
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8288
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8288
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8288
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8296
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8296
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8304
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8304
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8320
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8328
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8328
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8328
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8336
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8336
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8344
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8344
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8352
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8352
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8352
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8360
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8360
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8368
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8368
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8368
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8376
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8376
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8392
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8392
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8400
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8400
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8400
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8432
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8432
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8432
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8440
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8440
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8448
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8448
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8448
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8456
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8456
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8456
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8464
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8464
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8472
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8472
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8472
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8480
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8480
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8488
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8488
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8488
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8496
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8496
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_mixpos=11976, writepos=12288, mixlen=8496
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=65224, mixpos=78496/147960 (36060/67968), primary_miUnhandled exception: page fault on write access to 0xffffffff in 32-bit code (0x7c04bff2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7c04bff2 ESP:0033f889 EBP:0033f8d4 EFLAGS:00210212(   - 00      - RIA1)
 EAX:ffffffff EBX:7eae637e ECX:0020ce58 EDX:00000000
 ESI:00000000 EDI:0033f88f
Stack dump:
0x0033f889:  0033f88f 007eae63 14000000 3c7c04c4
0x0033f899:  757ea7ef d4000087 01002172 cc000000
0x0033f8a9:  800033f8 067eae63 d4000000 000033f8
0x0033f8b9:  02000000 02000000 01000000 80000000
0x0033f8c9:  067eae63 44000000 44000000 ff0033f9
0x0033f8d9:  d87ea284 58000000 780020ce 8017e8c8
Backtrace:
=>1 0x7c04bff2 (0x0033f8d4)
  2 0x7ea284ff ActivateContext+0x3ff() in wined3d (0x0033f944)
  3 0x7ea54d0b drawPrimitive+0x15b() in wined3d (0x0033fbe4)
  4 0x7ea33dbd in wined3d (+0x23dbd) (0x0033fc54)
  5 0x7eafee4e in d3d9 (+0xee4e) (0x0033fc84)
  6 0x005ef341 in iw3mp (+0x1ef341) (0x00000000)
0x7c04bff2: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (99 modules)
PE        400000- d935000       Export          iw3mp
PE       d940000- dcaf000       Deferred        d3dx9_34
PE      17ce0000-17cf6000       Deferred        mileseq.flt
PE      17e10000-17e21000       Deferred        msseax.flt
PE      18000000-18033000       Deferred        binkw32
PE      21100000-21197000       Deferred        mss32
PE      22300000-22306000       Deferred        mssds3d.flt
PE      24100000-24112000       Deferred        mssdsp.flt
PE      26400000-2642a000       Deferred        mssvoice.asi
PE      26f00000-26f20000       Deferred        mssmp3.asi
ELF     7b800000-7b92b000       Deferred        kernel32<elf>
  \-PE  7b820000-7b92b000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf65000-7bf70000       Deferred        libgcc_s.so.1
ELF     7bf70000-7bf76000       Deferred        libnss_dns.so.2
ELF     7bf76000-7bf79000       Deferred        libnss_mdns4_minimal.so.2
ELF     7bfb9000-7bfeb000       Deferred        uxtheme<elf>
  \-PE  7bfc0000-7bfeb000       \               uxtheme
ELF     7bfeb000-7c000000       Deferred        midimap<elf>
  \-PE  7bff0000-7c000000       \               midimap
ELF     7c34a000-7c371000       Deferred        msacm32<elf>
  \-PE  7c350000-7c371000       \               msacm32
ELF     7c371000-7c389000       Deferred        msacm32<elf>
  \-PE  7c380000-7c389000       \               msacm32
ELF     7c389000-7c44f000       Deferred        libasound.so.2
ELF     7c44f000-7c452000       Deferred        libnss_mdns4.so.2
ELF     7c462000-7c498000       Deferred        winealsa<elf>
  \-PE  7c470000-7c498000       \               winealsa
ELF     7c498000-7c4a1000       Deferred        libxcursor.so.1
ELF     7c4a1000-7c4be000       Deferred        imm32<elf>
  \-PE  7c4b0000-7c4be000       \               imm32
ELF     7c4be000-7c4c4000       Deferred        libxrandr.so.2
ELF     7c4c4000-7c4cc000       Deferred        libxrender.so.1
ELF     7cb28000-7cb2d000       Deferred        libxfixes.so.3
ELF     7d2a0000-7d2a9000       Deferred        librt.so.1
ELF     7d2a9000-7e266000       Deferred        fglrx_dri.so
ELF     7e266000-7e2f0000       Deferred        libgl.so.1.2
ELF     7e2f0000-7e2f5000       Deferred        libxdmcp.so.6
ELF     7e2f5000-7e2f8000       Deferred        libxau.so.6
ELF     7e2f8000-7e3e9000       Deferred        libx11.so.6
ELF     7e3e9000-7e3f7000       Deferred        libxext.so.6
ELF     7e3f7000-7e3fc000       Deferred        libxxf86vm.so.1
ELF     7e3fc000-7e414000       Deferred        libice.so.6
ELF     7e414000-7e41c000       Deferred        libsm.so.6
ELF     7e42f000-7e4bb000       Deferred        winex11<elf>
  \-PE  7e440000-7e4bb000       \               winex11
ELF     7e50b000-7e52b000       Deferred        libexpat.so.1
ELF     7e52b000-7e556000       Deferred        libfontconfig.so.1
ELF     7e556000-7e56b000       Deferred        libz.so.1
ELF     7e56b000-7e5db000       Deferred        libfreetype.so.6
ELF     7e5db000-7e630000       Deferred        ddraw<elf>
  \-PE  7e5e0000-7e630000       \               ddraw
ELF     7e630000-7e6ef000       Deferred        comctl32<elf>
  \-PE  7e640000-7e6ef000       \               comctl32
ELF     7e6ef000-7e748000       Deferred        shlwapi<elf>
  \-PE  7e700000-7e748000       \               shlwapi
ELF     7e748000-7e84c000       Deferred        shell32<elf>
  \-PE  7e760000-7e84c000       \               shell32
ELF     7e84c000-7e8a8000       Deferred        rpcrt4<elf>
  \-PE  7e860000-7e8a8000       \               rpcrt4
ELF     7e8a8000-7e94a000       Deferred        ole32<elf>
  \-PE  7e8c0000-7e94a000       \               ole32
ELF     7e94a000-7e994000       Deferred        dsound<elf>
  \-PE  7e950000-7e994000       \               dsound
ELF     7e994000-7e9fc000       Deferred        msvcrt<elf>
  \-PE  7e9b0000-7e9fc000       \               msvcrt
ELF     7e9fc000-7eae8000       Export          wined3d<elf>
  \-PE  7ea10000-7eae8000       \               wined3d
ELF     7eae8000-7eb17000       Export          d3d9<elf>
  \-PE  7eaf0000-7eb17000       \               d3d9
ELF     7eb17000-7eb2a000       Deferred        libresolv.so.2
ELF     7eb3d000-7eb5b000       Deferred        iphlpapi<elf>
  \-PE  7eb40000-7eb5b000       \               iphlpapi
ELF     7eb5b000-7eb88000       Deferred        ws2_32<elf>
  \-PE  7eb60000-7eb88000       \               ws2_32
ELF     7eb88000-7eb9c000       Deferred        mswsock<elf>
  \-PE  7eb90000-7eb9c000       \               mswsock
ELF     7eb9c000-7ebb6000       Deferred        wsock32<elf>
  \-PE  7eba0000-7ebb6000       \               wsock32
ELF     7ebb6000-7ec02000       Deferred        advapi32<elf>
  \-PE  7ebc0000-7ec02000       \               advapi32
ELF     7ec02000-7ec9a000       Deferred        gdi32<elf>
  \-PE  7ec10000-7ec9a000       \               gdi32
ELF     7ec9a000-7edd7000       Deferred        user32<elf>
  \-PE  7ecc0000-7edd7000       \               user32
ELF     7edd7000-7ee65000       Deferred        winmm<elf>
  \-PE  7ede0000-7ee65000       \               winmm
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c94000-b7c9d000       Deferred        libnss_compat.so.2
ELF     b7c9e000-b7ca2000       Deferred        libdl.so.2
ELF     b7ca2000-b7dec000       Deferred        libc.so.6
ELF     b7ded000-b7e05000       Deferred        libpthread.so.0
ELF     b7e18000-b7f2c000       Deferred        libwine.so.1
ELF     b7f2e000-b7f4a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3mp.exe
        00000012    0
        00000011    0
        00000010   15
        0000000e   15
        0000000d   -1
        00000009    0 <==
Backtrace:
=>1 0x7c04bff2 (0x0033f8d4)
  2 0x7ea284ff ActivateContext+0x3ff() in wined3d (0x0033f944)
  3 0x7ea54d0b drawPrimitive+0x15b() in wined3d (0x0033fbe4)
  4 0x7ea33dbd in wined3d (+0x23dbd) (0x0033fc54)
  5 0x7eafee4e in d3d9 (+0xee4e) (0x0033fc84)
  6 0x005ef341 in iw3mp (+0x1ef341) (0x00000000)
err:ntdll:RtlpWaitForCriticalSection section 0x7eb16e90 "d3d9_main.c: d3d9_cs" wait timed out in thread 000d, blocked by 0009, retrying (60 sec)

```

PLease somebody help me get this to work :confused:

---

### Post by ahaslam on 2008-02-24
> **Private_Bug said:**
> specs: cpu:AMD Turion, videocard:ATI X700, Ubuntu 7.10 Gnome

My videocard works good, I can play 3d games etc. (Tremulous, ...)
I've downloaded d3dx9_24.dll...d3dx9_35.dll and placed them in my system32 folder.

I'm sure this is due to your graphics driver. Have you had success with any other DX9 games under Wine? Native games like Tremulous should always work, though ATi + Wine is known to produce issues.

:(

---

### Post by Aramir on 2008-03-06
Hello I installed Call of duty 4  and cofigured wine following this [http://ubuntuforums.org/showpost.php?p=4047498&postcount=13](http://ubuntuforums.org/showpost.php?p=4047498&postcount=13)
but after I start call of duty it start to loading for some time and than error appears
code:
```
----- Initializing Renderer ----
----- Client Initialization Complete -----
Attempting 44 kHz 16 bit [Windows default] sound
ERROR: Couldn't initialize digital driver: DirectSoundCreate() failed in get_system_speaker_configuration()


Error during initialization:
Miles sound system initialization failed.
Make sure you have your sound card's latest drivers and DirectX installed
```

If someone know what to do with this plz help...and excuse my bad english...:)

---

### Post by Aramir on 2008-03-06
One more thing ... id did some sound settings in wine so now It don`t do the sound error, but it starts loading, my resolution change to 1024x768 and tan it d=falls down

```
aramir@Chimera:/media/sda7/Games/ccod4$ wine iw3sp.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33f8fc,0x00000000), stub!
aramir@Chimera:/media/sda7/Games/ccod4$ winecfg
aramir@Chimera:/media/sda7/Games/ccod4$ wine iw3sp.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33f8fc,0x00000000), stub!
aramir@Chimera:/media/sda7/Games/ccod4$ winecfg
aramir@Chimera:/media/sda7/Games/ccod4$ wine iw3sp.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33f8fc,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at
present
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1cb0b0) Event query: Unimplemented,
but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1cb0b0) Event query: Unimplemented,
but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1cb0b0) Event query: Unimplemented,
but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1cb0b0) Event query: Unimplemented,
but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1cb0b0) Event query: Unimplemented,
but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1cb0b0) Event query: Unimplemented,
but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1cb0b0) Event query: Unimplemented,
but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1cb0b0) Event query: Unimplemented,
but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1cb0b0) Event query: Unimplemented,
but pretending to be supported
err:ntdll:RtlpWaitForCriticalSection section 0x7e56b640 "x11drv_main.c: X11DRV_C
ritSection" wait timed out in thread 0013, blocked by 0009, retrying (60 sec)
wine: Critical section 7e56b640 wait failed at address 0x7bc398d0 (thread 0013),                        starting debugger...
Unhandled exception: wait failed on critical section 0x7e56b640 thread_data_tls_                       index+0x40
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc398d                       0
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
0000000c
        0000000f    0
        0000000e    0
        0000000d    0
00000010
        00000012    0
        00000011    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
aramir@Chimera:/media/sda7/Games/ccod4$

```

---

### Post by ahaslam on 2008-03-06
```
err:ntdll:RtlpWaitForCriticalSection section 0x7e56b640 "x11drv_main.c: X11DRV_C
ritSection" wait timed out in thread 0013, blocked by 0009, retrying (60 sec)
```
This pops up every now & then, unfortunately I've not seen a solution.
You may want to try your luck with Wine 0.9.56, note you'll not need the .dll file.

---

### Post by beefcurry on 2008-03-12
> **jdlf said:**
> Hello, just follow the steps you gave us and installed CoD4 in my computer. I noticed that single player works for me (hurray!), but that multiplayer does not (crashes at startup). Currently using patched 0.9.50 v of wine and followed your instructions. Have you got any ideas? 

*using Ubuntu 7.10. 

I just want multiplayer to play on LAN (we don't use Punkbuster).

Thanks for all,

JDLF

I have this same problem as well, it would be nice if someone has a solution.. But I am using a patched 0.9.56 wine and I don;t know why it is not working. Single player works without any problems but multiplayer crashes on start up.

---

### Post by ahaslam on 2008-03-12
[http://ubuntuforums.org/showpost.php?p=4325581&postcount=67](http://ubuntuforums.org/showpost.php?p=4325581&postcount=67)

---

### Post by beefcurry on 2008-03-12
Yeah I did read every single post, still no answers unfortunately. I use an Intel HD Audio driver not realtek, and I've tried all the other tricks like renaming the ssmp3.asi and occupying the mic jack. I even upgraded to Wine 0.9.57 patched, it did make single player alot faster but multilayer still fails to load... odd

---

### Post by ahaslam on 2008-03-13
Post your output, I'll have a look. It is odd though, I can't guarantee anything...

PS. Have you tried patching the game?

---

### Post by beefcurry on 2008-03-16
hm, the crash happens after the dialog box asking you if you want to set optimum settings (it crashes after both yes and no). I suspect it to be a actual bug of the game similar to the sound card issue one.. its currently patched to 1.4, I'll see what happens with a newer patch.

```
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33f8fc,0x00000000), stub!
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 407
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 407
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 407
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 407
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 407
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 407
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 407
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 407
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x17f206d8) : pBox=(nil) stub
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2670
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2670
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2670
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2670

```

Thanks.

---

### Post by ahaslam on 2008-03-16
Do you get this with a patched Wine 0.9.50?

---

### Post by beefcurry on 2008-03-16
with a patched 0.9.57.

Single player works perfectly so running it shouldn't be the problem.

---

### Post by ahaslam on 2008-03-16
I don't see what's causing your problem. One consideration would be the .dll. I assume you removed this before upgrading to 0.9.56 (see release notes)? If not, do so & run wineprefixcreate.

If this doesn't help, start a fresh with Wine 0.9.50. If that doesn't work it's not Wine.

---

### Post by sookster54 on 2008-03-19
Unusual problems here in the thread, I have CoD4 (and CoDUO & CoD2) going under 0.9.57, only thing was the wierd graphics and turning off "smooth smoke edges" fixed it.  I can play both SP and MP, but no punkbuster in MP.  I had to grab the d3dx9_33.dll files I think it was.

---

### Post by sookster54 on 2008-03-19
> **msjones said:**
> Damn it lol. It was a struggle getting my X1650 to work in ubuntu. Ive moved completely over to linux now, this was the only thing i was moving over lol.

Thanks for the quick reply!

I love that card, but the ATI drivers for Linux are god awful with so many problems in X, it's better off using it in Windows instead.  Seems to me NVidia are more supported in Linux than ATI is.

---

### Post by kungfunarusu on 2008-04-15
I'm having problems with COD4 Im running patched wine just like youre guide says, and it installed perfect except it said something about directx not working, i ignored it and installed directx how you said, and i try to run the game and it goes black and crashes and gives me this

[email]robbie@kungfuchicken:~/.wine[/email]/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$ wine iw3mp.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33f91c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x17ef3158) : pBox=(nil) stub
fixme:d3d:state_separateblend (WINED3DRS_SEPARATEALPHABLENDENABLE,1) not yet implemented
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat)
 @ state.c / 2503
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat)
 @ state.c / 2503
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat)
 @ state.c / 2503
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat)
 @ state.c / 2503
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 384
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x190320) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:D3D9CB_CreateSurface (0x190320) IDirect3DDevice9_CreateSurface failed
fixme:d3d:IWineD3DDeviceImpl_CreateTexture Failed to create surface  0x1f49db58
fixme:d3d9:IDirect3DDevice9Impl_CreateTexture (0x190320) call to IWineD3DDevice_CreateTexture failed
Segmentation fault (core dumped)


if you could give me some advice id appreciate it, (it does this with both single and multiplayer)

---

### Post by SLA_leandrin on 2008-04-23
> **ahaslam said:**
> 
```
OffscreenRenderingMode   fbo    [I](more stable than pbuffer)
[/I]VideoMemorySize          256    *(or whatever your card has)*
```


Thank you for this ahaslam, I've got COD4 finally working!!!

---

### Post by SLA_leandrin on 2008-04-23
> **kungfunarusu said:**
> 
if you could give me some advice id appreciate it, (it does this with both single and multiplayer)

I was having exactly the same issues. 
If you have tryied to install directx from the COD4 DVD, then you have to do all the proccess again and when the installation gets to the install of directx, just don't accept the license and don't install it.

After that, just have to do this:

[http://ubuntuforums.org/showpost.php?p=4141273&postcount=25]("http://ubuntuforums.org/showpost.php?p=4141273&postcount=25")

That worked for me!
Good Luck---

---

### Post by ahaslam on 2008-04-23
Cheers ;)

---

### Post by thefishki345 on 2008-04-23
> **ahaslam said:**
> Cheers ;)
Hi I am having some problems running cod4, I patched wine using ahaslam´s tutorial and this one: [http://www.filledvoid.com/2008/02/16/compiling-wine-for-ubuntu-gutsy-gibbon-64-bit/](http://www.filledvoid.com/2008/02/16/compiling-wine-for-ubuntu-gutsy-gibbon-64-bit/) (because I am running 64 bit)
Its patched fine, wine runs fine, I get correct output when I type wine in terminal.
so anyway, I installed cod4 fine, but when I launch it, on panels it says ¨starting call of duty 4¨ and then...nothing and it crashes...no error message no nothing, then when I try it again it says ¨it appears cod4 did not close properly last time, do you want to run in safe mode? so if I click yes or no it still crashes.
when I run it in terminal by this command:
cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare && wine iw3sp.exe

I get this:

```
$ cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare && wine iw3sp.exe
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:wgl:X11DRV_ChoosePixelFormat No OpenGL support compiled in.
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ebb9024 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7ebb9024).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7ebb9024 ESP:0032f88c EBP:0032f8e4 EFLAGS:00010212(   - 00      - RIA1)
 EAX:0032f8b0 EBX:7ebcc678 ECX:7ebcce80 EDX:00000000
 ESI:00138520 EDI:7ebcce7c
Stack dump:
0x0032f88c:  7ebcce7c 00000000 000008ec 7eb7b854
0x0032f89c:  0000000a 0000000a 0000000a 0000000a
0x0032f8ac:  00000000 0032f8fc 0032fafc 0032fcfc
0x0032f8bc:  0032fd1c 0032fd24 0032fd28 0032fd2c
0x0032f8cc:  0032fd30 0032fd34 0032fd44 00000000
0x0032f8dc:  00138520 7b88b210 0032fd60 00593836
Backtrace:
=>1 0x7ebb9024 IDirect3D9Impl_GetAdapterIdentifier+0x84(iface=0x138520, Adapter=0x0, Flags=0x0, pIdentifier=0x32f8fc) [/home/josh/wine/dlls/d3d9/directx.c:124] in d3d9 (0x0032f8e4)
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 665f4c49 in module L"iw3sp"
  2 0x00593836 in iw3sp (+0x193836) (0x0032fd60)
  3 0x00595626 in iw3sp (+0x195626) (0x0032ff08)
  4 0x7b876447 start_process+0xc7(arg=0x0) [/home/josh/wine/dlls/kernel32/process.c:839] in kernel32 (0x0032ffe8)
  5 0xf7e86a37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7ebb9024 IDirect3D9Impl_GetAdapterIdentifier+0x84 [/home/josh/wine/dlls/d3d9/directx.c:124] in d3d9: movl	0x0(%edx),%ecx
124	    hr = IWineD3D_GetAdapterIdentifier(This->WineD3D, Adapter, Flags, &adapter_id);
Modules:
Module	Address			Debug info	Name (74 modules)
PE	  400000- 2101000	Export          iw3sp
PE	 2110000- 247f000	Deferred        d3dx9_34
PE	18000000-18033000	Deferred        binkw32
PE	21100000-21197000	Deferred        mss32
ELF	7b800000-7b92c000	Dwarf           kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e2c3000-7e2f5000	Deferred        uxtheme<elf>
  \-PE	7e2d0000-7e2f5000	\               uxtheme
ELF	7e2f5000-7e31b000	Deferred        msacm32<elf>
  \-PE	7e300000-7e31b000	\               msacm32
ELF	7e31b000-7e332000	Deferred        msacm32<elf>
  \-PE	7e320000-7e332000	\               msacm32
ELF	7e332000-7e3f5000	Deferred        libasound.so.2
ELF	7e3f5000-7e42b000	Deferred        winealsa<elf>
  \-PE	7e400000-7e42b000	\               winealsa
ELF	7e42b000-7e430000	Deferred        libxfixes.so.3
ELF	7e430000-7e438000	Deferred        libxrender.so.1
ELF	7e438000-7e441000	Deferred        libxcursor.so.1
ELF	7e441000-7e45f000	Deferred        imm32<elf>
  \-PE	7e450000-7e45f000	\               imm32
ELF	7e45f000-7e477000	Deferred        libxcb.so.1
ELF	7e477000-7e55e000	Deferred        libx11.so.6
ELF	7e55e000-7e56c000	Deferred        libxext.so.6
ELF	7e56c000-7e5e7000	Deferred        winex11<elf>
  \-PE	7e580000-7e5e7000	\               winex11
ELF	7e5e7000-7e5fc000	Deferred        libz.so.1
ELF	7e5fc000-7e66c000	Deferred        libfreetype.so.6
ELF	7e66c000-7e67f000	Deferred        libresolv.so.2
ELF	7e681000-7e695000	Deferred        midimap<elf>
  \-PE	7e690000-7e695000	\               midimap
ELF	7e695000-7e6b3000	Deferred        iphlpapi<elf>
  \-PE	7e6a0000-7e6b3000	\               iphlpapi
ELF	7e6b3000-7e714000	Deferred        rpcrt4<elf>
  \-PE	7e6c0000-7e714000	\               rpcrt4
ELF	7e714000-7e7b8000	Deferred        ole32<elf>
  \-PE	7e720000-7e7b8000	\               ole32
ELF	7e7b8000-7e80e000	Deferred        ddraw<elf>
  \-PE	7e7c0000-7e80e000	\               ddraw
ELF	7e80e000-7e8cd000	Deferred        comctl32<elf>
  \-PE	7e820000-7e8cd000	\               comctl32
ELF	7e8cd000-7e926000	Deferred        shlwapi<elf>
  \-PE	7e8e0000-7e926000	\               shlwapi
ELF	7e926000-7ea32000	Deferred        shell32<elf>
  \-PE	7e940000-7ea32000	\               shell32
ELF	7ea32000-7ea9b000	Deferred        msvcrt<elf>
  \-PE	7ea40000-7ea9b000	\               msvcrt
ELF	7ea9b000-7eb9d000	Deferred        wined3d<elf>
  \-PE	7eab0000-7eb9d000	\               wined3d
ELF	7eb9d000-7ebcd000	Dwarf           d3d9<elf>
  \-PE	7eba0000-7ebcd000	\               d3d9
ELF	7ebcd000-7ec1f000	Deferred        advapi32<elf>
  \-PE	7ebe0000-7ec1f000	\               advapi32
ELF	7ec1f000-7ecb9000	Deferred        gdi32<elf>
  \-PE	7ec30000-7ecb9000	\               gdi32
ELF	7ecb9000-7edff000	Deferred        user32<elf>
  \-PE	7ecd0000-7edff000	\               user32
ELF	7edff000-7ee8d000	Deferred        winmm<elf>
  \-PE	7ee10000-7ee8d000	\               winmm
ELF	7efad000-7efc5000	Deferred        libnsl.so.1
ELF	7efc5000-7efea000	Deferred        libm.so.6
ELF	7efeb000-7eff6000	Deferred        libnss_files.so.2
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	f7cf3000-f7cfc000	Deferred        libnss_compat.so.2
ELF	f7cfd000-f7d01000	Deferred        libdl.so.2
ELF	f7d01000-f7e50000	Deferred        libc.so.6
ELF	f7e51000-f7e69000	Deferred        libpthread.so.0
ELF	f7e6b000-f7e70000	Deferred        libxdmcp.so.6
ELF	f7e70000-f7e72000	Deferred        libxcb-xlib.so.0
ELF	f7e72000-f7e75000	Deferred        libxau.so.6
ELF	f7e7f000-f7fb5000	Dwarf           libwine.so.1
ELF	f7fb7000-f7fd6000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3sp.exe
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	0000000e    0
	0000000d    0
0000000f 
	00000012    0
	00000011    0
	00000010    0
00000015 
	00000016    0
Backtrace:
=>1 0x7ebb9024 IDirect3D9Impl_GetAdapterIdentifier+0x84(iface=0x138520, Adapter=0x0, Flags=0x0, pIdentifier=0x32f8fc) [/home/josh/wine/dlls/d3d9/directx.c:124] in d3d9 (0x0032f8e4)
  2 0x00593836 in iw3sp (+0x193836) (0x0032fd60)
  3 0x00595626 in iw3sp (+0x195626) (0x0032ff08)
  4 0x7b876447 start_process+0xc7(arg=0x0) [/home/josh/wine/dlls/kernel32/process.c:839] in kernel32 (0x0032ffe8)
  5 0xf7e86a37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$ 

``` 

sorry for the long code. any solution?
[http://ubuntuforums.org/showthread.php?t=763803](http://ubuntuforums.org/showthread.php?t=763803) please post there or here.
thanks!

---

### Post by cogadh on 2008-04-23
It looks like you don't have the accelerated/restricted drivers for your video card installed. What model video card do you have?

---

### Post by thefishki345 on 2008-04-24
I have a nvidia 8800gts 512mb 
I have enabled the drivers in the hardware drivers, but im not sure if I need anything else, do I?
thanks for the quick reply

---

### Post by cogadh on 2008-04-24
All you should need to do is enable the restricted driver in the Restricted Drivers Manager (and then reboot). Check your \etc\X11\xorg.conf file and see if the driver listed for your video card says "nv" or "nvidia". If it says "nv", then you aren't using the restricted driver, you are using the generic Nvidia driver that comes with the default Ubuntu install (which can't really do 3D).

---

### Post by thefishki345 on 2008-04-24
Thanks again for the reply, it says nvidia. and I tried using envy to install the drivers, but I still get the same error messages in terminal. please help.

---

### Post by thefishki345 on 2008-04-25
The error is that opengl did not compile properly when I compiled it with wine git from my tutorial, how to fix this I do not no. help please!!!!!

---

### Post by ahaslam on 2008-04-25
That guide looks good & it's the first I've seen that's not copied form either here or linuX-gamers. I've not read it all but I suggest 2 things; don't use git & use my compile options (which include opengl). Wine is a complex app & is rendered useless if compiled incorrectly.

---

### Post by thefishki345 on 2008-04-25
OK I will try your way, but cos im on 64 bit should I still run the script that the guide I am using suggests?

---

### Post by thefishki345 on 2008-04-26
I tried doing your guide ahalasam, everything went well until:
```
./configure --prefix=/usr --sysconfdir=/etc --enable-opengl --with-x

```

I get the same error when I config using your guide something like ¨error no opengl support found on this system, opengl and direct3d will not be enabled¨ which is the same error I get when I try everything. Any suggestions?

and on a side note, now when I try to even run the command again I get this: bash: ./configure: No such file or directory

---

### Post by ahaslam on 2008-04-26
Can you confirm the following links exist:

```
ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so
ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so

```

I went to have a proper look at the other guide but it's not accessible atm. If this doesn't help I'll have a go myself on Hardy64.

On a side note & as a heads-up, the latest Wine release requires a different patch. I'll test 0.9.60 & update the guide if there's any improvement.

---

### Post by ahaslam on 2008-04-26
0.9.60 compiles fine with Ben P's 3dmark patch on 64-bit Hardy:

```
sudo apt-get build-dep wine
mkdir wine && cd wine
wget http://easynews.dl.sourceforge.net/sourceforge/wine/wine-0.9.60.tar.bz2
tar -xvjf wine-0.9.60.tar.bz2 && cd wine-0.9.60
wget http://www.bennyp.org/wine/wine-0.9.59-3dmark.patch
patch -p1 < wine-0.9.59-3dmark.patch
mkdir -p `pwd`/lib32
ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so
ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so
ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so
ln -s /usr/lib32/libfontconfig.so.1 `pwd`/lib32/libfontconfig.so
ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so
ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so
ln -s /usr/lib32/libXrender.so.1 `pwd`/lib32/libXrender.so
ln -s /usr/lib32/libXinerama.so.1 `pwd`/lib32/libXinerama.so
ln -s /usr/lib32/libXxf86vm.so.1 `pwd`/lib32/libXxf86vm.so
ln -s /usr/lib32/libXi.so.6 `pwd`/lib32/libXi.so
ln -s /usr/lib32/libXrandr.so.2 `pwd`/lib32/libXrandr.so
ln -s /usr/lib32/liblcms.so.1 `pwd`/lib32/liblcms.so
ln -s /usr/lib32/libpng12.so.0 `pwd`/lib32/libpng.so
ln -s /usr/lib32/libcrypto.so.0.9.8 `pwd`/lib32/libcrypto.so
ln -s /usr/lib32/libssl.so.0.9.8 `pwd`/lib32/libssl.so
ln -s /usr/lib32/libxml2.so.2 `pwd`/lib32/libxml2.so
ln -s /usr/lib32/libjpeg.so.62 `pwd`/lib32/libjpeg.so
ln -s /usr/lib32/libXcomposite.so.1 `pwd`/lib32/libXcomposite.so
ln -s /usr/lib32/libcups.so.2 `pwd`/lib32/libcups.so
ln -s /usr/lib32/libXcursor.so.1 `pwd`/lib32/libXcursor.so
ln -s /usr/lib32/libdbus-1.so.3 `pwd`/lib32/libdbus-1.so
ln -s /usr/lib32/libhal.so.1 `pwd`/lib32/libhal.so
ln -s /usr/lib32/libsane.so.1 `pwd`/lib32/libsane.so
ln -s /usr/lib32/libgphoto2.so.2 `pwd`/lib32/libgphoto2.so
ln -s /usr/lib32/libgphoto2_port.so.0 `pwd`/lib32/libgphoto2_port.so
ln -s /usr/lib32/libldap-2.4.so.2 `pwd`/lib32/libldap.so
ln -s /usr/lib32/libldap_r-2.4.so.2 `pwd`/lib32/libldap_r.so
ln -s /usr/lib32/liblber-2.4.so.2 `pwd`/lib32/liblber.so
ln -s /usr/lib32/libxslt.so.1 `pwd`/lib32/libxslt.so
ln -s /usr/lib32/libcapi20.so.3 `pwd`/lib32/libcapi20.so
ln -s /usr/lib32/libjack.so.0 `pwd`/lib32/libjack.so
ln -s /usr/lib32/libodbc.so.1 `pwd`/lib32/libodbc.so
CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure --prefix=/usr --sysconfdir=/etc --enable-opengl --with-x
make 
sudo make install
```

Game installation & play not tested yet, hope to have time tomorrow.

;)

---

### Post by thefishki345 on 2008-04-26
well, wine 9.60 wine git works in cod4 singleplayer noe on 64 bit 8.04 with the old patch yay!! thanksyou all for your help, but I have no idea how I got it to work, I think I had to install some extra opengl stuff, but its all fine now, except when I try and run multiplayer it just crashes on startup, any suggestions? But that new guide looks good, basically what I had to do on that other guide except I made a script (check that other guide) but I will just stick to what I´ve got now unless I dont get multiplayer to work.

---

### Post by thefishki345 on 2008-04-27
damn! for some reason now cod4 doesnt work, singleplayer or multiplayer, so I am trying your new guide now, thanks ahalasam!

---

### Post by andrebrait on 2008-04-27
here it starts,. but freeze when you are supposed to choose the game difficulty...

---

### Post by ahaslam on 2008-04-27
SP & MP work fine here with the [1.4 cod patch]("http://www.gamershell.com/download_22482.shtml"). It's not as fast as with Wine 0.9.50 under Arch 64 though.

If referring to my previous guide for installation/setup, you can now skip the d3dx9_34.dll, it's no longer required. As always, issue 'wineprefixcreate' after a Wine upgrade. 

;)

---

### Post by thefishki345 on 2008-04-27
Sorry andrebait, I am not sure what to suggest, did you turn off the special graphics features (soften smoke edges etc, go to page 2 for more info)
anyway, thanks ahalasam for that guide, you have been thanked and thanks ben.p for the patch, singleplayer plays and runs fine, but still, multiplayer crashes at startup and does not respond, any ideas?

EDIT: sorry ahalasam didnt see your last post, I will try the 1.4 patch later (when my download rate restarts :)

---

### Post by andrebrait on 2008-04-27
yes
I created a topic about it

this is what I get

[quote]err:seh:setup_exception_record stack overflow 816 bytes in thread 001c eip f7ca9be8 esp 7cad5000 stack 0x7cad4000-0x7cad5000-0x7cbd5000
err:ntdll:RtlpWaitForCriticalSection section 0x7eba1e7c "d3d9_main.c: d3d9_cs" wait timed out in thread 0009, blocked by 001c, retrying (60 sec)
[quote]

---

### Post by ahaslam on 2008-04-27
> **andrebrait said:**
> d3d9_main.c: d3d9_cs
Weird. As long as directx didn't attempt installation & you have no MS .dll's you shouldn't see this. Can you confirm these points?

If you've upgraded from a previous Wine version run wineprefixcreate. If directx attempted installation rm -r ~/.wine prior to wineprefixcreate. Any MS .dll's can be safely removed.

---

### Post by andrebrait on 2008-04-27
no, that's a clean install

and I hadn't the dlls, but this is seen with both, native dlls and builtin ones..

anyway, I discovbered that disabling some graphical options would help..

I don't know which one, I'll find out later

---

### Post by andrebrait on 2008-04-27
Got it!!

There must be a problem with the vertex shaders!

Disabling the Shadows solved all the errors, improved the performance A LOT... but reduced proportionally the realism...

I've read somewhere that newer nvidia drivers could make irt work..

Someone know a way to make deb packages with them, just like envy do?

---

### Post by ahaslam on 2008-04-27
Glad it's sorted ;)

Hardy has the latest driver (& shadows do work), what release are you running? 

The .run from Nvidia is the simplest way to get updated drivers imo, but then I'm a little out of touch with Ubuntu & have never tried Envy. If you really want to build a package here's an good guide with relevant scripts: [http://www.xs4all.nl/~carlo17/howto/nvidia.html](http://www.xs4all.nl/~carlo17/howto/nvidia.html)

;)

---

### Post by andrebrait on 2008-04-27
How exactly did you got it to work?

---

### Post by Rylin on 2008-04-27
Any of you guys know how to get passed this issue here? I'm stumped :confused:

---

### Post by ahaslam on 2008-04-28
What video cards are you both running?

Andrebrait, you could try the [FBO rendering mode & memory size registry entries]("http://wiki.winehq.org/UsefulRegistryKeys"). 

Rylin, have you tried without composite? That desktop's too nice ;)

---

### Post by Rylin on 2008-04-28
> **ahaslam said:**
> What video cards are you both running?

Andrebrait, you could try the [FBO rendering mode & memory size registry entries]("http://wiki.winehq.org/UsefulRegistryKeys"). 

Rylin, have you tried without composite? That desktop's too nice ;)


I disabled composite but no success in running COD4. Still getting that same message. I see people are having to paste certain .dll files but my error message doesn't seem to relate to that (as far as I can see). Anyone else get this message before and found a solution? I'm running a GeForce 6800 Ultra by the way, which runs COD4 fine under windows.

Thanks for the compliment btw. :)

---

### Post by thefishki345 on 2008-04-28
Rylin I got this error too, I dont think wine compiled properly with opengl when you compiled it. and btw, how did you get that cool gnome desktop? pm me a tutorial if you get time :) :p

---

### Post by Rylin on 2008-04-28
If the compiling went wrong when I installed wine, how would I go about fixing that then?

Pm'ed you thefishki345 :popcorn:

---

### Post by ahaslam on 2008-04-28
Due to high demand I've decided to share my build. It's only a checkinstall, though I have added the relevant dependencies. 

It is stressed that this package is for use with 64-bit Hardy Heron (8.04) only & comes with no guarantee. 

Download: [wine_0.9.60-1_amd64.deb]("http://static.digitalvault.bt.com/static/anthonyhaslam/storage/0d7ab399c73fa3fd3f41928614684757/481600c4/YQOz7u.deb/wine_0.9.60-1_amd64.deb?save")
[RapidShare]("http://rapidshare.com/files/111274293/wine_0.9.60-1_amd64.deb.html")
md5: 6a396c5066fae5e172f65f0fdbc9c250

---

### Post by Rylin on 2008-04-28
Can it be altered in anyway to work with 32-bit version?

Appreciate the help btw. :)

---

### Post by ahaslam on 2008-04-28
I doubt the arch can be forced & there're extra dependencies. It's a lot quicker & simpler to compile 32-bit Wine though. Just follow my guide on page 2 & substitute the patch for the one I used on page 11 if the Wine version is >0.9.58.

---

### Post by andrebrait on 2008-04-28
In order to run COD4 you have to use the patch for 3DMark 06 in Wine's source

If you are compiling in 64-bit, read in WineHQ how to compile it for 64-bit Hardy.

I'll try these entries when I get in my home.

For now, I tried these combinations:

Old 3DMark patch + Git Wine
Old 3DMark Patch + wine 0.9.60
New 3DMark Patch + Wine 0.9.60
New 3DMark Patch + Somebody's patch I've found + Wine 0.9.60

The best combo was the New 3DMark + Wine 0.9.60

I Trie with nVidia drivers 169.12 and 173.08 and got the same results

Now I disovered I have to disable:
Specular map
Shadows
Glow

In order to achieve a 100% Stable game. :mad:

---

### Post by thefishki345 on 2008-04-29
ALSO soften smoke edges!!! the game gets all screwed up if you keep this.
sad that you have to turn off most of the cool effects
I enabled shadows and it played fine except that the shadows didnt show.
also glow works, and I think you have to have this enabled if you wanna use night vision.
Does anyone else have a problem that in most fps games running under wine, when you press the, say W button to move forward and hold it, and sometimes when you let go it moves automatically? then when you exit it then go into say, a text editor it will just repedatley type ¨WWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWW¨ etc etc
 and then you have to log out and log back in.
I find this really, really, really, really annoying, especially when it happens practically everytime I play cod4!

---

### Post by Rylin on 2008-04-29
> **andrebrait said:**
> In order to run COD4 you have to use the patch for 3DMark 06 in Wine's source

If you are compiling in 64-bit, read in WineHQ how to compile it for 64-bit Hardy.

I'll try these entries when I get in my home.

For now, I tried these combinations:

Old 3DMark patch + Git Wine
Old 3DMark Patch + wine 0.9.60
New 3DMark Patch + Wine 0.9.60
New 3DMark Patch + Somebody's patch I've found + Wine 0.9.60

The best combo was the New 3DMark + Wine 0.9.60

I Trie with nVidia drivers 169.12 and 173.08 and got the same results

Now I disovered I have to disable:
Specular map
Shadows
Glow

In order to achieve a 100% Stable game. :mad:


How do I go about installing this patch?

---

### Post by ahaslam on 2008-04-29
Rylin, Look over my previous post again, please say if I'm missing something.

thefishki345, if I have the nautilus file manager open I'll see its search box fill with w's, a's, s's, d's, etc until I fire with the mouse. My only other observation is a huge performance drop in Ubuntu over Arch. Under Arch I can set textures to 'extra' & it's faster than 'normal' under Ubuntu. The texture settings are more important than effects imo & really add realism.

Extra screens:

---

### Post by thefishki345 on 2008-04-29
Yeah..
DAMNIT!!
does anyone else sometimes have this thing where when you go and launch cod4 singleplayer OR multiplayer it doesnt launch? before it was just multiplayer and that was cos of the patch, this is really annoying cos then I have to go and uninstall it and start the game again from the VERY beginning!!!

---

### Post by ahaslam on 2008-04-29
Not here, maybe a reinstall is needed for you. You don't need to start from the beginning though, just backup your profile.

~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare/players/profiles

;)

---

### Post by thefishki345 on 2008-04-29
Yeah, thats what im doing, but I am recompiling wine now, AGAIN for the 4th time cos when I just normally reinstall cod4 it doesnt make any desktop shortcuts, so then I cant patch it with the no dvd patch, and it prolly doesnt work properly anyway.
and, when wine gets updated to 9.61 or something, how do you update it if you have compiled it from source?

---

### Post by ahaslam on 2008-04-29
You're on 64-bit aren't you? You could yse my deb to save time. 

Desktop links (whether applied or not) will not affect the use of a fixed exe.

If compiled from source & used checkinstall, it's no different to updating any other package. If you've not used this & still have your source dir laying around you can cd to it & issue 'make uninstall' (check the makefile), before compiling/installing a new version.

PS. Why update Wine unless you know there's a fix that you need? Still running 0.9.50 on my main rig. :)

---

### Post by andrebrait on 2008-04-29
Just grab th ptch somewhere
In AppDB, you can find my testing, before these bugs became real and:

The old patch, In the Information camp.
The new patch, in 2 posts right below the information camp,one is mine and other is from its creator.

to patch, download wine's source code and extract it

```
wget wine-0.9.60.tar.bz2
tar xjfv  wine-0.9.60.tar.bz2
cd wine-0.9.60
patch -p1 < patch-new.patch
(IF YOU ARE IN 64-BIT, READ [THIS]("http://wiki.winehq.org/WineOn64bit"))
./configure
make dep && make
sudo make install
```

and here you go =D

---

### Post by ahaslam on 2008-04-29
Déjà vu

---

### Post by woahitsmatt on 2008-04-29
This is going to sound absolutely absurd...but I am a linux noob and I just cannot get this to work after going through all the steps on the thread.

I try to run Cod4 and I get the same error:
```

"----- Initializing Renderer ----
----- Client Initialization Complete -----
Attempting 44 kHz 16 bit [Windows default] sound
ERROR: Couldn't initialize digital driver: DirectSoundCreate() failed in get_system_speaker_configuration()


Error during initialization:
Miles sound system initialization failed.
Make sure you have your sound card's latest drivers and DirectX installed."
```


I've installed the DirectX .dll's....but I still have no clue why this is not working....I am using an ATI Radeon x1700....Hardy AMD64bit

---

### Post by andrebrait on 2008-04-30
I got it once, but it fixed I don't know how

I'm giving up
No matter what I do, it won't run...

And other strange thing happened today

If I try to run the command in the launcher, I get an error..

the command is

env WINEPREFIX="/home/andrebrait/.cod4" wine "C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3sp.exe"

and I get, if not launching it from the launcher

A Window that says

WIN_IMPROPER_QUIT_BODY
YES - NO - CANCEL

and The Game's console open and show me this: (Attachment) :mad: :mad: :mad: :mad: :mad: :mad: :mad: :mad:

---

### Post by andrebrait on 2008-04-30
Ok, tested the flollowing combinations now

Wine 0.9.60 + Old 3DMark Pacth
Wine 0.9.60 + New 3DMark Patch
Wine 0.9.60 + Old 3DMark Patch + Rico Patch
Wine 0.9.60 + New 3DMark Patch + Rico Patch

With All of them, I had to use FBO rendering. 
But it would result in square lightning ¬¬"
And, with Backbuffer, see for yourself
The light RUN AWAY FROM ME!!!

THIS IS THE MOST WEIRD BUG IN WINE I'VE EVER SEEN!!

I took 3 screenshots
In 2 of them, the first and second ondes, you can see the light running away from me, and in the 3rd, the "square" illumination ¬¬"

---

### Post by andrebrait on 2008-04-30
Forgot the screenshots :lolflag:
As you can notice, in the second screenshot, the light in in the truck, and in the first, the light is in the van

It simply ran away from me when I walked in its direction

---

### Post by thefishki345 on 2008-05-01
poor you andrebait, that still looks pretty funny though (the light running away from you) my only suggestion is to try turning off ALL the special effects, then see if that works, then turn the ones that you know work 1 at a time so you know which ones screw up the gameplay.
now for my problem:
I updated to the 1.4 patch, and STILL cant run multiplayer, any ideas?

---

### Post by thefishki345 on 2008-05-02
erm...anyone?
bump

---

### Post by piratesmack on 2008-05-04
Hey can someone else try running the game in Wine 0.9.61?
I'm getting insane graphical glitches in this version (never had them in the previous versions) and I'm wondering if anyone else is having them as well.

Screenshot here:
[http://ubuntuforums.org/attachment.php?attachmentid=68706&d=1209874518](http://ubuntuforums.org/attachment.php?attachmentid=68706&d=1209874518)

Thanks

---

### Post by ahaslam on 2008-05-04
Do you need 0.9.61?

---

### Post by piratesmack on 2008-05-04
> **ahaslam said:**
> Do you need 0.9.61?

eh not really, but I like to have the latest Wine for some reason :-P

I do want to find out if others are having this problem before I go making a bug report, though

---

### Post by thefishki345 on 2008-05-04
hmm..im not sure, cos im not using .61 and no offence I dont want to cos I have no reason to.
but does anyone have anyadvice on what I posted before,
before or after I updated to the 1.4 patch cod4 multiplayer doesnt start/crashes at startup, any advice?

---

### Post by ahaslam on 2008-05-04
If you've not previously cleared out your ~/.wine dir then give it a shot & start over (a long haul, I know). Also, try my package on page 12 if on 64-bit & always ensure use of wineprefixcreate after upgrade. 

I know that's nothing new, but I don't see why it wouldn't work, other than there being an OS issue.

---

### Post by ahaslam on 2008-05-04
[QUOTE=piratesmack;4877663]
AppDB confirms glitches, unless that's your report. I would stick with what works & consult the DB before any upgrade.

---

### Post by piratesmack on 2008-05-04
> **ahaslam said:**
> [QUOTE=piratesmack;4877663]
AppDB confirms glitches, unless that's your report. I would stick with what works & consult the DB before any upgrade.

Thanks
Yeah that is my report

What I ended up doing is going back to a dual-boot with Vista.

---

### Post by piratesmack on 2008-05-04
> **thefishki345 said:**
> hmm..im not sure, cos im not using .61 and no offence I dont want to cos I have no reason to.
but does anyone have anyadvice on what I posted before,
before or after I updated to the 1.4 patch cod4 multiplayer doesnt start/crashes at startup, any advice?

Actually, I had the same problem on my other PC. Single player would run fine but multiplayer would crash on startup. It turned out the problem was with my soundcard. (not sure exactly why) But this is what fixed it for me:

Open a terminal and type
```

winecfg

```

Then click the audio tab and change the driver from ALSA to OSS. I think it mentions this in the AppDB as well

---

### Post by ahaslam on 2008-05-04
^ & earlier in this thread now you mention it (completely forgot, sorry thefishki345)...

I use ALSA tho & all is well (so obviously depends on setup), bear in mind you'll loose mixing with OSS.

---

### Post by thefishki345 on 2008-05-05
tried that piratesmack and ahalasam before, and still it crashes, in avant window navigator the icon just stays there and my mouse pointer is usually black but in desktop when I scroll over the middle it goes white like the cod4 mouse pointer. any other ideas?
I wanna play multiplayer cos I almost finishes singleplayer!

PS: also, I dont have an extra sound card, im using the onboard sound on the ASUS M3A board.

---

### Post by thefishki345 on 2008-05-06
Bump, and I heard on some other forum (but its for windows so im not sure if it will work or not but it says to just simply plug in a microphone cos I am using realtek onboard sound on asus M3A and apparently there is an error with those cards, does neone else have these problems?
Im yet to try the microphone one, because I dont have a mic (yet) so I will borrow my friends.

---

### Post by ahaslam on 2008-05-06
If that has any weight, you could try disabling sound device in bios or simply plugging headphones in to mic port.

---

### Post by thefishki345 on 2008-05-06
hmmm...ok
well I am yet to try the mic thing,but if that fails, does anyone have any suggestions?
could it be that the latest version of wine broke something for 64 bit and the older versions would work?

on a side note: I have almost finished cod4 singleplayer on vet, some of it is freaking hard!

---

### Post by thefishki345 on 2008-05-06
so I tried it with wine 9.50 but it doesnt work, the installer wont launch, so im going back to 9.60
but CRAP! i removed my activison directory AND the save files, so I have to start all ofver again F***!!!!!!!!!!!!!!!!!!!!!!!!!

EDIT: Phew, nevermind, found a thing on the internet, you just have to edit something in the config file, google it if yuo have the same problem as me.
that was close cos I was on the 2nd last level lol.

---

### Post by ahaslam on 2008-05-07
You must be good to play on veteran. I've been playing FPS since Doom & only played on hardened. ;)

---

### Post by thefishki345 on 2008-05-07
whoops, sorry I mean hardened lol
I havent tried vet yet, but if hardened is sorta hard then vet will be.
waaah I wanna play MP!

---

### Post by thefishki345 on 2008-05-07
Ahalasam, Could you please if you have time or know how to make an amd 64 bit deb for wine 9.50 ubuntu 8.04 or a good solid wine that runs really well (cos in the appdb someone else is haveing the same prob as me (cant launch Mp but sp runs fine) and he says that it works on anthing lower than .97 so please, I would really appreciate that and we could use it  for anyone else having trouble.
oh yeah,and I found out what nexuiz is, looks pretty cool kinda like UT classic. might Dl it overnight or something...

---

### Post by ahaslam on 2008-05-07
I tested 0.9.60 to work on an ASUS P5K, my 64-bit build is [here]("http://rapidshare.com/files/111274293/wine_0.9.60-1_amd64.deb.html"). If you were using ArchLinux, I'd gladly provide a PKGBUILD for *.50, but you'd be better off compiling, I'm setting up water cooling tonight ;)

I'm wondering if Steve @ AppDB had made other upgrades within those 6 weeks? As both *.50 & *.60 work well here in MP...

Nexuiz? You're gonna get these peeps confused by mixing up our PM's ;)  There's a package in [universe] btw ;)

---

### Post by piratesmack on 2008-05-07
> **ahaslam said:**
> I tested 0.9.60 to work on an ASUS P5K, my 64-bit build is [here]("http://rapidshare.com/files/111274293/wine_0.9.60-1_amd64.deb.html"). If you were using ArchLinux, I'd gladly provide a PKGBUILD for *.50, but you'd be better off compiling, I'm setting up water cooling tonight ;)

**I'm wondering if Steve @ AppDB had made other upgrades within those 6 weeks? As both *.50 & *.60 work well here in MP...**

Nexuiz? You're gonna get these peeps confused by mixing up our PM's ;)  There's a package in [universe] btw ;)

[http://appdb.winehq.org/commentview.php?iAppId=5934&iVersionId=10429&iThreadId=33442](http://appdb.winehq.org/commentview.php?iAppId=5934&iVersionId=10429&iThreadId=33442)

yeah I realized that the problem was with my soundcard, I had recently taken out my PCI soundcard and used the onboard audio (Since my onboard audio was more Linux-compatible) I realized this was a problem with my soundcard when I tried the game in Vista and had the same problem. I managed to get it working in Linux by switching to OSS, but it didn't sound very good... So I just popped the PCI card back in and multiplayer worked fine

---

### Post by thefishki345 on 2008-05-08
Ok, well I will keep looking into this.

---

### Post by piratesmack on 2008-05-08
Hey can anyone help me with making a debian package for the patched version of Wine? I know how to make them with checkinstall, but I want to learn how to make them the "right" way. 

I've been looking at this guide:
[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

But I'm a little confused about how I would go about doing this with a patched Wine on Ubuntu x64.

Thanks

---

### Post by thefishki345 on 2008-05-08
Wouldnt the checkinstall thing work fine?
I am not sure, but if its compiled with a patch it should still work, are you making this for wine 9.60 + or before? if your making it for like wine 9.50 or wine 9.57 or in between I will happily try it out for you.

---

### Post by thefishki345 on 2008-05-08
Just finished cod4 singleplayer, F***ing awesome! except the ending was pretty sad and a bit stupid and im confused about it, I mean WTF happened? lol
anyway,
ahalasam, if you do get a spare moment, could you please make a package thing like you did for .60 on 64 bit for .50 or up to .57 but no later (with the older patch) whichever one you think might work best and post it here, if you get time, cos it will give me something to work with it works or if it doesnt. Thanks!

edit: yes I have tried compiling it but it didnt work very well.

edit2:
here is the code I get when I try and run Mp in command line:
```
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f8fc,0x00000000), stub!
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xd5b0c78) : pBox=(nil) stub
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
wine client error:1f: write: Bad file descriptor
username@hostname:~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$ cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare/
username@hostname:~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$ wine iw3mp.exe
wine: Unhandled page fault on read access to 0x0000015c at address 0x7d7df8ce (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0000015c in 32-bit code (0x7d7df8ce).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d7df8ce ESP:0032ef6c EBP:ffffffff EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7d4c2000 ECX:7c0bc978 EDX:00000000
 ESI:7c0bc978 EDI:7c0bc978
Stack dump:
0x0032ef6c:  7d4c2000 7e1b4008 7d4d7840 0001ffff
0x0032ef7c:  7c0dadc0 00dd5190 01000000 00000000
0x0032ef8c:  00000000 7c07c488 7c0dada8 00000001
0x0032ef9c:  f7cf1994 000d9ef8 00000001 f7dd3ff4
0x0032efac:  0032f167 0032efd4 f7cf2c0d 0032eff8
0x0032efbc:  0032f128 0032f167 0032f118 f7dd3ff4
Backtrace:
=>1 0x7d7df8ce in libglcore.so.1 (+0x2108ce) (0xffffffff)
0x7d7df8ce: movl	0x15c(%eax),%eax
Modules:
Module	Address			Debug info	Name (91 modules)
PE	  400000- d935000	Deferred        iw3mp
PE	18000000-18033000	Deferred        binkw32
PE	21100000-21197000	Deferred        mss32
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d5cf000-7e0e4000	Export          libglcore.so.1
ELF	7e0e4000-7e188000	Deferred        libgl.so.1
ELF	7e207000-7e239000	Deferred        uxtheme<elf>
  \-PE	7e210000-7e239000	\               uxtheme
ELF	7e239000-7e24d000	Deferred        midimap<elf>
  \-PE	7e240000-7e24d000	\               midimap
ELF	7e24d000-7e273000	Deferred        msacm32<elf>
  \-PE	7e250000-7e273000	\               msacm32
ELF	7e273000-7e28a000	Deferred        msacm32<elf>
  \-PE	7e280000-7e28a000	\               msacm32
ELF	7e28a000-7e2c5000	Deferred        wineoss<elf>
  \-PE	7e290000-7e2c5000	\               wineoss
ELF	7e2ea000-7e2ef000	Deferred        libxfixes.so.3
ELF	7e2f9000-7e2fb000	Deferred        libnvidia-tls.so.1
ELF	7e2fd000-7e306000	Deferred        libxcursor.so.1
ELF	7e306000-7e309000	Deferred        libxcomposite.so.1
ELF	7e309000-7e30f000	Deferred        libxrandr.so.2
ELF	7e30f000-7e317000	Deferred        libxrender.so.1
ELF	7e317000-7e31a000	Deferred        libxinerama.so.1
ELF	7e31a000-7e338000	Deferred        imm32<elf>
  \-PE	7e320000-7e338000	\               imm32
ELF	7e338000-7e33d000	Deferred        libxdmcp.so.6
ELF	7e33d000-7e355000	Deferred        libxcb.so.1
ELF	7e355000-7e43c000	Deferred        libx11.so.6
ELF	7e43c000-7e44a000	Deferred        libxext.so.6
ELF	7e44a000-7e44f000	Deferred        libxxf86vm.so.1
ELF	7e44f000-7e4e5000	Deferred        winex11<elf>
  \-PE	7e460000-7e4e5000	\               winex11
ELF	7e505000-7e526000	Deferred        libexpat.so.1
ELF	7e526000-7e550000	Deferred        libfontconfig.so.1
ELF	7e550000-7e565000	Deferred        libz.so.1
ELF	7e565000-7e567000	Deferred        libxcb-xlib.so.0
ELF	7e57c000-7e5ec000	Deferred        libfreetype.so.6
ELF	7e5ec000-7e642000	Deferred        ddraw<elf>
  \-PE	7e5f0000-7e642000	\               ddraw
ELF	7e642000-7e701000	Deferred        comctl32<elf>
  \-PE	7e650000-7e701000	\               comctl32
ELF	7e701000-7e75a000	Deferred        shlwapi<elf>
  \-PE	7e710000-7e75a000	\               shlwapi
ELF	7e75a000-7e866000	Deferred        shell32<elf>
  \-PE	7e770000-7e866000	\               shell32
ELF	7e866000-7e8c7000	Deferred        rpcrt4<elf>
  \-PE	7e870000-7e8c7000	\               rpcrt4
ELF	7e8c7000-7e96b000	Deferred        ole32<elf>
  \-PE	7e8e0000-7e96b000	\               ole32
ELF	7e96b000-7e9b5000	Deferred        dsound<elf>
  \-PE	7e970000-7e9b5000	\               dsound
ELF	7e9b5000-7e9d4000	Deferred        d3dx8<elf>
  \-PE	7e9c0000-7e9d4000	\               d3dx8
ELF	7e9d4000-7e9f1000	Deferred        d3dx9_36<elf>
  \-PE	7e9e0000-7e9f1000	\               d3dx9_36
ELF	7e9f1000-7ea0a000	Deferred        d3dx9_34<elf>
  \-PE	7ea00000-7ea0a000	\               d3dx9_34
ELF	7ea0a000-7eb0c000	Deferred        wined3d<elf>
  \-PE	7ea20000-7eb0c000	\               wined3d
ELF	7eb0c000-7eb3c000	Deferred        d3d9<elf>
  \-PE	7eb10000-7eb3c000	\               d3d9
ELF	7eb3c000-7eb5a000	Deferred        iphlpapi<elf>
  \-PE	7eb40000-7eb5a000	\               iphlpapi
ELF	7eb5a000-7eb86000	Deferred        ws2_32<elf>
  \-PE	7eb60000-7eb86000	\               ws2_32
ELF	7eb86000-7eba0000	Deferred        wsock32<elf>
  \-PE	7eb90000-7eba0000	\               wsock32
ELF	7eba0000-7ebf2000	Deferred        advapi32<elf>
  \-PE	7ebb0000-7ebf2000	\               advapi32
ELF	7ebf2000-7ec8d000	Deferred        gdi32<elf>
  \-PE	7ec00000-7ec8d000	\               gdi32
ELF	7ec8d000-7edd3000	Deferred        user32<elf>
  \-PE	7ecb0000-7edd3000	\               user32
ELF	7edd3000-7ee61000	Deferred        winmm<elf>
  \-PE	7ede0000-7ee61000	\               winmm
ELF	7ef81000-7ef8c000	Deferred        libnss_files.so.2
ELF	7ef8d000-7ef90000	Deferred        libxau.so.6
ELF	7ef90000-7efa3000	Deferred        libresolv.so.2
ELF	7efa3000-7efbb000	Deferred        libnsl.so.1
ELF	7efc8000-7efd2000	Deferred        libnss_nis.so.2
ELF	7efd2000-7efdb000	Deferred        libnss_compat.so.2
ELF	7efdb000-7f000000	Deferred        libm.so.6
ELF	f7c85000-f7c89000	Deferred        libdl.so.2
ELF	f7c89000-f7dd8000	Deferred        libc.so.6
ELF	f7dd9000-f7df1000	Deferred        libpthread.so.0
ELF	f7df1000-f7f27000	Deferred        libwine.so.1
ELF	f7f29000-f7f48000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3mp.exe
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	0000000e    0
	0000000d    0
0000000f 
	00000012    0
	00000011    0
	00000010    0
00000015 
	00000017    0
	00000016    0
Backtrace:
=>1 0x7d7df8ce in libglcore.so.1 (+0x2108ce) (0xffffffff)

```

that is very different from the one I get in SP (i think)

---

### Post by piratesmack on 2008-05-08
> **thefishki345 said:**
> Wouldnt the checkinstall thing work fine?
I am not sure, but if its compiled with a patch it should still work, are you making this for wine 9.60 + or before? if your making it for like wine 9.50 or wine 9.57 or in between I will happily try it out for you.

I heard checkinstall isn't the best way to do it if you plan on distributing the package. but here's a package I made for Wine 0.9.57 with the 3dmark patch for 32bit:
[http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html](http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html)

---

### Post by piratesmack on 2008-05-08
> **thefishki345 said:**
> Just finished cod4 singleplayer, F***ing awesome! except the ending was pretty sad and a bit stupid and im confused about it, I mean WTF happened? lol
anyway,
ahalasam, if you do get a spare moment, could you please make a package thing like you did for .60 on 64 bit for .50 or up to .57 but no later (with the older patch) whichever one you think might work best and post it here, if you get time, cos it will give me something to work with it works or if it doesnt. Thanks!

edit: yes I have tried compiling it but it didnt work very well.

edit2:
here is the code I get when I try and run Mp in command line:
```
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f8fc,0x00000000), stub!
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xd5b0c78) : pBox=(nil) stub
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 423
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2673
wine client error:1f: write: Bad file descriptor
josh@Mackenzie:~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$ cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare/
josh@Mackenzie:~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$ wine iw3mp.exe
wine: Unhandled page fault on read access to 0x0000015c at address 0x7d7df8ce (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0000015c in 32-bit code (0x7d7df8ce).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d7df8ce ESP:0032ef6c EBP:ffffffff EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7d4c2000 ECX:7c0bc978 EDX:00000000
 ESI:7c0bc978 EDI:7c0bc978
Stack dump:
0x0032ef6c:  7d4c2000 7e1b4008 7d4d7840 0001ffff
0x0032ef7c:  7c0dadc0 00dd5190 01000000 00000000
0x0032ef8c:  00000000 7c07c488 7c0dada8 00000001
0x0032ef9c:  f7cf1994 000d9ef8 00000001 f7dd3ff4
0x0032efac:  0032f167 0032efd4 f7cf2c0d 0032eff8
0x0032efbc:  0032f128 0032f167 0032f118 f7dd3ff4
Backtrace:
=>1 0x7d7df8ce in libglcore.so.1 (+0x2108ce) (0xffffffff)
0x7d7df8ce: movl	0x15c(%eax),%eax
Modules:
Module	Address			Debug info	Name (91 modules)
PE	  400000- d935000	Deferred        iw3mp
PE	18000000-18033000	Deferred        binkw32
PE	21100000-21197000	Deferred        mss32
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d5cf000-7e0e4000	Export          libglcore.so.1
ELF	7e0e4000-7e188000	Deferred        libgl.so.1
ELF	7e207000-7e239000	Deferred        uxtheme<elf>
  \-PE	7e210000-7e239000	\               uxtheme
ELF	7e239000-7e24d000	Deferred        midimap<elf>
  \-PE	7e240000-7e24d000	\               midimap
ELF	7e24d000-7e273000	Deferred        msacm32<elf>
  \-PE	7e250000-7e273000	\               msacm32
ELF	7e273000-7e28a000	Deferred        msacm32<elf>
  \-PE	7e280000-7e28a000	\               msacm32
ELF	7e28a000-7e2c5000	Deferred        wineoss<elf>
  \-PE	7e290000-7e2c5000	\               wineoss
ELF	7e2ea000-7e2ef000	Deferred        libxfixes.so.3
ELF	7e2f9000-7e2fb000	Deferred        libnvidia-tls.so.1
ELF	7e2fd000-7e306000	Deferred        libxcursor.so.1
ELF	7e306000-7e309000	Deferred        libxcomposite.so.1
ELF	7e309000-7e30f000	Deferred        libxrandr.so.2
ELF	7e30f000-7e317000	Deferred        libxrender.so.1
ELF	7e317000-7e31a000	Deferred        libxinerama.so.1
ELF	7e31a000-7e338000	Deferred        imm32<elf>
  \-PE	7e320000-7e338000	\               imm32
ELF	7e338000-7e33d000	Deferred        libxdmcp.so.6
ELF	7e33d000-7e355000	Deferred        libxcb.so.1
ELF	7e355000-7e43c000	Deferred        libx11.so.6
ELF	7e43c000-7e44a000	Deferred        libxext.so.6
ELF	7e44a000-7e44f000	Deferred        libxxf86vm.so.1
ELF	7e44f000-7e4e5000	Deferred        winex11<elf>
  \-PE	7e460000-7e4e5000	\               winex11
ELF	7e505000-7e526000	Deferred        libexpat.so.1
ELF	7e526000-7e550000	Deferred        libfontconfig.so.1
ELF	7e550000-7e565000	Deferred        libz.so.1
ELF	7e565000-7e567000	Deferred        libxcb-xlib.so.0
ELF	7e57c000-7e5ec000	Deferred        libfreetype.so.6
ELF	7e5ec000-7e642000	Deferred        ddraw<elf>
  \-PE	7e5f0000-7e642000	\               ddraw
ELF	7e642000-7e701000	Deferred        comctl32<elf>
  \-PE	7e650000-7e701000	\               comctl32
ELF	7e701000-7e75a000	Deferred        shlwapi<elf>
  \-PE	7e710000-7e75a000	\               shlwapi
ELF	7e75a000-7e866000	Deferred        shell32<elf>
  \-PE	7e770000-7e866000	\               shell32
ELF	7e866000-7e8c7000	Deferred        rpcrt4<elf>
  \-PE	7e870000-7e8c7000	\               rpcrt4
ELF	7e8c7000-7e96b000	Deferred        ole32<elf>
  \-PE	7e8e0000-7e96b000	\               ole32
ELF	7e96b000-7e9b5000	Deferred        dsound<elf>
  \-PE	7e970000-7e9b5000	\               dsound
ELF	7e9b5000-7e9d4000	Deferred        d3dx8<elf>
  \-PE	7e9c0000-7e9d4000	\               d3dx8
ELF	7e9d4000-7e9f1000	Deferred        d3dx9_36<elf>
  \-PE	7e9e0000-7e9f1000	\               d3dx9_36
ELF	7e9f1000-7ea0a000	Deferred        d3dx9_34<elf>
  \-PE	7ea00000-7ea0a000	\               d3dx9_34
ELF	7ea0a000-7eb0c000	Deferred        wined3d<elf>
  \-PE	7ea20000-7eb0c000	\               wined3d
ELF	7eb0c000-7eb3c000	Deferred        d3d9<elf>
  \-PE	7eb10000-7eb3c000	\               d3d9
ELF	7eb3c000-7eb5a000	Deferred        iphlpapi<elf>
  \-PE	7eb40000-7eb5a000	\               iphlpapi
ELF	7eb5a000-7eb86000	Deferred        ws2_32<elf>
  \-PE	7eb60000-7eb86000	\               ws2_32
ELF	7eb86000-7eba0000	Deferred        wsock32<elf>
  \-PE	7eb90000-7eba0000	\               wsock32
ELF	7eba0000-7ebf2000	Deferred        advapi32<elf>
  \-PE	7ebb0000-7ebf2000	\               advapi32
ELF	7ebf2000-7ec8d000	Deferred        gdi32<elf>
  \-PE	7ec00000-7ec8d000	\               gdi32
ELF	7ec8d000-7edd3000	Deferred        user32<elf>
  \-PE	7ecb0000-7edd3000	\               user32
ELF	7edd3000-7ee61000	Deferred        winmm<elf>
  \-PE	7ede0000-7ee61000	\               winmm
ELF	7ef81000-7ef8c000	Deferred        libnss_files.so.2
ELF	7ef8d000-7ef90000	Deferred        libxau.so.6
ELF	7ef90000-7efa3000	Deferred        libresolv.so.2
ELF	7efa3000-7efbb000	Deferred        libnsl.so.1
ELF	7efc8000-7efd2000	Deferred        libnss_nis.so.2
ELF	7efd2000-7efdb000	Deferred        libnss_compat.so.2
ELF	7efdb000-7f000000	Deferred        libm.so.6
ELF	f7c85000-f7c89000	Deferred        libdl.so.2
ELF	f7c89000-f7dd8000	Deferred        libc.so.6
ELF	f7dd9000-f7df1000	Deferred        libpthread.so.0
ELF	f7df1000-f7f27000	Deferred        libwine.so.1
ELF	f7f29000-f7f48000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3mp.exe
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	0000000e    0
	0000000d    0
0000000f 
	00000012    0
	00000011    0
	00000010    0
00000015 
	00000017    0
	00000016    0
Backtrace:
=>1 0x7d7df8ce in libglcore.so.1 (+0x2108ce) (0xffffffff)

```

that is very different from the one I get in SP (i think)


Did you cry on the level, **Aftermath**?
I did... shhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh

[http://www.youtube.com/watch?v=OSCVtvxXeLI](http://www.youtube.com/watch?v=OSCVtvxXeLI)

---

### Post by thefishki345 on 2008-05-09
I sort of did, I got pretty sad and upset lol.
so does ne one have ne suggestions?

---

### Post by ahaslam on 2008-05-09
Can you borrow a soundcard from someone?

Building a .deb for you would be no problem, booting Ubuntu to do it is though (for the next week, at least) & I'm unsure of its worth. 

Try compiling again & PM me with any issues.

---

### Post by thefishki345 on 2008-05-10
Okay, will do.
and ahalasam, how come your on ubuntu forums if you run arch?

I might be able to borrow a soundcard aswell.

---

### Post by thefishki345 on 2008-05-10
umm, ahalasam could you please make a guide for compiling wine 9.50 for 64 bit with 3dmark patch because I tried your old one (p2) and it didnt work, please make a guide as easy to follow as your one for 9.60

---

### Post by ahaslam on 2008-05-10
```
sudo apt-get build-dep wine
mkdir wine && cd wine
wget http://easynews.dl.sourceforge.net/sourceforge/wine/wine-0.9.50.tar.bz2
tar -xvjf wine-0.9.50.tar.bz2 && cd wine-0.9.50
wget http://bugs.winehq.org/attachment.cgi?id=8548
cp attachment.cgi\?id\=8548 wine-0.9.50/3dmark.diff && cd wine-0.9.50
patch -p1 < 3dmark.diff
mkdir -p `pwd`/lib32
ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so
ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so
ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so
ln -s /usr/lib32/libfontconfig.so.1 `pwd`/lib32/libfontconfig.so
ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so
ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so
ln -s /usr/lib32/libXrender.so.1 `pwd`/lib32/libXrender.so
ln -s /usr/lib32/libXinerama.so.1 `pwd`/lib32/libXinerama.so
ln -s /usr/lib32/libXxf86vm.so.1 `pwd`/lib32/libXxf86vm.so
ln -s /usr/lib32/libXi.so.6 `pwd`/lib32/libXi.so
ln -s /usr/lib32/libXrandr.so.2 `pwd`/lib32/libXrandr.so
ln -s /usr/lib32/liblcms.so.1 `pwd`/lib32/liblcms.so
ln -s /usr/lib32/libpng12.so.0 `pwd`/lib32/libpng.so
ln -s /usr/lib32/libcrypto.so.0.9.8 `pwd`/lib32/libcrypto.so
ln -s /usr/lib32/libssl.so.0.9.8 `pwd`/lib32/libssl.so
ln -s /usr/lib32/libxml2.so.2 `pwd`/lib32/libxml2.so
ln -s /usr/lib32/libjpeg.so.62 `pwd`/lib32/libjpeg.so
ln -s /usr/lib32/libXcomposite.so.1 `pwd`/lib32/libXcomposite.so
ln -s /usr/lib32/libcups.so.2 `pwd`/lib32/libcups.so
ln -s /usr/lib32/libXcursor.so.1 `pwd`/lib32/libXcursor.so
ln -s /usr/lib32/libdbus-1.so.3 `pwd`/lib32/libdbus-1.so
ln -s /usr/lib32/libhal.so.1 `pwd`/lib32/libhal.so
ln -s /usr/lib32/libsane.so.1 `pwd`/lib32/libsane.so
ln -s /usr/lib32/libgphoto2.so.2 `pwd`/lib32/libgphoto2.so
ln -s /usr/lib32/libgphoto2_port.so.0 `pwd`/lib32/libgphoto2_port.so
ln -s /usr/lib32/libldap-2.4.so.2 `pwd`/lib32/libldap.so
ln -s /usr/lib32/libldap_r-2.4.so.2 `pwd`/lib32/libldap_r.so
ln -s /usr/lib32/liblber-2.4.so.2 `pwd`/lib32/liblber.so
ln -s /usr/lib32/libxslt.so.1 `pwd`/lib32/libxslt.so
ln -s /usr/lib32/libcapi20.so.3 `pwd`/lib32/libcapi20.so
ln -s /usr/lib32/libjack.so.0 `pwd`/lib32/libjack.so
ln -s /usr/lib32/libodbc.so.1 `pwd`/lib32/libodbc.so
CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure --prefix=/usr --sysconfdir=/etc --enable-opengl --with-x
make 
sudo make install
```
^ Should be what you need to do. I've not checked it, it's just my *.60 guide using *.50 & the original patch... Don't forget that you'll need the d3dx9_34.dll for this release:

```
mkdir dx9 && cd dx9
wget http://www.m3fe.com/files/d3dx9_34.zip
unzip d3dx9_34.zip
mv d3dx9_34.dll ~/.wine/drive_c/windows/system32/
```

> how come your on Ubuntu forums if you run arch?
Because I really liked the older releases & it's still a good place to be. You'll notice a lot of people here use something other than Ubuntu and still hang out, there's no harm in that. This thread wouldn't exist if I'd cut all ties with Ubuntu upon jumping ship. :p

P.S. 'ahalasam' :confused:  If you get into Nexuiz, you'll have to join [COLOR="Red"][NSB][/COLOR] :lolflag:

---

### Post by thefishki345 on 2008-05-10
yes, and I am bloody thankful for that man!
I will try your guide very soon (5 mins lol) and report back
thanks!

edit: LOL sorry, just realized that I have been calling you ahalasam, sorry ahaslam.

---

### Post by thefishki345 on 2008-05-10
damn!
compiled it and cod4 sp works fine, changed the things in winecfg to oss and even in sounds in preferences I changed everything to OSS, and MP still doesnt work!!!! :(

---

### Post by andrebrait on 2008-05-10
why the hell I'm the only one with f**** damn bugs?!
I'm not a noob
I'm doing everything just like it should be done

In Wine 1.0 RC1 I couldn't even get it running. Tried to go back to 0.9.60, but I still have the same old bugs. With 0.9.57, I can't run it too... I'm going mad!!

---

### Post by ahaslam on 2008-05-11
Maybe because you're after the latest & greatest :p

---

### Post by ahaslam on 2008-05-11
> **thefishki345 said:**
> damn!
compiled it and cod4 sp works fine, changed the things in winecfg to oss and even in sounds in preferences I changed everything to OSS, and MP still doesnt work!!!! :(

I may have asked before but does it work if you disable your sound device in the BIOS?

Looks like you're going to have to borrow a supported card or become a Nexuiz pro ;)

---

### Post by thefishki345 on 2008-05-11
lol, I will try disabling sound in bios, but whats cod4 without sound, I may be able to get an extra sound card, but it prolly wont be a good one, so the sound wont be very great :(

---

### Post by thefishki345 on 2008-05-12
tried disabling sound in bios, didnt work :(

might be able to borrow a soundcard, but does anyone have any tweaks or stuff?
or will wine 9.61 fix all this hopefully?

---

### Post by ahaslam on 2008-05-12
[There are a few ALSA options]("http://wiki.winehq.org/UsefulRegistryKeys"), but I doubt they'll help & I've never needed them (so take with a pinch of salt).

Will .61 do the honors? I dunno, but with a quad you aren't going to be wasting too much time finding out. :p

I can't find any info on your sound device other than it being 7.1 (tho I only spent 2 mins).... The fact that SP works fine but MP doesn't & supposedly (from many sources) due to the sound device, doesn't compute with me. Though trying a different audio device seems to be the only real option atm, I certainly wouldn't buy one though.

---

### Post by thefishki345 on 2008-05-12
yeah, neither would I, but my friend builds computers for the community and puts linux on them, so I might be able to borrow one off him, but even if I do, what do I do if it works?

and im looking into that alsa thing.
thanks

edit: I looked at that alsa page, went into regedit, but umm, I have no idea what im meant to do. :( sorry, i´m as you already know a complete linux noob.

---

### Post by ahaslam on 2008-05-13
It's the same as Windows regedit. Follow the tree, if a key doesn't exist create it & all values are strings. I know little of these ALSA settings tho, so take caution. 

I'm guessing you've not tried FBO rendering then? For the best performance/stability in most games I set sound to ALSA in winecfg & off screen rendering mode to FBO in regedit...

---

### Post by thefishki345 on 2008-05-13
thanks, 
Okay I tried the fbo rendering thing, still didnt work,
and I still have no idea what im meant to do with that alsa thing, but I will ask someone else who knows about this stuff hopefully today or tomorrow,
if anyone else, not just ahaslam has any other suggestions I will be happy to try them

---

### Post by thefishki345 on 2008-05-14
:( :( :( :( :( :( :( :( 
bump *sob* I wanna play multiplayer so bad!

this is for vista, but how could I do this or something like this in ubuntu 8.04?


If you are running realtek hd audio on your vista then all you have to do is go to your control panel. click hardware and sound. then sound. click the recording tab on your screen. then right click show disabled. then enable stereo mix.

Use Vista drivers for your sound instead of the device drivers

---

### Post by ahaslam on 2008-05-14
> **thefishki345 said:**
> :( :( :( :( :( :( :( :( 
bump *sob* I wanna play multiplayer so bad!

this is for vista, but how could I do this or something like this in ubuntu 8.04?


If you are running realtek hd audio on your vista then all you have to do is go to your control panel. click hardware and sound. then sound. click the recording tab on your screen. then right click show disabled. then enable stereo mix.

Use Vista drivers for your sound instead of the device drivers

You can do that in alsamixer.

---

### Post by thefishki345 on 2008-05-14
cool, thanks, im trying it now (downloading the gui from synaptic)

ok I got it, but what am I meant to do?
this just lets me alter the sound volume, please do you know what I am meant to do?
I feel like such a n00b.

---

### Post by ahaslam on 2008-05-14
> I feel like such a n00b.
:p

I don't know what GUI you're using & would suggest you just open a terminal & issue 'alsamixer'. You can (un)mute channels/devices & alter levels. 'man alsamixer' for more ;)

---

### Post by thefishki345 on 2008-05-15
thanks, I tried it, turned everything up full volume ( :p ) including  mics even though I dont have one. im getting pretty frustrated now, but I will try borrowing a soundcard.

---

### Post by thefishki345 on 2008-05-16
damn! it might be a long time before I can try another sound card, the guy who I thought would of had one doesn´t (yet) so please...anything else?

---

### Post by ahaslam on 2008-05-16
I can give you a game of Nex ;)

---

### Post by thefishki345 on 2008-05-17
:( lol, I actually downloaded nexuiz and everything, it looks like a cheap take of UT classic :p
but anyone!>??? incase you dont know my problem is:
I compiled wine 9.50 And 9.60 for amd 64 with 3dmark patch or ben P´s patch, it works fine, singleplayer runs flawlessly, but multiplayer just crashes on startip. I have tried:
reinstalling the game
changing the sound in winecfg to oss and vice versa
disabled sound in bios
changed mssmp3.asi to mssmp3.bak
but it still gives me the same crash! any ideas please, I really wanna play cod4 multiplayer before cod5 comes out :p

---

### Post by koocho on 2008-05-21
hi!

just installed a patched wine ([this one](http://oliverdeisenroth.de/index.php?option=com_remository&Itemid=85&func=fileinfo&id=20)) but i can't run cod4. here's what terminal shows when trying to start from there: 

```
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f8e4,0x00000000), stub!
err:d3d:CreateContext Requesting MultiSampleType=4
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 498
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 498
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 498
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 498
Killed 
```

i use a geforce 8600gt. any idea whats wrong? :confused:

koocho

---

### Post by ahaslam on 2008-05-21
I recommend that you follow one of my guides here. Let us know how you get on.

;)

---

### Post by koocho on 2008-05-21
i already tried [this]("http://ubuntuforums.org/showpost.php?p=4047498&postcount=13") guide written by you - but i had several problems...

after "make depend && make" terminal says:
```
signal_i386.o: In function `setup_exception':
/home/koocho/wine/wine-0.9.50/dlls/ntdll/signal_i386.c:940: undefined reference to `VALGRIND_MAKE_WRITABLE'
collect2: ld gab 1 als Ende-Status zurück
winegcc: gcc failed
make[2]: *** [ntdll.dll.so] Fehler 2
make[2]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/dlls/ntdll'
make[1]: *** [ntdll] Fehler 2
make[1]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/dlls'
make: *** [dlls] Fehler 2
koocho@koocho-desktop:~/wine/wine-0.9.50$ 
```

and when i try to compile it anyway, terminal says: 
```
make[1]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/tools'
make[1]: »makedep« ist bereits aktualisiert.
make[1]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/tools'
make[1]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/libs'
make[2]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/libs/port'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/libs/port'
make[2]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/libs/wine'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/libs/wine'
make[2]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/libs/wpp'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/libs/wpp'
make[1]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/libs'
make[1]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/tools'
make[2]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/widl'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/widl'
make[2]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/winebuild'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/winebuild'
make[2]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/winedump'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/winedump'
make[2]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/winegcc'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/winegcc'
make[2]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/wmc'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/wmc'
make[2]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/wrc'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/tools/wrc'
make[1]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/tools'
make[1]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/include'
make[1]: Für das Ziel »all« ist nichts zu tun.
make[1]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/include'
make[1]: Betrete Verzeichnis '/home/koocho/wine/wine-0.9.50/include'
../tools/mkinstalldirs -m 755 /usr/include/wine/windows/ddk
mkdir /usr/include/wine
chmod 755 /usr/include/wine
chmod: Beim Setzen der Zugriffsrechte für „/usr/include/wine“: No such file or directory
make[1]: *** [/usr/include/wine/windows/ddk] Fehler 1
make[1]: Verlasse Verzeichnis '/home/koocho/wine/wine-0.9.50/include'
make: *** [include/__install__] Fehler 2 
```

---

### Post by ahaslam on 2008-05-21
Sorry to be brief (busy):

What distro is this?
Have you previously had (a vanilla) Wine installed?
Are the dep's satisfied?
Have you tried 0.9.60?

---

### Post by koocho on 2008-05-21
distro is ubuntu 8.04 - don't know what wine was installed before i followed your guide but i completely uninstalled it. i tried it with several versions of wine - it's been a few days now so i can't say exactly which ones sry.. but i also used the newest wine and it didn't work. what do you mean with "are the dep's satisfied"? 

sry for my bad english, trying to improve ;)

---

### Post by ahaslam on 2008-05-21
I honestly can't see what's wrong if you're on Hardy & followed the guide here. I hope someone else can help, I'm a little stretched atm & can't see anything obvious.

---

### Post by thefishki345 on 2008-05-22
I had this error, it means that wine wasnt compiled properly, you need to download some stuff (check back on the previous pages of the thread when I was having trouble)
hope that helps!

and sadly, I STILL cant get cod4 Multiplayer working, so any suggestions would be grateful.

---

### Post by thefishki345 on 2008-05-24
bumpy bump, I am kinda giving up on this sadly, which I am pretty p1ssed off at, I hope I will get it working, so if anyone has found any other solutions to cod4 multiplayer crashing at startup it would be really appreciated (stupid onboard realtek soundcard)

---

### Post by ahaslam on 2008-05-25
I wouldn't bash Realtek too much. Mine works, tho with a different chipset. & remember there's no concrete proof that's it. I would try on a different distro to confirm some system stuff isn't fubar, tho I know it's not an option for you.

Sorry to have come to a dead end :(

---

### Post by thefishki345 on 2008-05-26
Its okay, I am just sad :(

would enabling something called ¨full duplex audio¨ help? and does realtek have linux drivers?

---

### Post by piratesmack on 2008-05-26
update:
The graphical glitches are fixed in Wine 1.0 RC2 :)

However, I'm having trouble getting multiplayer working in 1.0 RC2 :(

So I guess I'll continue to use 0.9.60 :mad:

---

### Post by ahaslam on 2008-05-27
Thanks for the update.

What glitches were these? The problems with the mentioned effects? 

Does it still need patching?

Still on 0.9.50 here =)

PS. If you could resolve your MP prob, it may well help thefishki345.

---

### Post by piratesmack on 2008-05-27
> **ahaslam said:**
> Thanks for the update.

What glitches were these? The problems with the mentioned effects? 

Does it still need patching?

Still on 0.9.50 here =)

PS. If you could resolve your MP prob, it may well help thefishki345.

In Wine 0.9.61 through version 1.0 RC1, the game looks like this when you don't enable anti-aliasing (anti-aliasing makes the game run a bit slow for me):
[http://ubuntuforums.org/attachment.php?attachmentid=68706&d=1209874518](http://ubuntuforums.org/attachment.php?attachmentid=68706&d=1209874518)


I'm pretty sure you still need the patch, but I didn't try without it.


I managed to get multiplayer to start by switching the sound driver to OSS and enabling "sound driver emulation," but it'd still crash at startup like 19 out of 20 times.  Maybe I'll make a bug report, they're in code freeze and got to my last bug report pretty fast. I'll keep you guys updated


Edit:
btw, Wine 1.0 is looking awesome so far

---

### Post by ahaslam on 2008-05-27
& does AA actually work when enabled? That would be a 1st for Wine. I'd assume that if the patch applied it was required.

So there's a specific option for thefishki345 to try which I overlooked (damn regulars eh, alway missing the small things). ;)

---

### Post by Vrekk on 2008-05-27
Hey i am having the same error as the guy who started this, but i am trying to run it on Crossover? Any ideas? Also, i got it off of steam, not cd if that makes a differnece

---

### Post by piratesmack on 2008-05-27
> **Vrekk said:**
> Hey i am having the same error as the guy who started this, but i am trying to run it on Crossover? Any ideas? Also, i got it off of steam, not cd if that makes a differnece

I don't think it works with crossover, you have to patch and compile wine

---

### Post by piratesmack on 2008-05-28
I installed the new Linux Mint 5 Beta 048 today (nice distro btw), so I decided to try COD4 in Wine 1.0 RC 2 again.

It's weird, if I install the game and play single player first, multiplayer won't work. And if I install the game and play multiplayer first, single player won't work. But I did get both working. I'm not sure if this will help thefishki345, but it's worth a try. 

All I did was start multiplayer, let it freeze, then press ALT+F4 until it asked me to force quit. Then I started it up again, it gave me this message:
> 
It appears COD4 didn't quit properly the last time it was run, do you want to run the game in safe mode?


I chose "yes" and multiplayer started working.

I also updated all the way to 1.5 (update 1.5 is just a multiplayer patch, so the 1.4 no-dvd crack works fine with it)

Here's some screenshots:
[http://www.vulomedia.com/images/3912singleplayer.png](http://www.vulomedia.com/images/3912singleplayer.png)

[http://www.vulomedia.com/images/6396multiplayer.png](http://www.vulomedia.com/images/6396multiplayer.png)

---

### Post by thefishki345 on 2008-05-30
Hey guys, just got back from holidays, thanks for all your input helping me. The safe mode thing doesnt work, but I havent perivered with it ( configuring options) I may try rc2 or something later, maybe I will see what rc3 brings :p

---

### Post by piratesmack on 2008-05-30
> **thefishki345 said:**
> Hey guys, just got back from holidays, thanks for all your input helping me. The safe mode thing doesnt work, but I havent perivered with it ( configuring options) I may try rc2 or something later, maybe I will see what rc3 brings :p

Just tried 1.0 RC 3 today

COD4 is running great, I didn't even have to start multiplayer in safe mode. There even seems to be a bit of a performance increase, does anyone know how I can check FPS?

---

### Post by thefishki345 on 2008-05-30
cool, but did you have to patch it to run cod4?

and what about 64 bit people do you still need the extra dlls etc?

---

### Post by piratesmack on 2008-05-31
> **thefishki345 said:**
> cool, but did you have to patch it to run cod4?

and what about 64 bit people do you still need the extra dlls etc?

yeah still have to patch. 

I don't think you need any extra dlls anymore

---

### Post by koocho on 2008-05-31
hi!

i installed cod4 with wine 1rc3 too but when i wanted to start cod there was the error that some files were missing - in fact the whole files in the /zone/german (or /zone/english ;))! i copied the files from a windows installation and it works... any idea why the files haven't been installed? it's an original dvd...

---

### Post by thefishki345 on 2008-06-02
Sorry, I have no idea koocho, ahaslam propably does, and thanks piratesmack, I will try it with rc3 soon, but the thing is, I dont think its a wine problem, cos this is happening with people on windows 2.

---

### Post by thefishki345 on 2008-06-04
bump.

---

### Post by willtell on 2008-06-06
Sorry for the lack of knowledge, but I've been trying to get this to work for a while and keep hitting road blocks.  

  I updated wine to 1rc3 and read that it still needs to be patched.  Should I just use the old 0.9.59 patch or is there another that works better with 1rc3?  And, how do I install that correctly?  I keep messing up with the patch.  Thanks for you help!

---

### Post by thefishki345 on 2008-06-06
Hi willtell, if you are on 64 bit just use ahaslam´s guide a couple of pages back, because that is the new patch for wine 9.60 or above (benny p´s patch) but if you were already using that patch for 9.59 it should work. If you are not on 64 bit you can still follow ahaslams guide a couple of pages back (like page 12-18) you just dont need the extra symbolic links.

hope I helped, and if I didnt someone else will soon.

---

### Post by thefishki345 on 2008-06-08
bump

---

### Post by kayfes on 2008-06-11
I could us some help as I am running into a problem with checkinstall.  It doesn't finish and then when I try wineprefixcreate
that obviously doesn't work.

---

### Post by kayfes on 2008-06-11
steven@steven-desktop:~/wine-0.9.50$ sudo checkinstall
[sudo] password for steven: 

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@steven-desktop ]
1 -  Summary: [ one ]
2 -  Name:    [ wine ]
3 -  Version: [ 0.9.50 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ wine-0.9.50 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make[1]: Entering directory `/home/steven/wine-0.9.50/tools'
make[1]: `makedep' is up to date.
make[1]: Leaving directory `/home/steven/wine-0.9.50/tools'
make[1]: Entering directory `/home/steven/wine-0.9.50/libs'
make[2]: Entering directory `/home/steven/wine-0.9.50/libs/port'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/steven/wine-0.9.50/libs/port'
make[2]: Entering directory `/home/steven/wine-0.9.50/libs/wine'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/steven/wine-0.9.50/libs/wine'
make[2]: Entering directory `/home/steven/wine-0.9.50/libs/wpp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/steven/wine-0.9.50/libs/wpp'
make[1]: Leaving directory `/home/steven/wine-0.9.50/libs'
make[1]: Entering directory `/home/steven/wine-0.9.50/tools'
make[2]: Entering directory `/home/steven/wine-0.9.50/tools/widl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/steven/wine-0.9.50/tools/widl'
make[2]: Entering directory `/home/steven/wine-0.9.50/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/steven/wine-0.9.50/tools/winebuild'
make[2]: Entering directory `/home/steven/wine-0.9.50/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/steven/wine-0.9.50/tools/winedump'
make[2]: Entering directory `/home/steven/wine-0.9.50/tools/winegcc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/steven/wine-0.9.50/tools/winegcc'
make[2]: Entering directory `/home/steven/wine-0.9.50/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/steven/wine-0.9.50/tools/wmc'
make[2]: Entering directory `/home/steven/wine-0.9.50/tools/wrc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/steven/wine-0.9.50/tools/wrc'
make[1]: Leaving directory `/home/steven/wine-0.9.50/tools'
make[1]: Entering directory `/home/steven/wine-0.9.50/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/steven/wine-0.9.50/include'
make[1]: Entering directory `/home/steven/wine-0.9.50/include'
../tools/mkinstalldirs -m 755 /usr/local/include/wine/windows/ddk
mkdir /usr/local/include/wine
chmod 755 /usr/local/include/wine
chmod: changing permissions of `/usr/local/include/wine': No such file or directory
make[1]: *** [/usr/local/include/wine/windows/ddk] Error 1
make[1]: Leaving directory `/home/steven/wine-0.9.50/include'
make: *** [include/__install__] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by ahaslam on 2008-06-11
Were the previous stages completed without error?

If so, try 'sudo make install' before 'sudo checkinstall' 
If the first finishes without error but checkinstall fails, you'll have Wine installed, just not through APT.

---

### Post by thefishki345 on 2008-06-12
i had that error. I dno if it worked or not, but makeinstall worked I think...

---

### Post by willtell on 2008-06-12
I've run into problem after problem trying to get this to work, I think most of it is my ineptness.  So, I am trying to reinstall wine again and get the patch to work using [[COLOR="Blue"]this[/COLOR]]("http://wine-review.blogspot.com/2008/05/how-to-compile-wine-with-3dmark-patch.html") as a guide, following the guide I was actually able to patch wine (1.0 rc4) successfully but when I run make depend && make or just make depend, it says 

william@ubuntu:~/wine/wine-1.0-rc4$ make depend && make
make: *** No rule to make target `depend'.  Stop.

What am I doing wrong?

When I look in the Makefile.in there is a bit in there about depend, but not in the make.rules.in file that I can see; here's the line from the makefile
```
depend $(RECURSE_TARGETS): $(MAKEDEP)

$(MAKEDEP): include/config.h
	@cd $(TOOLSDIR)/tools && $(MAKE) makedep

```

---

### Post by blackvd on 2008-06-13
I installed it following all the directions posted around here. Problem I have is when trying to run it I get the following error:

```
fast file for zone 'code_post_gfx' is corrupt unreadable
```

Tried copying that file from the cd to the c: drive with no luck. Anyone else encountering this problem? Googled it and found a lot of other people to have but no solutions. Also I tried reinstalling a few times.

Thanks.

---

### Post by thefishki345 on 2008-06-14
@ willtell: Before we can help you are you running 64 bit or 32 bit? I got this error with 64 bit, I think it means wine wasnt compiled properly or something went wrong, try ahaslams guide/s a couple of pages back replacing wine 9.60 with rc 4. but in my opinion I think there might not be much point compiling with release candidates if wine is just on the doorstep (due pretty soon now).

@blackvd: same thing, we need to know what wine ver you are using and are you running 64 bit (your sig says otherwise, but always good to check :P) 
I have no idea what this error is, so maybe ask ahaslam.

I know this isnt very helpful but as I am still new to ubuntu and wine its the best I can do.

---

### Post by blackvd on 2008-06-14
I compiled wine from git with the patch for COD following the instructions I found on one the previous pages in this forum. So its the latest version wine 1.0-rc5. It doesnt seem to be a wine error though cause lots of other people are experiencing this problem in windows though I couldn't find a solution. Thought maybe someone on here might have had the same problem.

Thanks,
blackvd

---

### Post by thefishki345 on 2008-06-15
I tried to use wine git aswell and got that error, try using the wine source not wine git (and I think I linked to that guide and it didnt work for me...)

---

### Post by |{urse on 2008-06-18
Hullo,

I have this game running (fantastically) on my other box with an 8800gtx. I was hoping to put it on another machine with an x1600 pro (ati bleh). Install went reasonably well. on loading, i get this

> Backtrace:
=>1 0x7c032c77 (0x0033f454)
  2 0x7ead596f ActivateContext+0x3ff() in wined3d (0x0033f4c4)
  3 0x7eb073f8 drawPrimitive+0xd8() in wined3d (0x0033f7e4)
  4 0x7eae176d in wined3d (+0x2176d) (0x0033f854)
  5 0x7ebb33ee in d3d9 (+0x133ee) (0x0033f884)
  6 0x00602691 in iw3sp (+0x202691) (0x00000000)
err:ntdll:RtlpWaitForCriticalSection section 0x7ebcb7dc "d3d9_main.c: d3d9_cs" wait timed out in thread 0013, blocked by 0009, retrying (60 sec)


Looks as if the device won't play with dx9 on linux well.. Any ideas?

---

### Post by thefishki345 on 2008-06-19
well, there doesnt seem to be much sucess with ati cards under wine, and they dont really have good graphics drivers for linux anyway apparently. I am not sure about this sorry, but could you tell us what wine ver you are using (soon to be pointless cos wine 1.0 is released) and are you running 64 bit etc etc

and ahaslam could you please post a guide for 64 bit users (and 32 bit users possibly) on how to compile wine 1.0 from source for cod4 on ubuntu 8.04

---

### Post by kayfes on 2008-06-20
I really need some help with installing COD4 with wine.  I got through the make depend && make command the first time I tried the guide on this thread but I didn't really understand or maybe still don't understand how to use checkinstall.  But now thats not the problem.  I have 2 Hard Drives one for my main Ubuntu and one smaller driver to fiddle around with games.  When I want to figure out how to get a game to work I reformat and reinstall ubuntu, update and then install my graphic card drivers.  I have an Nvidia 9600gt and am using the latest driver for it: NVIDIA-Linux-x86-173.14.09.  Everything works fine compiz all that.  When I try to go through the guide when I get to the make depend && make it has been freezing or at least the last two times I tried it has.  Then when I start back over with reformatting it doesn't work.  I am wondering if anyone could explain or maybe show me a revised edition of the guide that would all me to install wine and COD4 with the latest version of wine and the patch needed.  I am fairly new to wine and understand a little bit of how to it but I tried doing it myself and it didn't work.  Any help would be great and thank you a lot in advance.

In the mean time I am going to try and do this:

Reformat and Reinstall Ubuntu
Update ubuntu
Follow guide up to installing COD4 
Install graphics drivers
Install COD4 

And see if that help me out because I think my graphics drivers are interfering with the installation of wine and patching of wine somehow.  Just an uneducated guess but whatever maybe it will work :P

---

### Post by kayfes on 2008-06-20
Update

That didn't work it froze again.  I have no idea what could be causing it to do that.  I ran the ram test to see if my memory was corrupt but I passed that.  I am going to run the memory test again when I go to bed and let it run for an extended period of time just to be sure.  So for now I know my problem isn't the latest version of the Nvidia driver.

---

### Post by thefishki345 on 2008-06-20
like I said, I am not really sure. try installing and running envy graphics driver installation, maybe that will fix some of your graphics problems, other than that I am not really sure sorry.

---

### Post by kayfes on 2008-06-21
to be honest I think I have to have the lates version(s) of the driver for it to work properly.

But yeah I have given up on COD4 for a while.  It needs more support in the meantime I guess I will just try getting WoW to work.

---

### Post by thefishki345 on 2008-06-22
Fair enough, but ahaslam has just came back from his break, and he will probably post up and have a solution so keep your eye out on this thread...

---

### Post by jazz452 on 2008-06-22
> **thefishki345 said:**
> Fair enough, but ahaslam has just came back from his break, and he will probably post up and have a solution so keep your eye out on this thread...

I will tell him to reply or go to nexuiz game log into (pk server) and tell him yourself. Its better than cod 4 (but free).

---

### Post by ahaslam on 2008-06-22
> **kayfes said:**
> Update

That didn't work it froze again.  I have no idea what could be causing it to do that.  I ran the ram test to see if my memory was corrupt but I passed that.  I am going to run the memory test again when I go to bed and let it run for an extended period of time just to be sure.  So for now I know my problem isn't the latest version of the Nvidia driver.

Freezing during the make shows a hardware fault imo. It passed memtest but that means very little. I'd run mprime in torture mode over each core. Something serious enough to cause this fault will be revealed within the 1st hour.     

My guess is either insufficient cpu cooling/current.

---

### Post by ahaslam on 2008-06-22
> **jazz452 said:**
> I will tell him to reply or go to nexuiz game log into (pk server) and tell him yourself. Its better than cod 4 (but free).

I consider myself told, hi Jazz ;)

My 64bit 0.9.60 build is here:
[http://rapidshare.com/files/111274293/wine_0.9.60-1_amd64.deb.html](http://rapidshare.com/files/111274293/wine_0.9.60-1_amd64.deb.html)
md5: 6a396c5066fae5e172f65f0fdbc9c250

Looking at the wine appdb, it should be the same procedure to build 1.0 as my 0.9.60 guide on page 11.

thefishki345, It was also written that oss helps some to play mp. I'm sure you tried it already, can't hurt to try again but with new version. 

;)

---

### Post by thefishki345 on 2008-06-22
I tried that like you said, but I am gonna try compiling wine 1.0 with the patch tonigh, but if that doesnt work I will just wait for you to make s guide.

---

### Post by thefishki345 on 2008-06-22
Okay, here is my guide for compiling wine 1.0 with 3dmark patch to make call of duty 4 modern warfare run under wine for 64 bit (and 32 bit you just dont need the extra libs)

PLEASE NOTE: I DID NOT COME UP WITH THIS this is just a rip of ahaslams guide for wine 9.60 for 64 bit, just with a change in the wine version

ENTER THIS INTO A TERMINAL ONE PARAGRAPH AT A TIME (applications-accessories-terminal)

Lets get started:


```
sudo apt-get build-dep wine
```

Get the wine source and the patch:

```
mkdir wine && cd wine
get http://easynews.dl.sourceforge.net/sourceforge/wine/wine-1.0.tar.bz2
tar -xvjf wine-1.0.tar.bz2 && cd wine-1.0

wget http://www.bennyp.org/wine/wine-0.9.59-3dmark.patch

```
Patch wine:

```
patch -p1 < wine-0.9.59-3dmark.patch
```

Get the extra libs: (64 bit users only, and I am not sure if you still need these)

```
mkdir -p `pwd`/lib32
ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so
ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so
ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so
ln -s /usr/lib32/libfontconfig.so.1 `pwd`/lib32/libfontconfig.so
ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so
ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so
ln -s /usr/lib32/libXrender.so.1 `pwd`/lib32/libXrender.so
ln -s /usr/lib32/libXinerama.so.1 `pwd`/lib32/libXinerama.so
ln -s /usr/lib32/libXxf86vm.so.1 `pwd`/lib32/libXxf86vm.so
ln -s /usr/lib32/libXi.so.6 `pwd`/lib32/libXi.so
ln -s /usr/lib32/libXrandr.so.2 `pwd`/lib32/libXrandr.so
ln -s /usr/lib32/liblcms.so.1 `pwd`/lib32/liblcms.so
ln -s /usr/lib32/libpng12.so.0 `pwd`/lib32/libpng.so
ln -s /usr/lib32/libcrypto.so.0.9.8 `pwd`/lib32/libcrypto.so
ln -s /usr/lib32/libssl.so.0.9.8 `pwd`/lib32/libssl.so
ln -s /usr/lib32/libxml2.so.2 `pwd`/lib32/libxml2.so
ln -s /usr/lib32/libjpeg.so.62 `pwd`/lib32/libjpeg.so
ln -s /usr/lib32/libXcomposite.so.1 `pwd`/lib32/libXcomposite.so
ln -s /usr/lib32/libcups.so.2 `pwd`/lib32/libcups.so
ln -s /usr/lib32/libXcursor.so.1 `pwd`/lib32/libXcursor.so
ln -s /usr/lib32/libdbus-1.so.3 `pwd`/lib32/libdbus-1.so
ln -s /usr/lib32/libhal.so.1 `pwd`/lib32/libhal.so
ln -s /usr/lib32/libsane.so.1 `pwd`/lib32/libsane.so
ln -s /usr/lib32/libgphoto2.so.2 `pwd`/lib32/libgphoto2.so
ln -s /usr/lib32/libgphoto2_port.so.0 `pwd`/lib32/libgphoto2_port.so
ln -s /usr/lib32/libldap-2.4.so.2 `pwd`/lib32/libldap.so
ln -s /usr/lib32/libldap_r-2.4.so.2 `pwd`/lib32/libldap_r.so
ln -s /usr/lib32/liblber-2.4.so.2 `pwd`/lib32/liblber.so
ln -s /usr/lib32/libxslt.so.1 `pwd`/lib32/libxslt.so
ln -s /usr/lib32/libcapi20.so.3 `pwd`/lib32/libcapi20.so
ln -s /usr/lib32/libjack.so.0 `pwd`/lib32/libjack.so
ln -s /usr/lib32/libodbc.so.1 `pwd`/lib32/libodbc.so
```

Compile wine:

For 64 bit users:

```
CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure --prefix=/usr --sysconfdir=/etc --enable-opengl --with-x 
```

For 32 bit users:
```

./configure --prefix=/usr --sysconfdir=/etc --enable-opengl --with-x
```

and then for everyone:

```

make

sudo make install:
```

```
winecfg
```

(this will launch the config panel, and make the hidden .wine directory)

ENJOY!

after that, insert the cod4 cd, run the setup exe in the cd and enjoy! :popcorn::)


if you get an error saying invalid cd, use a no cd patch from [www.gameburnworld.com](www.gameburnworld.com) or elswhere (google it)

There are some settings which make the game unplayable which you need to turn off:

Anti-aliasing - Doesn't work.
Sync Every Frame
Shadows
Specular Map
Depth of Field
Glow (I have it on though)
Number of Dynamic Lights
Soften Smoke Edges - Unplayable with this option enabled.




Also, if you have trouble running multiplayer,

change the audio in winecfg to OSS or put in a mic. It didnt work for me but worked for others...


:popcorn::):KS

---

### Post by kayfes on 2008-06-23
Thank you for that guide.  Will give it a try tonight and let you know.  Thank you.

---

### Post by kayfes on 2008-06-23
> **ahaslam said:**
> Freezing during the make shows a hardware fault imo. It passed memtest but that means very little. I'd run mprime in torture mode over each core. Something serious enough to cause this fault will be revealed within the 1st hour.     

My guess is either insufficient cpu cooling/current.

I ran memtest for a day strait without a single error.  If it does freeze again after trying to the guide for 1.0 then I am going just buy some new ram I want to upgrade to 4 gigs anyhow and that means replacing the 4 512mb sticks.  I don't think its a cooling problem as I have the heat sink properly mounted using artic silver 5 and another fan that I jerry rigged inside of my computer to blow on the cpu also.  I plan on changing my mobo in the near future also to an sli compatible board so worst case scenario is that I just get the hardware faster than I planned :)

---

### Post by kayfes on 2008-06-23
Solved for me at least.  Followed the new guide still froze.  Opened up the puter took out factory installed ram and what do you know it stopped freezing.  Thank you for the guide and GAME ON!

---

### Post by thefishki345 on 2008-06-23
Your welcome, hope you enjoy the game.

---

### Post by thefishki345 on 2008-06-25
Just bumping this for people who need help with cod4

---

### Post by shivans on 2008-06-26
> **blackvd said:**
> I installed it following all the directions posted around here. Problem I have is when trying to run it I get the following error:

```
fast file for zone 'code_post_gfx' is corrupt unreadable
```

Tried copying that file from the cd to the c: drive with no luck. Anyone else encountering this problem? Googled it and found a lot of other people to have but no solutions. Also I tried reinstalling a few times.

Thanks.


I have exactly the same problem and can't find a fix. Does anyone else have any ideas? I know my CD isn't corrupt as it works within Vista.

---

### Post by thefishki345 on 2008-06-26
Sorry, I have no idea what this means, but have you tried a no cd patch?

---

### Post by shivans on 2008-06-27
Yeah, I've tried the game without patching to 1.4 (+nocd patch) and after patching (with the 1.4 nocd patch).

I get the same "fast file for zone 'code_post_gfx' is corrupt unreadable" error regardless of game version.

---

### Post by thefishki345 on 2008-06-27
Okay, well then I have no idea, except maybe, where did you get the patch from???

---

### Post by ahaslam on 2008-06-27
Your guide looks fine. I'd just point out that 32bit users wont need:
```
CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32"
```
Just 
```
./configure --prefix=/usr --sysconfdir=/etc --enable-opengl --with-x
```
As normal.

Nice to see you helping out. I'm looking @ other stuff right now, you know where I am tho.

;)

PS. shivans, try without any fixed exe, secureROM is reported to work for some. ;)

---

### Post by thefishki345 on 2008-06-27
ok ill edit that in my guide, thanks ahaslam.

---

### Post by piratesmack on 2008-06-28
update:
Wine 1.1.0 was released today

But the 3dmark patch fails to apply


I'm not sure if this was a good idea or not, but I got the patch to apply correctly by copying and replacing Wine 1.0's directx.c (located in /wine-1.0/dlls/wined3d/directx.c) over Wine 1.10's directx.c
compiling now and will tell you if the game works

---

### Post by shivans on 2008-06-28
I got CoD4 working. I had to copy an installed version from my windows partition, but at least I'm up and running now.

---

### Post by piratesmack on 2008-06-28
> **piratesmack said:**
> update:
Wine 1.1.0 was released today

But the 3dmark patch fails to apply


I'm not sure if this was a good idea or not, but I got the patch to apply correctly by copying and replacing Wine 1.0's directx.c (located in /wine-1.0/dlls/wined3d/directx.c) over Wine 1.10's directx.c
compiling now and will tell you if the game works

Just finished compiling and installing the game, everything seems to be working great.

Made a patched debian package for 32bit users:
[http://files.filefront.com/wine+110+i386deb/;10843454;/fileinfo.html](http://files.filefront.com/wine+110+i386deb/;10843454;/fileinfo.html)

I may make a 64bit one later

---

### Post by thefishki345 on 2008-06-28
wait piratesmack...you said that wine 1.10 doesn´t work with 3dmark, then you went and posted a deb of it with 1.10...that doesnt make sense...
and congrats shivans!

---

### Post by thefishki345 on 2008-06-28
wait piratesmack...you said that wine 1.10 doesn´t work with 3dmark, then you went and posted a deb of it with 1.10...that doesnt make sense...
and congrats shivans!

---

### Post by piratesmack on 2008-06-29
> **thefishki345 said:**
> wait piratesmack...you said that wine 1.10 doesn´t work with 3dmark, then you went and posted a deb of it with 1.10...that doesnt make sense...
and congrats shivans!

yeah I said it doesn't work, but then I said I got the patch to apply by copying and replacing Wine 1.0's directx.c over Wine 1.1.0's
So it's basically Wine 1.1.0 without the changes they made to directx

Seems to have worked out pretty well, actually. I was pretty proud of myself when I came up with that idea =P

---

### Post by pegmag on 2008-06-29
Well I don't know, if changing the directx.c is a good idea, because obviousely they changed something.

Well I did this:
I looked in the 3dmark patch and searched for the lines causing problems. Then I searched for this Lines in the directx.c and replaced them manually, and deleted the lines in the patch file.
Then applied the patch and compiled.

(Sorry for my bad English.. I'm not a native Speaker)

---

### Post by piratesmack on 2008-06-29
> **pegmag said:**
> Well I don't know, if changing the directx.c is a good idea, because obviousely they changed something.

Well I did this:
I looked in the 3dmark patch and searched for the lines causing problems. Then I searched for this Lines in the directx.c and replaced them manually, and deleted the lines in the patch file.
Then applied the patch and compiled.

(Sorry for my bad English.. I'm not a native Speaker)

Thanks, I'll try that

Your English is pretty good for not being a native speaker :)

---

### Post by pegmag on 2008-06-29
Thanks
I just created a new patch.. works on my machine

---

### Post by piratesmack on 2008-06-29
> **pegmag said:**
> Thanks
I just created a new patch.. works on my machine

Awesome good job :)

I added a link to your patch in the AppDB:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429)

---

### Post by thefishki345 on 2008-06-29
cool, although I dont think I will be compiling wine  1.10 for a while since I just got wine 1.0 lol. are they going to be releasing a new wine ver every 2 weeks again?

---

### Post by piratesmack on 2008-06-30
> **thefishki345 said:**
> cool, although I dont think I will be compiling wine  1.10 for a while since I just got wine 1.0 lol. are they going to be releasing a new wine ver every 2 weeks again?

I think so

But Wine 1.0 is considered the first stable release, Wine 1.1.0 and later will be development releases up until Wine 2.0. I think I'll be sticking with 1.0 for quite a while, too

---

### Post by thefishki345 on 2008-06-30
yeah...hopefully by wine ver 100 they will have every window program runable in linux, but by then there will prolly be a cooler open source OS lol...

---

### Post by piratesmack on 2008-06-30
> **thefishki345 said:**
> yeah...hopefully by wine ver 100 they will have every window program runable in linux, but by then there will prolly be a cooler open source OS lol...

haha the world will already end by Wine 100

It took like 15 years just to get to 1.0, I can't imagine living to see even Wine 3.0 =P


For anyone who wants it, here is a 32bit deb for Wine 1.1.0 with pegmag's 3dmark patch. Seems to be working for me, let me know if it works for you. I'm pretty new to this debian package making thing

[http://files.filefront.com/wine+110+i386deb/;10865887;/fileinfo.html](http://files.filefront.com/wine+110+i386deb/;10865887;/fileinfo.html)

---

### Post by superppl on 2008-06-30
Thanks for the patch. :)

---

### Post by Sneaky07 on 2008-07-01
Hi Im sort of new to Ubuntu but I keep trying to get it to work but when I run the .exe I get this:

```
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !

```
I got that error A LOT!! (meaning it displayed it a lot)

```

err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl

```

Then it dumps a bunch of stuff... I looked around and asked some people but I just can't seem to get this working... I know it has to be a graphics issue but I can't seem to find the problem.  Also the Nvidia logo doesn't come up on startup which I believe means that the good drivers aren't installed (according to the tut).  Is there something wrong with Wine or is it really my graphics?

---

### Post by hofa on 2008-07-03
Im still having trouble with wine 0.9.50...

I followed the tutorial on page 2 (copy paste tutorial :) ) and I get an error when I run checkinstall

Anyone know how I could fix this?

```
========================= Installation results ===========================
make[1]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools'
make[1]: `makedep' is up to date.
make[1]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools'
make[1]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/libs'
make[2]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/libs/port'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/libs/port'
make[2]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/libs/wine'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/libs/wine'
make[2]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/libs/wpp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/libs/wpp'
make[1]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/libs'
make[1]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools'
make[2]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/widl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/widl'
make[2]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/winebuild'
make[2]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/winedump'
make[2]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/winegcc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/winegcc'
make[2]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/wmc'
make[2]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/wrc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools/wrc'
make[1]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/tools'
make[1]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/include'
make[1]: Entering directory `/home/hofa/Desktop/winesource/wine-0.9.50/include'
../tools/mkinstalldirs -m 755 /usr/include/wine/windows/ddk
mkdir /usr/include/wine
chmod 755 /usr/include/wine
chmod: changing permissions of `/usr/include/wine': No such file or directory
make[1]: *** [/usr/include/wine/windows/ddk] Error 1
make[1]: Leaving directory `/home/hofa/Desktop/winesource/wine-0.9.50/include'
make: *** [include/__install__] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```

---

### Post by zabzoo on 2008-07-03
> **pegmag said:**
> Thanks
I just created a new patch.. works on my machine

SEE EDIT BELOW:

Hi there

The file doesn't appear to download correctly, when I try to tar xvf the file i get the following error -

```

$ tar xvf wine-1.1.0-3dmark.patch.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors

```

EDIT:  
Noob here - soz; used gunzip!!!! :D

Am I doing something wrong?

---

### Post by thefishki345 on 2008-07-04
so zabzoo, does that mean your problem is sorted by your edit?

Hofa: try the command ¨makeinstall¨ instead of ¨checkinstall"and see if that works,

Sneaky: I think  it might be your graphics or that wine doesnt recognise your hardware or you havent compiled properly. Try reinstalling your graphics drivers with the program ¨envy¨
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

Hope that helps guys, but I am no expert on this.

---

### Post by thefishki345 on 2008-07-04
Hey guys, now I would like you to help me with a little problem I am having in cod4.
The problem is I get no background sound (the cool music) in the menus or in game, which makes the game kind of boring, I dont know how it stopped working because it used to work fine... any ideas?

EDIT: nevermind, its just when i  changed msmp3.asi to msmp3.bak I forgot to change it back...

---

### Post by jmr257 on 2008-07-05
Hello all

Could someone kindly tell me how to patch my version of Wine.
I have installed 1.1.0 and have the right patch for it (from this thread).
But what am I supposed to do then? I mean, what do I do with those.

I tried a bit of googling and I came to the answer that I have to download the source code and compile it??? Is that right or what do I have to do?

Thanks in advance

EDIT: thanks thefishki345, did as it said in guide and it works like charmed now :)

---

### Post by n3ga on 2008-07-05
hi all
i'm newbie and i cant compile wine 1.1.0 on ubuntu
this is the error 
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

i have just instlled build-essential and i don't know where is the problem
some one could help me please?

someone have tested cod4 1.7 with previous wine version? works ok?

---

### Post by thefishki345 on 2008-07-06
@ n3ga: sorry, I do not know why that is happening, but if it works on previous vers (wine 1.0)  then why bother changing it. But, if you want someone else to help, please post the exact command you put in which gave that output.

@jmr257: You have to actually compile it from the wines source code, not install plain wine and then  patch it. again, there have been problems with wine 1.10 and cod4 so I dont see why people want the latest version of wine so badly, I am still on wine 1.0 and is fine. What you have to do is in my guide (which is ripped from ahaslams) here on this page, halfway down:

[http://ubuntuforums.org/showthread.php?t=641987&page=24](http://ubuntuforums.org/showthread.php?t=641987&page=24)

hope that helps!

---

### Post by desertboy on 2008-07-06
I installed these deb's to play C&C 3 which needs a cursor patch but they have the 3dmark patch as well and work fine with COD4 I've been playing it most of the day, performance is below windows but still 20-30fps at 1680x1050.

[http://oliverdeisenroth.de/index.php?option=com_remository&Itemid=85&func=select&id=3](http://oliverdeisenroth.de/index.php?option=com_remository&Itemid=85&func=select&id=3)

he keeps them up to date, great for CNC3 and Kane's wrath as well.

---

### Post by TheCoach on 2008-07-08
-delete-

---

### Post by thefishki345 on 2008-07-11
-Why?-

and bump

---

### Post by superppl on 2008-07-25
Well, looks like it's broken again.

---

### Post by Bellegueulle damien on 2008-07-26
Hello ,

For information : 3Dmark patch not work with Wine 1.1.2

patching file dlls/wined3d/directx.c
Hunk #1 succeeded at 852 (offset 1 line).
Hunk #2 succeeded at 2981 (offset 9 lines).
Hunk #3 succeeded at 3250 (offset 9 lines).
Hunk #4 FAILED at 3268.

bye ,

---

### Post by cowboyup6983 on 2008-08-06
i got really far with no problems of the installation of COD4, the final part after i cut and past the no DVD patch, was to actually run the program.. 

i go to wine>programs>cod4

this is my error message i get, seems like i might not have the right directX installed. could someone please help with this

---

### Post by ahaslam on 2008-08-07
May I ask what gfx card you have & the driver you're using?

Nice wallpaper btw. ;)

---

### Post by cowboyup6983 on 2008-08-07
> **ahaslam said:**
> May I ask what gfx card you have & the driver you're using?

Nice wallpaper btw. ;)

thanks.. i have 2-xfx 8600 doing SLI i guess. i installed the drivers using ENVY. it says version 173.14.09 and im using wine version 1.1.2

in the library section of wine i have existing override of d3dx9_34 (natitve)

---

### Post by ahaslam on 2008-08-07
Ok, get rid of that dll, you don't need it with the newer versions of Wine.

;)

---

### Post by cowboyup6983 on 2008-08-07
> **ahaslam said:**
> Ok, get rid of that dll, you don't need it with the newer versions of Wine.

;)

same message! i just went into the libraries and removed the dll thing. how do i know if i have the proper directx patch or anything with directx to play games

here are all the screen shots of my wine configuration

---

### Post by ahaslam on 2008-08-07
You shouldn't have installed directx & there's no need for any MS dll's. What patch did you use? Should be: [http://ubuntuforums.org/showpost.php?p=5286516&postcount=255](http://ubuntuforums.org/showpost.php?p=5286516&postcount=255)

I'd be interested to see how it goes with only one gfx card installed as I've not heard of others with SLI. Failing that, follow my original guide on page 2 to the letter. That still works best for me, tho not had time to try 1.0 yet.

---

### Post by cowboyup6983 on 2008-08-07
> **ahaslam said:**
> You shouldn't have installed directx & there's no need for any MS dll's. What patch did you use? Should be: [http://ubuntuforums.org/showpost.php?p=5286516&postcount=255](http://ubuntuforums.org/showpost.php?p=5286516&postcount=255)

I'd be interested to see how it goes with only one gfx card installed as I've not heard of others with SLI. Failing that, follow my original guide on page 2 to the letter. That still works best for me, tho not had time to try 1.0 yet.

first of all i just want to say thanks for helping. how can i completely start over. i wanna play COD4 real bad on this system. 

please someone tell me what should i do, first uninstall COD4, and uninstall wine?? i want this to work and im willing to try any way.

---

### Post by ahaslam on 2008-08-08
Follow my guide on page 2 to start from scratch.

---

### Post by hofa on 2008-08-08
I got single player working, up until the point that I actually have to start playing, thank you very much for that (page 2 guide). Then I get 1fps if not worse...

I get a lot of this in terminal:

fixme:d3d:state_separateblend (WINED3DRS_SEPARATEALPHABLENDENABLE,1) not yet implemented



edit: I got it working after setting all graphics options to the lowest setting. :)
I still get a lot of the errormessage above and it's not running 100% smooth but it's still cool

---

### Post by ahaslam on 2008-08-08
Glad it works for you. ;)

Errors are to be expected, you can prevent debugging & gain 1 or 2 fps with "WINEDEBUG=-all". You can also gain a few more fps by over clocking your gfx card. If you proceed with overclocking, do so with caution. 

Here's an old launch script of mine: 

```
#! /bin/bash

nvidia-settings -a GPUOverclockingState=1 -a GPU3DClockFreqs=720,1080
cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare && WINEDEBUG=-all wine iw3sp.exe
nvidia-settings --load-config-only && nvidia-settings -a GPUOverclockingState=0
```

Don't just use that, read up & test first. Your settings may be different & xorg.conf will need editing.

Happy fragging ;)

---

### Post by hofa on 2008-08-08
Got it working in Wine 1.0 just now, same quality as the version 0.9.50
Just thought you'd be pleased to know :)

edit: It doesn't run as smoothly as 0.9.50, the boat level (first mission) is unplayable, got like 10 fps I think.
WINEDEBUG=-all really did some good things for the intro-level (shooting range etc.)
I'm really not gonna go and try overclocking, I'm using a laptop with GeForce go 7900gtx 512mb so 
#1: it's gonna get too warm in there because it's still a laptop
#2: My graphics card is good enough for playing on 800x600 =D

---

### Post by ahaslam on 2008-08-08
Ok, just keep gfx & res at a min with 0.9.50 & no debugging.

When writing the guide I had a 7950gt oc'd to the level of a 7900gtx & running smoothly @ 1440x900.

What are the other spec's of your laptop? My laptop can't even run a screensaver...

---

### Post by hofa on 2008-08-09
I've got a Dell XPS 1710

- Intel T7200 Core 2 Duo @ 2GHz
- 2Gb memory
- 600 MHz fsb I think
- geforce go 7900 gtx @ 512 mb

Maybe It'll run better if I turn off Compiz, or wouldn't it?

BTW It will only run when I turn off everything that uses sounds: MPD, thwirl... or else I get the Miles Sound Driver error.
Also: Multiplayer doesn't work :(


edit: Turning off compiz fusion did the trick, smooth gameplay now ^^
Now I still have to be able to run multiplayer, it's the only reason why I still use Windows in my spare time...


edit again: Multiplayer does work ^^
Still I'm gonna reboot to Windows for playing online. It's just nog the same :)

thanks for all your help!

---

### Post by Vadi on 2008-08-10
getdeb.net built .debs: [http://www.getdeb.net/search.php?keywords=wine](http://www.getdeb.net/search.php?keywords=wine)

---

### Post by telemetry9 on 2008-08-30
Actually - wine 1.0 works very well with the latest HD 4850.  Just add some entries into the registry by creating Direct 3D key and you will be amazed.

Actually - my HD 4850 plays half life 2 and shadow of chernobyl without a glitch and performance is impressive.  You are as likely to have as many problems with an Nvidia card.

---

### Post by rashwan on 2008-09-11
[CENTER][SIZE="4"]cowboyup6983 rather than patching and compiling here is a prepatched and precompiled version 1.1.0
[URL="http://www.archive.org/download/wine-1.1.0/wine_1.1.0_i386.deb"]http://www.archive.org/download/wine-1.1.0/wine_1.1.0_i386.deb

[/URL][/SIZE][/CENTER]

also i think the latest version does not need to be patched
cheers

---

### Post by Dabblo on 2008-10-30
Hi, I'm not sure if I'm posting this in the right place.. I been trying to install COD4 in wine with no luck.. I can get it installed, however I get this error when I try starting it up: Error during initialization:
Miles sound system initialization failed.
Make sure you have your sound card's latest drivers and DirectX installed. 

I have tried following various guides, and tried different versions of wine with 1.1.3 - 1.1.4 - 1.1.7 - 0.9.56 version including ones with 3DMark patch.. I've tried a guide with d3dxp_34.dll and streamci.dll + mscoree.dll.. And I even tried installing DirectX 9c With all the required native dlls. I have the iw3sp.exe I installed COD4 with Gmount IS0, And I even tried installing DirectX with wine doors.. No luck. I turned to help now it's telling me DirectX has an irrecoverable error.. Please someone help :confused:

System:
Pentium 4 @ 2.533 Ghz
Ram  768 Mb
Nvidia 7300 256 Mb (video)
Ubuntu hardy 8.04 upgraded from 7.10

---

### Post by ahaslam on 2008-10-30
Start a fresh, rm -r ~/.wine

Wine no longer needs patching or extra dll's & directx should not be installed.

If you have no luck, follow my original guide on page 2. A patched Wine 0.9.50 is still the best way of running COD4 on Linux.

---

### Post by hofa on 2008-10-30
I've had that error with some Windows games on Linux (CoD4, NFH2, ...)

It always works when I just shut down everything that can address your sound card. (Music player, Firefox, twhirl, pidgin, emesene... ). It's all ALSA's fault I think

---

### Post by dvergur on 2008-11-23
Thanks a lot ahaslam.
This easy to follow guide is unfortunately all too rare.
I am quite new to Linux and this guide was great and I think I even learned something about Linux in the process.
Best regards,
dvergur.

---

### Post by IOmega666 on 2008-11-24
well, i was trying the new wine, 1.1.9 , i compiled it, and then install cod4, patched it with the 1.6 version of the patch, run it with the command 

wine iw3sp.exe

and then, i got a black screen, but sound, and i can hear the mouse going over the options, and the sound when you are over the options. 

something i can do ? to have image ?

---

### Post by piratesmack on 2008-11-25
Hi guys. Been without internet for a while, but I'm back now. Not sure if this has been posted yet (only checked back a few pages), but according to this page:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804)

Those patches are supposed to make Punkbuster work on Wine 1.1.5. I just applied them and am compiling it right now, I'll post back the results. (Note: those patches won't apply to the latest wine, so I'm not sure if PunkBuster will work with an unpatched Wine 1.1.9)

Wow wine doesn't need the 3dmark patch anymore? Awesome

---

### Post by ahaslam on 2008-11-25
> **dvergur said:**
> Thanks a lot ahaslam.
This easy to follow guide is unfortunately all too rare.
I am quite new to Linux and this guide was great and I think I even learned something about Linux in the process.
Best regards,
dvergur.

You're welcome :)

---

### Post by piratesmack on 2008-11-25
Update:
No luck with punkbuster

It still gave me the same error as usual with the patches. I tried updating punkbuster, but that just gave me this:
[http://www.vulomedia.com/images/30805snapshot1.png](http://www.vulomedia.com/images/30805snapshot1.png)
:(

I tried it on Slackware 12.1. The howto in the WineHQ was for Ubuntu, so maybe it'll work on Ubuntu.

---

### Post by Allochtoon on 2009-01-17
vanilla wine-1.1.6
card=ati HD4850

```
----- Initializing Renderer ----
----- Client Initialization Complete -----
Attempting 44 kHz 16 bit [Windows default] sound
----- R_Init -----
Getting Direct3D 9 interface...
Pixel shader version is 3.0
Vertex shader version is 3.0
Video card or driver doesn't accelerate dynamic textures.
Video card or driver doesn't support separate alpha blend, glow will be disabled.


Error during initialization:
Video card or driver doesn't support separate alpha blend, glow will be disabled.
```

then it just hangs.

---

### Post by pmasterp on 2009-02-20
> **Allochtoon said:**
> vanilla wine-1.1.6
card=ati HD4850

```
----- Initializing Renderer ----
----- Client Initialization Complete -----
Attempting 44 kHz 16 bit [Windows default] sound
----- R_Init -----
Getting Direct3D 9 interface...
Pixel shader version is 3.0
Vertex shader version is 3.0
Video card or driver doesn't accelerate dynamic textures.
Video card or driver doesn't support separate alpha blend, glow will be disabled.


Error during initialization:
Video card or driver doesn't support separate alpha blend, glow will be disabled.
```

then it just hangs.

I've got the same issue under the same card ATI Radeon HD4850, damn ATI and Linux are not talking each other.

---

### Post by tkdzj on 2009-03-02
I personally think that halo 3 is a good game, as far as fps,along with call of duty... their both great games,and i don't know why people always have to say something negative about the other game. it's just retarded. but i think call of duty is much more fun to play online rather than halo 3 be it self adicting me to playing it all night with my neighbor,lol, if you guy's have xbox live you can add me if you want: Xbz Pro 
 and Yourobesemother is my neighbors gamertag. Thank you!

---

### Post by Jimmy92 on 2009-03-23
Hi, when i try to install cod4 from the guide on page 2 i get to "make depend && make" when i get this:
> 
signal_i386.c: I funktion "merge_vm86_pending_flags":
signal_i386.c:502: fel: "VIF_MASK" är odeklarerad (första förekomsten i denna funktion)
signal_i386.c:502: fel: (Varje odeklarerad identifierare rapporteras bara en gång
signal_i386.c:502: fel: för varje funktion den finns i.)
signal_i386.c:513: fel: "VIP_MASK" är odeklarerad (första förekomsten i denna funktion)
signal_i386.c: I funktion "raise_vm86_sti_exception":
signal_i386.c:1084: fel: "VIP_MASK" är odeklarerad (första förekomsten i denna funktion)
signal_i386.c: I funktion "__wine_enter_vm86":
signal_i386.c:1484: fel: "VIF_MASK" är odeklarerad (första förekomsten i denna funktion)
signal_i386.c:1485: fel: "VIP_MASK" är odeklarerad (första förekomsten i denna funktion)
make[2]: *** [signal_i386.o] Fel 1
make[2]: Lämnar katalogen "/home/jimmy/wine/wine-0.9.50/dlls/ntdll"
make[1]: *** [ntdll] Fel 2
make[1]: Lämnar katalogen "/home/jimmy/wine/wine-0.9.50/dlls"
make: *** [dlls] Fel 2

---

### Post by ahaslam on 2009-03-23
The newer versions of Wine don't need patching. I'm currently using version 1.1.14 & it runs COD4 perfectly. Try a pre built package: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Jimmy92 on 2009-03-23
> **ahaslam said:**
> The newer versions of Wine don't need patching. I'm currently using version 1.1.14 & it runs COD4 perfectly. Try a pre built package: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Thanks :) Now i installed everything. But when i start, a black screen appears and i cant do anything but i have the sound. Any idea?:-k

---

### Post by slovix on 2009-04-28
Hello guys.

can someone just put a working tutorial how to install and play the game, becouse I believe since 2007 something has changed :)

I sadly cant install, wine setup.exe says:
fixme:msi:MSI_OpenDatabaseW open failed r = 80030050 for L"C:\\windows\\temp\\msie1b.tmp"

And I get an isntallation error: 
Error 1628: Failed to complete the instalation.

Using ubuntu 9.04, newest wine, clean .iso. Any comments welcome..

---

### Post by Terdog on 2009-05-26
Ok, so for the newer versions of Call of Duty 4, does that mean I should install Direct X, or not? Also, does Punkbuster work?

---

### Post by Vrekk on 2009-05-26
> **Terdog said:**
> Ok, so for the newer versions of Call of Duty 4, does that mean I should install Direct X, or not? Also, does Punkbuster work?

Install Direct x.  

Punkbuster will not work :'(

---

### Post by Snyper64 on 2009-06-15
I looked through a few pages but have not seen my problem here. I have gotten the single player working with no problem but when I go to launch the multiplayer portion it shows the COD4 logo and than the screen flashes and I get a fatal error message. I than have to ALT+F4 and close the game. it also changes my resolution down to 800*600 and I have to change everything back to my normal resolution.

Does anybody have a fix for this. I installed wine right from the repository and am running the most current version 1.1.23(I have had this problem on earlier versions of wine also). Also I do not have Punkbuster installed.

---

