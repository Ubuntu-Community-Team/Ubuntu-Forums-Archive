---
title: "No Joystick in WINE -0.9.54"
date: 2008-02-01
forum: Wine
---

### Post by pm124493 on 2008-02-01
I installed WINE at version 0.9.52 and have been getting updates since. I installed FSO2 and the game works except for no Joystick. I have a Logitech X3D that calibrates fine in Ubuntu v7.10, but wine does not see it. There is no registry for directinput under HKEY_CURRENT_USER, Software, Wine.

How do I get wine properly setup to use a joystick?

Ubuntu v7.10_64bit, 2GB 800Mhz, 160GB HD SATAII, Nivida GeForce 7900GS KO OC, WINE 0.9.54., INTEL Duo Core E6300.

I have searched Ubuntu Forums, WINEHQ, WINE Forums, Google Search. It seems very few people have this problem or not that many are playing games under WINE with a joystick.

Please let me know if I need to attach a file and how to get it, like regedit.

Thanks

---

### Post by Resonance378 on 2008-02-01
There are reg entries you can make for Joysticks:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

Found via: [http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff) which was found via: [http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

HKey_Current_User>Software>Wine>
```

      +-DirectInput
      |  |
      |  +->*<joystick name> = <axes mapping>
      |      [Linux only (js* devices). This maps axis of joystick "joystick name".  The "axes mapping" is comma
      |       separated list of "axes type"s - one for each joystick axes (hat-pov uses 2 axis).
      |       "axes type" is one of: X, Y, Z, Rx, Ry, Rz, Slider1, Slider2, POV1, POV2, POV3, POV4.
      |       To find the joystick name run 'WINEDEBUG=+dinput wine program.exe 2>&1 | grep joydev_enum_device'
      |       Example: "Logitech Logitech Dual Action"="X,Y,Rz,Slider1,POV1". (two "Logitech" is not a typo)]

```

Not sure this is what you need however I think it may be a start.  Best of luck!

---

### Post by pm124493 on 2008-02-01
I found that entry and tried running WINEDEBUG as stated, but it returned nothing. Still at a loss.

Thank you for your comment and suggestion.

---

### Post by Resonance378 on 2008-02-01
You might have been too literal with the instructions...

```
WINEDEBUG=+dinput wine program.exe 2>&1 | grep joydev_enum_device
```

Where program.exe should be the name of the application you are trying to use a joystick with...

Say something like X-wing vs. Tie Fighter (only think I can think of right now that use a joystick) and say the name of the game exe is XwTf.exe

It'd look something like:

```
WINEDEBUG=+dinput wine XwTf.exe 2>&1 | grep joydev_enum_device
```

Is your joystick Analog or USB btw?  There may be other resources you could look into.  Try searching for USB Joystick or Analog Joystick here on the forums... you might find something, even if it is old and crusty, there are many truths to it.

Hope this helps.

---

### Post by pm124493 on 2008-02-01
I tried:
WINEDEBUG=+dinput wine FreeSpace2.exe 2>&1 | grep joydev_enum_device
I got the same results. No output.
It is a USB Joystick.
@UBUNTU:~$ sudo lsusb -v | grep Logitech

Bus 001 Device 004: ID 046d:c215 Logitech, Inc. 
  idVendor           0x046d Logitech, Inc.
  iManufacturer           1 Logitech
  iProduct                2 Logitech Extreme 3D
Bus 001 Device 003: ID 046d:092e Logitech, Inc. 
  idVendor           0x046d Logitech, Inc.
It is the Logitech Extreme 3D. The other is the mouse.

If someone else was using a joystick and provided me an example of the registry setting, I might could get it to work. I also would think there should be someway to load the directinput driver in WINE and auto detect the joystick much in the same as audio, mouse, video etc.

Again I thank you for your assistance.

---

### Post by pm124493 on 2008-02-02
I managed to get the following output from WINEDEBUG. The wine config does show it detects a joystick.

@UBUNTU:~$ WINEDEBUG=+dinput wine c:\\"Program Files"\\Freespace\\FreeSpace2.exe 2>&1
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
trace:dinput:DirectInputCreateEx (0x400000,0500,{9a4cb684-236d-11d3-8e9d-00c04f6844ae},0x349bb0,(nil))
trace:dinput:check_hook_thread IDirectInputs left: 1
trace:dinput:IDirectInputAImpl_QueryInterface (0x14e840)->({9a4cb684-236d-11d3-8e9d-00c04f6844ae},0x349bb0)
trace:dinput:IDirectInputAImpl_AddRef (0x14e840) incrementing from 0
trace:dinput:IDirectInputAImpl_EnumDevices (this=0x14e840,0x0004 'DIDEVTYPE_JOYSTICK',0x4144f0,0x349bb4,0000)
trace:dinput:_dump_EnumDevices_dwFlags  flags: DIEDFL_ALLDEVICES  - checking device 0 ('Wine mouse driver')
trace:dinput:IDirectInputAImpl_EnumDevices   - checking device 1 ('Wine keyboard driver')
trace:dinput:IDirectInputAImpl_EnumDevices   - checking device 2 ('Wine Linux-input joystick driver')
trace:dinput:IDirectInputAImpl_EnumDevices   - checking device 3 ('Wine Linux joystick driver')
trace:dinput:joydev_enum_deviceA Enumerating the linux Joystick device: /dev/input/js0 (Logitech Logitech Extreme 3D)
trace:dinput:IDirectInputAImpl_EnumDevices   - checking device 3 ('Wine Linux joystick driver')
trace:dinput:IDirectInputAImpl_Release (0x14e840) releasing from 1
trace:dinput:check_hook_thread IDirectInputs left: 0
trace:dinput:hook_thread_proc Processing hook change notification lp:0
trace:dinput:DirectInputCreateEx (0x400000,0500,{9a4cb684-236d-11d3-8e9d-00c04f6844ae},0x34bbc0,(nil))
trace:dinput:check_hook_thread IDirectInputs left: 1
trace:dinput:IDirectInputAImpl_QueryInterface (0x14edf8)->({9a4cb684-236d-11d3-8e9d-00c04f6844ae},0x34bbc0)
trace:dinput:IDirectInputAImpl_AddRef (0x14edf8) incrementing from 0
trace:dinput:IDirectInputAImpl_EnumDevices (this=0x14edf8,0x0004 'DIDEVTYPE_JOYSTICK',0x4144f0,0x34bbc4,0000)
trace:dinput:_dump_EnumDevices_dwFlags  flags: DIEDFL_ALLDEVICES  - checking device 0 ('Wine mouse driver')
trace:dinput:IDirectInputAImpl_EnumDevices   - checking device 1 ('Wine keyboard driver')
trace:dinput:IDirectInputAImpl_EnumDevices   - checking device 2 ('Wine Linux-input joystick driver')
trace:dinput:IDirectInputAImpl_EnumDevices   - checking device 3 ('Wine Linux joystick driver')
trace:dinput:joydev_enum_deviceA Enumerating the linux Joystick device: /dev/input/js0 (Logitech Logitech Extreme 3D)
trace:dinput:IDirectInputAImpl_EnumDevices   - checking device 3 ('Wine Linux joystick driver')
trace:dinput:IDirectInputAImpl_Release (0x14edf8) releasing from 1
trace:dinput:check_hook_thread IDirectInputs left: 0
trace:dinput:hook_thread_proc Processing hook change notification lp:0
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
pmcdade@UBUNTU:~$ fixme:heap:RtlCompactHeap (0x1150000, 0x1) stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32eb94,0x00000000), stub!
err:d3d7:IDirect3DDeviceImpl_2_GetRenderState Unexpected texture stage state setup, returning D3DTBLEND_MODULATE - likely erroneous
fixme:ras:RasEnumConnectionsA (0x34c704,0x34c638,0x34c630),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!

