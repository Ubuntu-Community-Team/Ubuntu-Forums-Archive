---
title: "WoW Crashes on starting Wine error 132"
date: 2008-05-14
forum: Wine
---

### Post by katyl on 2008-05-14
Hey guys, thanks for the help.
I have a fresh install of Kubuntu w/ wine 1.0 rc1 from winehq's repos. WoW crashes after a few moments of thinking before it ever goes full screen; the error is 132. I'm using the latest flgrx driver w/ a good couple of thousand running glxgears. glxinfo shows direct rendering is enabled. I've uninstalled the driver and while performance is of course horrible, wow does open up. lspci, the error and the like are below. I'm of course happy to provide any extra info that's needed. 

lspci```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAMController
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
```
xorg.conf
```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"      "true"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Driver          "fglrx"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Extensions"
        Option          "Composite"     "Disable"
EndSection
```


Info from the wow error is 
```
==============================================================================
World of WarCraft (build 8278)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     May 14, 2008 11:41:01.003 PM
User:     katyl
Computer: katyl
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0023:7C06BFA8

The instruction at "0x7C06BFA8" referenced memory at "0x7C06BFA8".
The memory could not be "written".


WoWBuild: 8278
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=0033C22C  EBX=7E95BC84  ECX=0012D1E0  EDX=7E95C920  ESI=00000000
EDI=7E949BC7  EBP=0033C248  ESP=0033C1FC  EIP=7C06BFA8  FLG=00010202
CS =0023      DS =002B      ES =002B      SS =002B      FS =0063      GS =006B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 10/10 threads...

--- Thread ID: 37 ---

--- Thread ID: 36 ---
7BC68EDB 728FD514 0001:00057EDB C:\windows\system32\ntdll.dll
7BC69BFB 728FD614 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 728FD644 0001:00058ED2 C:\windows\system32\ntdll.dll
7B88BF22 728FD794 0001:0006AF22 C:\windows\system32\KERNEL32.dll
7B88C07A 728FD7B4 0001:0006B07A C:\windows\system32\KERNEL32.dll
007F180B 728FDA0C 0001:003F080B C:\Program Files\World of Warcraft\Wow.exe
007F10B8 728FDA1C 0001:003F00B8 C:\Program Files\World of Warcraft\Wow.exe
00550277 728FDA38 0001:0014F277 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 728FDA48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 728FDAE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 728FE3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D8D4FB 728FE4C8 0000:00000000 <unknown>

--- Thread ID: 35 ---
7BC68EDB 72A0E748 0001:00057EDB C:\windows\system32\ntdll.dll
7BC69BFB 72A0E848 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 72A0E878 0001:00058ED2 C:\windows\system32\ntdll.dll
7B88BF22 72A0E9C8 0001:0006AF22 C:\windows\system32\KERNEL32.dll
7B88C11C 72A0E9E8 0001:0006B11C C:\windows\system32\KERNEL32.dll
00554010 72A0E9F8 0001:00153010 C:\Program Files\World of Warcraft\Wow.exe
007F0FA5 72A0EA10 0001:003EFFA5 C:\Program Files\World of Warcraft\Wow.exe
007F10E1 72A0EA1C 0001:003F00E1 C:\Program Files\World of Warcraft\Wow.exe
00550277 72A0EA38 0001:0014F277 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 72A0EA48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 72A0EAE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 72A0F3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D8D4FB 72A0F4C8 0000:00000000 <unknown>

--- Thread ID: 34 ---

--- Thread ID: 33 ---

--- Thread ID: 32 ---
7BC68EDB 72D8B840 0001:00057EDB C:\windows\system32\ntdll.dll

--- Thread ID: 31 ---

--- Thread ID: 30 ---
7BC68EDB 7BBFE818 0001:00057EDB C:\windows\system32\ntdll.dll
F7D94E14 7BBFE850 0000:00000000 <unknown>

--- Thread ID: 29 ---

--- Thread ID: 28 [Current Thread] ---
7C06BFA8 0033C248 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7E89074C 0033C2C8 0001:0001F74C C:\windows\system32\wined3d.dll
7E8C526B 0033C5D8 0001:0005426B C:\windows\system32\wined3d.dll
7E89CFCB 0033C648 0001:0002BFCB C:\windows\system32\wined3d.dll
7E976C5E 0033C678 0001:00005C5E C:\windows\system32\d3d9.dll
00647AEA 0033C6AC 0001:00246AEA C:\Program Files\World of Warcraft\Wow.exe
004AF9D3 0033C6E4 0001:000AE9D3 C:\Program Files\World of Warcraft\Wow.exe
004B0D48 0033C7B8 0001:000AFD48 C:\Program Files\World of Warcraft\Wow.exe
004B0FEC 0033FB30 0001:000AFFEC C:\Program Files\World of Warcraft\Wow.exe
007B7B5D 0033FC08 0001:003B6B5D C:\Program Files\World of Warcraft\Wow.exe
007744C2 0033FC20 0001:003734C2 C:\Program Files\World of Warcraft\Wow.exe
007A9312 0033FCA8 0001:003A8312 C:\Program Files\World of Warcraft\Wow.exe
007C43B7 0033FCC4 0001:003C33B7 C:\Program Files\World of Warcraft\Wow.exe
007C48BC 0033FCE0 0001:003C38BC C:\Program Files\World of Warcraft\Wow.exe
00799C50 0033FDAC 0001:00398C50 C:\Program Files\World of Warcraft\Wow.exe
007DD3AB 0033FDDC 0001:003DC3AB C:\Program Files\World of Warcraft\Wow.exe
007DA7F9 0033FE54 0001:003D97F9 C:\Program Files\World of Warcraft\Wow.exe
007DBC61 0033FE6C 0001:003DAC61 C:\Program Files\World of Warcraft\Wow.exe
004062B8 0033FF08 0001:000052B8 C:\Program Files\World of Warcraft\Wow.exe
7B8776D7 0033FFE8 0001:000566D7 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 10/10 threads...

--- Thread ID: 37 ---

--- Thread ID: 36 ---
7BC68EDB ntdll.dll    <unknown symbol>+0 (0x728FD548,0x728FD568,0x728FD5DC,0x728FD5B8)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x728FD67C,0x00000004,0x728FD77C)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x728FD67C,0x00000000,0x00000000)
7B88BF22 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x728FD8D8,0x00000000,0x000001F4)
7B88C07A KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x728FD8D8,0x00000000,0x000001F4)
007F180B Wow.exe      <unknown symbol>+0 (0x007F10F0,0x007F10FB,0x728FDA38,0x00550277)
007F10B8 Wow.exe      <unknown symbol>+0 (0x05D4F808,0x00550240,0x05D42388,0x7BC88444)
00550277 Wow.exe      <unknown symbol>+0 (0x00002184,0x00550240,0x728FDAE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x00550240,0x05D42388,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x728FDB1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x728FE490,0x728FE490,0x728FE490)
F7D8D4FB              start_thread+203 (0x728FEB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 35 ---
7BC68EDB ntdll.dll    <unknown symbol>+0 (0x72A0E77C,0x7B84E46C,0x72A0E810,0x72A0E7EC)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x72A0E8B0,0x00000004,0x72A0E9B0)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x72A0E8B0,0x00000000,0x00000000)
7B88BF22 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x72A0E9F0,0x00000000,0x000003E8)
7B88C11C KERNEL32.dll WaitForSingleObject+60 (0x000020F4,0x000003E8,0x72A0EA10,0x007F0FA5)
00554010 Wow.exe      <unknown symbol>+0 (0x000003E8,0x05D4F818,0x007F10D0,0x00000023)
007F0FA5 Wow.exe      <unknown symbol>+0 (0x00000000,0x72A0EA38,0x00550277,0x05D4F818)
007F10E1 Wow.exe      <unknown symbol>+0 (0x05D4F818,0x00550240,0x05D42388,0x7BC88444)
00550277 Wow.exe      <unknown symbol>+0 (0x00002180,0x00550240,0x72A0EAE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x00550240,0x05D42388,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x72A0EB1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x72A0F490,0x72A0F490,0x72A0F490)
F7D8D4FB              start_thread+203 (0x72A0FB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 34 ---

--- Thread ID: 33 ---

--- Thread ID: 32 ---
7BC68EDB ntdll.dll    <unknown symbol>+0 (0x7BC88444,0x00000000,0x00000001,0x72D8B884)

--- Thread ID: 31 ---

--- Thread ID: 30 ---
7BC68EDB ntdll.dll    <unknown symbol>+0 (0x7BC88444,0x00000000,0x00000001,0x7BBFE85C)
F7D94E14              <unknown symbol>+0 (0x7B88C0E0,0x7BBFE9AC,0x7B88BF22,0x00000001)
00000001 <unknown module> <unknown symbol>+0 (0x00000000,0xF7D0A7A0,0xF7DBCA20,0xF7D97C90)

--- Thread ID: 29 ---

--- Thread ID: 28 [Current Thread] ---
7C06BFA8 <unknown module> <unknown symbol>+0 (0x000000D8,0x00130968,0x037C80A0,0xF7D83FF4)
7E89074C wined3d.dll  ActivateContext+1276 (0x0012D1E0,0x0013E808,0x00000002,0x00000003)
7E8C526B wined3d.dll  drawPrimitive+379 (0x0012D1E0,0x00000004,0x0000007B,0x00000000)
7E89CFCB wined3d.dll  <unknown symbol>+0 (0x0012D1E0,0x00000004,0x00000000,0x0000008A)
7E976C5E d3d9.dll     <unknown symbol>+0 (0x0012E2B8,0x00000004,0x00000000,0x00000000)
00647AEA Wow.exe      <unknown symbol>+0 (0x00000001,0x00000000,0x00000001,0x00000000)
004AF9D3 Wow.exe      <unknown symbol>+0 (0x00000000,0x07D87500,0x07512208,0x0040C05B)
004B0D48 Wow.exe      <unknown symbol>+0 (0x00000000,0x07DE0008,0x07E1E608,0x0000002B)
004B0FEC Wow.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x0603D884,0x3F800000)
007B7B5D Wow.exe      <unknown symbol>+0 (0x3F800000,0x00000003,0xFF000000,0x07D87508)
007744C2 Wow.exe      <unknown symbol>+0 (0x07527808,0x00000001,0x0603D808,0x0603D884)
007A9312 Wow.exe      <unknown symbol>+0 (0x0603D884,0x05FFACF4,0x00000006,0x05FFA008)
007C43B7 Wow.exe      <unknown symbol>+0 (0x02607888,0x05FA6DA0,0x05FA6D88,0x00000000)
007C48BC Wow.exe      <unknown symbol>+0 (0x00000000,0x05FA6D90,0x05FA6DA0,0x40C3A5E4)
00799C50 Wow.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x01433008,0x00000000)
007DD3AB Wow.exe      <unknown symbol>+0 (0x01433008,0x00000011,0x00000000,0x007DBB7D)
007DA7F9 Wow.exe      <unknown symbol>+0 (0x00000001,0x00406278,0x00000001,0x00000001)
007DBC61 Wow.exe      <unknown symbol>+0 (0x00409EA9,0x00400000,0x00000000,0x001119FC)
004062B8 Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B8776D7 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00EBF000  C:\Program Files\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x72C40000 - 0x72C7C000  C:\windows\system32\dsound.dll
0x7B820000 - 0x7B92D000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA4000  C:\windows\system32\ntdll.dll
0x7BCB0000 - 0x7BCEF000  C:\windows\system32\dbghelp.dll
0x7BF40000 - 0x7BF53000  C:\windows\system32\psapi.dll
0x7BFC0000 - 0x7BFF0000  C:\windows\system32\uxtheme.dll
0x7E1E0000 - 0x7E1E7000  C:\windows\system32\midimap.dll
0x7E1F0000 - 0x7E1FE000  C:\windows\system32\msacm32.drv
0x7E200000 - 0x7E239000  C:\windows\system32\wineoss.drv
0x7E280000 - 0x7E301000  C:\windows\system32\winex11.drv
0x7E400000 - 0x7E407000  C:\windows\system32\lz32.dll
0x7E410000 - 0x7E420000  C:\windows\system32\version.dll
0x7E430000 - 0x7E481000  C:\windows\system32\rpcrt4.dll
0x7E490000 - 0x7E525000  C:\windows\system32\ole32.dll
0x7E540000 - 0x7E556000  C:\windows\system32\iphlpapi.dll
0x7E560000 - 0x7E582000  C:\windows\system32\ws2_32.dll
0x7E590000 - 0x7E5A8000  C:\windows\system32\msacm32.dll
0x7E5B0000 - 0x7E667000  C:\windows\system32\comctl32.dll
0x7E680000 - 0x7E776000  C:\windows\system32\shell32.dll
0x7E780000 - 0x7E7CF000  C:\windows\system32\shlwapi.dll
0x7E7E0000 - 0x7E7F0000  C:\windows\system32\mpr.dll
0x7E800000 - 0x7E83E000  C:\windows\system32\wininet.dll
0x7E840000 - 0x7E85E000  C:\windows\system32\imm32.dll
0x7E870000 - 0x7E960000  C:\windows\system32\wined3d.dll
0x7E970000 - 0x7E990000  C:\windows\system32\d3d9.dll
0x7EB40000 - 0x7EBA3000  C:\windows\system32\opengl32.dll
0x7EBB0000 - 0x7EBF5000  C:\windows\system32\advapi32.dll
0x7EC10000 - 0x7EC90000  C:\windows\system32\gdi32.dll
0x7ECB0000 - 0x7EDD7000  C:\windows\system32\user32.dll
0x7EDE0000 - 0x7EE69000  C:\windows\system32\winmm.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 7C06BFA8)

7C06BFA8: A1 60 79 A2  7E 85 C0 74  06 FF A0 E0  0C 00 00 E8  .`y.~..t........


