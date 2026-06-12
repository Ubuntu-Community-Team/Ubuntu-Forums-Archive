---
title: "Shockwave crashes Firefox...?"
date: 2008-06-13
forum: Wine
---

### Post by Jesdisciple on 2008-06-13
In my quest to get Shockwave working, I started with Google which led me to [http://www.ubuntux.org/shockwave-player-ubuntu-linux]("http://www.ubuntux.org/shockwave-player-ubuntu-linux").  But then Shockwave just stared at me...  [http://www.ubuntux.org/shockwave-on-wine]("http://www.ubuntux.org/shockwave-on-wine")  So I tried Google again and found [https://help.ubuntu.com/community/Shockwave]("https://help.ubuntu.com/community/Shockwave").  Now Shockwave works so hard that Firefox crashes.

Help, please!

---

### Post by cogadh on 2008-06-13
Post the terminal output from Wine when Firefox crashes.

---

### Post by Jesdisciple on 2008-06-13
When I opened Firefox, it first opened "my windows and tabs from last time" which included Gmail and maybe another tab.  I only kept the Gmail tab and sent it to [https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave) where I clicked the link to Adobe's Shockwave test.  Firefox's window turned gray and the talkback window did its thing.  I pressed both X's and had to click the Force Quit button for Firefox.```
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dcdf9e8, overlapped 0x7dcdf9cc): stub
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0xb463dc)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:system:SetProcessDPIAware stub!
fixme:bidi:mirror stub: mirroring of characters not yet implemented
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject no class object {591209c7-767b-42b2-9fba-44ee4615f2c7} could be created for context 0x3
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:imm:ImmReleaseContext (0x5003c, 0x138be0): stub
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:secur32:schan_FreeCredentialsHandle (0x3de5a08): stub
fixme:system:SystemParametersInfoW Unknown action: 108
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:secur32:schan_FreeCredentialsHandle (0x292c970): stub
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {1f3cb77d-d339-49e0-b8e4-fecd6d6f8cb8} could be created for context 0x15
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side compressed DIB copy
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
wine: Call from 0x7b840fc8 to unimplemented function gdiplus.dll.GdipAddPathRectangleI, aborting
wine: Unimplemented function gdiplus.dll.GdipAddPathRectangleI called at address 0x7b840fc8 (thread 0009), starting debugger...
Unhandled exception: unimplemented function gdiplus.dll.GdipAddPathRectangleI called in 32-bit code (0x7b841042).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b841042 ESP:0033b810 EBP:0033b874 EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82c171 EBX:7b8ac8a0 ECX:00000000 EDX:0033b88c
 ESI:0033b88c EDI:00000015
Stack dump:
0x0033b810:  0033b88c 00000008 7bc330af 80000100
0x0033b820:  00000001 00000000 7b840fc8 00000002
0x0033b830:  7c9725e0 7c972780 0033b8f8 00000015
0x0033b840:  0033b860 7c97120f 00000018 0000000a
0x0033b850:  0000002c 03fb3900 00000000 00110000
0x0033b860:  03f00000 7c97a224 7b840fd2 0000003b
Backtrace:
=>1 0x7b841042 RaiseException+0x7a() in kernel32 (0x0033b874)
  2 0x7c972589 in gdiplus (+0x12589) (0x0033b894)
  3 0x7c961610 in gdiplus (+0x1610) (0x00000072)
  4 0x00000000 (0x00000000)
