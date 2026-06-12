---
title: "Steam close when I try to start a game."
date: 2008-01-02
forum: Wine
---

### Post by ODF on 2008-01-02
I installed steam with a SteamInstall.exe file then everything is working until I click Launch game.

Steam is simply closing itself.

---

### Post by Borbus on 2008-01-02
Which version of Wine, which graphics card, which driver?

---

### Post by ODF on 2008-01-02
Wine 0.9.52

Nvidia 8800 GTS

Drivers : The restriced drivers and the NVidia binary X.Org driver ('new' driver) in the add/remove application. Don't know much about drivers and ubuntu.

---

### Post by orrie on 2008-01-09
I have the exact same problem.

**Graphic card:**
```
orrie@ubuntu:~$ lspci|grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 Ultra (rev a2)

```

**Wine version:**
```
orrie@ubuntu:~$ wine --version
wine-0.9.46

```

**Driver:**
```
orrie@ubuntu:~$ nvidia-installer -v

nvidia-installer:  version 1.0.7  (buildmeister@builder26)  Thu Dec 13 18:55:51 PST 2007
  The NVIDIA Software Installer for Unix/Linux.

  This program is used to install and upgrade The NVIDIA Accelerated Graphics Driver Set for Linux-x86_64.

  Copyright (C) 2003 NVIDIA Corporation.

```

```
orrie@ubuntu:~$ ls *.run
NVIDIA-Linux-x86_64-169.07-pkg2.run

```

Anyone know's how to fix it? :)

---

### Post by Zellio on 2008-01-10
You need to install tahoma font, and change your permisions to your name (search for how), and then steam works.

Done those yet?

I can help you with the first.  GOogle tahoma font (it lets words on steam appear).  You'll need to use the cp command in terminal to install it.

Ask someone else how to change permissions of the wine folder to your name.

The new version of steam with steam community doesn't load correctly unless you do these things.

Try exiting steam and reentering.  You'll find it has an error unless the permissions are correct.

A few other things to try:

Set 'allow dx apps to stop the mouse from leaving the window'.  This will make the game full screen if dx wasn't allowing that.

Set steam for windows vista compatibility.  While steam games are more compatible with xp, steam seems oddly more vista compatible from my experence.

---

### Post by orrie on 2008-01-10
```
orrie@ubuntu:~$ cat tahomafix.sh 
# this script fixes the "bug" with no font in Steam
wget http://www.webpagepublicity.com/free-fonts/t/Tahoma.ttf
mv Tahoma.ttf ~/.wine/drive_c/windows/fonts
echo "Bug in Steam is fixed."

orrie@ubuntu:~$ sh tahomafix.sh
....
...
...
Bug in Steam is fixed.

```
Yep, I have fixed the Tahoma thing.

```
root@ubuntu:/home/orrie# chown orrie:orrie .wine
```
And I am now the owner of the folder ".wine".

And as I forget to tell.. I ran wine iexplore to install the Gecko so that shouldn't be any problem.

I made an startup-script to Steam looking like this:
```
orrie@ubuntu:~$ cat steam-startup.sh 
#!/bin/bash

# WINE binary
CDLOADER_WINE="wine"

# Steam dir
STEAMDIR="$HOME/.wine/drive_c/Programfiler/Steam"

cd "$STEAMDIR"

$CDLOADER_WINE "steam.exe" -- "$@" &

```

Steam runs fine, until I'm clicking on Counter-Strike and Install.
Then does this error-message pop up in the console:
```
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl

```

