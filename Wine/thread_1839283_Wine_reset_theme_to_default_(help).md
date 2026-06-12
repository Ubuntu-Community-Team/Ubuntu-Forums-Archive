---
title: "Wine: reset theme to default (help)"
date: 2011-09-05
forum: Wine
---

### Post by astrobob.tk on 2011-09-05
Hello guys,

I recently, & by mistake, changed the default theme of wine to a theme used by a software I use under wine; the theme is one a "red mode" or "night mode" one used in astronomy softwares.

The result is as in the attchement & is annoying.

I am writing for help in reseting the themeto the default one.

thanks in advance

---

### Post by astrobob.tk on 2011-09-06
bump

---

### Post by astrobob.tk on 2011-09-22
anyone pleasee ?!

---

### Post by astrobob.tk on 2012-02-04
bump :S

---

### Post by Toz on 2012-02-04
In that same screenshot, there is a "Desktop Integration" tab that allows you to specify/change appearance properties. How are they currently set?

EDIT: And can you also post back the first 50 lines of the file **~/.wine/user.reg**?

---

### Post by astrobob.tk on 2012-02-04
> **Toz said:**
> In that same screenshot, there is a "Desktop Integration" tab that allows you to specify/change appearance properties. How are they currently set?

EDIT: And can you also post back the first 50 lines of the file **~/.wine/user.reg**?

attached is the Desktop Integration section: all is empty!

which part of user.reg do you need? it's long & I already located parts where there the problem lies!

---

### Post by Toz on 2012-02-04
The [Control Panel\\Colors] section would be of interest. Plus the areas where you think the problem lies.

Also, can you unset the theme change you made in the astronomy program?

---

### Post by astrobob.tk on 2012-02-04
>  Also, can you unset the theme change you made in the astronomy program?What I did is not set the theme in the program. I mistakingly used the "Install themes" under "Desktop Integration & selected the theme used by the astro program! I cannot unset it (see attachements).

> **Toz said:**
> The [Control Panel\\Colors] section would be of interest. Plus the areas where you think the problem lies.

The software is called "BisqueSoftware **TheSky** 6", and the theme used by it is called "TheSky 6 Night Vision Mode.Theme".

First let me start with the keyword "theme":
```
[Software\\Microsoft\\Windows\\CurrentVersion\\ThemeManager] 1313370004
"ThemeActive"="0"

[Software\\Microsoft\\Windows\\CurrentVersion\\Themes\\InstalledThemes] 1313367859

```As for those containing "TheSky" & the part you asked for:

