---
title: "Not another WoW in WINE thread..."
date: 2012-01-24
forum: Wine
---

### Post by Charlie: on 2012-01-24
Heya guys, new-ish user here.

I'm running Ubuntu 11.10 on it's own HDD, my other HDD has Windows 7 64-bit installed but caught a nasty virus, and is blocking anything from getting out past my modem.

Video Card is NVIDIA, GeForce 9800 GTX, and the NVIDIA Driver Version shown in NVIDIA X Server Settings is 173.14.30. Interesting is on the GPU 0 tab, I see Bus Type as PCI Express x16, and Bus ID as ?@?:?:?, PCI Device ID: Unknown, PCI Vendor ID: Unknown. Display Device is a VIZIO TV, using HDMI.

I've been struggling, trying to get WoW to run using WINE for the past 8 hours and can't seem to catch a break. I first got stuck when I tried to install the new NVIDIA drivers from their site, leading to headaches when I couldn't figure out how to get X to restart. 

Up to that point I had WoW running, but the screen was flickering every second or more, so I was trying to fix that.

Anyway, reinstalled Ubuntu 11.10 on my desktop.

Today I started again, leaving my drivers alone (as they came), and installing WINE, running wineconf, then installing WoW with the launcher from battle.net. It's having some issues. 

I run this:
```
wine "C:\Program Files\World of Warcraft\WoW.exe"
```And get an ERROR #132(0x85100084) Fatal Exception! From the WoW client.