And Steam are closed :(

---

### Post by orrie on 2008-01-18
Anyone for the rescue?

---

### Post by EricJames on 2008-01-23
I'm also having this same problem.  Client just exits on clicking 'launch' to download.  I manually installed the game and it still exits wine on clicking 'launch'.  Help us!  :confused:

Edit:  I have a 8400m GS 128MB using the standard restricted drivers.

---

### Post by ScottKidder on 2008-01-24
I'm having an issue along these lines. After I click launch I get a Starting Counter Striker dialog and then it closes, here is console output

```
scott@merrill011:~/Downloads$ env WINEPREFIX="/home/scott/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 10
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:shdocvw:ViewObject_SetAdvise (0x137c38d8)->(1 00000002 0x139dc18)
fixme:shdocvw:PersistStreamInit_InitNew (0x137c38d8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x137c38d8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x137c38d8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x10b3a858)->(1 00000002 0x139dc80)
fixme:shdocvw:PersistStreamInit_InitNew (0x10b3a858)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10b3a858)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10b3a858)->(ffffffff)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x34c3ac,0x00000000), stub!
err:systray:delete_icon invalid tray icon ID specified: 1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x13b2bc20)->(1 00000002 0x139f2b0)
fixme:shdocvw:PersistStreamInit_InitNew (0x13b2bc20)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x13b2bc20)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x13b2bc20)->(ffffffff)
fixme:process:IsWow64Process (0xffffffff 0x3e7e88) stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,58,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,58,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,58,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,125,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,125,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,167,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,224,2): stub!
wine: Unhandled page fault on write access to 0x00000000 at address 0x7ebf0003 (thread 002e), starting debugger...
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,202,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,144,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,144,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,83,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,33,2): stub!
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7ebf0003).
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,0,2): stub!
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ebf0003 ESP:0034fe18 EBP:0034fe07 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000246 EBX:00000000 ECX:00000000 EDX:0034fe2c
 ESI:0034fea8 EDI:00000008
Stack dump:
0x0034fe18:  0034fea8 00000018 0034fe2c 0140c9cc
0x0034fe28:  0140c9a4 00000000 00000000 00440041
0x0034fe38:  00410056 00490050 00320033 0064002e
0x0034fe48:  006c006c 7efe0000 00000000 001108a8
0x0034fe58:  0034fea8 7efa06d0 0034fea0 0034fe80
0x0034fe68:  00000000 00000000 7efa10a9 7efe461c
Backtrace:
=>1 0x7ebf0003 in advapi32 (+0x3) (0x0034fe07)
  2 0xe2100400 (0x00024600)
  3 0x00000000 (0x00000000)
0x7ebf0003: addb        %al,0x0(%ebx)
Modules:
Module  Address                 Debug info      Name (29 modules)
PE       1400000- 3516000       Deferred        hl
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ea08000-7eaa1000       Deferred        gdi32<elf>
  \-PE  7ea20000-7eaa1000       \               gdi32
ELF     7eaa1000-7ebde000       Deferred        user32<elf>
  \-PE  7eac0000-7ebde000       \               user32
ELF     7ebde000-7ec2b000       Dwarf           advapi32<elf>
  \-PE  7ebf0000-7ec2b000       \               advapi32
ELF     7ec2b000-7ec3d000       Deferred        libresolv.so.2
ELF     7ec3d000-7ec5b000       Deferred        iphlpapi<elf>
  \-PE  7ec40000-7ec5b000       \               iphlpapi
ELF     7ec5b000-7ec87000       Deferred        ws2_32<elf>
  \-PE  7ec60000-7ec87000       \               ws2_32
ELF     7ec87000-7eca1000       Deferred        wsock32<elf>
  \-PE  7ec90000-7eca1000       \               wsock32
ELF     7eca1000-7ecab000       Deferred        libnss_files.so.2
ELF     7ecab000-7ecc2000       Deferred        libnsl.so.1
ELF     7ecc2000-7ecca000       Deferred        libnss_compat.so.2
ELF     7edfb000-7ef26000       Deferred        kernel32<elf>
  \-PE  7ee20000-7ef26000       \               kernel32
ELF     7ef26000-7ef4b000       Deferred        libm.so.6
ELF     7ef51000-7ef5b000       Deferred        libnss_nis.so.2
ELF     7ef5d000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef70000-7f000000       \               ntdll
ELF     b7cde000-b7ce2000       Deferred        libdl.so.2
ELF     b7ce2000-b7e16000       Deferred        libc.so.6
ELF     b7e17000-b7e2e000       Deferred        libpthread.so.0
ELF     b7e40000-b7f54000       Deferred        libwine.so.1
ELF     b7f56000-b7f72000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008
        0000002b    0
        00000029    0
        00000046    0
        00000045    0
        00000044    1
        00000043    0
        00000042    1
        00000041    0
        00000040    1
        0000003f    0
        0000003e    1
        0000003d    0
        0000003c    1
        0000003b    0
        0000003a    1
        00000036    0
        00000035    0
        00000034    1
        00000033    0
        00000032    0
        00000030    0
        0000002f    1
        0000002a    0
        00000028    0
        00000027   15
        00000026   15
        00000022   15
        0000001f    0
        0000001e    0
        0000001d    0
        0000001c    0
        0000001b    0
        0000001a    1
        00000019    0
        00000018    0
        00000017    0
        00000016    0
        00000015    0
        00000014    0
        00000013    0
        00000009    0
0000000a
        0000000b    0
0000000c
        0000000f    0
        0000000e    0
        0000000d    0
00000010
        00000012    0
        00000011    0
00000031 (D) C:\Program Files\Steam\steamapps\scottkidder\counter-strike\hl.exe
        0000002e    0 <==
Backtrace:
=>1 0x7ebf0003 in advapi32 (+0x3) (0x0034fe07)
  2 0xe2100400 (0x00024600)
  3 0x00000000 (0x00000000)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x13b2bc20)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x13b2bc20)
fixme:shdocvw:OleObject_Close (0x13b2bc20)->(1)
```

Also after some time on the winehq IRC channel I switched graphics drivers twice from 169.07 to 169.09, which I found out were both "garbage" and moved back to 100.14.19, to no avail with almost the same console output. 

ALSO, This problem only started occuring to me after I had installed CS:Source, and then tried to go back and play CS:1.6

---

### Post by ScottKidder on 2008-01-24
I found a fix, First, if you're using Nvidia drivers either 169.07 or 167.09, go back to  100.14.19, and I also went back to Wine 0.9.49 and I was up and running.

---

### Post by orrie on 2008-03-21
I had to do something more since it still were closing after downgraded Wine.
BUT, this make's it all work!

Download [Wine 0.9.49](http://wine.budgetdedicated.com/archive/index.html).
To install Wine 0.9.49:
```
sudo dpkg -i wine_0.9.49*.deb
```
To create a .wine-folder:
```
winecfg
```
To fix the font-trouble in wine/steam:
```
wget http://pub.orrie.org/sh/tahomafix.sh
```
```
sh tahomafix.sh
```
To install Gecko-engine:
```
wine iexplore
```


That **should** make it all work ;)

---