```
WINE REGISTRY Version 2
;; All keys relative to \\User\\S-1-5-21-0-0-0-1000

#arch=win32

[AppEvents\\Schemes\\Apps\\.Default\\MenuPopup] 1318331095

[AppEvents\\Schemes\\Apps\\Explorer\\Navigating\\.Current] 1285107448
@=""

[AppEvents\\Schemes\\Apps\\TheSky6\\Background] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\End] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\Identify] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\ImageLink] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewAbort] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewDuring] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewEnd] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewStart] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\Start] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\TelescopeEstablish] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\TelescopeSuspend] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\TelescopeTerminate] 1313368232

[Console] 1312237924
"CursorSize"=dword:00000019
"CursorVisible"=dword:00000001
"EditionMode"=dword:00000000
"ExitOnDie"=dword:00000001
"FaceName"="Lucida Console\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"
"FontSize"=dword:0010000a
"FontWeight"=dword:00000000
"HistoryBufferSize"=dword:00000032
"HistoryNoDup"=dword:00000000
"MenuMask"=dword:00000000
"QuickEdit"=dword:00000000
"ScreenBufferSize"=dword:00190050
"ScreenColors"=dword:0000000f
"WindowSize"=dword:00190050

**[Control Panel\\Colors] 1313370004**
"ActiveBorder"="128 0 0"
"ActiveTitle"="128 0 0"
"AppWorkSpace"="100 0 0"
"Background"="128 0 0"
"ButtonAlternateFace"="181 181 181"
"ButtonDkShadow"="128 0 0"
"ButtonFace"="128 0 0"
"ButtonHilight"="200 0 0"
"ButtonLight"="212 208 200"
"ButtonShadow"="85 0 0"
"ButtonText"="0 0 0"
"GradientActiveTitle"="166 202 240"
"GradientInactiveTitle"="192 192 192"
"GrayText"="130 0 0"
"Hilight"="120 0 0"
"HilightText"="225 0 0"
"HotTrackingColor"="0 0 128"
"InactiveBorder"="128 0 0"
"InactiveTitle"="0 0 0"
"InactiveTitleText"="128 0 0"
"InfoText"="0 0 0"
"InfoWindow"="255 255 225"
"Menu"="128 0 0"
"MenuBar"="212 208 200"
"MenuHilight"="10 36 106"
"MenuText"="0 0 0"
"Scrollbar"="200 0 0"
"TitleText"="0 0 0"
"Window"="128 0 0"
"WindowFrame"="128 0 0"
"WindowText"="0 0 0"

[Control Panel\\Desktop] 1285107448
"DragFullWindows"="0"
"FontSmoothing"="0"
"LowPowerActive"="0"
"MenuShowDelay"="400"
"SmoothScroll"=hex:00,00,00,00
"UserPreferenceMask"=hex:10,00,00,80

[Control Panel\\Desktop\\WindowMetrics] 1313370004
"BorderWidth"="1"
"CaptionFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,bc,02,00,00,\
  00,00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,20,\
  00,44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"CaptionHeight"="18"
"CaptionWidth"="18"
"IconFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,90,01,00,00,00,\
  00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,20,00,\
  44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"MenuFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,90,01,00,00,00,\
  00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,20,00,\
  44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"MenuHeight"="18"
"MenuWidth"="18"
"MessageFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,90,01,00,00,\
  00,00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,20,\
  00,44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"ScrollHeight"="16"
"ScrollWidth"="16"
"Shell Icon Size"="32"
"SmCaptionFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,90,01,00,\
  00,00,00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,\
  20,00,44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"SmCaptionHeight"="15"
"SmCaptionWidth"="13"
"StatusFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,90,01,00,00,\
  00,00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,20,\
  00,44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00

[Control Panel\\International] 1285107438
"iCalendarType"="1"
"iCountry"="1"
"iCurrDigits"="2"
"iCurrency"="0"
"iDate"="0"
"iDigits"="2"
"iFirstDayOfWeek"="6"
"iFirstWeekOfYear"="0"
"iLDate"="0"
"iLZero"="1"
"iMeasure"="1"
"iNegCurr"="0"
"iNegNumber"="1"
"iPaperSize"="1"
"iTime"="0"
"iTimePrefix"="0"
"iTLZero"="0"
"LC_CTYPE"="00000409"
"LC_MEASUREMENT"="00000409"
"LC_MONETARY"="00000409"
"LC_NUMERIC"="00000409"
"LC_PAPER"="00000409"
"LC_TELEPHONE"="00000409"
"LC_TIME"="00000409"
"Locale"="00000409"
"Numshape"="1"
"s1159"="AM"
"s2359"="PM"
"sCountry"="United States"
"sCurrency"="$"
"sDate"="/"
"sDecimal"="."
"sGrouping"="3;0"
"sLanguage"="ENU"
"sList"=","
"sLongDate"="dddd, MMMM dd, yyyy"
"sMonDecimalSep"="."
"sMonGrouping"="3;0"
"sMonThousandSep"=","
"sNativeDigits"="0123456789"
"sNegativeSign"="-"
"sPositiveSign"=""
"sShortDate"="M/d/yyyy"
"sThousand"=","
"sTime"=":"
"sTimeFormat"="h:mm:ss tt"
"sYearMonth"="MMMM, yyyy"

[Environment] 1285107444
"TEMP"="C:\\users\\astrobob\\Temp"
"TMP"="C:\\users\\astrobob\\Temp"

[Keyboard Layout\\Preload] 1285107439
"1"="00000409"

```There are also the following parts containing "TheSky":

