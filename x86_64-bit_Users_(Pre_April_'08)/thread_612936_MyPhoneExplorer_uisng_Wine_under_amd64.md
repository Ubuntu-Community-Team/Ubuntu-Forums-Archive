---
title: "MyPhoneExplorer uisng Wine under amd64"
date: 2007-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by abrichr on 2007-11-14
I have Wine 0.9.49 installed on Gutsy amd64.  I downloaded the latest version of MyPhoneExplorer 1.6.4, a utility to access Sony Ericsson mobile units from a PC.  I tried installing it, but the installing window hangs at the line "Registering: c:\Program Files\MyPhoneExplorer\DLL\ShellMgr.dll".

Terminal output:

```
$ wine MyPhoneExplorer_Setup_1.6.4.exe
fixme:shell:SHAutoComplete SHAutoComplete stub
wine: Unhandled page fault on read access to 0x00000001 at address 0x10061409 (thread 000c), starting debugger...
Unhandled exception: page fault on read access to 0x00000001 in 32-bit code (0x10061409).
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 04c48310 in module L"sport"
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:10061409 ESP:7d04a09c EBP:7d04a120 EFLAGS:00010202(   - 00      - -RI1)
 EAX:103bf001 EBX:10000000 ECX:00000001 EDX:00000001
 ESI:00000001 EDI:00000000
Stack dump:
0x7d04a09c:  00000202 1005f000 001977a0 00005000
0x7d04a0ac:  00000000 00000001 10000000 00000008
0x7d04a0bc:  001557a0 00000008 00110014 7bc8665c
0x7d04a0cc:  7cf3a500 00000000 7d04a104 7bc326f7
0x7d04a0dc:  00110000 00000000 00000020 00000000
0x7d04a0ec:  001558b0 001557a0 001558b4 001558c8
Backtrace:
=>1 0x10061409 in sport (+0x61409) (0x7d04a120)
  2 0x10060ab3 in sport (+0x60ab3) (0x7d04a188)
  3 0x100622f5 in sport (+0x622f5) (0x7d04a2a0)
  4 0x1006238b in sport (+0x6238b) (0x7d04a3b0)
  5 0x1006085b in sport (+0x6085b) (0x7d04a42c)
  6 0x10072ee7 in sport (+0x72ee7) (0x7d04a44c)
  7 0x7bc42ff5 call_dll_entry_point+0x15() in ntdll (0x7d04a46c)
  8 0x7bc449cd in ntdll (+0x349cd) (0x7d04a4fc)
  9 0x7bc45024 in ntdll (+0x35024) (0x7d04a54c)
  10 0x7bc46df7 LdrLoadDll+0x87() in ntdll (0x7d04a57c)
  11 0x7b866d20 in kernel32 (+0x46d20) (0x7d04a7dc)
  12 0x7b866f24 LoadLibraryExW+0x44() in kernel32 (0x7d04a80c)
  13 0x7b867043 LoadLibraryExA+0x43() in kernel32 (0x7d04a82c)
  14 0x7b86707d LoadLibraryA+0x2d() in kernel32 (0x7d04a84c)
  15 0x00402019 in myphoneexplorer_setup_1.6.4 (+0x2019) (0x7d04aa08)
  16 0x0040138f in myphoneexplorer_setup_1.6.4 (+0x138f) (0x7d04aa38)
  17 0x7bc6a402 in ntdll (+0x5a402) (0x7d04aad8)
  18 0x7bc6a6c2 in ntdll (+0x5a6c2) (0x7d04b3d8)
  19 0xf7e4046b start_thread+0xcb() in libpthread.so.0 (0x7d04b4c8)
  20 0xf7dc58ce __clone+0x5e() in libc.so.6 (0x00000000)
0x10061409: arpl        %ss:0x0(%esi),%si
Modules:
Module  Address                 Debug info      Name (71 modules)
PE        400000-  436000       Export          myphoneexplorer_setup_1.6.4
PE      10000000-10135000       Export          sport
ELF     7b800000-7b92a000       Export          kernel32<elf>
  \-PE  7b820000-7b92a000       \               kernel32
ELF     7bc00000-7bca2000       Export          ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cde0000-7ce80000       Deferred        oleaut32<elf>
  \-PE  7cdf0000-7ce80000       \               oleaut32
ELF     7ce80000-7ce9b000       Deferred        comcat<elf>
  \-PE  7ce90000-7ce9b000       \               comcat
ELF     7ced3000-7cf3b000       Deferred        msvcrt<elf>
  \-PE  7cee0000-7cf3b000       \               msvcrt
ELF     7d04c000-7d092000       Deferred        riched20<elf>
  \-PE  7d060000-7d092000       \               riched20
ELF     7d383000-7d3b5000       Deferred        uxtheme<elf>
  \-PE  7d390000-7d3b5000       \               uxtheme
ELF     7d3b5000-7d3be000       Deferred        libxcursor.so.1
ELF     7d3be000-7d3db000       Deferred        imm32<elf>
  \-PE  7d3d0000-7d3db000       \               imm32
ELF     7d3db000-7d3e0000       Deferred        libxfixes.so.3
ELF     7d3e0000-7d3e3000       Deferred        libxcomposite.so.1
ELF     7d3e3000-7d3e9000       Deferred        libxrandr.so.2
ELF     7d3e9000-7d3ec000       Deferred        libxinerama.so.1
ELF     7dbc8000-7e560000       Deferred        libglcore.so.1
ELF     7e560000-7e5f6000       Deferred        libgl.so.1
ELF     7e5f6000-7e5fb000       Deferred        libxdmcp.so.6
ELF     7e5fb000-7e5fe000       Deferred        libxau.so.6
ELF     7e5fe000-7e6ef000       Deferred        libx11.so.6
ELF     7e6ef000-7e6fd000       Deferred        libxext.so.6
ELF     7e6fe000-7e706000       Deferred        libxrender.so.1
ELF     7e710000-7e7a1000       Deferred        winex11<elf>
  \-PE  7e720000-7e7a1000       \               winex11
ELF     7e80c000-7e82c000       Deferred        libexpat.so.1
ELF     7e82c000-7e857000       Deferred        libfontconfig.so.1
ELF     7e857000-7e86c000       Deferred        libz.so.1
ELF     7e86c000-7e8dc000       Deferred        libfreetype.so.6
ELF     7e8dc000-7e8f0000       Deferred        lz32<elf>
  \-PE  7e8e0000-7e8f0000       \               lz32
ELF     7e8f0000-7e90a000       Deferred        version<elf>
  \-PE  7e900000-7e90a000       \               version
ELF     7e90a000-7e91d000       Deferred        libresolv.so.2
ELF     7e930000-7e94e000       Deferred        iphlpapi<elf>
  \-PE  7e940000-7e94e000       \               iphlpapi
ELF     7e94e000-7e9a8000       Deferred        rpcrt4<elf>
  \-PE  7e960000-7e9a8000       \               rpcrt4
ELF     7e9a8000-7ea4a000       Deferred        ole32<elf>
  \-PE  7e9c0000-7ea4a000       \               ole32
ELF     7ea4a000-7eb09000       Deferred        comctl32<elf>
  \-PE  7ea50000-7eb09000       \               comctl32
ELF     7eb09000-7eb62000       Deferred        shlwapi<elf>
  \-PE  7eb20000-7eb62000       \               shlwapi
ELF     7eb62000-7ec65000       Deferred        shell32<elf>
  \-PE  7eb70000-7ec65000       \               shell32
ELF     7ec65000-7ecb1000       Deferred        advapi32<elf>
  \-PE  7ec70000-7ecb1000       \               advapi32
ELF     7ecb1000-7ed49000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed49000       \               gdi32
ELF     7ed49000-7ee86000       Deferred        user32<elf>
  \-PE  7ed60000-7ee86000       \               user32
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     f7ce0000-f7ce2000       Deferred        libnvidia-tls.so.1
ELF     f7ce2000-f7ceb000       Deferred        libnss_compat.so.2
ELF     f7cec000-f7cf0000       Deferred        libdl.so.2
ELF     f7cf0000-f7e3a000       Export          libc.so.6
ELF     f7e3b000-f7e53000       Export          libpthread.so.0
ELF     f7e66000-f7f7a000       Deferred        libwine.so.1
ELF     f7f7c000-f7f9a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
00000008 (D) Z:\home\rda\Downloads\mobile\sonyericsson\myphoneexplorer\MyPhoneExplorer_Setup_1.6.4.exe
        0000000c    0 <==
        00000009    0
```

...and it hangs.  It's not stuck, it just doesn't do anything.  I tried installing the VB6 runtime from Microsoft's website (VB6.0-KB290887-X86.exe).  The extraction works, but when I try to run the extracted install flile:

```
$ wine vbrun60sp6.exe 
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 33f9ac,0
err:setupapi:SetupDefaultQueueCallbackW copy error 0 L"C:\\windows\\temp\\IXP000.TMP\\OLEAUT32.DLL" -> L"c:\\windows\\system32\\OLEAUT32.DLL"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 33f9ac,0
err:setupapi:SetupDefaultQueueCallbackW copy error 0 L"C:\\windows\\temp\\IXP000.TMP\\OLEPRO32.DLL" -> L"c:\\windows\\system32\\OLEPRO32.DLL"
fixme:ole:DllRegisterServer stub

```

I don't want to have to create a Windows partition just for this.  Any input would be greatly appreciated.

---

### Post by VincenzoAMD64 on 2007-11-19
Hi,
I am also interested to use the application with my K700,
I tried to install using wine and I got the same problem,
now I am investigating the possibility to use VirtualBox and Bluetooth.

Bye
Vincenzo

---

### Post by loell on 2007-11-19
the problem is, the windows application that runs in wine can not access bluetooth or the data cable. this is still not possible at this time.

you can however use obexftp and/or obexfs and wammu to browse your phone natively.

---

### Post by svtfmook on 2007-11-19
i don't think that wine can access usb.  have you tried vmware or vbox?

---

### Post by Folvarok on 2008-04-30
I write script that install MyPhoneExplorer uisng Wine: :)

