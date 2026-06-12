---
title: "WoW - No Sound using Wine"
date: 2005-08-11
forum: Wine
---

### Post by seethru on 2005-08-11
I'm attempting to run WoW using Wine. Not winex, not cedega, just plain wine. Everything is working great EXCEPT the targetting bug, and I can't get sound working for the life of me.

I've tried deleting the Config.wtf, and switching between winealsa and wineoss. I've upgraded alsa to the newest version, from source. I'm at a loss at this point. I'm trying to avoid purchasing the 3 months of cedega for my own personal reasons.

Can anyone help me? Perhaps give me suggestions to try.

ps..sound works fine everywhere else.

---

### Post by Caboose on 2005-08-11
You could try getting cedega from cvs, that's free, and legal.

And from personal experiance, esd messes up the sound in WoW, kill it.

---

### Post by bdamon on 2005-08-11
[QUOTE=seethru]I'm attempting to run WoW using Wine. [/QUOTE]


If you get this working it would be great if you could please post a howto on how you did it.


Thanks
Ben

---

### Post by seethru on 2005-08-12
[QUOTE=Caboose]You could try getting cedega from cvs, that's free, and legal.

And from personal experiance, esd messes up the sound in WoW, kill it.[/QUOTE]

Tried the cvscedega, and I get the OpenGL32.dll could not be found error, even though I'm not using -opengl. Also tried killall esd, still no sound D:.

---