The game actually sees the joystick, but won't let me bind any buttons or throttle and does not work in the game.

---

### Post by Sockerdrickan on 2008-02-03
I'm hijacking this thread. :KS

pm124493: Does your Logitech Extreme 3D Pro work out of the box with native Linux games and which version of Ubuntu are you running? Thanks!

---

### Post by pm124493 on 2008-02-03
I loaded flight gear and the joystick works fine including the view POV and throttle.
I am running Ubuntu v7.10 x64.

I believe my problem is that there is no DirectInput in the WINE configuration. I ran regedit and I can not see DirectInput under HKEY_CURRENT_USER/Software/Wine.

If I new what to add there, I maybe able to get it to work.

Thanks.](*,)

---

### Post by Sockerdrickan on 2008-02-03
Great to hear that it works with native games!
I'll buy one in about 3 weeks, I might be able to help you then.

Bye

---

### Post by barbolani on 2008-02-04
I'm trying to make RealFlight G3.5 run and have not had much luck. This is a Radio Control flight simulator that comes with its own joystick that replicates the shape and functions of an actual radio control transmitter (in fact is manufactured by a popular R/C equipment brand)

The controller is plugged in a USB port and is recognized perfectly by jscalibrator. It even works with other native Linux games.

However ... the game installs fine and the launcher shows all the same options than in Windows XP. However, selecting the "Launch RealFlight" button shows the splash screen and then the program displays a dialog box saying that it is not able to find the controller.