```
[Software\\Microsoft\\Windows\\CurrentVersion\\App Paths\\C:\\SB.NET\\Apps\\TheSky\\Release\\TheSky6.exe] 1313368173
@="C:\\Program Files\\Astro\\Software Bisque\\TheSky6\\C:\\SB.NET\\Apps\\TheSky\\Release\\TheSky6.exe"
"Path"="C:\\Program Files\\Astro\\Software Bisque\\TheSky6;C:\\Program Files\\Common Files\\System"
``````
[Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\{14B3706A-EFED-4945-AD7C-DEA92D8BA665}] 1313368173
"DisplayName"="TheSky6"
"DisplayVersion"="6.0"
"InstallLocation"="C:\\Program Files\\Astro\\Software Bisque\\TheSky6"
"LogFile"="C:\\users\\astrobob\\Application Data\\InstallShield Installation Information\\{14B3706A-EFED-4945-AD7C-DEA92D8BA665}\\setup.ilg"
"LogMode"=dword:00000001
"MajorVersion"=dword:00000006
"MinorVersion"=dword:00000000
"ProductGuid"="{14B3706A-EFED-4945-AD7C-DEA92D8BA665}"
"UninstallString"="RunDll32 C:\\PROG~FBU\\COMM~CP1\\INST~JM1\\PROF~WEJ\\RunTime\\09\\01\\Intel32\\Ctor.dll,LaunchSetup \"C:\\users\\astrobob\\Application Data\\InstallShield Installation Information\\{14B3706A-EFED-4945-AD7C-DEA92D8BA665}\\setup.exe\" -l0x9 "
"Version"=dword:06000000
``````
[Software\\Software Bisque\\TheSky6\\6.0] 1313367859

[Software\\Software Bisque\\TheSky6\\App] 1313370527

[Software\\Software Bisque\\TheSky6\\BASEADDRESS] 1313368232

[Software\\Software Bisque\\TheSky6\\CLINK] 1315836122

[Software\\Software Bisque\\TheSky6\\DATABASE] 1313368232

[Software\\Software Bisque\\TheSky6\\Database Query] 1313368232

[Software\\Software Bisque\\TheSky6\\Find Dialog] 1313372062
"Dialog Height"=dword:0000029b
"Dialog Width"=dword:000001a2
"Dialog X"=dword:00000263
"Dialog Y"=dword:00000079

[Software\\Software Bisque\\TheSky6\\FOVI Dialog] 1313699096
"Column 1 Width"=dword:0000012e
"Column 2 Width"=dword:00000032
"Column 3 Width"=dword:00000064
"Column 4 Width"=dword:0000006c
"Column 5 Width"=dword:00000048

[Software\\Software Bisque\\TheSky6\\FOVI Sheet] 1313701117
"Active Page"=dword:00000000

[Software\\Software Bisque\\TheSky6\\General] 1313368700
"Color"=dword:00000001
"ObjectTips"=dword:00000000
"ToolTips"=dword:00000001

[Software\\Software Bisque\\TheSky6\\Horizon] 1313368233
"Filename"="C:\\users\\astrobob\\My Documents\\Software Bisque\\TheSky6\\Horizons\\Default horizon.horizon"

[Software\\Software Bisque\\TheSky6\\Id Window] 1313548890
"Size"=dword:00000001

[Software\\Software Bisque\\TheSky6\\Image Link] 1313368232

[Software\\Software Bisque\\TheSky6\\LX200] 1315836131

[Software\\Software Bisque\\TheSky6\\LX200Focuser] 1315836131
"Large"=dword:000003e8
"Small"=dword:00000032

[Software\\Software Bisque\\TheSky6\\MISCELLANEOUS] 1313368233

[Software\\Software Bisque\\TheSky6\\MKS] 1313368232

[Software\\Software Bisque\\TheSky6\\Object Paths] 1313548650

[Software\\Software Bisque\\TheSky6\\Options] 1313368228

[Software\\Software Bisque\\TheSky6\\PATHS] 1313372955
"Documents"="My Documents"

[Software\\Software Bisque\\TheSky6\\Recent File List] 1325287787
"File1"="C:\\users\\astrobob\\My Documents\\Software Bisque\\TheSky6\\Documents\\Normal Mode_West_Beirut_Sky6.sky"
"File2"="C:\\Program Files\\Astro\\Software Bisque\\TheSky6\\Data\\User\\Documents\\Chart Mode_West_Beirut_Sky6.sky"
"File3"="C:\\users\\astrobob\\My Documents\\Software Bisque\\TheSky6\\Documents\\Classic.sky"
"File4"="C:\\users\\astrobob\\My Documents\\Software Bisque\\TheSky6\\Documents\\Normal.sky"

[Software\\Software Bisque\\TheSky6\\Registration] 1313367724
"Company"="Astrobob"
"Name"="Astrobob"
"Serial Number"="4150-F5AC60EF"

[Software\\Software Bisque\\TheSky6\\SATPROP] 1313368232

[Software\\Software Bisque\\TheSky6\\SBTELEPROTOCOL] 1315836122

[Software\\Software Bisque\\TheSky6\\SERVER] 1313368226

[Software\\Software Bisque\\TheSky6\\Settings] 1313369175
"WindowPos"="0,1,-1,-1,40,4,37,4,1600,899"

[Software\\Software Bisque\\TheSky6\\Sky Calender] 1313548845
"Dialog Height"=dword:000001c2
"Dialog Width"=dword:00000320
"Dialog X"=dword:00000190
"Dialog Y"=dword:000000e1

[Software\\Software Bisque\\TheSky6\\Sound] 1313368702
"BackgroundBase"=dword:0000001e
"BackgroundDelay"=dword:0000001e

[Software\\Software Bisque\\TheSky6\\STARTUP] 1313368233

[Software\\Software Bisque\\TheSky6\\STARTUPV6] 1313548931
"File"="Normal Mode_West_Beirut_Sky6.sky"
"Folder"="My Documents"

[Software\\Software Bisque\\TheSky6\\TELESCOPE] 1315836157
"Name"="LX200 non GPS by Meade Instruments Corporation"

[Software\\Software Bisque\\TheSky6\\Time Picker] 1315836293
"24-Hour Clock"=dword:00000000
"Analog/Digital"=dword:00000000
"Dialog Size"=dword:00000000
"Skip Text"="1x (real time)"

[Software\\Software Bisque\\TheSky6\\Tip] 1313369763
"FilePos"=dword:000000f5
"Startup"=dword:00000001
"TimeStamp"="Mon Jan 26 17:02:36 2004"

[Software\\Software Bisque\\TheSky6\\Warning] 1313705737
"Center Object"=dword:00000001

[Software\\Software Bisque\\TheSky6\\WINDOW-1563] 1325287787
"XPos"=dword:00000241
"YPos"=dword:00000159

[Software\\Software Bisque\\TheSky6\\WINDOW-367] 1313701332
"XPos"=dword:00000443
"YPos"=dword:000000b3

[Software\\Software Bisque\\TheSky6\\WINDOW-374] 1315836293
"XPos"=dword:000004df
"YPos"=dword:000000cd

[Software\\Software Bisque\\TheSky6\\WINDOW-455] 1313368702
"Height"=dword:000000c6
"Width"=dword:000000da
"XPos"=dword:000002c5
"YPos"=dword:00000160

[Software\\Software Bisque\\TheSky6\\WINDOW-478] 1313369763
"XPos"=dword:0000028e
"YPos"=dword:0000013d

[Software\\Software Bisque\\TheSky6\\WINDOW-Bar0] 1313548917
"BarID"=dword:0000e801

[Software\\Software Bisque\\TheSky6\\WINDOW-Bar1] 1313548917
"BarID"=dword:0000800d
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000020
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000000
"MRUDockRightPos"=dword:000000e0
"MRUDockTopPos"=dword:00000000
"MRUFloatStyle"=dword:00002004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"XPos"=dword:fffffffe
"YPos"=dword:fffffffe

[Software\\Software Bisque\\TheSky6\\WINDOW-Bar10] 1313548917
"Bar#0"=dword:00000000
"Bar#1"=dword:000080d0
"Bar#2"=dword:00000000
"BarID"=dword:0000e81f
"Bars"=dword:00000003
"Floating"=dword:00000001
"Horz"=dword:00000001
"XPos"=dword:00000034
"YPos"=dword:00000039

[Software\\Software Bisque\\TheSky6\\WINDOW-Bar2] 1313548917
"BarID"=dword:00008014
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:0000003c
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000000
"MRUDockRightPos"=dword:0000015b
"MRUDockTopPos"=dword:0000001c
"MRUFloatStyle"=dword:00002004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"XPos"=dword:fffffffe
"YPos"=dword:0000001c

[Software\\Software Bisque\\TheSky6\\WINDOW-Bar3] 1313548917
"BarID"=dword:00008015
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000020
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:000000e3
"MRUDockRightPos"=dword:00000273
"MRUDockTopPos"=dword:00000000
"MRUFloatStyle"=dword:00002004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"XPos"=dword:000000e3
"YPos"=dword:fffffffe

[Software\\Software Bisque\\TheSky6\\WINDOW-Bar4] 1313548917
"BarID"=dword:00008016
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:0000005a
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000000
"MRUDockRightPos"=dword:00000154
"MRUDockTopPos"=dword:0000003a
"MRUFloatStyle"=dword:00002000
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"XPos"=dword:fffffffe
"YPos"=dword:0000003a

[Software\\Software Bisque\\TheSky6\\WINDOW-Bar5] 1313548917
"BarID"=dword:00008018
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:0000003c
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:0000015e
"MRUDockRightPos"=dword:0000021e
"MRUDockTopPos"=dword:0000001c
"MRUFloatStyle"=dword:00002004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"XPos"=dword:0000015e
"YPos"=dword:0000001c

[Software\\Software Bisque\\TheSky6\\WINDOW-Bar6] 1313548917
"BarID"=dword:00008017
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:0000003c
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:0000021c
"MRUDockRightPos"=dword:00000297
"MRUDockTopPos"=dword:0000001c
"MRUFloatStyle"=dword:00002004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"XPos"=dword:0000021c
"YPos"=dword:0000001c

[Software\\Software Bisque\\TheSky6\\WINDOW-Bar7] 1313548917
"BarID"=dword:00008022
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:0000003c
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000295
"MRUDockRightPos"=dword:0000031f
"MRUDockTopPos"=dword:0000001c
"MRUFloatStyle"=dword:00002004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"XPos"=dword:00000295
"YPos"=dword:0000001c

[Software\\Software Bisque\\TheSky6\\WINDOW-Bar8] 1313548917
"BarID"=dword:000080d0
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000000
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000000
"MRUDockRightPos"=dword:00000000
"MRUDockTopPos"=dword:00000000
"MRUFloatStyle"=dword:00002000
"MRUFloatXPos"=dword:00000030
"MRUFloatYPos"=dword:00000025
"Visible"=dword:00000000
"XPos"=dword:00000000
"YPos"=dword:00000000

[Software\\Software Bisque\\TheSky6\\WINDOW-Bar9] 1313548917
"Bar#0"=dword:00000000
"Bar#1"=dword:0000800d
"Bar#10"=dword:00000000
"Bar#2"=dword:00008015
"Bar#3"=dword:00000000
"Bar#4"=dword:00008014
"Bar#5"=dword:00008018
"Bar#6"=dword:00008017
"Bar#7"=dword:00008022
"Bar#8"=dword:00000000
"Bar#9"=dword:00008016
"BarID"=dword:0000e81b
"Bars"=dword:0000000b

[Software\\Software Bisque\\TheSky6\\WINDOW-Summary] 1313548746
"Bars"=dword:0000000b
"ScreenCX"=dword:00000640
"ScreenCY"=dword:00000384

[Software\\Software Bisque\\TheSky6\\WindowPlacement] 1325287710
"MAINFRAME"="0,3,-1,-1,-4,28,37,4,1496,820"

[Software\\Software Bisque\\TheSky6\\Workspace] 1315836292
"0"=dword:00000001
"1"=dword:00000000
"2"=dword:00000000
"3"=dword:00000000
"4"=dword:00000000
"5"=dword:00000000
"6"=dword:00000000

``````
[Software\\Wine\\FileOpenAssociations\\.sky] 1313370525
"AppName"="TheSky6 "
"DesktopFile"="/home/astrobob/.local/share/applications/wine-extension-sky.desktop"
"MimeType"="application/x-wine-extension-sky"
"OpenWithIcon"="C2E6_TheSky6.0"
"ProgID"="TheSky6.Document"
```too long!!! sorry