### Post by Caboose on 2005-08-12
[http://www.dll-files.com/dllindex/dll-files.shtml?opengl32](http://www.dll-files.com/dllindex/dll-files.shtml?opengl32)

Try putting that in ~/.cvscedega/c_drive/windows/system

---

### Post by seethru on 2005-08-12
After pasting opengl32.dll into the system folder
```

err:win32:PE_fixup_imports No implementation for GLU32.dll.48(gluTessNormal) imp orted from C:\windows\system32\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.49(gluTessProperty) i mported from C:\windows\system32\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.44(gluTessBeginPolygo n) imported from C:\windows\system32\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.43(gluTessBeginContou r) imported from C:\windows\system32\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.47(gluTessEndPolygon)  imported from C:\windows\system32\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.46(gluTessEndContour)  imported from C:\windows\system32\opengl32.dll, setting to 0xdeadbeef
Building font metrics. This may take some time...
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--13-120-75-75-c-70-i so8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--13-120-75-75-c-80-i so8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--14-130-75-75-c-70-i so8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--15-140-75-75-c-90-i so8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--18-120-100-100-c-90 -iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-semicondensed--13-120-75-75 -c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859 '
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-o-normal--13-120-75-75-c-70 -iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-o-normal--13-120-75-75-c-80 -iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-o-semicondensed--13-120-75- 75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso88 59'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--6-60-75-75-c-40-i so8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--7-70-75-75-c-50-i so8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--8-80-75-75-c-50-i so8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--9-90-75-75-c-60-i so8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--10-100-75-75-c-60 -iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--13-120-75-75-c-70 -iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--13-120-75-75-c-80 -iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--14-130-75-75-c-70 -iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--15-140-75-75-c-90 -iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--18-120-100-100-c- 90-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--20-200-75-75-c-10 0-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-semicondensed--12-110-75- 75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso88 59'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-semicondensed--13-120-75- 75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso88 59'
Done building font metrics
fixme:wave:ALSA_WaveInit -fixme:wave:ALSA_WaveInit -
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory
fixme:win32:PE_CreateModule Security directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:msvcrt:_fstat :dwFileAttributes = 32, mode set to 0
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7a02074,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7a01e94,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7a02430,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7a02430,0x00000000), stub!
fixme:system:SystemParametersInfoA Unknown action: 113
./bin/cvscedega: line 87:  4702 Segmentation fault      "$ConfigurePrefix/bin/$W ineExecName" "$@"

```

and the error I get when running WoW w/ wine

```

err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/outp ut error)
err:wave:DSDB_MapBuffer Create string value : "HardwareAcceleration" = "Emulatio n" in the registry
under [HKEY_CURRENT_USER\Software\Wine\DirectSound].

```

---

### Post by seethru on 2005-08-16
After days of trying to get this to work, I'm at a loss.

I'm still attempting to use wine, and this is the only error regarding sound when starting WoW.

```
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Create string value : "HardwareAcceleration" = "Emulation" in the registry
```

and here is my wine config file. Could someone please take a look and tell me whats wrong?

```
WINE REGISTRY Version 2
;; inspired by Sidenet (http://sidenet.ddo.jp/winetips/)
;; continued for winetools by Joachim v. Thadden (http://vonthadden.de)
;; Version 2.1.1jo
;; All keys relative to \\Machine\\Software\\Wine\\Wine\\Config

;; If you think it is necessary to show others your complete config for a
;; bug report, filter out empty lines and comments with
;; grep -v "^;" ~/.wine/config | grep '.'

[wine]
"GraphicsDriver" = "x11drv"; (x11drv, ttydrv)
"ShowDotFiles" = "1"
"ShowDirSymlinks" = "1"
"Path" = "c:\\windows;c:\\windows\\system"
"Windows" = "c:\\windows"
"System" = "c:\\windows\\system"
"Temp" = "t:\\"
"Profile" = "c:\\windows\\Profiles\\Administrator"

# [wineconf]

[Version]
; Windows version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win2k3,win20,win30,win31)
; Set version to win98 is recommended.
"Windows" = "winxp"
; DOS version to imitate
; Only effect when "Windows" = "win31"
;"DOS" = "6.22"

; Be careful here, wrong DllOverrides settings have the potential
; to pretty much kill your setup.

[DllOverrides]
; Some native dlls won't work, so leave these builtin.
; Do not modify these lines.
"advapi32"     = "builtin";Native version won't work
"avicap32"     = "builtin";Hardware related
"capi2032"     = "builtin";Completely implemented
"comctl32"     = "builtin";Native version cause bugs.
"comdlg32"     = "builtin";thunk
"crtdll"       = "builtin";Completely implemented
"ctl3d32"      = "builtin";thunk
"d3d8"         = "builtin";Hardware related
"d3d9"         = "builtin";Hardware related
"dbghelp"      = "builtin";Native version won't work
"ddeml"        = "builtin";
"ddraw"        = "builtin";Hardware related
"ddrawex"      = "builtin";Hardware related
"dinput"       = "builtin";
"dinput8"      = "builtin";Hardware related
"dispdib"      = "builtin";Completely implemented
"display.drv"  = "builtin";Hardware related
"dmusic32"     = "builtin";thunk
"dplay"        = "builtin";
"dplayx"       = "builtin";
"dpnet"        = "builtin";
"dsound"       = "builtin";Hardware related
"dswave"       = "builtin";Hardware related
"dxdiagn"      = "builtin";
"gdi.exe"      = "builtin";Hardware related
"gdi32"        = "builtin";Hardware related
"glu32"        = "builtin";Hardware related
"gult32"       = "builtin";Hardware related
"icmp"         = "builtin";Hardware related
"ifsmgr.vxd"   = "builtin";Completely implemented
"imaadp32.acm" = "builtin";Completely implemented
"imm"          = "builtin";Special hack needed
"imm32"        = "builtin";Special hack needed
"iphlpapi"     = "builtin";Hardware related
"joystick.drv" = "builtin";Hardware related
"kernel32"     = "builtin";Hardware related
"keyboard.drv" = "builtin";Hardware related
"krnl386.exe"  = "builtin";Hardware related
"lz32"         = "builtin";Completely implemented
"lzexpand"     = "builtin";Completely implemented
"mcianim.drv"  = "builtin";Completely implemented
"mciavi.drv"   = "builtin";Completely implemented
"mcicda.drv"   = "builtin";Completely implemented
"mciseq.drv"   = "builtin";Completely implemented
"mciwave.drv"  = "builtin";Completely implemented
"midimap.drv"  = "builtin";Completely implemented
"mmsystem"     = "builtin";Hardware related
"mouse.drv"    = "builtin";Hardware related
"mpr"          = "builtin";thunk
"msacm.drv"    = "builtin";Completely implemented
"msacm32"      = "builtin";thunk
"msadp32.acm"  = "builtin";Completely implemented
"msvfw32"      = "builtin";Hardware related
"msvidc32"     = "builtin";Completely implemented
"mswsock"      = "builtin";Hardware related
"newdev"       = "builtin";Hardware related
"ntdll"        = "builtin";Hardware related
"opengl32"     = "builtin";Hardware related
"psapi"        = "builtin";Hardware related
"rasapi16"     = "builtin";Hardware related
"rasapi32"     = "builtin";Hardware related
"serialui"     = "builtin";Hardware related
"setupapi"     = "builtin";thunk
"shell"        = "builtin";Special hack needed
"shell32"      = "builtin";Special hack needed
"snmpapi"      = "builtin";Hardware related
"sound"        = "builtin";Hardware related
"sti"          = "builtin";Hardware related
"system.drv"   = "builtin";Hardware related
"tapi32"       = "builtin";Hardware related
"toolhelp"     = "builtin";Hardware related
"twain"        = "builtin";Hardware related
"twain_32"     = "builtin";Hardware related
"user.exe"     = "builtin";Hardware related
"user32"       = "builtin";Hardware related
"ver"          = "builtin";Special hack needed
"version"      = "builtin";Special hack needed
"vnbt.vxd"     = "builtin";
"vtdapi.vxd"   = "builtin";
"vwin32.vxd"   = "builtin";Hardware related
"w32skrnl"     = "builtin";Hardware related
"w32sys"       = "builtin";Hardware related
"win32s16"     = "builtin";Hardware related
"win87em"      = "builtin";Hardware related
"winaspi"      = "builtin";Hardware related
"wing"         = "builtin";Hardware related
"winmm"        = "builtin";Hardware related
"winnls32"     = "builtin";thunk
"winsock"      = "builtin";Hardware related
"wintab"       = "builtin";Hardware related
"wintab32"     = "builtin";Hardware related
"wnaspi32"     = "builtin";Hardware related
"wow32"        = "builtin";
"wprocs"       = "builtin";Hardware related
"ws2_32"       = "builtin";Hardware related
"wsock32"      = "builtin";Hardware related

;Windows Installer
; Install InstMsiA.exe if you get some errors.
"msi"         = "native"

; DCOM 98
; If you'd like to go without DCOM98, remove this line.
"ole32"        = "native"

; Windows ODBC
; If you'd like to use UNIX ODBC, remove this line.
"odbc32"       = "native, builtin"

; AcroReader 6 ActiveX plugin
; must be disabled because it crashes IE6
"pdf.ocx" = "builtin"

; you can specify applications too
; this one will apply for all notepad.exe
;"*notepad.exe" = "native, builtin"
; this one will apply only for a particular file
;"C:\\windows\\regedit.exe" = "native, builtin"

; some spy or definitely not working programs we don't like to be started
"*autorun.exe" = "native,builtin"
"*ctfmon.exe" = "builtin"
"*ddhelp.exe" = "builtin"
"eMusicClient.exe" = "builtin"
"*findfast.exe" = "builtin"
"icwconn1.exe" = "builtin"	;Prevent from loading ICW even if registry key was changed
"*maildoff.exe" = "builtin"
"*mdm.exe" = "builtin"
"*mosearch.exe" = "builtin"
;"*pstores.exe" = "builtin"	; needed for IE installation
"qttask.exe" = "builtin"
"realsched.exe" = "builtin"
"winampa.exe" = "builtin"
"AGENTSVR.EXE" = "builtin"

; default for all other dlls and executables
"*" = "native, builtin"
;"*" = "builtin, native"

[x11drv]
; Number of colors to allocate from the system palette
"AllocSystemColors" = "100"
; Use a private color map
"PrivateColorMap" = "N"
; Favor correctness over speed in some graphics operations
"PerfectGraphics" = "N"
; Color depth to use on multi-depth screens
;;"ScreenDepth" = "16"
; Allow the window manager to manage created windows
"Managed" = "Y"
; Use a desktop window of 640x480 for Wine
;"Desktop" = "1024x768"
; Use XFree86 DGA extension if present
; (make sure /dev/mem is accessible by you !)
"UseDGA" = "N"
; Use XVidMode extension if present
"UseXVidMode" = "Y"
; Use XRandR extension if present
"UseXRandR" = "N"
; Use the take focus protocol
"UseTakeFocus" = "Y"
; Enable DirectX mouse grab
"DXGrab" = "Y"
; Create the desktop window with a double-buffered visual
; (useful to play OpenGL games)
"DesktopDoubleBuffered" = "Y"
; Run in synchronous mode (useful for debugging X11 problems)
;;"Synchronous" = "Y"
;
; Use the Render extension to render client side fonts (default "Y")
;;"ClientSideWithRender" = "Y"
; Fallback on X core requests to render client side fonts (default "Y")
;;"ClientSideWithCore" = "Y"
; Set both of the previous two to "N" in order to force X11 server side fonts
;
; Anti-alias fonts if using the Render extension (default "Y")
;;"ClientSideAntiAliasWithRender" = "Y"
; Anti-alias fonts if using core requests fallback (default "Y")
;;"ClientSideAntiAliasWithCore" = "Y"
;
; Use the X Input Method (default "Y") 
;;"UseXIM" = "Y" 
; XIM Input Style (onthespot, offthespot, overthespot ,root) 
;;"InputStyle" = "onthespot" 
;
; Codepage for clipboard (0 for ANSI, 20932 for euc-jp)
"TextCP" = "0"

;[ppdev]
;; key:  io-base of the emulated port
;; value : parport-device{,timeout}
;; timeout for auto closing an open device ( not yet implemented)
;"378" = "/dev/parport0"
;"278" = "/dev/parport1"
;"3bc" = "/dev/parport2"

;[spooler]
;;Wine detects CUPS configuration automaticly.
;"FILE:" = "tmp.ps"
;"LPT1:" = "|lpr"
;"LPT2:" = "|gs -sDEVICE=bj200 -sOutputFile=/tmp/fred -q -"
;"LPT3:" = "/dev/lp3"

;[ports]
;"read"  = "0x779,0x379,0x280-0x2a0"
;"write" = "0x779,0x379,0x280-0x2a0"

;[Debug]
;"RelayExclude" = "RtlEnterCriticalSection;RtlLeaveCriticalSection"
;"RelayInclude" = "user32.CreateWindowA"
;"RelayFromExclude" = "user32;x11drv"
;"RelayFromInclude" = "sol.exe"
;"SnoopExclude" = "RtlEnterCriticalSection;RtlLeaveCriticalSection"
;"SpyExclude" = "WM_SIZE;WM_TIMER;"

[registry]
;These are all booleans.  Y/y/T/t/1 are true, N/n/F/f/0 are false.
;Defaults are read all, write to Home
; Where to find the global registries
;"GlobalRegistryDir" = "/etc";
; Global registries (stored in /etc)
"LoadGlobalRegistryFiles" = "Y"
; Load Windows registries from the Windows directory
"LoadWindowsRegistryFiles" = "Y"
; Registry periodic save timeout in seconds
; "PeriodicSave" = "600"
; Save only modified keys
"SaveOnlyUpdatedKeys" = "Y"

[Clipboard]
"ClearAllSelections" = "0"
"PersistentSelection" = "1"
"UsePrimary" = "0"

; List of all directories directly contain .AFM files
;[afmdirs]
;"1" = "/usr/share/ghostscript/fonts"
;"2" = "/usr/share/a2ps/afm"
;"3" = "/usr/share/enscript"
;"4" = "/usr/X11R6/lib/X11/fonts/Type1"

[WinMM]
; Uncomment the "Drivers" line matching your sound setting.

;"Drivers" = "wineoss.drv"      ; default for most common configurations
;"Drivers" = "winearts.drv"    ; for KDE
"Drivers" = "winealsa.drv"    ; for ALSA users
;"Drivers" = "winejack.drv"    ; for Jack sound server
;"Drivers" = "winenas.drv"     ; for NAS sound system
;"Drivers" = "wineaudioio.drv" ; for Solaris machines
;"Drivers" = ""                ; to disable sound
"WaveMapper" = "msacm.drv"
"MidiMapper" = "midimap.drv"

[dsound]
;; HEL only: Number of waveOut fragments ahead to mix in new buffers.
;"HELmargin" = "5"
;; HEL only: Number of waveOut fragments ahead to queue to driver.
;"HELqueue" = "5"
;; Max number of fragments to prebuffer
;"SndQueueMax" = "28"
;; Min number of fragments to prebuffer
;"SndQueueMin" = "12"
;; Forces emulation mode (using wave api)
;"HardwareAcceleration" = "Emulation"
;; Sets default playback device (0 - number of devices - 1)
"DefaultPlayback" = "0"	; use first device (/dev/dsp)
;"DefaultPlayback" = "1" 	; use second device (/dev/dsp1)
;"DefaultPlayback" = "2" 	; use third device (/dev/dsp2)
;; Sets default capture device (0 - number of devices - 1)
;"DefaultCapture" = "0"		; use first device (/dev/dsp)
;"DefaultCapture" = "1"		; use second device (/dev/dsp1)
;"DefaultCapture" = "2"		; use third device (/dev/dsp2)

[Network]
;; Use the DNS (Unix) host name always as NetBIOS "ComputerName" (boolean, default "Y").
;; Set to N if you need a persistent NetBIOS ComputerName that possibly differs 
;; from the Unix host name. You'll need to set ComputerName in 
;; HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ComputerName\ComputerName, too.
;"UseDnsComputerName" = "N"

;; Application specific configuration

; 3 InstallShield versions who like to put their full screen window in front,
; without any chance to switch to another X11 application.
; So just catch them in a desktop window.
; Note: KDE handles this correctry.
;
;[AppDefaults\\_INS0432._MP\\x11drv]
;"Desktop" = "640x480"
;
;[AppDefaults\\_INS0466._MP\\x11drv]
;"Desktop" = "640x480"
;
;[AppDefaults\\_INS0576._MP\\x11drv]
;"Desktop" = "640x480"
;
;[AppDefaults\\_INS5176._MP\\x11drv]
;"Desktop" = "640x480"
;
;[AppDefaults\\_INS5576._MP\\x11drv]
;"Desktop" = "800x600"


;Disable window management for some apps.
;
;Densi denwachou 2003
[AppDefaults\\Blarea8.exe\\x11drv]
"Managed" = "N"
;
;Half Life Demo
[AppDefaults\\hldemo.exe\\x11drv]
"Managed" = "N"
;
;Real Player 10
[AppDefaults\\realplay.exe\\x11drv]
"Managed" = "N"
;
;Winamp
[AppDefaults\\winamp.exe\\x11drv]
"Managed" = "N"


;;Some apps work better with native comctl32
;;NOTE: May cause side effects
;
;;Winamp
;[AppDefaults\\winamp.exe\\DllOverrides]
;"comctl32" = "native"
;
;;WinnyP
;[AppDefaults\\winnyp.exe\\DllOverrides]
;"comctl32" = "native"
;
;;Lunascape
;[AppDefaults\\Luna.exe\\DllOverrides]
;"comctl32" = "native"
;
;;Mame file 2
;[AppDefaults\\mame2.exe\\DllOverrides]
;"comctl32" = "native"


;OpenJane_IE sppedup hack
[AppDefaults\\Jane2ch.exe\\DllOverrides]
"mlang" = "builtin, native"
;"comctl32" = "native"
;;Internet Explorer
;[AppDefaults\\iexplore.exe\\DllOverrides]
;"mlang" = "builtin, native"

;IE4,5,6 Installer
[AppDefaults\\acmsetup.exe\\DllOverrides]
"*comctl32" = "builtin"
[AppDefaults\\grpconv.exe\\DllOverrides]
"*comctl32" = "builtin"
[AppDefaults\\iebatch.exe\\DllOverrides]
"*comctl32" = "builtin"
[AppDefaults\\updcrl.exe\\DllOverrides]
"*comctl32" = "builtin"

;;Windows Media Player 9 Installer
;;WARNING: Windows Media Player 9 Installer may brake your setup!
;[AppDefaults\\setup_wm.exe\\Version]
;"Windows" = "winme"
;[AppDefaults\\setup_wm.exe\\DllOverrides]
;"msvcrt" = "builtin"


;;Example: Catch setup.exe in a desktop window.
;[AppDefaults\\setup.exe\\x11drv]
;"Desktop" = "800x600"

;;Example: Catch full screen games in a desktop window.
;;Half Life Demo
;[AppDefaults\\hldemo.exe\\x11drv]
;"Desktop" = "640x480"

;;Example: XIM Input Style
;[AppDefaults\\notepad.exe\\x11drv]
;"InputStyle" = "offthespot"

;;Example: Windows version
;[AppDefaults\\sol.exe\\Version]
;"Windows" = "nt40"

;; You can add an AppDefault entry like this for such cases.
;[AppDefaults\\pickygame.exe\\dsound]
;"EmulDriver" = "N"

;[AppDefaults\\control.exe\\DllOverrides]
;"ole32"   = "builtin"
;"shlwapi" = "builtin"
;"shell32" = "builtin"
;"*" = "builtin, native"

[AppDefaults\\QuickTimePlayer.exe\\x11drv]
"Managed" = "N"
"Desktop" = "1024x768"

;[AppDefaults\\QuickTimePlayer.exe\\DllOverrides]
;"ddraw" = ""

[AppDefaults\\wmplayer2.exe\\DllOverrides]
"ddraw" = ""

;AcroReader 6
[AppDefaults\\AcroRd32.exe\\Version]
"Windows" = "win2k"

;Real Player 10
[AppDefaults\\realplay.exe\\x11drv]
"Managed" = "N"
"Desktop" = "1024x768"

[AppDefaults\\realplay.exe\\DllOverrides]
"ddraw" = ""

; Awasu RSS Feed Reader
[AppDefaults\\awasu.exe\\Version]
"Windows" = "win2k"

; Bottler XDCC Bott Interface
[AppDefaults\\Bottler.exe\\Version]
"Windows" = "win2k"

; PowBallDX
[AppDefaults\\PowBallDX.exe\\x11drv]
"Desktop" = "640x480"
"Managed" = "Y"
"PerfectGraphics" = "Y"

[AppDefaults\\PowBallDX.exe\\DllOverrides]
"ddraw" = ""

; Miranda IM
[AppDefaults\\miranda32.exe\\Version]
"Windows" = "winxp"

; Wegweiser (Agenda)
[AppDefaults\\WEGWEISER.EXE\\x11drv]
"Desktop" = ""360x500""
"Managed" = "N"

; TVgenial
[AppDefaults\\TVgenial.exe\\x11drv]
"Desktop" = "1024x768"
"Managed" = "N"

; PhotoFiltre
[AppDefaults\\PhotoFiltre.exe\\DllOverrides]
"twain_32" = ""

; KLV 4
[AppDefaults\\klv.exe\\x11drv]
"Desktop" = "1024x768"
"Managed" = "Y"

; MailWasher Pro
[AppDefaults\\MailWasher.exe\\DllOverrides]
"comctl32" = "native"

# [/wineconf]
```

---

### Post by und3rdog on 2005-08-16
I have the same problem with D2, everything runs, just no sound!  Hoary walkthrough was all I needed to have sound in other apps (xmms, mplayer, realplayer).  I'm wondering what [dsound] setting I'm missing.

---

### Post by seethru on 2005-08-17
well, it's still giving me the sound error, but it also looks like despite my choosing to use winealsa.drv it's trying to load OSS.....

---

### Post by jumanji on 2005-08-17
Try edit file like this...

[dsound]
;; HEL only: Number of waveOut fragments ahead to mix in new buffers.
;"HELmargin" = "5"
;; HEL only: Number of waveOut fragments ahead to queue to driver.
;"HELqueue" = "5"
;; Max number of fragments to prebuffer
;"SndQueueMax" = "28"
;; Min number of fragments to prebuffer
;"SndQueueMin" = "12"
;; Forces emulation mode (using wave api)

;"HardwareAcceleration" = "Emulation"  <----- REMOVE THE ";" AT THE BEGINNING!!!

;; Sets default playback device (0 - number of devices - 1)
"DefaultPlayback" = "0"	; use first device (/dev/dsp)
;"DefaultPlayback" = "1" 	; use second device (/dev/dsp1)
;"DefaultPlayback" = "2" 	; use third device (/dev/dsp2)
;; Sets default capture device (0 - number of devices - 1)

;"DefaultCapture" = "0"		; use first device (/dev/dsp) <----- REMOVE THE ";" AT THE BEGINNING!!!

;"DefaultCapture" = "1"		; use second device (/dev/dsp1)
;"DefaultCapture" = "2"		; use third device (/dev/dsp2)

save file and try again.. :)

