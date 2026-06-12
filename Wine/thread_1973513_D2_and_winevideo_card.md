---
title: "D2 and wine/video card?"
date: 2012-05-04
forum: Wine
---

### Post by Sumisoul on 2012-05-04
So I've been trying to get Diablo II to work on my friend's laptop. But it just doesn't what to comply.
I installed the game to my own machine and it works fine. I transfered the files over and it doesn't work. I figure it's got to be the same reason that it didn't want to install in the first place.

I tried wine and it would install up to when it needed to switch disks. Sometimes not even that far.
I tried POL but it wouldn't even show the user agreement.

After transferring the files from my own machine, I tried to start the game. It seems like it might for just a second but it just so happened to crash. I suspect it might be the video card. If so, is there a way to work with it?

here's the terminal:
```
smokeymcpot@azuresmoke:~$ wine ~/.wine/dosdevices/c:/"program files"/"Diablo II"/"Diablo II.exe"
Warning: could not find DOS drive for current working directory '/home/smokeymcpot', starting in the Windows directory.
fixme:advapi:SetSecurityInfo stub
smokeymcpot@azuresmoke:~$ fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f090,0x00000000), stub!
smokeymcpot@azuresmoke:~$ fixme:d3d:swapchain_init The application requested more than one back buffer, this is not properly supported.
Please configure the application to use double buffering (1 back buffer) if possible.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1487f0,0x148750): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1487f0,0x148750): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1487f0,0x148750): stub
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x8 @0! (XRandR)
err:d3d:wined3d_unregister_window Window 0x60138 is not registered with wined3d.
smokeymcpot@azuresmoke:~$ err:mmtime:TIME_MMTimeStop Timer still active?!
wine: Unhandled page fault on read access to 0x00530e80 at address 0x6f9b7878 (thread 0029), starting debugger...
Unhandled exception: page fault on read access to 0x00530e80 in 32-bit code (0x6f9b7878).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:6f9b7878 ESP:0220ea44 EBP:00000000 EFLAGS:00210202(  R- --  I   - - - )
 EAX:00530e80 EBX:02210000 ECX:7edfc024 EDX:00530e80
 ESI:02210000 EDI:6f9b7800
Stack dump:
0x0220ea44:  6f9b7800 7ffc0f10 0220ea78 7bc9cff4
0x0220ea54:  00000000 00530e80 00000000 f74a6641
0x0220ea64:  00000000 00000000 7bc716e0 00000000
0x0220ea74:  7ffc0f10 0220eb48 7bc718b0 6f9b7800
0x0220ea84:  00000000 00000000 7bc4ad5e ffffffff
0x0220ea94:  7bc883e0 7b8370c0 7bc9cff4 7ffc0f10
Backtrace:
0x6f9b7878: movl    0x0(%edx),%ebx
Modules:
Module    Address            Debug info    Name (140 modules)
PE      340000-  354000    Deferred        d2lang
PE      400000-  410000    Deferred        game
PE     1710000- 1751000    Deferred        binkw32
PE     2220000- 222d000    Deferred        d2net
PE    10000000-1001a000    Deferred        smackw32
PE    60000000-6002e000    Deferred        ijl11
PE    6f8c0000-6f8d3000    Deferred        d2ddraw
PE    6f8e0000-6f9ae000    Deferred        d2win
PE    6f9b0000-6f9c9000    Export          d2sound
PE    6fa20000-6fa34000    Deferred        d2mcpclient
PE    6fa40000-6fa6d000    Deferred        d2launch
PE    6fa80000-6faa1000    Deferred        d2gfx
PE    6fbf0000-6fc50000    Deferred        storm
PE    6fe10000-6ff18000    Deferred        d2cmp
PE    6ff20000-6ff44000    Deferred        bnclient
PE    6ff50000-6ffac000    Deferred        fog
ELF    7b800000-7b97d000    Deferred        kernel32<elf>
  \-PE    7b810000-7b97d000    \               kernel32
ELF    7bc00000-7bcb9000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb9000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c0bf000-7c0de000    Deferred        libgcc_s.so.1
ELF    7c2de000-7c305000    Deferred        msacm32<elf>
  \-PE    7c2e0000-7c305000    \               msacm32
ELF    7c305000-7c31e000    Deferred        msacm32<elf>
  \-PE    7c310000-7c31e000    \               msacm32
ELF    7cb1f000-7cc1b000    Deferred        libvorbisenc.so.2
ELF    7cc1b000-7cc83000    Deferred        libsndfile.so.1
ELF    7cef1000-7cf1a000    Deferred        libvorbis.so.0
ELF    7d457000-7d4a4000    Deferred        libflac.so.8
ELF    7d4a4000-7d4ad000    Deferred        libwrap.so.0
ELF    7d4ad000-7d4bb000    Deferred        libxi.so.6
ELF    7d4bb000-7d506000    Deferred        libpulsecommon-0.9.21.so
ELF    7d506000-7d548000    Deferred        libpulse.so.0
ELF    7d687000-7d68e000    Deferred        libogg.so.0
ELF    7d68e000-7d694000    Deferred        libxtst.so.6
ELF    7d694000-7d75c000    Deferred        libasound.so.2
ELF    7d75c000-7d793000    Deferred        winealsa<elf>
  \-PE    7d770000-7d793000    \               winealsa
ELF    7d8c1000-7d8cb000    Deferred        libdrm_intel.so.1
ELF    7d8cb000-7db7f000    Deferred        i965_dri.so
ELF    7db7f000-7db8a000    Deferred        libdrm.so.2
ELF    7db8a000-7dbef000    Deferred        libgl.so.1
ELF    7dbef000-7dc05000    Deferred        midimap<elf>
  \-PE    7dbf0000-7dc05000    \               midimap
ELF    7dc05000-7dc0c000    Deferred        libasound_module_pcm_pulse.so
ELF    7dc0c000-7dd44000    Deferred        wined3d<elf>
  \-PE    7dc20000-7dd44000    \               wined3d
ELF    7dd44000-7dd9c000    Deferred        ddraw<elf>
  \-PE    7dd50000-7dd9c000    \               ddraw
ELF    7dd9c000-7ddf4000    Deferred        dbghelp<elf>
  \-PE    7ddb0000-7ddf4000    \               dbghelp
ELF    7ddf4000-7ddf9000    Deferred        libgpg-error.so.0
ELF    7ddf9000-7de02000    Deferred        librt.so.1
ELF    7de02000-7de3b000    Deferred        libdbus-1.so.3
ELF    7de3b000-7deae000    Deferred        libgcrypt.so.11
ELF    7deae000-7debf000    Deferred        libtasn1.so.3
ELF    7debf000-7dec3000    Deferred        libkeyutils.so.1
ELF    7dec3000-7decb000    Deferred        libkrb5support.so.0
ELF    7decb000-7deef000    Deferred        libk5crypto.so.3
ELF    7deef000-7dfa0000    Deferred        libkrb5.so.3
ELF    7dfa0000-7dfb1000    Deferred        libavahi-client.so.3
ELF    7dfb1000-7dfbd000    Deferred        libavahi-common.so.3
ELF    7dfbd000-7e058000    Deferred        libgnutls.so.26
ELF    7e058000-7e087000    Deferred        libgssapi_krb5.so.2
ELF    7e087000-7e0ce000    Deferred        libcups.so.2
ELF    7e0d1000-7e0d5000    Deferred        libxdamage.so.1
ELF    7e0d5000-7e0eb000    Deferred        psapi<elf>
  \-PE    7e0e0000-7e0eb000    \               psapi
ELF    7e11b000-7e11f000    Deferred        libcom_err.so.2
ELF    7e135000-7e169000    Deferred        uxtheme<elf>
  \-PE    7e140000-7e169000    \               uxtheme
ELF    7e169000-7e173000    Deferred        libxcursor.so.1
ELF    7e173000-7e179000    Deferred        libxfixes.so.3
ELF    7e179000-7e17d000    Deferred        libxcomposite.so.1
ELF    7e17d000-7e185000    Deferred        libxrandr.so.2
ELF    7e185000-7e18f000    Deferred        libxrender.so.1
ELF    7e18f000-7e195000    Deferred        libxxf86vm.so.1
ELF    7e195000-7e199000    Deferred        libxinerama.so.1
ELF    7e199000-7e1bb000    Deferred        imm32<elf>
  \-PE    7e1a0000-7e1bb000    \               imm32
ELF    7e1bb000-7e1c1000    Deferred        libxdmcp.so.6
ELF    7e1c1000-7e1c5000    Deferred        libxau.so.6
ELF    7e1c5000-7e1df000    Deferred        libxcb.so.1
ELF    7e1df000-7e1e4000    Deferred        libuuid.so.1
ELF    7e1e4000-7e301000    Deferred        libx11.so.6
ELF    7e301000-7e311000    Deferred        libxext.so.6
ELF    7e311000-7e32a000    Deferred        libice.so.6
ELF    7e32a000-7e333000    Deferred        libsm.so.6
ELF    7e350000-7e3f3000    Deferred        winex11<elf>
  \-PE    7e360000-7e3f3000    \               winex11
ELF    7e40e000-7e435000    Deferred        libexpat.so.1
ELF    7e435000-7e465000    Deferred        libfontconfig.so.1
ELF    7e465000-7e47a000    Deferred        libz.so.1
ELF    7e47a000-7e4f0000    Deferred        libfreetype.so.6
ELF    7e4f0000-7e565000    Deferred        rpcrt4<elf>
  \-PE    7e500000-7e565000    \               rpcrt4
ELF    7e565000-7e665000    Deferred        ole32<elf>
  \-PE    7e580000-7e665000    \               ole32
ELF    7e665000-7e6fa000    Deferred        winmm<elf>
  \-PE    7e670000-7e6fa000    \               winmm
ELF    7e6fa000-7e742000    Deferred        dsound<elf>
  \-PE    7e700000-7e742000    \               dsound
ELF    7e742000-7e756000    Deferred        libresolv.so.2
ELF    7e773000-7e794000    Deferred        iphlpapi<elf>
  \-PE    7e780000-7e794000    \               iphlpapi
ELF    7e794000-7e7c1000    Deferred        ws2_32<elf>
  \-PE    7e7a0000-7e7c1000    \               ws2_32
ELF    7e7c1000-7e7dc000    Deferred        wsock32<elf>
  \-PE    7e7d0000-7e7dc000    \               wsock32
ELF    7e7dc000-7e7f0000    Deferred        lz32<elf>
  \-PE    7e7e0000-7e7f0000    \               lz32
ELF    7e7f0000-7e828000    Deferred        winspool<elf>
  \-PE    7e800000-7e828000    \               winspool
ELF    7e828000-7e913000    Deferred        comctl32<elf>
  \-PE    7e830000-7e913000    \               comctl32
ELF    7e913000-7e975000    Deferred        shlwapi<elf>
  \-PE    7e920000-7e975000    \               shlwapi
ELF    7e975000-7eb4f000    Deferred        shell32<elf>
  \-PE    7e980000-7eb4f000    \               shell32
ELF    7eb4f000-7ec0d000    Deferred        comdlg32<elf>
  \-PE    7eb60000-7ec0d000    \               comdlg32
ELF    7ec0d000-7ec68000    Deferred        advapi32<elf>
  \-PE    7ec20000-7ec68000    \               advapi32
ELF    7ec68000-7ecf4000    Deferred        gdi32<elf>
  \-PE    7ec70000-7ecf4000    \               gdi32
ELF    7ecf4000-7ee25000    Deferred        user32<elf>
  \-PE    7ed10000-7ee25000    \               user32
ELF    7ee25000-7ee31000    Deferred        libnss_files.so.2
ELF    7ee31000-7ee3b000    Deferred        libnss_nis.so.2
ELF    7ee3b000-7ee43000    Deferred        libnss_compat.so.2
ELF    7ee47000-7ee60000    Deferred        version<elf>
  \-PE    7ee50000-7ee60000    \               version
ELF    7efbd000-7efe3000    Deferred        libm.so.6
ELF    7efe9000-7f000000    Deferred        libnsl.so.1
ELF    f7478000-f747c000    Deferred        libdl.so.2
ELF    f747c000-f75d5000    Deferred        libc.so.6
ELF    f75d6000-f75ef000    Deferred        libpthread.so.0
ELF    f760c000-f774c000    Deferred        libwine.so.1
ELF    f774e000-f776c000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 winecfg.exe
    00000009    0
0000000e services.exe
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
00000019 explorer.exe
    0000001a    0
0000001d (D) C:\Program Files\Diablo II\Game.exe
    00000029    0 <==
    00000028   15
    00000025    1
    00000024    0
    0000001e    0
Backtrace:


```I would really appreciate the help.
Sorry if the thread is redundant.
I looked around already.

---