0x7b841042 RaiseException+0x7a in kernel32: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (194 modules)
PE        3a0000-  3c5000       Deferred        fullsoft
PE        3d0000-  3f6000       Deferred        metrics
PE        400000-  b64000       Deferred        firefox
PE       1830000- 1889000       Deferred        googletoolbar
PE       2c70000- 2c7e000       Deferred        macromix.x32
PE       2c80000- 2c88000       Deferred        sun au import export.x32
PE       2ca0000- 2cb4000       Deferred        realmedia asset.x32
PE       2cd0000- 2d19000       Deferred        plugin
PE       2f00000- 2f14000       Deferred        mix services.x32
PE       5ae0000- 5aed000       Deferred        sound control.x32
PE       6660000- 6682000       Deferred        png import export.x32
PE       6690000- 675c000       Deferred        textxtra.x32
PE       6760000- 67f5000       Deferred        havok.x32
PE       6a10000- 6a37000       Deferred        xmlparser.x32
PE       6a40000- 6da5000       Deferred        flash asset.x32
PE       6db0000- 6dc4000       Deferred        dvd asset.x32
PE       6dd0000- 6de3000       Deferred        sound import export.x32
PE       6df0000- 6e35000       Deferred        font xtra.x32
PE       6e50000- 6e5a000       Deferred        animated gif asset.x32
PE       6e60000- 6e6e000       Deferred        swastrm.x32
PE       6e70000- 6e81000       Deferred        cursor asset.x32
PE       6e90000- 6ea6000       Deferred        bitmapfilters.x32
PE       6eb0000- 6ecf000       Deferred        qt6asset.x32
PE       6ed0000- 6ee4000       Deferred        windows media asset.x32
PE       6f00000- 6f09000       Deferred        targa import export.x32
PE       6f10000- 6f1a000       Deferred        swa import export.x32
PE       6f20000- 6f37000       Deferred        text asset.x32
PE       6f40000- 71b2000       Deferred        dynamiks.x32
PE       71c0000- 71d0000       Deferred        font asset.x32
PE       71d0000- 71e2000       Deferred        mpeg 3 import export.x32
PE       71f0000- 7217000       Deferred        tiff import export.x32
PE       7220000- 7242000       Deferred        shockwave updater.x32
PE       7250000- 7258000       Deferred        directsound.x32
PE       7270000- 727d000       Deferred        netfile.x32
PE       7280000- 7287000       Deferred        cbrowser.x32
PE      10000000-10006000       Deferred        qfaservices
PE      30000000-30396000       Deferred        npswf32
PE      60010000-60022000       Deferred        jar50
PE      60030000-6003f000       Deferred        jsd3250
PE      60040000-6004a000       Deferred        myspell
PE      60050000-6005e000       Deferred        spellchk
PE      60090000-600c1000       Deferred        freebl3
PE      600d0000-60142000       Deferred        js3250
PE      601a0000-601c7000       Deferred        nspr4
PE      601d0000-6022b000       Deferred        nss3
PE      60230000-60272000       Deferred        nssckbi
PE      60280000-60287000       Deferred        plc4
PE      60290000-60296000       Deferred        plds4
PE      602b0000-602ca000       Deferred        smime3
PE      602d0000-6030f000       Deferred        softokn3
PE      60310000-60330000       Deferred        ssl3
PE      60330000-60336000       Deferred        xpcom
PE      60340000-60354000       Deferred        xpcom_compat
PE      60360000-603ca000       Deferred        xpcom_core
PE      68000000-681ba000       Deferred        dirapi
PE      69000000-690eb000       Deferred        iml32
PE      6a000000-6a012000       Deferred        swadcmpr.x32
PE      6c000000-6c01d000       Deferred        np32dsw
PE      6c100000-6c117000       Deferred        swmenu
PE      7a100000-7a28e000       Deferred        shockwave 3d asset.x32
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7c662000-7c6aa000       Deferred        dbghelp<elf>
  \-PE  7c670000-7c6aa000       \               dbghelp
ELF     7c7d2000-7c81c000       Deferred        dsound<elf>
  \-PE  7c7e0000-7c81c000       \               dsound
ELF     7c81c000-7c91c000       Deferred        wined3d<elf>
  \-PE  7c830000-7c91c000       \               wined3d
ELF     7c91c000-7c94c000       Deferred        d3d9<elf>
  \-PE  7c920000-7c94c000       \               d3d9
ELF     7c94c000-7c980000       Export          gdiplus<elf>
  \-PE  7c960000-7c980000       \               gdiplus
ELF     7ce4e000-7ce6e000       Deferred        mlang<elf>
  \-PE  7ce50000-7ce6e000       \               mlang
ELF     7ce78000-7ce83000       Deferred        libgcc_s.so.1
ELF     7ce92000-7cefa000       Deferred        crypt32<elf>
  \-PE  7cea0000-7cefa000       \               crypt32