---

### Post by seethru on 2005-08-17
[QUOTE=jumanji]Try edit file like this...

[dsound]
;; HEL only: Number of waveOut fragments ahead to mix in new buffers.
;"HELmargin" = "5"
;; HEL only: Number of waveOut fragments ahead to queue to driver.
;"HELqueue" = "5"
;; Max number of fragments to prebuffer
;"SndQueueMax" = "28"
;; Min number of fragments to prebuffer
;"SndQueueMin" = "12"
;; Forces emulation mode (using wave api)

;"HardwareAcceleration" = "Emulation"  <----- REMOVE THE ";" AT THE BEGINNING!!!

;; Sets default playback device (0 - number of devices - 1)
"DefaultPlayback" = "0"	; use first device (/dev/dsp)
;"DefaultPlayback" = "1" 	; use second device (/dev/dsp1)
;"DefaultPlayback" = "2" 	; use third device (/dev/dsp2)
;; Sets default capture device (0 - number of devices - 1)

;"DefaultCapture" = "0"		; use first device (/dev/dsp) <----- REMOVE THE ";" AT THE BEGINNING!!!

;"DefaultCapture" = "1"		; use second device (/dev/dsp1)
;"DefaultCapture" = "2"		; use third device (/dev/dsp2)

save file and try again.. :)[/QUOTE]