In my case, running 

WINEDEBUG=+dinput wine "C:\Archivos de programa\Archivos comunes\KnifeEdge\Launcher.exe" REALFLIGHT3 

Does not display the dinput messages, what I'm doing wrong?

---

### Post by Resonance378 on 2008-02-05
> **barbolani said:**
> I'm trying to make RealFlight G3.5 run and have not had much luck. This is a Radio Control flight simulator that comes with its own joystick that replicates the shape and functions of an actual radio control transmitter (in fact is manufactured by a popular R/C equipment brand)

The controller is plugged in a USB port and is recognized perfectly by jscalibrator. It even works with other native Linux games.

However ... the game installs fine and the launcher shows all the same options than in Windows XP. However, selecting the "Launch RealFlight" button shows the splash screen and then the program displays a dialog box saying that it is not able to find the controller.

In my case, running 

WINEDEBUG=+dinput wine "C:\Archivos de programa\Archivos comunes\KnifeEdge\Launcher.exe" REALFLIGHT3 

Does not display the dinput messages, what I'm doing wrong?

Launcher may not be the actual game executable?  Try another one in the directory and see what results you get.

---

### Post by yoav_by on 2008-02-08
> **barbolani said:**
> In my case, running 

WINEDEBUG=+dinput wine "C:\Archivos de programa\Archivos comunes\KnifeEdge\Launcher.exe" REALFLIGHT3 

Does not display the dinput messages, what I'm doing wrong?

I had the same trouble with a Windows game, I thought it was because of WINEDEBUG couldn't understand the full path to the executable, so I navigated to the program's folder:
```
cd /home/username/.wine/drive_c/Program\ Files/FolderName
```

Then I ran WINEDEBUG with only the name of the EXE file:

```
WINEDEBUG=+dinput wine ProgName.exe 2>&1 | grep joydev_enum_device
```

This got me a nice output.

HTH

---

### Post by tailStrike on 2008-03-05
So has anyone gotten any farther on getting RealFlight to run under wine?  I've found info scattered about forums and all complain about the Interlink not being detected, but I' not quite getting that far.  I'm actually getting a crash after the log is displayed without reference to the missing interlink.