Here is some of the terminal information:
```
fixme:process:GetLogicalProcessorInformation (0x426e370,0x426e970): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 10000
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x426e370,0x426e970): stub
fixme:process:GetLogicalProcessorInformation (0x426e370,0x426e970): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 10000
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x426e370,0x426e970): stub
fixme:process:GetLogicalProcessorInformation (0x426e370,0x426e970): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 10000
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
```It repeats in this cycle a dozen times, then spits this out:
```
wine: Unhandled page fault on read access to 0xffffffff at address 0x6bb486c5 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x6bb486c5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6bb486c5 ESP:0032edd4 EBP:00000001 EFLAGS:00210286(  R- --  I S - -P- )
 EAX:ffffffff EBX:00000000 ECX:7ca1f588 EDX:00000001
 ESI:7cba71a0 EDI:00000008
Stack dump:
0x0032edd4:  00000000 7ca1f588 7cba71a0 00000001
0x0032ede4:  7ebcd008 8000005c 682f4ff4 7ca1f588
0x0032edf4:  00000000 00000001 00000001 00000000
0x0032ee04:  7cba71a0 000000aa 7ca5165c 6bb48bb6
0x0032ee14:  00000000 7ca1f588 7cba71a0 00000001
0x0032ee24:  000183e8 00000001 00000001 00000000
Backtrace:
=>0 0x6bb486c5 in libglcore.so.1 (+0x5e86c5) (0x00000001)
0x6bb486c5: call    *%eax
Modules:
Module    Address            Debug info    Name (114 modules)
PE      400000- 10db000    Deferred        wow
ELF    68000000-68020000    Deferred        ld-linux.so.2
ELF    68020000-68162000    Dwarf           libwine.so.1
ELF    68162000-6817d000    Deferred        libpthread.so.0
ELF    6817d000-682f9000    Deferred        libc.so.6
ELF    682f9000-682fe000    Deferred        libdl.so.2
ELF    682fe000-68328000    Deferred        libm.so.6
ELF    68328000-68334000    Deferred        libnss_nis.so.2
ELF    68334000-68341000    Deferred        libnss_files.so.2
ELF    68341000-68481000    Deferred        user32<elf>
  \-PE    68350000-68481000    \               user32
ELF    68481000-6853c000    Deferred        gdi32<elf>
  \-PE    68490000-6853c000    \               gdi32
ELF    6853c000-6859c000    Deferred        advapi32<elf>
  \-PE    68550000-6859c000    \               advapi32
ELF    6859c000-685b5000    Deferred        version<elf>
  \-PE    685a0000-685b5000    \               version
ELF    685b5000-6866f000    Deferred        opengl32<elf>
  \-PE    685d0000-6866f000    \               opengl32
ELF    6866f000-68713000    Deferred        libgl.so.1
ELF    68713000-68719000    Deferred        libuuid.so.1
ELF    68719000-6871b000    Deferred        libnvidia-tls.so.1
ELF    6871b000-6872e000    Deferred        libxext.so.6
ELF    6872e000-68864000    Deferred        libx11.so.6
ELF    68864000-68883000    Deferred        libxcb.so.1
ELF    68883000-68887000    Deferred        libxau.so.6
ELF    68887000-6888e000    Deferred        libxdmcp.so.6
ELF    68890000-688c8000    Deferred        d3d9<elf>
  \-PE    688a0000-688c8000    \               d3d9
ELF    688c8000-689fb000    Deferred        wined3d<elf>
  \-PE    688d0000-689fb000    \               wined3d
ELF    689fb000-68a1d000    Deferred        imm32<elf>
  \-PE    68a00000-68a1d000    \               imm32
ELF    68a1d000-68a8b000    Deferred        wininet<elf>
  \-PE    68a30000-68a8b000    \               wininet
ELF    68a8b000-68aa0000    Deferred        libz.so.1
ELF    68aa0000-68ac6000    Deferred        mpr<elf>
  \-PE    68ab0000-68ac6000    \               mpr
ELF    68ac6000-68b30000    Deferred        shlwapi<elf>
  \-PE    68ad0000-68b30000    \               shlwapi
ELF    68b30000-68d46000    Deferred        shell32<elf>
  \-PE    68b40000-68d46000    \               shell32
ELF    68d46000-68e3d000    Deferred        comctl32<elf>
  \-PE    68d50000-68e3d000    \               comctl32
ELF    68e3d000-68e6f000    Deferred        ws2_32<elf>
  \-PE    68e40000-68e6f000    \               ws2_32
ELF    68e6f000-68e8b000    Deferred        dinput8<elf>
  \-PE    68e70000-68e8b000    \               dinput8
ELF    68e8b000-68f93000    Deferred        ole32<elf>
  \-PE    68ea0000-68f93000    \               ole32
ELF    68f93000-69009000    Deferred        rpcrt4<elf>
  \-PE    68fa0000-69009000    \               rpcrt4
ELF    69009000-69070000    Deferred        setupapi<elf>
  \-PE    69010000-69070000    \               setupapi
ELF    69070000-690aa000    Deferred        winspool<elf>
  \-PE    69080000-690aa000    \               winspool
ELF    690aa000-690bf000    Deferred        hid<elf>
  \-PE    690b0000-690bf000    \               hid
ELF    690bf000-69164000    Deferred        winmm<elf>
  \-PE    690d0000-69164000    \               winmm
ELF    69164000-6918c000    Deferred        msacm32<elf>
  \-PE    69170000-6918c000    \               msacm32
ELF    6918c000-691ab000    Deferred        libtinfo.so.5
ELF    691ab000-69242000    Deferred        libfreetype.so.6
ELF    69242000-692d4000    Deferred        winex11<elf>
  \-PE    69250000-692d4000    \               winex11
ELF    692d4000-692d8000    Deferred        libxinerama.so.1
ELF    692d8000-692de000    Deferred        libxxf86vm.so.1
ELF    692de000-692e7000    Deferred        libxrandr.so.2
ELF    692e7000-692eb000    Deferred        libxcomposite.so.1
ELF    692eb000-692f6000    Deferred        libxcursor.so.1
ELF    692f6000-692fc000    Deferred        libxfixes.so.3
ELF    692fc000-69330000    Deferred        uxtheme<elf>
  \-PE    69300000-69330000    \               uxtheme
ELF    69330000-6936e000    Deferred        libgssapi_krb5.so.2
ELF    6936e000-6941e000    Deferred        libgnutls.so.26
ELF    6941e000-6942c000    Deferred        libavahi-common.so.3
ELF    6942c000-6943f000    Deferred        libavahi-client.so.3
ELF    6943f000-69508000    Deferred        libkrb5.so.3
ELF    69508000-69531000    Deferred        libk5crypto.so.3
ELF    69531000-69535000    Deferred        libcom_err.so.2
ELF    69535000-6953e000    Deferred        libkrb5support.so.0
ELF    6953e000-69550000    Deferred        libtasn1.so.3
ELF    69550000-695d5000    Deferred        libgcrypt.so.11
ELF    695d5000-6961e000    Deferred        libdbus-1.so.3
ELF    6961e000-69635000    Deferred        libresolv.so.2
ELF    69635000-6963a000    Deferred        libgpg-error.so.0
ELF    6963a000-69643000    Deferred        librt.so.1
ELF    69643000-69647000    Deferred        libnss_mdns4_minimal.so.2
ELF    69647000-6964e000    Deferred        libnss_dns.so.2
ELF    6964e000-696ab000    Deferred        dbghelp<elf>
  \-PE    69660000-696ab000    \               dbghelp
ELF    696ab000-696bf000    Deferred        psapi<elf>
  \-PE    696b0000-696bf000    \               psapi
ELF    696bf000-6974c000    Deferred        msvcrt<elf>
  \-PE    696d0000-6974c000    \               msvcrt
ELF    6974c000-6976a000    Deferred        libgcc_s.so.1
ELF    6a6a1000-6a6ab000    Deferred        libnss_compat.so.2
ELF    6b560000-6c2a0000    Export          libglcore.so.1
ELF    6c55e000-6c569000    Deferred        libxrender.so.1
ELF    6ccda000-6ccf3000    Deferred        libnsl.so.1
ELF    6e9c4000-6e9ee000    Deferred        libexpat.so.1
ELF    73554000-73576000    Deferred        libncurses.so.5
ELF    750cc000-75101000    Deferred        libfontconfig.so.1
ELF    75686000-756a0000    Deferred        libice.so.6
ELF    75bde000-75c30000    Deferred        libcups.so.2
ELF    768e8000-768ec000    Deferred        libkeyutils.so.1
ELF    78207000-78210000    Deferred        libsm.so.6
ELF    78522000-78532000    Deferred        libxi.so.6
ELF    7b800000-7b9b7000    Deferred        kernel32<elf>
  \-PE    7b810000-7b9b7000    \               kernel32
ELF    7bc00000-7bcc3000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
    00000009    0 <==
0000000e services.exe
    0000001f    0
    0000001e    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001a    0
    00000019    0
    00000014    0
    00000013    0
0000001b plugplay.exe
    00000020    0
    0000001d    0
    0000001c    0
00000021 explorer.exe
    00000022    0
Backtrace:
=>0 0x6bb486c5 in libglcore.so.1 (+0x5e86c5) (0x00000001)
```Now I have no clue what to do, I didn't get these errors yesterday.
Here is the guide I followed for installation:
[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

I've read a dozen guides from all over the web regarding installing WoW on WINE, and am at a loss as far as where to go from here. Let me know if you need more information, please.

---

### Post by thatguruguy on 2012-01-24
Heya guy, here's the [Wine sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=313").

---

### Post by Charlie: on 2012-01-24
Thanks, I'll repost in the correct area.

---

### Post by ubudog on 2012-01-24
*Thread moved to the Wine subforum.*

Best,
ubudog

---

### Post by Charlie: on 2012-01-24
Heya guys, new-ish user here.

I'm running Ubuntu 11.10 on it's own HDD, my other HDD has Windows 7  64-bit installed but caught a nasty virus, and is blocking anything from  getting out past my modem.

Video Card is NVIDIA, GeForce 9800 GTX, and the NVIDIA Driver Version  shown in NVIDIA X Server Settings is 173.14.30. Interesting is on the  GPU 0 tab, I see Bus Type as PCI Express x16, and Bus ID as ?@?:?:?, PCI Device ID: Unknown, PCI Vendor ID: Unknown. Display Device is a VIZIO TV, using HDMI.

I've been struggling, trying to get WoW to run using WINE for the past 8  hours and can't seem to catch a break. I first got stuck when I tried  to install the new NVIDIA drivers from their site, leading to headaches  when I couldn't figure out how to get X to restart. 

Up to that point I had WoW running, but the screen was flickering every second or more, so I was trying to fix that.

Anyway, reinstalled Ubuntu 11.10 on my desktop.

Today I started again, leaving my drivers alone (as they came), and  installing WINE, running wineconf, then installing WoW with the launcher  from battle.net. It's having some issues. 

I run this:
```
wine "C:\Program Files\World of Warcraft\WoW.exe"
```And get an ERROR #132(0x85100084) Fatal Exception! From the WoW client.

Here is some of the terminal information:

```
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 10000
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x16fe370,0x16fe970): stub
fixme:process:GetLogicalProcessorInformation (0x16fe370,0x16fe970): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 10000
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x16fe370,0x16fe970): stub
fixme:process:GetLogicalProcessorInformation (0x16fe370,0x16fe970): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 10000
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x16fe370,0x16fe970): stub
fixme:process:GetLogicalProcessorInformation (0x16fe370,0x16fe970): stub
```It repeats in this cycle a dozen times, then spits this out:

```
wine: Unhandled page fault on read access to 0xffffffff at address 0x68cc76c5 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x68cc76c5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:68cc76c5 ESP:0032edd4 EBP:00000001 EFLAGS:00210286(  R- --  I S - -P- )
 EAX:ffffffff EBX:00000000 ECX:7d6cc588 EDX:00000001
 ESI:7d863328 EDI:00000008
Stack dump:
0x0032edd4:  00000000 7d6cc588 7d863328 00000001
0x0032ede4:  7ebcd008 8000005c 682d4ff4 7d6cc588
0x0032edf4:  00000000 00000001 00000001 00000000
0x0032ee04:  7d863328 000000a9 7d6fe65c 68cc7bb6
0x0032ee14:  00000000 7d6cc588 7d863328 00000001
0x0032ee24:  000153e8 00000001 00000001 00000000
Backtrace:
=>0 0x68cc76c5 in libglcore.so.1 (+0x5e86c5) (0x00000001)
0x68cc76c5: call    *%eax
Modules:
Module    Address            Debug info    Name (114 modules)
PE      400000- 10db000    Deferred        wow
ELF    68000000-68142000    Dwarf           libwine.so.1
ELF    68142000-6815d000    Deferred        libpthread.so.0
ELF    6815d000-682d9000    Deferred        libc.so.6
ELF    682d9000-682de000    Deferred        libdl.so.2
ELF    682de000-68308000    Deferred        libm.so.6
ELF    68308000-68312000    Deferred        libnss_compat.so.2
ELF    68312000-6832b000    Deferred        libnsl.so.1
ELF    6832b000-68337000    Deferred        libnss_nis.so.2
ELF    68337000-68344000    Deferred        libnss_files.so.2
ELF    68344000-68484000    Deferred        user32<elf>
  \-PE    68360000-68484000    \               user32
ELF    68484000-6853f000    Deferred        gdi32<elf>
  \-PE    68490000-6853f000    \               gdi32
ELF    6853f000-68558000    Deferred        version<elf>
  \-PE    68540000-68558000    \               version
ELF    68558000-68612000    Deferred        opengl32<elf>
  \-PE    68570000-68612000    \               opengl32
ELF    68612000-6861b000    Deferred        libsm.so.6
ELF    6861b000-686bf000    Deferred        libgl.so.1
ELF    686bf000-686d9000    Deferred        libice.so.6
ELF    686d9000-686df000    Deferred        libuuid.so.1
ELF    686df000-6941f000    Export          libglcore.so.1
ELF    6941f000-69421000    Deferred        libnvidia-tls.so.1
ELF    69421000-69557000    Deferred        libx11.so.6
ELF    69557000-69576000    Deferred        libxcb.so.1
ELF    69576000-6957a000    Deferred        libxau.so.6
ELF    6957a000-69581000    Deferred        libxdmcp.so.6
ELF    69583000-695bb000    Deferred        d3d9<elf>
  \-PE    69590000-695bb000    \               d3d9
ELF    695bb000-696ee000    Deferred        wined3d<elf>
  \-PE    695d0000-696ee000    \               wined3d
ELF    696ee000-69710000    Deferred        imm32<elf>
  \-PE    696f0000-69710000    \               imm32
ELF    69710000-69725000    Deferred        libz.so.1
ELF    69725000-6974b000    Deferred        mpr<elf>
  \-PE    69730000-6974b000    \               mpr
ELF    6974b000-697b5000    Deferred        shlwapi<elf>
  \-PE    69760000-697b5000    \               shlwapi
ELF    697b5000-699cb000    Deferred        shell32<elf>
  \-PE    697c0000-699cb000    \               shell32
ELF    699cb000-699fd000    Deferred        ws2_32<elf>
  \-PE    699d0000-699fd000    \               ws2_32
ELF    699fd000-69a19000    Deferred        dinput8<elf>
  \-PE    69a00000-69a19000    \               dinput8
ELF    69a19000-69a2e000    Deferred        hid<elf>
  \-PE    69a20000-69a2e000    \               hid
ELF    69a2e000-69a32000    Deferred        libxinerama.so.1
ELF    69a32000-69a38000    Deferred        libxxf86vm.so.1
ELF    69a38000-69a43000    Deferred        libxrender.so.1
ELF    69a43000-69a47000    Deferred        libxcomposite.so.1
ELF    69a47000-69a67000    Deferred        ld-linux.so.2
ELF    69a67000-69b5e000    Deferred        comctl32<elf>
  \-PE    69a70000-69b5e000    \               comctl32
ELF    69b5e000-69c66000    Deferred        ole32<elf>
  \-PE    69b70000-69c66000    \               ole32
ELF    69c66000-69ccd000    Deferred        setupapi<elf>
  \-PE    69c70000-69ccd000    \               setupapi
ELF    69ccd000-69d07000    Deferred        winspool<elf>
  \-PE    69cd0000-69d07000    \               winspool
ELF    69d07000-69dac000    Deferred        winmm<elf>
  \-PE    69d10000-69dac000    \               winmm
ELF    69dac000-69dce000    Deferred        libncurses.so.5
ELF    69dce000-69ded000    Deferred        libtinfo.so.5
ELF    69ded000-69e7f000    Deferred        winex11<elf>
  \-PE    69e00000-69e7f000    \               winex11
ELF    69e7f000-69e88000    Deferred        libxrandr.so.2
ELF    69e88000-69e98000    Deferred        libxi.so.6
ELF    69e98000-69ecd000    Deferred        libfontconfig.so.1
ELF    69ecd000-69ef7000    Deferred        libexpat.so.1
ELF    69ef7000-69f02000    Deferred        libxcursor.so.1
ELF    69f02000-69f08000    Deferred        libxfixes.so.3
ELF    69f08000-69f3c000    Deferred        uxtheme<elf>
  \-PE    69f10000-69f3c000    \               uxtheme
ELF    69f3c000-69f8e000    Deferred        libcups.so.2
ELF    69f8e000-69fcc000    Deferred        libgssapi_krb5.so.2
ELF    69fcc000-6a07c000    Deferred        libgnutls.so.26
ELF    6a07c000-6a08a000    Deferred        libavahi-common.so.3
ELF    6a08a000-6a09d000    Deferred        libavahi-client.so.3
ELF    6a09d000-6a0c6000    Deferred        libk5crypto.so.3
ELF    6a0c6000-6a0ca000    Deferred        libcom_err.so.2
ELF    6a0ca000-6a0d3000    Deferred        libkrb5support.so.0
ELF    6a0d3000-6a0e5000    Deferred        libtasn1.so.3
ELF    6a0e5000-6a16a000    Deferred        libgcrypt.so.11
ELF    6a16a000-6a1b3000    Deferred        libdbus-1.so.3
ELF    6a1b3000-6a1b7000    Deferred        libkeyutils.so.1
ELF    6a1b7000-6a1c0000    Deferred        librt.so.1
ELF    6a1c0000-6a1c4000    Deferred        libnss_mdns4_minimal.so.2
ELF    6a1c4000-6a1cb000    Deferred        libnss_dns.so.2
ELF    6a1cb000-6a258000    Deferred        msvcrt<elf>
  \-PE    6a1e0000-6a258000    \               msvcrt
ELF    6a258000-6a276000    Deferred        libgcc_s.so.1
ELF    6a4bd000-6a4d0000    Deferred        libxext.so.6
ELF    6bcf3000-6bd0a000    Deferred        libresolv.so.2
ELF    6e44c000-6e4c2000    Deferred        rpcrt4<elf>
  \-PE    6e460000-6e4c2000    \               rpcrt4
ELF    6ed34000-6ed94000    Deferred        advapi32<elf>
  \-PE    6ed40000-6ed94000    \               advapi32
ELF    6fed9000-6ff01000    Deferred        msacm32<elf>
  \-PE    6fee0000-6ff01000    \               msacm32
ELF    71798000-7179d000    Deferred        libgpg-error.so.0
ELF    73504000-73572000    Deferred        wininet<elf>
  \-PE    73510000-73572000    \               wininet
ELF    73d6e000-73e05000    Deferred        libfreetype.so.6
ELF    775a4000-7766d000    Deferred        libkrb5.so.3
ELF    77963000-77977000    Deferred        psapi<elf>
  \-PE    77970000-77977000    \               psapi
ELF    7b800000-7b9b7000    Deferred        kernel32<elf>
  \-PE    7b810000-7b9b7000    \               kernel32
ELF    7bc00000-7bcc3000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cddf000-7ce3c000    Deferred        dbghelp<elf>
  \-PE    7cdf0000-7ce3c000    \               dbghelp
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
    00000009    0 <==
0000000e services.exe
    0000001f    0
    0000001e    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001d    0
    0000001b    0
00000021 explorer.exe
    00000022    0
Backtrace:
=>0 0x68cc76c5 in libglcore.so.1 (+0x5e86c5) (0x00000001)
```Now I have no clue what to do, I didn't get these errors yesterday.
Here is the guide I followed for installation:
[http://www.wowwiki.com/World_of_Warc...nality_on_Wine]("http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine")

I've read a dozen guides from all over the web regarding installing WoW  on WINE, and am at a loss as far as where to go from here. Let me know  if you need more information, please.

---

### Post by Charlie: on 2012-01-24
Sorry ubu, posted this before I read your reply of 'moved' on the old thread. Feel free to delete one.

---

### Post by ubudog on 2012-01-24
> **Charlie: said:**
> Sorry ubu, posted this before I read your reply of 'moved' on the old thread. Feel free to delete one.

No worries, got it sorted.  :)

Btw, feel free to continue on this one.

---

### Post by Charlie: on 2012-01-24
Well, I feel dumb.

After reading[http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111)
I realized that I hadn't restarted after activating the current-version drivers with "Additional Drivers" in System.

sudo reboot, and I'm up and running. Still unsure why I had to go through all that unpleasant business yesterday but for now this is solved.

Thanks to ubudog for the forum help.

---

### Post by cwwilson721 on 2012-01-24
As a short (and not EXACT reason, but will do for the purposes of this thread) explanation:

After you install the Proprietary Drivers, thru whatever process, you are doing three things:
[LIST]
[*]Adding a module (driver) to the kernel. Since it is an addition, the kernel has no idea it is there, until the kerel is "re-read". A reboot acomplishes this. 
[*]A module is added to the x server. The xserver module cannot funtion without the kernel module.
[*]A few opengl specific "so" files are added for the graphics card/chip that you installed the drivers for. Some/most opengl functions would fail without these components. A "reboot" let's the kernel module, xserver, and thus WoW find everything.
[/LIST]
While there are ways to get around the 'reboot', for most users it is the easiest way.

So, if all else fails: Reboot. Might work.

---

### Post by Charlie: on 2012-01-25
Thanks, cwwilson721, for the clear explanation. It all makes much more sense to me now.

---

