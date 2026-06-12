---
title: "Wine works steam works half life doesn't"
date: 2007-11-06
forum: Wine
---

### Post by mipstien on 2007-11-06
I searched and searched and coulnd' tfind anything about my problem.  i believe i know the cause but was wondering if there was a way to fix this without changing my current Wine compile.
here is the output that i get when running the command in terminal
```
 env WINEPREFIX="/home/mipstien/.wine" wine "C:\Program Files\Valve\Steam\steam.exe" -applaunch 70 -game ns
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 300, std (d/m/y): 4/11/2007, dlt (d/m/y): 11/03/2007
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Valve\Steam\bin\ *.mix
dir: C:\Program Files\Valve\Steam\bin\ *.asi
dir: C:\Program Files\Valve\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
fixme:shdocvw:ViewObject_SetAdvise (0x10d302b0)->(1 00000002 0x161c968)
fixme:shdocvw:PersistStreamInit_InitNew (0x10d302b0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10d302b0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10d302b0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0xf16e630)->(1 00000002 0x161c9d0)
fixme:shdocvw:PersistStreamInit_InitNew (0xf16e630)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xf16e630)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xf16e630)->(ffffffff)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x34c5cc,0x00000000), stub!
err:systray:delete_icon invalid tray icon ID specified: 1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x1124aa70)->(1 00000002 0x161e618)
fixme:shdocvw:PersistStreamInit_InitNew (0x1124aa70)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1124aa70)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1124aa70)->(ffffffff)
fixme:process:IsWow64Process (0xffffffff 0x3f6e88) stub!
wine: Unhandled page fault on read access to 0x0007681d at address 0x7ee4a410 (thread 003a), starting debugger...
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,171,2): stub!
Unhandled exception: page fault on read access to 0x0007681d in 32-bit code (0x7ee4a410).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ee4a410 ESP:0034fd30 EBP:0034fe08 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000001 ECX:7efffba0 EDX:0000b800
 ESI:00000001 EDI:7efffba0
Stack dump:
0x0034fd30:  00360011 00350000 b7ea4ff4 00000008
0x0034fd40:  0034fe08 0034fd58 00000001 00000000
0x0034fd50:  7efffba0 00000000 00200246 ffffe410
0x0034fd60:  0034fe08 00000000 7efffba0 b7e9a419
0x0034fd70:  00000000 00000000 00000000 00000000
0x0034fd80:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x7ee4a410 SetComputerNameExA+0x20() in kernel32 (0x0034fe08)
  2 0x7efc0749 server_init_process_done+0xb9() in ntdll (0x0034fea8)
  3 0x7efa5b2c LdrInitializeThunk+0xdc() in ntdll (0x0034ff08)
  4 0x7ee85f2a in kernel32 (+0x55f2a) (0x0034ffe8)
  5 0xb7ec29d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7ee4a410 SetComputerNameExA+0x20 in kernel32: testb   $0x8,0x7681c(%ebx)
Modules:
Module  Address                 Debug info      Name (16 modules)
PE       1400000- 3516000       Deferred        hl
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7eca9000-7ecb4000       Deferred        libnss_files.so.2
ELF     7ecb4000-7ecbe000       Deferred        libnss_nis.so.2
ELF     7ecbe000-7ecd6000       Deferred        libnsl.so.1
ELF     7ecd6000-7ecdf000       Deferred        libnss_compat.so.2
ELF     7ee11000-7ef3a000       Export          kernel32<elf>
  \-PE  7ee30000-7ef3a000       \               kernel32
ELF     7ef3a000-7ef5f000       Deferred        libm.so.6
ELF     7ef5f000-7f000000       Export          ntdll<elf>
  \-PE  7ef70000-7f000000       \               ntdll
ELF     b7d41000-b7d45000       Deferred        libdl.so.2
ELF     b7d45000-b7e8f000       Deferred        libc.so.6
ELF     b7e90000-b7ea8000       Deferred        libpthread.so.0
ELF     b7ebb000-b7fcf000       Export          libwine.so.1
ELF     b7fd1000-b7fed000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000039 (D) C:\Program Files\Valve\Steam\SteamApps\mipstien\half-life\hl.exe
        0000003a    0 <==
0000000a 
        0000000b    0
00000008 
        00000038    0
        00000037    0
        00000036    0
        00000035    1
        00000033    0
        00000032    0
        00000031    1
        00000030    0
        0000002f    1
        0000002e    0
        0000002d    1
        0000002b    0
        0000002a    1
        00000027    0
        00000026    0
        00000025    0
        00000023    0
        00000022    1
        00000020    0
        0000001e   15
        0000001c    0
        0000001b   15
        0000001a   15
        00000019    0
        00000018    0
        00000017    0
        00000016    0
        00000015    0
        00000014    1
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        0000000c    0
        00000009    0
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,148,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,126,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,69,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,12,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30096,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1124aa70)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1124aa70)
fixme:shdocvw:OleObject_Close (0x1124aa70)->(1)

```

---

### Post by ScottKidder on 2008-01-24
Was this ever resolved, I'm having the same issues.

---

### Post by cmat on 2008-01-24
It's hard for me to tell from the terminal output. But what is the symptom of this error?

---

### Post by fatbuttlarry on 2008-02-08
I have similar issues. Output isn't very specific.  Here are the details for me:

Game loads up, I see gordon's face and "Options" and "Exit" at the bottom left, then the game closes.  If I force Direct3d with the properties >> launch options >> "-d3d", it works just fine (as fine as d3d can work).

OpenGL works amazing in Quake3 native, Quake3 wine, Quake2 wine, Compiz, GLXGears, but not in Half-Life, Counterstrike, or any hl1 related game.  I haven't tried HL2.

I have the latest Nvidia driver, v169.09.
kernel 2.6.22-14-generic
wine 0.9.54
Ubuntu 7.10 running the kubuntu-desktop.

```

    Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : legacy
```
^--- Fixed by removing the file (i couldn't find any help online)


And although sound works in wine, I get this also:

```
    ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 0
    ALSA lib ../../../src/pcm/pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default:0

```
^--- Sound test works ok, and error supresses when I uncheck audio.  Doesn't help make the game work.

Thanks for any assistance in this matter.  I'd be happy to set up an ssh account for anyone interested in connecting.

---

### Post by krylon on 2008-02-08
If you're trying to run a Source Engine based game with OpenGL, it won't work.  D3D only for those.

---

### Post by fatbuttlarry on 2008-02-08
> **krylon said:**
> If you're trying to run a Source Engine based game with OpenGL, it won't work.  D3D only for those.

Thanks for the info.

```
not in Half-Life, Counterstrike, or any hl1 related game. I haven't tried HL2.
```

For comparison, my brother also runs AMD64 Kubuntu and HL1 without these issues.  I've looked at lots of things, but can't pinpoint any major differences.

-Tres

---