Here is the dump:
```
kyle@augustus:~/.wine/drive_c/Program Files/RealFlightG3$ wine RealFlight.exe
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
wine: Unhandled exception 0xc06d007e at address 0x7fc2e770 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: 0xc06d007e in 32-bit code (0x7fc2e7e0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7fc2e7e0 ESP:7fb9cffc EBP:7fb9d060 EFLAGS:00000202(   - 00      - - I1)
 EAX:7fc19e71 EBX:7fc946dc ECX:00000000 EDX:7fb9d0d4
 ESI:7fb9d0d4 EDI:00000000
Stack dump:
0x7fb9cffc:  7fb9d0d4 00000004 eb5959ff c06d007e
0x7fb9d00c:  00000000 00000000 7fc2e770 00000001
0x7fb9d01c:  7fb9d084 7d7114f6 c6ef3720 7d71abf2
0x7fb9d02c:  00000000 00000001 00000000 94a02524
0x7fb9d03c:  2494a025 252494a0 a0252494 7ff8d95d
0x7fb9d04c:  7d71ac3a 94a02524 7fb9d06c 00000000
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7fc2e7e0 RaiseException+0x70 in kernel32 (0x7fc2e7e0)
err:dbghelp_msc:pe_load_debug_directory Got a page fault while loading symbols
  2 0x00928673 in realflight (+0x528673) (0x00928673)
  3 0x007bd4ab in realflight (+0x3bd4ab) (0x007bd4ab)
0x7fc2e7e0 RaiseException+0x70 in kernel32: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (110 modules)
PE      0x00400000-0106d000     Export          realflight
PE      0x10000000-10092000     Deferred        fmod
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7c84c000-7c860000     Deferred        lz32<elf>
  \-PE  0x7c850000-7c860000     \               lz32
ELF     0x7c860000-7c879000     Deferred        version<elf>
  \-PE  0x7c870000-7c879000     \               version
ELF     0x7c879000-7c89f000     Deferred        msvfw32<elf>
  \-PE  0x7c880000-7c89f000     \               msvfw32
ELF     0x7c89f000-7c8e0000     Deferred        dinput<elf>
  \-PE  0x7c8b0000-7c8e0000     \               dinput
ELF     0x7c8e0000-7c8f4000     Deferred        dinput8<elf>
  \-PE  0x7c8f0000-7c8f4000     \               dinput8
ELF     0x7c8f4000-7c919000     Deferred        d3dxof<elf>
  \-PE  0x7c900000-7c919000     \               d3dxof
ELF     0x7c919000-7c9ac000     Deferred        wined3d<elf>
  \-PE  0x7c930000-7c9ac000     \               wined3d
ELF     0x7c9ac000-7ca22000     Deferred        libglu.so.1
ELF     0x7ca22000-7ca50000     Deferred        d3d9<elf>
  \-PE  0x7ca30000-7ca50000     \               d3d9
PE      0x7cb70000-7cb7f000     Deferred        nlvscan2
PE      0x7cca0000-7ccb8000     Deferred        dibapi32
ELF     0x7cdd1000-7cde6000     Deferred        midimap<elf>
  \-PE  0x7cde0000-7cde6000     \               midimap
ELF     0x7cde6000-7cdfe000     Deferred        msacm<elf>
  \-PE  0x7cdf0000-7cdfe000     \               msacm
ELF     0x7cdfe000-7ce42000     Deferred        wineoss<elf>
  \-PE  0x7ce10000-7ce42000     \               wineoss
ELF     0x7ce42000-7ceca000     Deferred        winmm<elf>
  \-PE  0x7ce50000-7ceca000     \               winmm
ELF     0x7ceca000-7cef0000     Deferred        msacm32<elf>
  \-PE  0x7ced0000-7cef0000     \               msacm32
ELF     0x7cf0c000-7cf20000     Deferred        snmpapi<elf>
  \-PE  0x7cf10000-7cf20000     \               snmpapi
ELF     0x7d039000-7d09a000     Deferred        msvcrt<elf>
  \-PE  0x7d050000-7d09a000     \               msvcrt
ELF     0x7d09a000-7d130000     Deferred        oleaut32<elf>
  \-PE  0x7d0b0000-7d130000     \               oleaut32
ELF     0x7d130000-7d17c000     Deferred        libgcrypt.so.11
ELF     0x7d17c000-7d18c000     Deferred        libtasn1.so.2
ELF     0x7d18c000-7d1b9000     Deferred        libcrypt.so.1
ELF     0x7d1b9000-7d222000     Deferred        libgnutls.so.12
ELF     0x7d222000-7d250000     Deferred        libcups.so.2
ELF     0x7d2f1000-7d31d000     Deferred        winspool<elf>
  \-PE  0x7d300000-7d31d000     \               winspool
ELF     0x7d31d000-7d366000     Deferred        rpcrt4<elf>
  \-PE  0x7d330000-7d366000     \               rpcrt4
ELF     0x7d366000-7d3f7000     Deferred        ole32<elf>
  \-PE  0x7d380000-7d3f7000     \               ole32
ELF     0x7d3f7000-7d452000     Deferred        shlwapi<elf>
  \-PE  0x7d410000-7d452000     \               shlwapi
ELF     0x7d452000-7d51e000     Deferred        shell32<elf>
  \-PE  0x7d470000-7d51e000     \               shell32
ELF     0x7d51e000-7d5bb000     Deferred        comdlg32<elf>
  \-PE  0x7d530000-7d5bb000     \               comdlg32
ELF     0x7d5bb000-7d5da000     Deferred        iphlpapi<elf>
  \-PE  0x7d5c0000-7d5da000     \               iphlpapi
ELF     0x7d5da000-7d605000     Deferred        ws2_32<elf>
  \-PE  0x7d5e0000-7d605000     \               ws2_32
ELF     0x7d605000-7d61f000     Deferred        wsock32<elf>
  \-PE  0x7d610000-7d61f000     \               wsock32
ELF     0x7d61f000-7d650000     Deferred        uxtheme<elf>
  \-PE  0x7d630000-7d650000     \               uxtheme
ELF     0x7d650000-7d710000     Deferred        comctl32<elf>
  \-PE  0x7d660000-7d710000     \               comctl32
ELF     0x7d75b000-7d75f000     Deferred        libgpg-error.so.0
ELF     0x7d9a4000-7d9a8000     Deferred        libxfixes.so.3
ELF     0x7d9a8000-7d9b1000     Deferred        libxcursor.so.1
ELF     0x7d9b1000-7d9cd000     Deferred        imm32<elf>
  \-PE  0x7d9c0000-7d9cd000     \               imm32
ELF     0x7d9cd000-7d9d5000     Deferred        libxrender.so.1
ELF     0x7eae5000-7eaed000     Deferred        librt.so.1
ELF     0x7ebb7000-7f4b2000     Deferred        fglrx_dri.so
ELF     0x7f4b2000-7f552000     Deferred        libgl.so.1
ELF     0x7f552000-7f638000     Deferred        libx11.so.6
ELF     0x7f638000-7f650000     Deferred        libice.so.6
ELF     0x7f650000-7f6d3000     Deferred        winex11<elf>
  \-PE  0x7f660000-7f6d3000     \               winex11
ELF     0x7f6d3000-7f6f2000     Deferred        libexpat.so.1
ELF     0x7f6f2000-7f720000     Deferred        libfontconfig.so.1
ELF     0x7f720000-7f734000     Deferred        libz.so.1
ELF     0x7f734000-7f79e000     Deferred        libfreetype.so.6
ELF     0x7f79e000-7f7de000     Deferred        advapi32<elf>
  \-PE  0x7f7b0000-7f7de000     \               advapi32
ELF     0x7f8b3000-7f964000     Deferred        gdi32<elf>
  \-PE  0x7f8d0000-7f964000     \               gdi32
ELF     0x7f964000-7fa90000     Deferred        user32<elf>
  \-PE  0x7f980000-7fa90000     \               user32
ELF     0x7fba3000-7fbb0000     Deferred        libxext.so.6
ELF     0x7fbb1000-7fbbb000     Deferred        libgcc_s.so.1
ELF     0x7fbee000-7fcf0000     Export          kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe00000-7fe03000     Deferred        libxrandr.so.2
ELF     0x7fe04000-7fe09000     Deferred        libxxf86vm.so.1
ELF     0x7fe09000-7fe13000     Deferred        libnss_files.so.2
ELF     0x7fe13000-7fe1c000     Deferred        libnss_nis.so.2
ELF     0x7fe1c000-7fe31000     Deferred        libnsl.so.1
ELF     0x7fe31000-7fe3a000     Deferred        libnss_compat.so.2
ELF     0x7fe3d000-7fe42000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7df0000-b7df3000     Deferred        libxau.so.6
ELF     0xb7dfc000-b7dff000     Deferred        libdl.so.2
ELF     0xb7dff000-b7f2e000     Deferred        libc.so.6
ELF     0xb7f2e000-b7f40000     Deferred        libpthread.so.0
ELF     0xb7f51000-b7f6b000     Deferred        libwine.so.1
ELF     0xb7f6e000-b7f84000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\RealFlightG3\RealFlight.exe
        0000000c    0
        0000000a    0
        00000009    0 <==

```