still no sound, same error :/

```
err:wave:DSDB_MapBuffer Create string value : "HardwareAcceleration" = "Emulation" in the registry
under [HKEY_CURRENT_USER\Software\Wine\DirectSound].
```

edit: I manually created the "HardwareAcceleration" = "Emulation" key. New error now :)

```
fixme:wave:OSS_AddRingMessage two fast messages in the queue!!!! toget = 4(WINE_WM_RESTARTING), tosave=5(UNKNOWN(0x00000000))
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.err:wave:wodPlayer_Reset grin
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=16384 < primary_done=40572)
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7bcbada8
```

---

### Post by seethru on 2005-08-17
edit: I manually created the "HardwareAcceleration" = "Emulation" key. New error now :)

```
fixme:wave:OSS_AddRingMessage two fast messages in the queue!!!! toget = 4(WINE_WM_RESTARTING), tosave=5(UNKNOWN(0x00000000))
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.err:wave:wodPlayer_Reset grin
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=16384 < primary_done=40572)
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7bcbada8
```

---

### Post by jumanji on 2005-08-17
...do you use latest version of Wine(20050725)?

---

### Post by seethru on 2005-08-17
[QUOTE=jumanji]...do you use latest version of Wine(20050725)?[/QUOTE]
 I sure do, thats why I don't understand why such an issue with sound lol.