ELF     7cf14000-7cf39000       Deferred        netapi32<elf>
  \-PE  7cf20000-7cf39000       \               netapi32
ELF     7cf39000-7cf5f000       Deferred        secur32<elf>
  \-PE  7cf40000-7cf5f000       \               secur32
ELF     7d186000-7d19b000       Deferred        psapi<elf>
  \-PE  7d190000-7d19b000       \               psapi
ELF     7d6fd000-7d710000       Deferred        msimg32<elf>
  \-PE  7d700000-7d710000       \               msimg32
ELF     7d710000-7d730000       Deferred        cabinet<elf>
  \-PE  7d720000-7d730000       \               cabinet
ELF     7d730000-7d76e000       Deferred        urlmon<elf>
  \-PE  7d740000-7d76e000       \               urlmon
ELF     7d76e000-7d813000       Deferred        msi<elf>
  \-PE  7d780000-7d813000       \               msi
ELF     7d813000-7d834000       Deferred        mpr<elf>
  \-PE  7d820000-7d834000       \               mpr
ELF     7d834000-7d881000       Deferred        wininet<elf>
  \-PE  7d840000-7d881000       \               wininet
ELF     7d881000-7d887000       Deferred        libnss_dns.so.2
ELF     7daa9000-7dabf000       Deferred        msimtf<elf>
  \-PE  7dab0000-7dabf000       \               msimtf
ELF     7df03000-7df22000       Deferred        imm32<elf>
  \-PE  7df10000-7df22000       \               imm32
ELF     7df22000-7df73000       Deferred        libgcrypt.so.11
ELF     7df73000-7df77000       Deferred        libgpg-error.so.0
ELF     7df77000-7df87000       Deferred        libtasn1.so.3
ELF     7df87000-7df8f000       Deferred        libkrb5support.so.0
ELF     7df8f000-7dfbd000       Deferred        libcrypt.so.1
ELF     7dfbd000-7e02d000       Deferred        libgnutls.so.13
ELF     7e02d000-7e052000       Deferred        libk5crypto.so.3
ELF     7e052000-7e0da000       Deferred        libkrb5.so.3
ELF     7e0da000-7e103000       Deferred        libgssapi_krb5.so.2
ELF     7e103000-7e138000       Deferred        libcups.so.2
ELF     7e18b000-7e1bd000       Deferred        uxtheme<elf>
  \-PE  7e190000-7e1bd000       \               uxtheme
ELF     7e1bd000-7e1d1000       Deferred        midimap<elf>
  \-PE  7e1c0000-7e1d1000       \               midimap
ELF     7e1d1000-7e1f7000       Deferred        msacm32<elf>
  \-PE  7e1e0000-7e1f7000       \               msacm32
ELF     7e1f7000-7e20e000       Deferred        msacm32<elf>
  \-PE  7e200000-7e20e000       \               msacm32
ELF     7e20e000-7e2d4000       Deferred        libasound.so.2
ELF     7e2de000-7e313000       Deferred        winealsa<elf>
  \-PE  7e2f0000-7e313000       \               winealsa
ELF     7e313000-7e31c000       Deferred        libxcursor.so.1
ELF     7e31c000-7e321000       Deferred        libxfixes.so.3
ELF     7e321000-7e324000       Deferred        libxcomposite.so.1
ELF     7e324000-7e32a000       Deferred        libxrandr.so.2
ELF     7e32a000-7e332000       Deferred        libxrender.so.1
ELF     7e332000-7e337000       Deferred        libxdmcp.so.6
ELF     7e337000-7e33a000       Deferred        libxau.so.6
ELF     7e33a000-7e42b000       Deferred        libx11.so.6
ELF     7e42b000-7e439000       Deferred        libxext.so.6
ELF     7e439000-7e43e000       Deferred        libxxf86vm.so.1
ELF     7e43e000-7e456000       Deferred        libice.so.6
ELF     7e456000-7e45e000       Deferred        libsm.so.6
ELF     7e45e000-7e461000       Deferred        libnss_mdns4_minimal.so.2
ELF     7e461000-7e463000       Deferred        libkeyutils.so.1
ELF     7e463000-7e466000       Deferred        libcom_err.so.2
ELF     7e468000-7e4f6000       Deferred        winex11<elf>
  \-PE  7e480000-7e4f6000       \               winex11