```
#!/bin/bash
export WINEPREFIX=${HOME}/.myphoneexplorer
# Create the myphoneexplorer wine drive
if [ ! -d ${WINEPREFIX} ]; then
   echo --- Creating WINE prefix ${WINEPREFIX}...
   wineprefixcreate > myphoneexplorer.log 2>&1
fi
if [ ! -f "MyPhoneExplorer_wine.zip" ]; then
	echo ---  download http://www.fjsoft.at/files/MyPhoneExplorer_wine.zip...
	wget "http://www.fjsoft.at/files/MyPhoneExplorer_wine.zip"
fi
echo --- Download VB6 runtimes
if [ ! -f "vbrun60sp6.exe" ]; then
	wget "http://download.microsoft.com/download/5/a/d/5ad868a0-8ecd-4bb0-a882-fe53eb7ef348/VB6.0-KB290887-X86.exe"
	rm VB6.0-KB290887-X86.exe
	cabextract -F vbrun60sp6.exe VB6.0-KB290887-X86.exe vbrun60sp6.exe
fi
echo -e REGEDIT4\\n\\n[HKEY_CURRENT_USER\\Software\\Wine\\DllOverrides]\\n\"asycfilt\"=\"native\"\\n\"comcat\"=\"native\"\\n\"msvbvm60\"=\"native\"\\n\"oleaut32\"=\"native\"\\n\"oleaut32\"=\"native\"\\n\"olepro32\"=\"native\"\\n\"stdole2.tlb\"=\"native\"\\n[HKEY_CURRENT_USER\\Software\\MyPhoneExplorer]\\n\"Language\"=\"English.lng\" > temp.reg
wine regedit temp.reg
mv ${WINEPREFIX}/drive_c/windows/system32/oleaut32.dll ${WINEPREFIX}/drive_c/windows/system32/oleaut32-alt.dll
mv ${WINEPREFIX}/drive_c/windows/system32/olepro32.dll ${WINEPREFIX}/drive_c/windows/system32/olepro32-alt.dll
wine vbrun60sp6.exe /Q >> myphoneexplorer.log 2>&1
unzip -q MyPhoneExplorer_wine.zip -d ${WINEPREFIX}/drive_c
wine regsvr32 c:/MyPhoneExplorer/DLL/ccrpDtp6.ocx
wine regsvr32 c:/MyPhoneExplorer/DLL/ccrpUCW6.dll
wine regsvr32 c:/MyPhoneExplorer/DLL/ShellMgr.dll
wine regsvr32 c:/MyPhoneExplorer/DLL/SSubTmr6.dll
wine regsvr32 c:/MyPhoneExplorer/DLL/vbalExpBar6.ocx
wine regsvr32 c:/MyPhoneExplorer/DLL/vbalIml6.ocx
wine regsvr32 c:/MyPhoneExplorer/DLL/vbalSGrid6.ocx
ln -is /dev/ttyACM0 ${WINEPREFIX}/dosdevices/com1
ln -is /dev/rfcomm0 ${WINEPREFIX}/dosdevices/com2
sudo chmod 777 ${WINEPREFIX}/dosdevices/com1 ${WINEPREFIX}/dosdevices/com2
#Desktop Icon...
echo -e [Desktop Entry]\\nEncoding=UTF-8\\nType=Application\\nTerminal=false\\nName[ru_RU]=My Phone Explorer\\nExec=env WINEPREFIX=${WINEPREFIX} wine c:/MyPhoneExplorer/MyPhoneExplorer.exe\\nName=My Phone Explorer\\nIcon=20e3_myphoneexplorer.0 > ~/Desktop/MyPhoneExplorer
chmod 777 ~/Desktop/MyPhoneExplorer

```