---

### Post by jumanji on 2005-08-17
Have you tried the "winecfg" command in a Terminal window, and configured your game from there?

---

### Post by seethru on 2005-08-17
[QUOTE=jumanji]Have you tried the "winecfg" command in a Terminal window, and configured your game from there?[/QUOTE]
 did not even know that exists, ty will try that :)

ok, booted back to *nix finally to give this a go. Ran it, told it to autodetect the sound, and it chose OSS. When I clicked configure it said it couldn't open wineoss.drv.

---

### Post by seethru on 2005-08-18
[QUOTE=seethru]did not even know that exists, ty will try that :)

ok, booted back to *nix finally to give this a go. Ran it, told it to autodetect the sound, and it chose OSS. When I clicked configure it said it couldn't open wineoss.drv.[/QUOTE]
 broke down and bought cedega/point2play. I must say, I'm impressed.

---

### Post by VvWolverinevV on 2008-02-21
My WINE sound test (through winecfg) was working fine but I was getting no sound at all in WoW.  Thanks to a suggestion in the ##wow channel on irc.freenode.net, **I tried running WoW as root, and voila!  Perfect sound!**  The screen was a little messed up at first, so I had to modify config.wtf to login the first time.  My ONLY remaining complaint is a very slightly laggy mouse cursor due to the lack of hardware mouse support in the openGL API: [http://ubuntuforums.org/showthread.php?t=340193](http://ubuntuforums.org/showthread.php?t=340193)