ELF     7e555000-7e575000       Deferred        libexpat.so.1
ELF     7e575000-7e5a0000       Deferred        libfontconfig.so.1
ELF     7e5a0000-7e5b5000       Deferred        libz.so.1
ELF     7e5b5000-7e625000       Deferred        libfreetype.so.6
ELF     7e625000-7e6c6000       Deferred        oleaut32<elf>
  \-PE  7e630000-7e6c6000       \               oleaut32
ELF     7e6c6000-7e6fc000       Deferred        winspool<elf>
  \-PE  7e6d0000-7e6fc000       \               winspool
ELF     7e6fc000-7e7a4000       Deferred        comdlg32<elf>
  \-PE  7e700000-7e7a4000       \               comdlg32
ELF     7e7a4000-7e7b8000       Deferred        lz32<elf>
  \-PE  7e7b0000-7e7b8000       \               lz32
ELF     7e7b8000-7e7d1000       Deferred        version<elf>
  \-PE  7e7c0000-7e7d1000       \               version
ELF     7e7d1000-7e82f000       Deferred        rpcrt4<elf>
  \-PE  7e7e0000-7e82f000       \               rpcrt4
ELF     7e82f000-7e8cf000       Deferred        ole32<elf>
  \-PE  7e840000-7e8cf000       \               ole32
ELF     7e8cf000-7e98e000       Deferred        comctl32<elf>
  \-PE  7e8e0000-7e98e000       \               comctl32
ELF     7e98e000-7e9e5000       Deferred        shlwapi<elf>
  \-PE  7e9a0000-7e9e5000       \               shlwapi
ELF     7e9e5000-7eaed000       Deferred        shell32<elf>
  \-PE  7e9f0000-7eaed000       \               shell32
ELF     7eaed000-7eb52000       Deferred        msvcrt<elf>
  \-PE  7eb00000-7eb52000       \               msvcrt
ELF     7eb52000-7ebeb000       Deferred        gdi32<elf>
  \-PE  7eb60000-7ebeb000       \               gdi32
ELF     7ebeb000-7ed2b000       Deferred        user32<elf>
  \-PE  7ec00000-7ed2b000       \               user32
ELF     7ed2b000-7edb7000       Deferred        winmm<elf>
  \-PE  7ed40000-7edb7000       \               winmm
ELF     7edb7000-7edca000       Deferred        libresolv.so.2
ELF     7edd4000-7edf2000       Deferred        iphlpapi<elf>
  \-PE  7ede0000-7edf2000       \               iphlpapi
ELF     7edf2000-7ee1d000       Deferred        ws2_32<elf>
  \-PE  7ee00000-7ee1d000       \               ws2_32
ELF     7ee1d000-7ee36000       Deferred        wsock32<elf>
  \-PE  7ee20000-7ee36000       \               wsock32
ELF     7ee36000-7ee85000       Deferred        advapi32<elf>
  \-PE  7ee40000-7ee85000       \               advapi32
ELF     7efa4000-7efaf000       Deferred        libnss_files.so.2
ELF     7efaf000-7efb9000       Deferred        libnss_nis.so.2
ELF     7efb9000-7efd1000       Deferred        libnsl.so.1
ELF     7efd1000-7eff6000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c89000-b7c8d000       Deferred        libdl.so.2
ELF     b7c8d000-b7dd7000       Deferred        libc.so.6
ELF     b7dd8000-b7df0000       Deferred        libpthread.so.0
ELF     b7dfa000-b7f0e000       Deferred        libwine.so.1
ELF     b7f10000-b7f2c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Mozilla Firefox\firefox.exe
        0000002d    0
        0000002c    0
        0000002b    0
        00000029   15
        00000026    0
        00000025    0
        00000024    0
        00000023    0
        00000022    0
        00000021    0
        00000020    0
        0000001f    0
        0000001e    0
        0000001d    0
        0000001c    0
        0000001b    0
        0000001a    0
        00000009    0 <==