Stack: 1024 bytes starting at (ESP = 0033C1FC)

* = addr                                         **                       *   
0033C1F0: 58 84 59 73  C0 84 00 00  48 C2 33 00  F9 BD 8E 7E  X.Ys....H.3....~
0033C200: 75 87 00 00  2C C2 33 00  00 00 00 00  01 00 00 00  u...,.3.........
0033C210: 02 00 00 00  01 00 00 00  01 00 00 00  71 C2 8E 7E  ............q..~
0033C220: C7 9B 94 7E  00 00 80 3F  C7 9B 94 7E  00 00 00 00  ...~...?...~....
0033C230: 00 00 00 00  00 00 00 00  00 00 00 00  84 BC 95 7E  ...............~
0033C240: 06 00 00 00  43 00 00 00  C8 C2 33 00  4C 07 89 7E  ....C.....3.L..~
0033C250: D8 00 00 00  68 09 13 00  A0 80 7C 03  F4 3F D8 F7  ....h.....|..?..
0033C260: 00 00 00 00  70 01 00 00  CB B0 90 7E  84 BC 95 7E  ....p......~...~
0033C270: 60 B9 12 00  78 6C 95 7E  C8 C2 33 00  CE 83 8F 7E  `...xl.~..3....~
0033C280: 60 B9 12 00  78 6C 95 7E  C8 C5 33 00  EE 84 8F 7E  `...xl.~..3....~
0033C290: 03 00 00 00  A0 80 7C 03  60 7B 95 7E  8C AC 90 7E  ......|.`{.~...~
0033C2A0: AC 64 ED F7  D4 C2 33 00  A0 B5 DB F7  F8 0C C9 7B  .d....3........{
0033C2B0: 03 00 00 00  00 00 00 03  00 00 00 00  84 BC 95 7E  ...............~
0033C2C0: 74 D2 95 7E  E0 D1 12 00  D8 C5 33 00  6B 52 8C 7E  t..~......3.kR.~
0033C2D0: E0 D1 12 00  08 E8 13 00  02 00 00 00  03 00 00 00  ................
0033C2E0: 00 00 17 00  00 00 00 00  10 00 00 00  34 C3 33 00  ............4.3.
0033C2F0: 29 ED D0 F7  70 01 00 00  37 36 C7 7B  0E 64 32 72  )...p...76.{.d2r
0033C300: 43 00 00 00  70 01 00 00  44 84 C8 7B  F8 63 32 72  C...p...D..{.c2r
0033C310: 00 00 00 00  78 6C 95 7E  FF 39 C6 7B  02 00 00 00  ....xl.~.9.{....
0033C320: 7C C3 33 00  00 00 00 00  44 84 02 00  C9 39 C6 7B  |.3.....D....9.{
0033C330: 44 84 C8 7B  54 C4 33 00  35 53 C7 7B  E0 0C C9 7B  D..{T.3.5S.{...{
0033C340: 7C C3 33 00  03 00 00 00  90 C3 33 00  29 ED D0 F7  |.3.......3.)...
0033C350: 20 00 00 00  37 36 C7 7B  D6 39 00 7C  43 00 00 00   ...76.{.9.|C...
0033C360: 20 00 00 00  44 84 C8 7B  00 39 00 7C  00 00 4F 08   ...D..{.9.|..O.
0033C370: 00 00 17 00  FF FF 00 00  02 00 00 00  00 00 00 00  ................
0033C380: 00 00 00 00  44 84 C8 7B  C9 39 C6 7B  88 58 1C 00  ....D..{.9.{.X..
0033C390: E0 C3 33 00  CF 33 C4 7B  E0 0C C9 7B  D8 C3 33 00  ..3..3.{...{..3.
0033C3A0: 28 00 00 00  14 00 11 00  C8 58 1C 00  E0 58 1C 00  (........X...X..
0033C3B0: 00 00 11 00  44 84 C8 7B  80 58 1C 00  30 00 00 00  ....D..{.X..0...
0033C3C0: E0 C3 33 00  2E 2A C4 7B  00 00 1D 00  00 00 0C 00  ..3..*.{........
0033C3D0: C8 58 1C 00  7F 37 C3 7B  80 58 1C 00  44 84 C8 7B  .X...7.{.X..D..{
0033C3E0: 40 C4 33 00  FE 3C C4 7B  48 00 11 00  00 00 00 00  @.3..<.{H.......
0033C3F0: 00 00 00 00  00 00 00 00  AC 64 ED F7  5C C8 95 7E  .........d..\..~
0033C400: 40 C4 33 00  52 90 DB F7  5C C8 95 7E  00 00 00 00  @.3.R...\..~....
0033C410: 00 00 00 00  00 00 00 00  88 58 1C 00  00 00 11 00  .........X......
0033C420: 02 00 00 00  CF 33 C4 7B  00 00 00 00  00 00 00 00  .....3.{........
0033C430: 14 00 11 00  84 BC 95 7E  30 00 00 00  C0 7E 1C 00  .......~0....~..
0033C440: D0 C4 33 00  FD D4 92 7E  88 58 1C 00  88 29 15 00  ..3....~.X...)..
0033C450: 30 00 00 00  E4 50 95 7E  C0 7E 1C 00  09 00 00 00  0....P.~.~......
0033C460: 38 00 00 00  14 00 11 00  90 29 15 00  B8 29 15 00  8........)...)..
0033C470: 00 00 11 00  44 84 C8 7B  80 29 15 00  38 00 00 00  ....D..{.)..8...
0033C480: D0 C4 33 00  A6 2A C4 7B  88 29 15 00  20 00 00 00  ..3..*.{.).. ...
0033C490: 04 00 00 00  85 12 C4 7B  00 00 00 00  00 00 0C 00  .......{........
0033C4A0: 08 75 1C 00  4E 1B C4 7B  C0 7E 1C 00  00 00 11 00  .u..N..{.~......
0033C4B0: 14 00 11 00  D9 60 97 7E  00 00 00 00  00 00 00 00  .....`.~........
0033C4C0: 14 00 11 00  7F 37 C3 7B  14 00 11 00  44 84 C8 7B  .....7.{....D..{
0033C4D0: 10 C5 33 00  69 A6 92 7E  78 F6 98 7E  01 00 00 00  ..3.i..~x..~....
0033C4E0: 10 C5 33 00  B2 39 98 7E  B8 E2 12 00  00 00 11 00  ..3..9.~........
0033C4F0: 00 01 00 00  E8 03 00 00  00 00 00 00  00 00 00 00  ................
0033C500: 40 C5 33 00  35 39 8A 7E  E0 D1 12 00  E6 03 00 00  @.3.59.~........
0033C510: E8 03 00 00  E0 D1 12 00  C0 7E 1C 00  4C C5 33 00  .........~..L.3.
0033C520: 38 63 89 7E  D1 3D C3 7B  E8 03 00 00  00 00 00 00  8c.~.=.{........
0033C530: 80 FE 98 7E  7F 37 C3 7B  50 38 8A 7E  78 F6 98 7E  ...~.7.{P8.~x..~
0033C540: 70 C5 33 00  5C 68 97 7E  7C FE 98 7E  00 00 00 00  p.3.\h.~|..~....
0033C550: 30 74 1C 00  00 00 00 00  20 00 00 00  00 F3 98 7E  0t...... ......~
0033C560: 7C C5 33 00  8C C5 33 00  08 80 42 01  00 00 00 00  |.3...3...B.....
0033C570: 8C C6 33 00  24 6D 64 00  B8 E2 12 00  00 00 00 00  ..3.$md.........
0033C580: 70 29 15 00  00 00 00 00  20 00 00 00  20 00 00 00  p)...... ... ...
0033C590: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C5A0: 00 00 00 00  00 00 00 00  00 00 00 00  1E 18 8D 7E  ...............~
0033C5B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C5C0: 08 08 43 01  00 00 00 00  60 B9 12 00  84 BC 95 7E  ..C.....`......~
0033C5D0: 02 00 00 00  10 59 1C 00  48 C6 33 00  CB CF 89 7E  .....Y..H.3....~
0033C5E0: E0 D1 12 00  04 00 00 00  7B 00 00 00  00 00 00 00  ........{.......
0033C5F0: 8A 00 00 00  E7 00 00 00  02 00 00 00  E0 8B 1C 00  ................


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        15
Processor Revision:     26625

Percent memory used:    22
Total physical memory:  1978888192
Free Memory:            1538097152
Page file:              3618852864
Total virtual memory:   2147352575
```

When run from terminal, the output is 
```
katyl@katyl:~$ wine "C:\program files\world of warcraft\wow.exe"
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:powrprof:DllMain (0x7bfa0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7bfa0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x32eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec94,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3520
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a0,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests morethan one back buffer, this can't be supported properly. Please configure theapplication to use double buffering(=1 back buffer) if possible
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x12d258) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x32f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x37402b24) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
```

---

### Post by thisismalhotra on 2008-05-15
I have no idea what your problem is exactly but few things..

1. Is you winecfg setup and is the game usiong win xp settings??
2. (I am sure you have done this but..) did you make changes to config.wtf so that WoW open with openGL instead of D3D
3. Did you make the registry edit ...
4. What do you mean when you say I have uninstalled the driver??

Here are some links ... I am sure you have been here ...

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

Good luck with ATi man .. I can't tell you how many hours I have soent on that but still does not work on my laptop :(

---

### Post by brigux on 2008-05-15
because of:
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
You should first restart your computer (not just the X server) it usually fixes it.

Now for the error itself, you might have a problem with the latest wow patch. Download the patch manually, wine the patch, then try again.

Please let us know if it helps.

---

### Post by katyl on 2008-05-15
I've tried those thisismalhotra, no love. As for uninstalling the driver, As for the last I mean if I go back into envy and uninstall the ATI proprietary driver ((falling back on vesa,))
As for the latest patch, brigux, I tend to think that is not my issue, I have moved my game folder to home, and reinstalled the traditional vanilla wow from an original CD w/ no patches, still no go. Same error. While it's not your exact instructions, I think it's good enough to test if it's a bigger issue than the patch.

---

### Post by brigux on 2008-05-15
wine "C:\program files\world of warcraft\wow.exe" -opengl 
?

---

### Post by katyl on 2008-05-15
Crashes w/ OpenGL or the -d3d option, though the opengl is set via config.wtf

---

### Post by thisismalhotra on 2008-05-15
> **katyl said:**
> I've tried those thisismalhotra, no love. As for uninstalling the driver, As for the last I mean if I go back into envy and uninstall the ATI proprietary driver ((falling back on vesa,))
As for the latest patch, brigux, I tend to think that is not my issue, I have moved my game folder to home, and reinstalled the traditional vanilla wow from an original CD w/ no patches, still no go. Same error. While it's not your exact instructions, I think it's good enough to test if it's a bigger issue than the patch.

vesa driver will never be ableto render wow IMO, I think fgrlx is your best bet forward ...

did you try using windowed mode ...(I am sure you have so sorry for repeting if so)

---

### Post by katyl on 2008-05-15
Don't get me wrong, I wasn't thinking I could run the game using VESA, I just wanted to see if it would crash. So kinda points to FGRLX as the issue. I just wish I knew what it was. I've always had this issue trying to use wine w/ wow so I don't think it's the latest patch. I've been playing via Cedega for a long time untill this most recent patch broke my load time. Did my normal install routine. Perhapse that will help someone out. as I said this was a fresh install so I can you what the exact packages were on the machine

envynv-qt
ATI driver via envy
cedega's binary
openjava
(Jwowupdater- Java application for managing wow addons.)
libxtst-dev
g++
libgtk2.0-0
libxml++2.6-dev
fluid
libfltk1.1-dev
libxtst-dev
libgtk2.0-dev 
[nostromo drivers ]("http://sourceforge.net/project/showfiles.php?group_id=61608&package_id=91299&release_id=382235")compiled from source and installed via checkinstall 
wine.

Besides that those the only change from a default installation was a 10-local-rules file I add to the /etc/udev/rules.d folder to allow read write to the nostromo speed pad. I don't have the exact file with me. But from what I remember it looks at the info of a plugged in usb device if it matches the info for the speedpad, it'll allow read/write to a specific gruop.

---

### Post by thisismalhotra on 2008-05-16
I really know what you mean though ... and what your feeling ... I have gateway laptop which I have tried my arms and legs to fix the WoW issues with Ati Radeon xpress 200m, it not one of the greatest card but on XP it runs about 20fps(some tweaking there ofcourse lol).. and just want to get rid of XP.

Sorry could not help you much ... can you try using an older version of wine or the Ati driver .. Also there is an open driver for Ati too ..

Also did you try this (I am sure you did but...), it is one of the links I sent you ...

**ATI enter game world crash**

For users with an ATI video card: certain cards have trouble rendering games and video in opengl using current flgrx drivers which will cause your computer to hard locks when you attempt to enter a domain. This error will occur just after character creation/selection, as the game environment is loading, or possibly after a short period of play. In order to fix this error, add the following three lines of code to your xorg.conf file in the ATI device section:

    ```
*

       Option "Capabilities" "0x00000800"
       Option "UseFastTLS" "off"
       Option "KernelModuleParm" "locked-userpages=0"

      You edit the file by doing this command:

       gksudo gedit /etc/X11/xorg.conf

      The section should look something similar to this after editing:

       Section "Device"
         Identifier  "aticonfig-Device[0]"
         Driver      "fglrx"
         Option       "Capabilities" "0x00000800"
         Option       "UseFastTLS" "off"
         Option       "KernelModuleParm" "locked-userpages=0"
       EndSection


```

---