---

### Post by kopilo on 2008-02-21
How I fixed sound with wine...
press:alt + f2 type: winecfg

*click audio and wait for... 2 minutes for it to load*
Deselected everything but ALSA Driver, pressed ok

opened terminal and typed: alsamixer
increased values, pressed esc.

Opened WoW with: aoss wine >insertpath< -opengl

---

### Post by VvWolverinevV on 2008-02-21
After some more testing, I finally found that the problem is in setting winecfg to to use Vista mode.  All of the other versions of Windows have working sound, but they seem to have some memory dumping issues.  I would like to get sound working in Vista mode.  Does anyone have any ideas?

---

### Post by thisismalhotra on 2008-03-12
> **VvWolverinevV said:**
> After some more testing, I finally found that the problem is in setting winecfg to to use Vista mode.  All of the other versions of Windows have working sound, but they seem to have some memory dumping issues.  I would like to get sound working in Vista mode.  Does anyone have any ideas?

Thanks for the tip dude I had a perfect wow install but sound and as soon as I changed it to XP it worked like magic !!

---

### Post by nfear24 on 2008-06-10
> **thisismalhotra said:**
> Thanks for the tip dude I had a perfect wow install but sound and as soon as I changed it to XP it worked like magic !!

Ya thanks alot.  I was running into the same problem.  Works perfect in windows xp mode.  My mouse still seems slow or laggy even though the game is running fine.  I do notice that I get about half the fps in linux vs vista.  When running the game in vista Im around 60-65 fps and in linux wine I get around 30-35.  I think part of the problem for me though is the poor nvidia linux drivers.

