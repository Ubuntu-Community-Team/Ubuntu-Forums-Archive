---
title: "[SOLVED] Play Chinese Chess (XiangQi) online through Wine"
date: 2008-03-27
forum: Wine
---

### Post by hosammy on 2008-03-27
The [http://www.chesssky.net/](http://www.chesssky.net/) is the highest level in playing XiqngQi in the world.
To play this chess game through the internet. I need to download the relevant software from [http://www.chesssky.net/cdenglu.htm](http://www.chesssky.net/cdenglu.htm) and download the file: ESCMSetup.exe

My question is: can I install it through WINE in Ubuntu 7.10 and play XiangQi online?
If so, how?

I have already install WINE and running the IE6.0

Please advise ...

---

### Post by akimatsu123 on 2008-03-27
it seems like a fairly simple program. one that doesn't need special windows dll or anything. my guess is that it will work fine. why don't you test it out? you can always just uninstall it if it doesn't work no big deal.

---

### Post by hosammy on 2008-03-27
My question is what is the procedure to install it?

Thanks...

---

### Post by hosammy on 2008-03-27
I follow the instruction from [http://psychocats.net/ubuntu/wine](http://psychocats.net/ubuntu/wine) to install it and use the directory z:\home\sammy\.wine\drive_c\Program Files\Movesky
After the installation, a shorcut appear on the Desktop, the starter path is:
env WINEPREFIX="/home/sammy/.wine" wine "Z:\home\sammy\.wine\drive_c\Program Files\Movesky\ECMS.exe"

I double cleck it, it starts for a moment but nothing happens after 10 seconds.

Please advise ...

---

### Post by happyhamster on 2008-03-28
Try running ECMS.exe from a terminal: advantage is that you can see what's going on (you will get a lot of feedback).

- First navigate to the folder:

cd "$HOME/.wine/drive_c/Program Files/Movesky"

- Then run it:

wine ECMS.exe

- Or:

WINEDEBUG=fixme-all wine ECMS.exe

---

### Post by hosammy on 2008-03-28
> **happyhamster said:**
> Try running ECMS.exe from a terminal: advantage is that you can see what's going on (you will get a lot of feedback).

- First navigate to the folder:

cd "$HOME/.wine/drive_c/Program Files/Movesky"

- Then run it:

wine ECMS.exe

- Or:

WINEDEBUG=fixme-all wine ECMS.exe

The Ubuntu is in my office, will update the result when I come back to office.

Regards...

---

### Post by hosammy on 2008-03-31
> **happyhamster said:**
> Try running ECMS.exe from a terminal: advantage is that you can see what's going on (you will get a lot of feedback).

- First navigate to the folder:

cd "$HOME/.wine/drive_c/Program Files/Movesky"

- Then run it:

wine ECMS.exe

- Or:

WINEDEBUG=fixme-all wine ECMS.exe

I try and the following results:

[COLOR="DarkOliveGreen"]sammy@sammy-desktop:~/.wine/drive_c/ProgramFiles/movesky$ ls
ads         image         SkinLoad.dll.bak  uninstal.ini
background  jsboard2      stored            wave
ECMS.exe    SkinLoad.dll  uninstal.exe      xp_silver.skin[/COLOR][/COLOR]
[COLOR="Red"]sammy@sammy-desktop:~/.wine/drive_c/ProgramFiles/movesky$ wine ECMS.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\ProgramFiles\\movesky\\SkinLoad.dll") not found
err:module:import_dll Library SkinLoad.dll (which is needed by L"C:\\ProgramFiles\\movesky\\ECMS.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\ProgramFiles\\movesky\\ECMS.exe" failed, status c0000135[/COLOR]
[COLOR="Blue"]sammy@sammy-desktop:~/.wine/drive_c/ProgramFiles/movesky$ WINEDEBUG=fixme-all wine ECMS.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\ProgramFiles\\movesky\\SkinLoad.dll") not found
err:module:import_dll Library SkinLoad.dll (which is needed by L"C:\\ProgramFiles\\movesky\\ECMS.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\ProgramFiles\\movesky\\ECMS.exe" failed, status c0000135
[email]sammy@sammy-desktop:~/.wine[/email]/drive_c/ProgramFiles/movesky$ 
[/COLOR]

Please advise ...

---

### Post by happyhamster on 2008-03-31
> **hosammy said:**
> err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\ProgramFiles\\movesky\\SkinLoad.dll") not found
The game needs a native windows .dll file (mfc42.dll, which doesn't come along with wine). 

You could try searching the net to download that file and put it into wine's system32 folder.

A better way is probably installing  vcrun6 using the winetricks script. To download the script, see this page:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

- Navigate to where you downloaded the script:
cd /path/to/where/you/downloaded/the/script

- Make the script executable:
chmod +x winetricks

- Run winetricks to install vcrun6:
./winetricks vcrun6

- Or just run winetricks to see all options:
./winetricks

- Perhaps you'll need cabextract to get things to install, in that case:
sudo apt-get install cabextract

Good luck.

---

### Post by hosammy on 2008-04-01
> **happyhamster said:**
> The game needs a native windows .dll file (mfc42.dll, which doesn't come along with wine). 

You could try searching the net to download that file and put it into wine's system32 folder.

A better way is probably installing  vcrun6 using the winetricks script. To download the script, see this page:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

- Navigate to where you downloaded the script:
cd /path/to/where/you/downloaded/the/script

- Make the script executable:
chmod +x winetricks

- Run winetricks to install vcrun6:
./winetricks vcrun6

- Or just run winetricks to see all options:
./winetricks

- Perhaps you'll need cabextract to get things to install, in that case:
sudo apt-get install cabextract

Good luck.

sammy@sammy-desktop:~/Temp$ chmod +x winetricks
[COLOR="DarkRed"]sammy@sammy-desktop:~/Temp$ ./winetricks vcrun6
--12:21:54--  [http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe](http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe)
           => `vc6redistsetup_enu.exe'
download.microsoft.com... 63.150.131.180, 63.150.131.181
connecting download.microsoft.com|63.150.131.180|:80... connected&#12290;
 HTTP demand requested&#65292;waiting for response... 200 OK
length&#65306; 1,833,232 (1.7M) [application/octet-stream]

100%[====================================>] 1,833,232    597.47K/s    ETA 00:00

12:21:58 (596.23 KB/s) - `vc6redistsetup_enu.exe' saved
[1833232/1833232]

Executing sha1sum --status -c /home/sammy/.winetrickscache/./vc6redistsetup_enu.exe.sha1sum
Executing wine /home/sammy/.winetrickscache/vc6redistsetup_enu.exe /T:c:\winetrickstmp /c
Executing cabextract /home/sammy/.winetrickscache/vcredist.exe
Extracting cabinet: /home/sammy/.winetrickscache/vcredist.exe
  extracting VCRedist.inf
  extracting PreSetup.exe
  extracting 50comupd.exe
  extracting asycfilt.dll
  extracting atla.dll
  extracting comcat.dll
  extracting mfc42.dll
  extracting mfc42u.dll
  extracting msvcirt.dll
  extracting msvcp60.dll
  extracting msvcrt.dll
  extracting oleaut32.dll
  extracting olepro32.dll
  extracting stdole2.tlb
  extracting atlu.dll
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Install of vcrun6 done
winetricks done.[/COLOR]
[COLOR="Blue"]sammy@sammy-desktop:~/Temp$ wine ECMS.exe
wine: could not load L"c:\\windows\\system32\\ECMS.exe": Module not found[/COLOR]
sammy@sammy-desktop:~/Temp$ 

I have installed the cabextract ver 1.2 through synaptic

Please advise ...

---

### Post by happyhamster on 2008-04-01
> **hosammy said:**
> 
sammy@sammy-desktop:~/Temp$ wine ECMS.exe
wine: could not load L"c:\\windows\\system32\\ECMS.exe": Module not found
sammy@sammy-desktop:~/Temp$

You're trying to run it from some random folder; first navigate to wherever ECMS.exe is. 

cd "$HOME/.wine/drive_c/Program Files/Movesky"

wine ECMS.exe

---

### Post by hosammy on 2008-04-01
[COLOR="Blue"]sammy@sammy-desktop:~$ cd /home/sammy/.wine/drive_c/ProgramFiles/movesky
[email]sammy@sammy-desktop:~/.wine[/email]/drive_c/ProgramFiles/movesky$ 
[email]sammy@sammy-desktop:~/.wine[/email]/drive_c/ProgramFiles/movesky$ WINEDEBUG=fixme-all wine ECMS.exe
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
wine: Unhandled page fault on read access to 0x04578780 at address 0x7e3b78a5 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x04578780 in 32-bit code (0x7e3b78a5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e3b78a5 ESP:0034f008 EBP:0034f040 EFLAGS:00210206(   - 00      - RIP1)
 EAX:0000005c EBX:7e40788c ECX:ffffffff EDX:00000000
 ESI:04578780 EDI:7c563520
Stack dump:
0x0034f008:  ffffffff ffffffff 00000444 0000005c
0x0034f018:  00000000 00000000 00000000 00000000
0x0034f028:  7c563ae0 7c563520 00000000 04578780
0x0034f038:  00000170 7e406460 0034f200 7e3b3cc3
0x0034f048:  00000170 00000010 04578780 00000450
0x0034f058:  7c563520 fffffa40 00002e00 00000010
Backtrace:
=>1 0x7e3b78a5 convert_888_to_0888_asis+0xf5(width=0x170, height=0x10, srcbits=0x4578780, srclinebytes=0x450, dstbits=0x7c563520, dstlinebytes=0xfffffa40) [/build/buildd/wine-0.9.46/dlls/winex11.drv/dib_convert.c:852] in winex11 (0x0034f040)
  2 0x7e3b3cc3 X11DRV_DIB_SetImageBits+0x1ff3(descr=0x34f224) [/build/buildd/wine-0.9.46/dlls/winex11.drv/dib.c:2543] in winex11 (0x0034f200)
  3 0x7e3b5bda X11DRV_SetDIBits+0x1da(physDev=0x141d548, hbitmap=0x2534, startscan=0x0, lines=0x10, bits=0x4578780, info=0x7de710, coloruse=0x0) [/build/buildd/wine-0.9.46/dlls/winex11.drv/dib.c:3945] in winex11 (0x0034f2b0)
  4 0x7ed82543 SetDIBits+0x133(hdc=0x2528, hbitmap=0x2534, startscan=0x0, lines=0x10, bits=0x4578780, info=0x7de710, coloruse=0x0) [/build/buildd/wine-0.9.46/dlls/gdi32/dib.c:328] in gdi32 (0x0034f2f0)
  5 0x7ed83cea StretchDIBits+0x1ca(hdc=0x251c, xDst=0x0, yDst=0x0, widthDst=0x170, heightDst=0x10, xSrc=0x0, ySrc=0x0, widthSrc=0x170, heightSrc=<register EDI not in topmost frame>, bits=0x4578780, info=0x7de710, wUsage=0x0, dwRop=0xcc0020) [/build/buildd/wine-0.9.46/dlls/gdi32/dib.c:267] in gdi32 (0x0034f370)
  6 0x004a6a0c in ecms (+0xa6a0c) (0x0034f3c4)
  7 0x004076e4 in ecms (+0x76e4) (0x0000021c)
  8 0x00000000 (0x00000000)
0x7e3b78a5 convert_888_to_0888_asis+0xf5 [/build/buildd/wine-0.9.46/dlls/winex11.drv/dib_convert.c:852] in winex11: movl        0x0(%esi),%edx
Unable to open file '/build/buildd/wine-0.9.46/dlls/winex11.drv/dib_convert.c'
Modules:
Module  Address                 Debug info      Name (158 modules)
PE        360000-  366000       Deferred        xpcom
PE        3b0000-  3d7000       Deferred        nspr4
PE        3e0000-  3e7000       Deferred        plc4
PE        3f0000-  3f6000       Deferred        plds4
PE        400000-  592000       Export          ecms
PE        8d0000-  939000       Deferred        xpcom_core
PE        a50000-  a5f000       Deferred        jsd3250
PE        a60000-  ad1000       Deferred        js3250
PE        ae0000-  b15000       Deferred        xpc3250
PE        b20000-  b51000       Deferred        freebl3
PE        b60000-  b76000       Deferred        gkgfx
PE        b80000-  b93000       Deferred        jsj3250
PE        ba0000-  ba6000       Deferred        mozctlx
PE        bb0000-  bc1000       Deferred        mozz
PE        bd0000-  c2b000       Deferred        nss3
PE        c30000-  c6f000       Deferred        softokn3
PE        c70000-  cae000       Deferred        nssckbi
PE        cb0000-  cca000       Deferred        smime3
PE        cd0000-  cf0000       Deferred        ssl3
PE        cf0000-  d04000       Deferred        xpcom_compat
PE        d10000-  d16000       Deferred        xpistub
PE        d20000-  d9d000       Deferred        necko
PE        da0000-  dac000       Deferred        xppref32
PE        db0000-  dde000       Deferred        i18n
PE        de0000-  dff000       Deferred        embedcomponents
PE        e00000-  e0f000       Deferred        caps
PE        e10000-  e1c000       Deferred        typeaheadfind
PE        e20000- 10b9000       Deferred        gklayout
PE       10c0000- 10e7000       Deferred        imglib2
PE       10f0000- 110b000       Deferred        rdf
PE       1110000- 1148000       Deferred        appcomps
PE       1150000- 1160000       Deferred        appshell
PE       1160000- 116f000       Deferred        profile
PE       1170000- 1177000       Deferred        xpcom_compat_c
PE       1180000- 1187000       Deferred        sroaming
PE       1190000- 11a0000       Deferred        chrome
PE       11a0000- 11d9000       Deferred        gkparser
PE       11e0000- 129e000       Deferred        uconv
PE       12a0000- 12cc000       Deferred        docshell
PE       12d0000- 12da000       Deferred        nsprefm
PE       12e0000- 12ee000       Deferred        webbrwsr
PE       12f0000- 1315000       Deferred        gkwidget
PE       1320000- 1344000       Deferred        gkgfxwin
PE       1350000- 1358000       Deferred        pipboot
PE       1360000- 136c000       Deferred        oji
PE       1480000- 148d000       Deferred        jar50
PE      10000000-1000f000       Deferred        skinload
PE      5f400000-5f4f2000       Deferred        mfc42
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cc80000-7cc94000       Deferred        lz32<elf>
  \-PE  7cc90000-7cc94000       \               lz32
ELF     7cc94000-7ccae000       Deferred        version<elf>
  \-PE  7cca0000-7ccae000       \               version
ELF     7ccae000-7cd30000       Deferred        mshtml<elf>
  \-PE  7ccc0000-7cd30000       \               mshtml
ELF     7cd30000-7cd50000       Deferred        mpr<elf>
  \-PE  7cd40000-7cd50000       \               mpr
ELF     7cd50000-7cd9a000       Deferred        wininet<elf>
  \-PE  7cd60000-7cd9a000       \               wininet
ELF     7cd9a000-7cdd5000       Deferred        urlmon<elf>
  \-PE  7cda0000-7cdd5000       \               urlmon
ELF     7ce3c000-7ce76000       Deferred        shdocvw<elf>
  \-PE  7ce40000-7ce76000       \               shdocvw
ELF     7ce76000-7ce8b000       Deferred        midimap<elf>
  \-PE  7ce80000-7ce8b000       \               midimap
ELF     7ce8b000-7ceb2000       Deferred        msacm32<elf>
  \-PE  7ce90000-7ceb2000       \               msacm32
ELF     7ceb2000-7ceca000       Deferred        msacm32<elf>
  \-PE  7cec0000-7ceca000       \               msacm32
ELF     7ceca000-7cf04000       Deferred        wineoss<elf>
  \-PE  7ced0000-7cf04000       \               wineoss
ELF     7cf04000-7cf55000       Deferred        libgcrypt.so.11
ELF     7cf55000-7cf59000       Deferred        libgpg-error.so.0
ELF     7cf59000-7cf69000       Deferred        libtasn1.so.3
ELF     7cf69000-7cf71000       Deferred        libkrb5support.so.0
ELF     7cf71000-7cf9f000       Deferred        libcrypt.so.1
ELF     7cf9f000-7d00f000       Deferred        libgnutls.so.13
ELF     7d00f000-7d034000       Deferred        libk5crypto.so.3
ELF     7d034000-7d0bc000       Deferred        libkrb5.so.3
ELF     7d0bc000-7d0e5000       Deferred        libgssapi_krb5.so.2
ELF     7d0e5000-7d11a000       Deferred        libcups.so.2
ELF     7d3e6000-7d3e8000       Deferred        libkeyutils.so.1
ELF     7d40c000-7d43e000       Deferred        uxtheme<elf>
  \-PE  7d410000-7d43e000       \               uxtheme
ELF     7d43e000-7d443000       Deferred        libxfixes.so.3
ELF     7d443000-7d44c000       Deferred        libxcursor.so.1
ELF     7d44c000-7d469000       Deferred        imm32<elf>
  \-PE  7d450000-7d469000       \               imm32
ELF     7d469000-7d471000       Deferred        libxrender.so.1
ELF     7d47c000-7d47f000       Deferred        libcom_err.so.2
ELF     7d81e000-7e1b6000       Deferred        libglcore.so.1
ELF     7e1b6000-7e24c000       Deferred        libgl.so.1
ELF     7e24c000-7e251000       Deferred        libxdmcp.so.6
ELF     7e251000-7e342000       Deferred        libx11.so.6
ELF     7e342000-7e350000       Deferred        libxext.so.6
ELF     7e350000-7e368000       Deferred        libice.so.6
ELF     7e368000-7e370000       Deferred        libsm.so.6
ELF     7e371000-7e377000       Deferred        libxrandr.so.2
ELF     7e382000-7e40d000       Dwarf           winex11<elf>
  \-PE  7e390000-7e40d000       \               winex11
ELF     7e520000-7e540000       Deferred        libexpat.so.1
ELF     7e540000-7e56b000       Deferred        libfontconfig.so.1
ELF     7e56b000-7e580000       Deferred        libz.so.1
ELF     7e580000-7e5f0000       Deferred        libfreetype.so.6
ELF     7e5f0000-7e67e000       Deferred        winmm<elf>
  \-PE  7e600000-7e67e000       \               winmm
ELF     7e67e000-7e6ab000       Deferred        ws2_32<elf>
  \-PE  7e690000-7e6ab000       \               ws2_32
ELF     7e6ab000-7e6c5000       Deferred        wsock32<elf>
  \-PE  7e6b0000-7e6c5000       \               wsock32
ELF     7e6c5000-7e763000       Deferred        oleaut32<elf>
  \-PE  7e6e0000-7e763000       \               oleaut32
ELF     7e763000-7e777000       Deferred        olepro32<elf>
  \-PE  7e770000-7e777000       \               olepro32
ELF     7e777000-7e78a000       Deferred        libresolv.so.2
ELF     7e78b000-7e78d000       Deferred        libnvidia-tls.so.1
ELF     7e78d000-7e792000       Deferred        libxxf86vm.so.1
ELF     7e79c000-7e7ba000       Deferred        iphlpapi<elf>
  \-PE  7e7a0000-7e7ba000       \               iphlpapi
ELF     7e7ba000-7e813000       Deferred        rpcrt4<elf>
  \-PE  7e7d0000-7e813000       \               rpcrt4
ELF     7e813000-7e8b4000       Deferred        ole32<elf>
  \-PE  7e820000-7e8b4000       \               ole32
ELF     7e8b4000-7e8d6000       Deferred        oledlg<elf>
  \-PE  7e8c0000-7e8d6000       \               oledlg
ELF     7e8d6000-7e90b000       Deferred        winspool<elf>
  \-PE  7e8e0000-7e90b000       \               winspool
ELF     7e90b000-7e9ac000       Deferred        comdlg32<elf>
  \-PE  7e910000-7e9ac000       \               comdlg32
ELF     7e9ac000-7ea6a000       Deferred        comctl32<elf>
  \-PE  7e9c0000-7ea6a000       \               comctl32
ELF     7ea6a000-7eac3000       Deferred        shlwapi<elf>
  \-PE  7ea80000-7eac3000       \               shlwapi
ELF     7eac3000-7ebc6000       Deferred        shell32<elf>
  \-PE  7ead0000-7ebc6000       \               shell32
ELF     7ebc6000-7ed04000       Deferred        user32<elf>
  \-PE  7ebe0000-7ed04000       \               user32
ELF     7ed04000-7ed4d000       Deferred        advapi32<elf>
  \-PE  7ed10000-7ed4d000       \               advapi32
ELF     7ed4d000-7ede8000       Dwarf           gdi32<elf>
  \-PE  7ed60000-7ede8000       \               gdi32
ELF     7ede8000-7ee50000       Deferred        msvcrt<elf>
  \-PE  7ee00000-7ee50000       \               msvcrt
ELF     7efa6000-7efb1000       Deferred        libnss_files.so.2
ELF     7efb1000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7efee000       Deferred        libm.so.6
ELF     7efee000-7eff1000       Deferred        libxau.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d01000-b7d0a000       Deferred        libnss_compat.so.2
ELF     b7d0b000-b7d0f000       Deferred        libdl.so.2
ELF     b7d0f000-b7e59000       Deferred        libc.so.6
ELF     b7e5a000-b7e72000       Deferred        libpthread.so.0
ELF     b7e84000-b7f98000       Deferred        libwine.so.1
ELF     b7f9a000-b7fb6000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\ProgramFiles\movesky\ECMS.exe
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        00000009    0 <==
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ecc9860, level 2): Holding 0x7edd7c40, level 3. Expect deadlock!
err:syslevel:_CheckNotSysLevel Holding lock 0x7edd7c40 level 3

[/COLOR]

Then the terminal halt, please advise ..

---

### Post by happyhamster on 2008-04-01
- Well, such a backtrace is way beyond my skill level I'm afraid. You're using wine 0.9.46 correct? (You can check with the command "wine --version") Try running:

winecfg

- and select another windows version (winxp). You could also try experimenting with the Direct3D settings under the graphics tab (disable stuff).

- Another thing you could try is installing the current version of wine (0.9.58 ).  Follow the instructions here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

(Add the key and the corrrect repository for your ubuntu version, then run "sudo apt-get update" and "sudo apt-get upgrade" and allow wine to be updated.)

Good luck.

---

### Post by hosammy on 2008-04-09
> **happyhamster said:**
> - Well, such a backtrace is way beyond my skill level I'm afraid. You're using wine 0.9.46 correct? (You can check with the command "wine --version") Try running:

winecfg

- and select another windows version (winxp). You could also try experimenting with the Direct3D settings under the graphics tab (disable stuff).

- Another thing you could try is installing the current version of wine (0.9.58 ).  Follow the instructions here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

(Add the key and the corrrect repository for your ubuntu version, then run "sudo apt-get update" and "sudo apt-get upgrade" and allow wine to be updated.)

Good luck.

Yes, after upgrade to Wine 0.9.59 and changed the winecfg to Windows XP & disable the stuff under the graphic tab, the program can run normally.

Thanks a lot for your support!

My problem here is solved!:lolflag::guitar::popcorn:

---