0000000c 
        00000016    0
        0000000e    0
        0000000d    0
00000012 
        00000015    0
        00000014    0
        00000013    0
00000017 
        00000019    0
        00000018    0
00000030 
        00000031    0
Backtrace:
=>1 0x7b841042 RaiseException+0x7a() in kernel32 (0x0033b874)
  2 0x7c972589 in gdiplus (+0x12589) (0x0033b894)
  3 0x7c961610 in gdiplus (+0x1610) (0x00000072)
  4 0x00000000 (0x00000000)
wine: Call from 0x7b840fc8 to unimplemented function gdiplus.dll.GdipAddPathRectangles, aborting
Killed
```

---

### Post by cogadh on 2008-06-13
The first thing you need to do is install the winbind package:
```
sudo apt-get install windbind
```
The second thing is get a copy of gdiplus.dll from a Windows machine, copy it into Wine's system32 directory and apply a library override for it. After you fix those two thing, re-run it from the terminal again. It may still crash, but a bunch of those errors should go away, which may make the actual cause of the problem more apparent. If it does still crash, post the output again.

---

### Post by Jesdisciple on 2008-06-13
I got all of that done except the library override...  Is there a howto for that somewhere?

EDIT: Or so I thought...```
$ sudo apt-get install windbind
[sudo] password for chris:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package windbind
```EDIT: Oh, 'winbind' not 'windbind'...  That worked.  :)  I also got the library overridden.  Now Adobe's test works but I still can't use Shockwave...  I just get a big gray box and applets ask me to download a file with a weird name - from my cache...?

EDIT:  OK, this is really weird...  My above successes are occurring in native Firefox while Wine's Firefox still gets "Adobe Shockwave Player is now installing," but the directions posted at [https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave) for Wine are accomplishing the successes in native Firefox.

EDIT: I've managed to get the applets to open in their own small windows, but the fix posted at help.ubuntu.com isn't fixing that.  Help!
Thanks!

---

### Post by cogadh on 2008-06-13
Whoops, sorry about that typo.

If you've got it to the point where they are opening in their own window but killing all running Wine processes isn't fixing it, then you are probably running into the second possible cause of that problem:
> **Cause 2:** mozplugger does not handle multiple objects. Unfortunately, there is no fix currently known for this.

---

### Post by Jesdisciple on 2008-06-13
If the problem is with multiple objects, how can I only run one object?

Can I not still try to get Wine's Firefox working if the native Firefox can't handle it?

---

### Post by cogadh on 2008-06-13
For sites that have multiple objects on a single page, I would assume that the only way you might get it to work is by using the Windows version of Firefox directly, instead of using mozplugger. What happens when you try to just use Firefox through Wine? Don't go directly to a Shockwave site, go someplace simple, like Google.

---

### Post by Jesdisciple on 2008-06-13
Firefox's basic functionality works fine on Wine, even on pages with Shockwave objects.  The reason that native Firefox took the above fixes seems to be that Shockwave found the native installation of Firefox rather than the Wine one - so the native is hiding the other (probably because I tried to install Shockwave directly to the native, i.e. without saving the installer, at the very first).  How can I get around the native?

EDIT: I thought about it a bit, and the counterpart of Wine for the native would be Ubuntu itself.  So I restarted my computer to try that fix, and it kind of worked.  Now I get the 'loading' animation in the main Shockwave object but that animation never leaves...  Then I get the same animation in a small window, but that one actually proceeds to execute a program.  How can I get past the 'loading' animation in the main object?

---

### Post by cogadh on 2008-06-13
Honestly, you've completely lost me at this point. The whole purpose of mozplugger is to do exactly what you are trying to do: use the native Firefox for browsing, but automatically run the Windows version through Wine when you encounter Shockwave content. As long as you have followed the instructions on the Ubuntu Community docs page correctly, it should be working, though a bit clunky.

---

### Post by Jesdisciple on 2008-06-14
Oh, I thought mozplugger was only for the Wine Firefox, not a bridge between them...  So why can the Wine Firefox not play the objects?  I need to get around the limitations of mozplugger which would mean not using the native Firefox, right?

---