---

### Post by Ranidan on 2008-07-06
> **kopilo said:**
> How I fixed sound with wine...
press:alt + f2 type: winecfg

*click audio and wait for... 2 minutes for it to load*
Deselected everything but ALSA Driver, pressed ok

opened terminal and typed: alsamixer
increased values, pressed esc.

Opened WoW with: aoss wine >insertpath< -opengl

When I opened alsamixer, I noticed the MM in the center.  This whole time, the thing was on mute.  I kicked myself.  It works fine now, thanks!

---

### Post by Diskbox on 2010-08-25
Finally my sound is *mostly* working with wine/wow.

Thanks to the above post I changed my winecfg settings from Windows 7 to XP and now it's working.

However, in wow I now have system default, default, default  (yes default twice) in the sound options.  It seems to work on one then after a random period all sound goes and I have to go in and change it to another to get it back.  This process keeps going for hours and I cycle through all the options.

Now that I can hear sounds, anyone have an idea how to keep it working?

ps. I'm using Creative Arena Gaming headphones though it happens when I'm not too.

---

### Post by -=- Mr. Tux -=- on 2011-07-05
so i looked this up cause likewise same error... however i have got sound working in guild wars xfire and other windows games im runnin on this machine  however i have noticed that sound in other programs can be dependent on resources im using  for example if i start the wow installer before i run xfire the sounds that were handled well n normal before become choppy...  i just stumbled on this thread so im gonna take a minute n see  in your winecfg make sure the sound is set to emulation... and not full... that seems to be the big problem with guild wars... try that if you havent

---

### Post by -=- Mr. Tux -=- on 2011-07-05
i just found out that since im using winetricks to run wow and have installed other programs manually winetricks set its own prefixes for wow...  so i had to change those manually again sound from full to emulation.

sound works fine... after a restart no broken choppy audio as well.

runs great

---