---

### Post by Duranxl on 2008-07-17
> **Folvarok said:**
> I write script that install MyPhoneExplorer uisng Wine: :)

```
#!/bin/bash
export WINEPREFIX=${HOME}/.myphoneexplorer
# Create the myphoneexplorer wine drive
if [ ! -d ${WINEPREFIX} ]; then
   echo --- Creating WINE prefix ${WINEPREFIX}...
   wineprefixcreate > myphoneexplorer.log 2>&1
fi
if [ ! -f "MyPhoneExplorer_wine.zip" ]; then
	echo ---  download http://www.fjsoft.at/files/MyPhoneExplorer_wine.zip...
	wget "http://www.fjsoft.at/files/MyPhoneExplorer_wine.zip"
fi
echo --- Download VB6 runtimes
if [ ! -f "vbrun60sp6.exe" ]; then
	wget "http://download.microsoft.com/download/5/a/d/5ad868a0-8ecd-4bb0-a882-fe53eb7ef348/VB6.0-KB290887-X86.exe"
	rm VB6.0-KB290887-X86.exe
	cabextract -F vbrun60sp6.exe VB6.0-KB290887-X86.exe vbrun60sp6.exe
fi
echo -e REGEDIT4\\n\\n[HKEY_CURRENT_USER\\Software\\Wine\\DllOverrides]\\n\"asycfilt\"=\"native\"\\n\"comcat\"=\"native\"\\n\"msvbvm60\"=\"native\"\\n\"oleaut32\"=\"native\"\\n\"oleaut32\"=\"native\"\\n\"olepro32\"=\"native\"\\n\"stdole2.tlb\"=\"native\"\\n[HKEY_CURRENT_USER\\Software\\MyPhoneExplorer]\\n\"Language\"=\"English.lng\" > temp.reg
wine regedit temp.reg
mv ${WINEPREFIX}/drive_c/windows/system32/oleaut32.dll ${WINEPREFIX}/drive_c/windows/system32/oleaut32-alt.dll
mv ${WINEPREFIX}/drive_c/windows/system32/olepro32.dll ${WINEPREFIX}/drive_c/windows/system32/olepro32-alt.dll
wine vbrun60sp6.exe /Q >> myphoneexplorer.log 2>&1
unzip -q MyPhoneExplorer_wine.zip -d ${WINEPREFIX}/drive_c
wine regsvr32 c:/MyPhoneExplorer/DLL/ccrpDtp6.ocx
wine regsvr32 c:/MyPhoneExplorer/DLL/ccrpUCW6.dll
wine regsvr32 c:/MyPhoneExplorer/DLL/ShellMgr.dll
wine regsvr32 c:/MyPhoneExplorer/DLL/SSubTmr6.dll
wine regsvr32 c:/MyPhoneExplorer/DLL/vbalExpBar6.ocx
wine regsvr32 c:/MyPhoneExplorer/DLL/vbalIml6.ocx
wine regsvr32 c:/MyPhoneExplorer/DLL/vbalSGrid6.ocx
ln -is /dev/ttyACM0 ${WINEPREFIX}/dosdevices/com1
ln -is /dev/rfcomm0 ${WINEPREFIX}/dosdevices/com2
sudo chmod 777 ${WINEPREFIX}/dosdevices/com1 ${WINEPREFIX}/dosdevices/com2
#Desktop Icon...
echo -e [Desktop Entry]\\nEncoding=UTF-8\\nType=Application\\nTerminal=false\\nName[ru_RU]=My Phone Explorer\\nExec=env WINEPREFIX=${WINEPREFIX} wine c:/MyPhoneExplorer/MyPhoneExplorer.exe\\nName=My Phone Explorer\\nIcon=20e3_myphoneexplorer.0 > ~/Desktop/MyPhoneExplorer
chmod 777 ~/Desktop/MyPhoneExplorer

```

```
17:24:09 (239.78 KB/s) - `VB6.0-KB290887-X86.exe' saved [1064736/1064736]

VB6.0-KB290887-X86.exe: No such file or directory
vbrun60sp6.exe: No such file or directory

All done, errors in processing 2 file(s)
mv: cannot stat `/home/wp/.myphoneexplorer/drive_c/windows/system32/oleaut32.dll': No such file or directory
mv: cannot stat `/home/wp/.myphoneexplorer/drive_c/windows/system32/olepro32.dll': No such file or directory


```
I can't install it.
Same goes for the .sh found on the fjsoft forums, I can't install the VB package.

---