---

### Post by pm124493 on 2008-03-08
I am no further along now as before. What I can conclude is that it is a wine issue. The joystick is detected and jscalibrator sees the joystick and does allow calibration. Linux games like FlightGear work with the joystick. 
I have been trying to get it to work with Free Space 2 Open. The games' options does see the joystick and correctly identifies it. It will not calibrate or detect the axis or buttons in the settings options of the game. And none of the axis or buttons work in the game. 
The game detects the joystick, but no translation from wine is my assumption. Running the winedebug steps shows some output of the joystick, but not much. I should see every event the joystick produces, but only see two random events. 

I have another Ubuntu v7.10 system using a different motherboard and CPU. I installed wine on that system and FSO2 with the exact same results. The other game I have can use a joystick so I configured it to use a joystick with minimal results. The only thing to work was button one.

I am running wine 0.9.56 and nothing has changed. I looks to me like there is no interest in the wine development team to address this problem. It would be nice if there was a way to install the specific M$ driver for the joystick in wine.

I figure someday it will happen.

Thank you all for your posts on this issue.

---

### Post by janfsd on 2008-03-20
I heard that jscalibrator is kind of buggy, so better try to remove jscalibrator with all its configuration files. If you want to calibrate your pad, better try "joystick" in the repos.

---

### Post by pm124493 on 2008-03-24
I will give it a try. Update when I complete suggestion.

