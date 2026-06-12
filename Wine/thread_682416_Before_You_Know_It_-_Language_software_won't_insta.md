---
title: "Before You Know It - Language software won't install"
date: 2008-01-30
forum: Wine
---

### Post by rjmarshall on 2008-01-30
I found a link in the appdb for wine that says "Before You Know It" v3.6 has been tested on Ubuntu.  But when I try to run the installer (for Chinese) it gives me an error saying, "Current software cannot be installed on your OS."

Does anyone know how they installed "Before You Know It" and got it working?

The link to the test results is:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5797](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5797)

Thanks,

Rob

---

### Post by yabbadabbadont on 2008-01-30
They listed what they had to do to get it to run:
> Testing Lite version - Everything, program and download new lists all work.

riched20.dll & riched32.dll must be in native mode

Also have ole32, oleaut32, & rpcrt4 in native, builtin mode (not sure if these help or not, I have as default settings.
Are you using the Lite version?  Did you change the settings for the listed dlls to be what was listed?

The wine documentation explains how to do dll overrides if you need that information:

[http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN241](http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN241)

---

### Post by rjmarshall on 2008-01-30
Yeah, that's what I've been trying.  I set up the dll's the way they suggested, and I am trying to download the lite version.

It's a file called BYKIDownloaderPC.exe.  When I open it in Wine it comes up with the "smart downloader" window, It says it will download all the components necessary, I click on "start", it says, "Query for updates..." and then comes back with, "current software cannot be installed on your OS" and the only thing it lets me do is click on "close".

So, I'm not sure if I'm missing a step or doing something else wrong.  I can't seem to find a version of the download that is just a zip file of the program and files, and it seems like the only way to get it is to use their "smart downloader".

Any suggestions?

Thank-you,

Rob

---

### Post by rjmarshall on 2008-01-30
Never mind...the problem was that Wine was configured as "Windows 2000".  When I selected "Windows XP" it started the download fine...It suddenly hit me that the problem may be the OS it thinks I have, and viola!

Thanks,

Rob

---

### Post by rjmarshall on 2008-01-30
I guess my excitement was short-lived...I got it to install and can even get the window to come up that allows me to select the list I want to work on (with riched20 configured as native, it complained about not finding it, so I set it up as native/builtin), but then it crashes with an unhandled exception.  

Any help would be appreciated...

Here's the output:

```
fixme:keyboard:X11DRV_LoadKeyboardLayout L"E0010412", 0100: stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34effc,0x00000000), stub!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:dciman:DCICreatePrimary 0x350 0xd4126c
err:tooltips:TOOLTIPS_WindowProc unknown msg 041f wp=00000001 lp=0034d230
fixme:richedit:fnTextSrv_QueryInterface Unknown interface: {8cc497c0-a1df-11ce-8098-00aa0047be5d}
wine: Unhandled page fault on read access to 0x00000000 at address 0x42743a (thread 0019), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0042743a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0042743a ESP:0034df04 EBP:0034df50 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:0034df84 EBX:00000000 ECX:0034df88 EDX:00000000
 ESI:00000000 EDI:0034df84
Stack dump:
0x0034df04:  0034e2a4 00918d08 00000000 00000024
0x0034df14:  00000000 7c1693cd 00000024 0034dfc4
0x0034df24:  0034df84 00000000 00000000 00000000
0x0034df34:  0034df84 004803fd 00000000 0034df04
0x0034df44:  0034e158 004a0290 00000000 00ca9140
0x0034df54:  0044e5bd 00ca9140 00000000 00000000
Backtrace:
=>1 0x0042743a in byki36winlite (+0x2743a) (0x0034df50)
  2 0x0044e5bd in byki36winlite (+0x4e5bd) (0x00ca9140)
0x0042743a: movl        0x0(%esi),%ecx
Modules:
Module  Address                 Debug info      Name (107 modules)
PE        350000-  3a9000       Deferred        widgets
PE        400000-  51b000       Export          byki36winlite
PE        520000-  6aa000       Deferred        tlsound
PE        e50000-  f45000       Deferred        bykires
PE      10000000-1007b000       Deferred        keymapdll
PE      70d00000-70ea0000       Deferred        gdiplus
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c140000-7c243000       Deferred        mfc71
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7d31c000-7d330000       Deferred        dciman32<elf>
  \-PE  7d320000-7d330000       \               dciman32
ELF     7dc96000-7dd21000       Deferred        winex11<elf>
  \-PE  7dcb0000-7dd21000       \               winex11
ELF     7e089000-7e09f000       Deferred        msftedit<elf>
  \-PE  7e090000-7e09f000       \               msftedit
ELF     7e09f000-7e0e5000       Deferred        riched20<elf>
  \-PE  7e0b0000-7e0e5000       \               riched20
ELF     7e0e5000-7e117000       Deferred        uxtheme<elf>
  \-PE  7e0f0000-7e117000       \               uxtheme
ELF     7e117000-7e12c000       Deferred        midimap<elf>
  \-PE  7e120000-7e12c000       \               midimap
ELF     7e12c000-7e153000       Deferred        msacm32<elf>
  \-PE  7e130000-7e153000       \               msacm32
ELF     7e153000-7e16b000       Deferred        msacm32<elf>
  \-PE  7e160000-7e16b000       \               msacm32
ELF     7e16b000-7e1a5000       Deferred        wineoss<elf>
  \-PE  7e170000-7e1a5000       \               wineoss
ELF     7e1a5000-7e1f6000       Deferred        libgcrypt.so.11
ELF     7e1f6000-7e206000       Deferred        libtasn1.so.3
ELF     7e206000-7e234000       Deferred        libcrypt.so.1
ELF     7e234000-7e2a4000       Deferred        libgnutls.so.13
ELF     7e2c9000-7e351000       Deferred        libkrb5.so.3
ELF     7e351000-7e37a000       Deferred        libgssapi_krb5.so.2
ELF     7e37a000-7e3af000       Deferred        libcups.so.2
ELF     7e3c2000-7e3cb000       Deferred        libxcursor.so.1
ELF     7e3cb000-7e3d1000       Deferred        libxrandr.so.2
ELF     7e3d1000-7e3d9000       Deferred        libxrender.so.1
ELF     7e3d9000-7e3e3000       Deferred        libdrm.so.2
ELF     7e3e3000-7e3e8000       Deferred        libxfixes.so.3
ELF     7e3e8000-7e3eb000       Deferred        libxdamage.so.1
ELF     7e3eb000-7e44c000       Deferred        libgl.so.1
ELF     7e44c000-7e451000       Deferred        libxdmcp.so.6
ELF     7e451000-7e454000       Deferred        libxau.so.6
ELF     7e454000-7e545000       Deferred        libx11.so.6
ELF     7e545000-7e553000       Deferred        libxext.so.6
ELF     7e553000-7e558000       Deferred        libxxf86vm.so.1
ELF     7e558000-7e570000       Deferred        libice.so.6
ELF     7e570000-7e578000       Deferred        libsm.so.6
ELF     7e578000-7e57c000       Deferred        libgpg-error.so.0
ELF     7e57c000-7e57e000       Deferred        libkeyutils.so.1
ELF     7e57e000-7e586000       Deferred        libkrb5support.so.0
ELF     7e5ff000-7e61f000       Deferred        libexpat.so.1
ELF     7e61f000-7e64a000       Deferred        libfontconfig.so.1
ELF     7e64a000-7e65f000       Deferred        libz.so.1
ELF     7e65f000-7e6cf000       Deferred        libfreetype.so.6
ELF     7e6cf000-7e7d2000       Deferred        shell32<elf>
  \-PE  7e6e0000-7e7d2000       \               shell32
ELF     7e7d2000-7e7f2000       Deferred        mpr<elf>
  \-PE  7e7e0000-7e7f2000       \               mpr
ELF     7e7f2000-7e83c000       Deferred        wininet<elf>
  \-PE  7e800000-7e83c000       \               wininet
ELF     7e83c000-7e84f000       Deferred        libresolv.so.2
ELF     7e862000-7e880000       Deferred        iphlpapi<elf>
  \-PE  7e870000-7e880000       \               iphlpapi
ELF     7e880000-7e8d9000       Deferred        rpcrt4<elf>
  \-PE  7e890000-7e8d9000       \               rpcrt4
ELF     7e8d9000-7e97a000       Deferred        ole32<elf>
  \-PE  7e8f0000-7e97a000       \               ole32
ELF     7e97a000-7ea18000       Deferred        oleaut32<elf>
  \-PE  7e990000-7ea18000       \               oleaut32
ELF     7ea18000-7ea71000       Deferred        shlwapi<elf>
  \-PE  7ea30000-7ea71000       \               shlwapi
ELF     7ea71000-7ea8e000       Deferred        imm32<elf>
  \-PE  7ea80000-7ea8e000       \               imm32
ELF     7ea8e000-7eb4c000       Deferred        comctl32<elf>
  \-PE  7eaa0000-7eb4c000       \               comctl32
ELF     7eb4c000-7ebda000       Deferred        winmm<elf>
  \-PE  7eb60000-7ebda000       \               winmm
ELF     7ebda000-7ec01000       Deferred        msvfw32<elf>
  \-PE  7ebe0000-7ec01000       \               msvfw32
ELF     7ec01000-7ec36000       Deferred        winspool<elf>
  \-PE  7ec10000-7ec36000       \               winspool
ELF     7ec36000-7ec4a000       Deferred        lz32<elf>
  \-PE  7ec40000-7ec4a000       \               lz32
ELF     7ec4a000-7ec64000       Deferred        version<elf>
  \-PE  7ec50000-7ec64000       \               version
ELF     7ec64000-7ecff000       Deferred        gdi32<elf>
  \-PE  7ec80000-7ecff000       \               gdi32
ELF     7ecff000-7ee3d000       Deferred        user32<elf>
  \-PE  7ed20000-7ee3d000       \               user32
ELF     7ee3d000-7ee86000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee86000       \               advapi32
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cb4000-b7cb8000       Deferred        libdl.so.2
ELF     b7cb8000-b7e02000       Deferred        libc.so.6
ELF     b7e02000-b7e1a000       Deferred        libpthread.so.0
ELF     b7e2d000-b7f41000       Deferred        libwine.so.1
ELF     b7f43000-b7f5f000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000018 (D) C:\Program Files\Transparent\Before You Know It 3.6\Lite\BYKI36WinLite.exe
        0000001d    0
        0000001c    0
        0000001b    0
        0000001a    0
        00000019    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000009    0

```

---

### Post by happyhamster on 2008-01-30
When using native dll's, make sure you get the latest ones (at least appropriate for the chosen windows version). In this case, make sure you put winxp versions of riched20.dll and riched32.dll into the ~/.wine/drive_c/windows/system32 folder.

---

### Post by saunders on 2008-01-30
I'm having the same problem as rjmarshall...

I've managed to install the software using the dll's, and setting wine to winXP. The application refuses to start.

How do I make sure I've got the XP dll's?

Cheers

---

### Post by happyhamster on 2008-01-30
The ones that work for me:  5.30.23.1221 and 5.1.2600.0 for riched20 and 32 respectively (check the download page you used). Put those files in wine's system32 folder and start the program using:

WINEDLLOVERRIDES="riched20,riched32=n" wine BYKI36WinLite.exe

If it still doesn't work, start it like this*:

WINEDEBUG=-all,+loaddll WINEDLLOVERRIDES="riched20,riched32=n" wine BYKI36WinLite.exe

Which will allow you to check if the dll's are loaded natively or not.

I'm using wine 0.9.54 and Ubuntu Gutsy Gibbon (no compiz-fusion).

edit: you'll have to navigate to the correct folder first of course, in my case: 

cd "$HOME/.wine/drive_c/Program Files/Transparent/Before You Know It 3.6/Lite"

---

### Post by rjmarshall on 2008-01-30
Well...it just is not working.  I tried to uninstall and then reinstall it, and now it won't even install properly.  It gets to the point where it's importing the lists and never comes back.  I even tried removing wine (along with deleting .wine under my home directory) and reinstalling, but it still won't work.

Is there some way to be absolutely sure that I've completely removed all of BYKI as well as wine so that I can start with a "fresh" install?

Thanks,

Rob

---

### Post by rjmarshall on 2008-01-30
One more question...riched20.dll doesn't come with BYKI, and I'm not sure where it is that is "native".  Where do you get the native version?  The one under system32 says it's a "Wine fake DLL" when I run winedump against it.

Thanks again,

Rob

---

### Post by rjmarshall on 2008-01-31
Well...progress :)  I found a riched20.dll that came with ies4linux (I tried installing ie6/ie7 and neither one works correctly...but that's another story), so I copied it to the BYKI folder and now it works.  The only problem is that the display on the "recognize it" portion is missing some stuff in the pane on the top right (above where the scores are...can't remember what was there), and the font for the pinyin is not that good.

But it is working.

Thanks,

Rob

---

### Post by happyhamster on 2008-01-31
With "native" I meant "an original windows dll file". You'll usually have to get one from a windows pc, or download from one of several available sites.

Anyway, congrats on getting it to work. :)

---