hope this helps ? I appreciate your help & time. thanks

---

### Post by Toz on 2012-02-04
Ok, try this first (make sure that program isn't running). Let's make a backup of the file just in case:
```
cp ~/.wine/user.reg ~/.wine/user.reg.BAK
```

Then, edit the file and delete the entries in red below:
```

WINE REGISTRY Version 2
;; All keys relative to \\User\\S-1-5-21-0-0-0-1000

#arch=win32

[COLOR="Red"][AppEvents\\Schemes\\Apps\\.Default\\MenuPopup] 1318331095[/COLOR]

[AppEvents\\Schemes\\Apps\\Explorer\\Navigating\\.Current] 1285107448
@=""

[COLOR="Red"][AppEvents\\Schemes\\Apps\\TheSky6\\Background] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\End] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\Identify] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\ImageLink] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewAbort] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewDuring] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewEnd] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewStart] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\Start] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\TelescopeEstablish] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\TelescopeSuspend] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\TelescopeTerminate] 1313368232
[/COLOR]
[Console] 1312237924
"CursorSize"=dword:00000019
"CursorVisible"=dword:00000001
"EditionMode"=dword:00000000
"ExitOnDie"=dword:00000001
"FaceName"="Lucida Console\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"
"FontSize"=dword:0010000a
"FontWeight"=dword:00000000
"HistoryBufferSize"=dword:00000032
"HistoryNoDup"=dword:00000000
"MenuMask"=dword:00000000
"QuickEdit"=dword:00000000
"ScreenBufferSize"=dword:00190050
"ScreenColors"=dword:0000000f
"WindowSize"=dword:00190050

[Control Panel\\Colors] 1313370004
[COLOR="Red"]"ActiveBorder"="128 0 0"
"ActiveTitle"="128 0 0"
"AppWorkSpace"="100 0 0"
"Background"="128 0 0"
"ButtonAlternateFace"="181 181 181"
"ButtonDkShadow"="128 0 0"
"ButtonFace"="128 0 0"
"ButtonHilight"="200 0 0"
"ButtonLight"="212 208 200"
"ButtonShadow"="85 0 0"
"ButtonText"="0 0 0"
"GradientActiveTitle"="166 202 240"
"GradientInactiveTitle"="192 192 192"
"GrayText"="130 0 0"
"Hilight"="120 0 0"
"HilightText"="225 0 0"
"HotTrackingColor"="0 0 128"
"InactiveBorder"="128 0 0"
"InactiveTitle"="0 0 0"
"InactiveTitleText"="128 0 0"
"InfoText"="0 0 0"
"InfoWindow"="255 255 225"
"Menu"="128 0 0"
"MenuBar"="212 208 200"
"MenuHilight"="10 36 106"
"MenuText"="0 0 0"
"Scrollbar"="200 0 0"
"TitleText"="0 0 0"
"Window"="128 0 0"
"WindowFrame"="128 0 0"
"WindowText"="0 0 0"[/COLOR]

[Control Panel\\Desktop] 1285107448
"DragFullWindows"="0"
"FontSmoothing"="0"
"LowPowerActive"="0"
"MenuShowDelay"="400"
"SmoothScroll"=hex:00,00,00,00
"UserPreferenceMask"=hex:10,00,00,80

```

Save the file and try running the program again.

---

### Post by astrobob.tk on 2012-02-05
> **Toz said:**
> Ok, try this first (make sure that program isn't running). Let's make a backup of the file just in case:
```
cp ~/.wine/user.reg ~/.wine/user.reg.BAK
```Then, edit the file and delete the entries in red below:
```

WINE REGISTRY Version 2
;; All keys relative to \\User\\S-1-5-21-0-0-0-1000

#arch=win32

[COLOR=Red][AppEvents\\Schemes\\Apps\\.Default\\MenuPopup] 1318331095[/COLOR]

[AppEvents\\Schemes\\Apps\\Explorer\\Navigating\\.Current] 1285107448
@=""

[COLOR=Red][AppEvents\\Schemes\\Apps\\TheSky6\\Background] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\End] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\Identify] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\ImageLink] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewAbort] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewDuring] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewEnd] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\SlewStart] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\Start] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\TelescopeEstablish] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\TelescopeSuspend] 1313368232

[AppEvents\\Schemes\\Apps\\TheSky6\\TelescopeTerminate] 1313368232
[/COLOR]
[Console] 1312237924
"CursorSize"=dword:00000019
"CursorVisible"=dword:00000001
"EditionMode"=dword:00000000
"ExitOnDie"=dword:00000001
"FaceName"="Lucida Console\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"
"FontSize"=dword:0010000a
"FontWeight"=dword:00000000
"HistoryBufferSize"=dword:00000032
"HistoryNoDup"=dword:00000000
"MenuMask"=dword:00000000
"QuickEdit"=dword:00000000
"ScreenBufferSize"=dword:00190050
"ScreenColors"=dword:0000000f
"WindowSize"=dword:00190050

[Control Panel\\Colors] 1313370004
[COLOR=Red]"ActiveBorder"="128 0 0"
"ActiveTitle"="128 0 0"
"AppWorkSpace"="100 0 0"
"Background"="128 0 0"
"ButtonAlternateFace"="181 181 181"
"ButtonDkShadow"="128 0 0"
"ButtonFace"="128 0 0"
"ButtonHilight"="200 0 0"
"ButtonLight"="212 208 200"
"ButtonShadow"="85 0 0"
"ButtonText"="0 0 0"
"GradientActiveTitle"="166 202 240"
"GradientInactiveTitle"="192 192 192"
"GrayText"="130 0 0"
"Hilight"="120 0 0"
"HilightText"="225 0 0"
"HotTrackingColor"="0 0 128"
"InactiveBorder"="128 0 0"
"InactiveTitle"="0 0 0"
"InactiveTitleText"="128 0 0"
"InfoText"="0 0 0"
"InfoWindow"="255 255 225"
"Menu"="128 0 0"
"MenuBar"="212 208 200"
"MenuHilight"="10 36 106"
"MenuText"="0 0 0"
"Scrollbar"="200 0 0"
"TitleText"="0 0 0"
"Window"="128 0 0"
"WindowFrame"="128 0 0"
"WindowText"="0 0 0"[/COLOR]

[Control Panel\\Desktop] 1285107448
"DragFullWindows"="0"
"FontSmoothing"="0"
"LowPowerActive"="0"
"MenuShowDelay"="400"
"SmoothScroll"=hex:00,00,00,00
"UserPreferenceMask"=hex:10,00,00,80

```Save the file and try running the program again.

:D thank you. this undid the colors :D

[IMG]http://ubuntuforums.org/%3Ca%20href=%22http://img201.imageshack.us/i/wineconfiguration011.png/%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://img201.imageshack.us/img201/7720/wineconfiguration011.png%22%20alt=%22Free%20Image%20Hosting%20at%20www.ImageShack.us%22%20border=%220%22/%3E%3C/a%3E[/IMG][IMG]http://img201.imageshack.us/img201/7720/wineconfiguration011.png[/IMG]

but the Night vision in TheSky6 is still giving the same error. Do you think it is related?

Thanks again :D

---

### Post by Toz on 2012-02-05
> **astrobob.tk said:**
> 
but the Night vision in TheSky6 is still giving the same error. Do you think it is related?

What is the error?

---

### Post by astrobob.tk on 2012-02-05
> **Toz said:**
> What is the error?

[IMG]http://img189.imageshack.us/img189/208/thesky6011.png[/IMG]

---

### Post by Toz on 2012-02-05
When do you get this error message? Is it when you're starting the program, or when you are trying to do something?

Reference link: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14746]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14746")

---

### Post by astrobob.tk on 2012-02-05
> **Toz said:**
> When do you get this error message? Is it when you're starting the program, or when you are trying to do something?

Reference link: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14746]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14746")


No not when i start the program. It occurs when I try the Night mode (i.e; red mode; it should make use of the theme I mentioned earlier to change the software's -not the system- colors & stars to red for dark adaptation).

I think I should submit a test result when I'm free. But I have to note that before the theme issue, the night mode was working normally!

---

### Post by Toz on 2012-02-06
Unfortunately, I'm not familiar with that program to be able to assist with its inner workings. However, you may wish to rename your .wine folder:
```
mv ~/.wine ~/.wine.BAK
```
...and try reinstalling the application to see if that helps.

If you ever want your original install back, you just need to mv back the .wine folder:
```
mv ~/.wine.BAK ~/.wine
```

---

### Post by astrobob.tk on 2012-02-06
> **Toz said:**
> Unfortunately, I'm not familiar with that program to be able to assist with its inner workings. However, you may wish to rename your .wine folder:
```
mv ~/.wine ~/.wine.BAK
```...and try reinstalling the application to see if that helps.

If you ever want your original install back, you just need to mv back the .wine folder:
```
mv ~/.wine.BAK ~/.wine
```

No problem. Thanks anyways for your earlier help :D

---