Thanks,

Pete

---

### Post by janfsd on 2008-03-24
I would like to know if it worked for you, in case one day I'll need to use my pad with wine. Other thing, did you add the DirecInput wine regitry key?

---

### Post by pm124493 on 2008-03-26
I have seen posts about the DirectInput registry key, but was not sure it applied to later versions of Wine. I am now at v0.9.58. If someone could provide instructions on adding the DirectInput registry key I would add it.

Thanks,

Pete

---

### Post by janfsd on 2008-03-26
You could always try the wine forums, some devs are around there.

---

### Post by Entity` on 2008-12-03
Jscallibrator gave me no problems in configuring my Logitech Wingman Extreme Digital 3D on my soundcards game port.  My only problem is that Wine 1.1.4 only partially recognizes the joystick so as to let me operate the buttons but not any of the axis-based movements.  This is troublesome because I am trying to play an old game called Hellbender with it.  All I have right now is the keyboard.  Can someone please help me?

---

### Post by Solomoriah on 2008-12-13
I'm having the same problem with a USB joystick and Linux SDL games: the buttons work, but the stick itself (i.e. the axes) don't.  But jstest and jscalibrator both show axial response.

I wish I knew what I was doing wrong.  If the buttons work, shouldn't the axes work too?

---

### Post by yoav_by on 2008-12-13
> **Solomoriah said:**
> I'm having the same problem with a USB joystick and Linux SDL games: the buttons work, but the stick itself (i.e. the axes) don't.  But jstest and jscalibrator both show axial response.

I wish I knew what I was doing wrong.  If the buttons work, shouldn't the axes work too?

Having similar problem in Ubuntu/wine with my Saitek ST290 Pro: axes, buttons and slider work, but not POV hat. The kubuntu josytick calibration program recognizes the POV hat, but games under wine don't. The strangest thing is that the stick works perfectly in wine on Mandriva 2009.

---

### Post by cypherdtraitor on 2009-12-11
I'm going to add my name onto this list of folks who can't get the joystick to work.

Intrepid Ibex 64bit, works in Ubuntu OS, does not work in anything emulated in Wine. Oddly, the buttons ON my joystick work fine, but the actual x, y, and z values of the joystick and the throttle bar do not. I use a Logitech Attack3 joystick. 

I have not yet tried to emulate the Logitech software in wine.

---

### Post by oelmekki on 2010-06-10
This thread is old, but seems unresolved, so I post in there.

I had the same problem with wine not recognizing my joystick. First, I found out that the games I used (x-wing vs tie-fighter) didn't used the dinput driver, but the old joystick one. So, the good debug variable is WINEDEBUG=+joystick , rather than WINEDEBUG=+dinput .

Then, I realized my mouse was recognized as an joystick by the system : it was on /dev/input/js0 . And that was the problem : wine expects the main joystick to be on /dev/input/js0. 

So I just unplugged the mouse and the joystick, then plug back firstly the joystick, then the mouse, and all ran fine. I guess I may have add a udev rule or something, but you know, I'm not up to do some sysadmin when I want to play.

EDIT: typos

---

