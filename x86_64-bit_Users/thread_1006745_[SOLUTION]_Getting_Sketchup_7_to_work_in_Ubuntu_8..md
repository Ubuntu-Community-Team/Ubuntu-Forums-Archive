---
title: "[SOLUTION] Getting Sketchup 7 to work in Ubuntu 8.10 64bit"
date: 2008-12-09
forum: x86 64-bit Users
---

### Post by briandu on 2008-12-09
Long post - not as bad as it looks! :KS
[I][B]
PREPARE[/B][/I]
I collected so icons and downloaded Sketchup onto my Desktop.

I ensured wine was installed - I use wine 1.0.1 [  **sudo apt-get install wine** ]

I suggest you select Configure Wine (via menu Applications.....Wine....Configure Wine) to ensure all the paths are initiated.

On Desktop I selected GoogleSketchUpWEN.exe and installed into the default directory (as if it was windoze)

Once done, delete the Sketchup.lnk it places on the desktop.

Select your Text Editor (via menu Applications...Accessories....Text Editor) and drag it onto the Desktop.  This means that must ensure it has a + symbol on it as you drag it - just hold the left button down.

***FIRST STEP*** (do this if Sketchup 7 proper does not appear on your desktop)
Open the Text Editor on Desktop.

Open Nautilus and browse to Desktop.

Drag the Text Editor config file onto the open Text Editor

Select the complete content and delete everything. No cut 'n paste this into the Text Editor:

[Desktop Entry]
Encoding=UTF-8
Name=Sketchup 7
Exec=wine /home/xxxx/.wine/drive_c/Program\ Files/Google/Google\ SketchUp\ 7/Sketchup.exe
Icon=/usr/share/pixmaps/google_sketchup.png
Terminal=false
Type=Application
Categories=Application;Graphics;
StartupNotify=false

$note: xxxx is your login name


Save this into a file on the Desktop (so you can find it) called Sketchup7.reg
REGEDIT4

[HKEY_CURRENT_USER\Software\Google]

[HKEY_CURRENT_USER\Software\Google\SketchUp7]
@=""

[HKEY_CURRENT_USER\Software\Google\SketchUp7\AppGUID]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ApplicationGUID]
"GUID"="{3CC49BC6-C63D-11DD-3A8A-001E8CCEE189}"

[HKEY_CURRENT_USER\Software\Google\SketchUp7\AutoSave]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\BugSplat]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\Color_ Warning]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\CSkDialog]
"x"=dword:000002dc
"y"=dword:00000131

[HKEY_CURRENT_USER\Software\Google\SketchUp7\DimensionStyle]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\EPSOptions]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\Extensions]
"Dynamic Components"=dword:00000001

[HKEY_CURRENT_USER\Software\Google\SketchUp7\FileLocations]
"ComponentBrowser"="C:\\Program Files\\Google\\Google SketchUp 7\\Components\\"
"ComponentBrowser1"="C:\\Program Files\\Google\\Google SketchUp 7\\Components\\"
"ComponentBrowser2"="C:\\Program Files\\Google\\Google SketchUp 7\\Components\\"
"Components"="C:\\windows\\profiles\\briand\\M y Documents\\"
"Images"="C:\\windows\\profiles\\briand\\My Documents\\"
"ImportExport"="C:\\windows\\profiles\\briand\ \My Documents\\"
"Materials"="C:\\windows\\profiles\\briand\\My Documents\\"
"MaterialsBrowser"="C:\\Program Files\\Google\\Google SketchUp 7\\Materials\\"
"MaterialsBrowser2"="C:\\Program Files\\Google\\Google SketchUp 7\\Materials\\"
"Models"="C:\\windows\\profiles\\briand\\My Documents\\"
"Styles"="C:\\windows\\profiles\\briand\\My Documents\\"
"StylesBrowser"="C:\\Program Files\\Google\\Google SketchUp 7\\Styles\\"
"StylesBrowser2"="C:\\Program Files\\Google\\Google SketchUp 7\\Styles\\"
"Textures"="C:\\windows\\profiles\\briand\\My Documents\\"

[HKEY_CURRENT_USER\Software\Google\SketchUp7\FollowMe]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\GLConfig]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\GLConfig\Display]
"FIRST_TIME"=dword:00000000
"HW_OK"=dword:00000001

[HKEY_CURRENT_USER\Software\Google\SketchUp7\LODPreferences]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\MainFrame]
"FirstTime"=dword:00000000
"wp.bottom"=dword:0000041e
"wp.flags"=dword:00000000
"wp.left"=dword:00000001
"wp.ptMaxPosition.x"=dword:00000000
"wp.ptMaxPosition.y"=dword:00000000
"wp.ptMinPosition.x"=dword:00000000
"wp.ptMinPosition.y"=dword:00000000
"wp.right"=dword:0000077f
"wp.showCmd"=dword:00000001
"wp.top"=dword:0000001a

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ModelInfoDlg]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\PageOptions]
"ShowTransition"=dword:00000001
"TransitionTime"="1.5"

[HKEY_CURRENT_USER\Software\Google\SketchUp7\PDFOptions]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\Preferences]
"AnglePrecision"=dword:00000001
"AngleSnapping"=dword:00000001
"AutoDrawingPlane"=dword:00000001
"AviExportAntiAlias"=dword:00000001
"AviExportAR"="1.333333"
"AviExportFPS"="10.000000"
"AviExportHeight"=dword:000000f0
"AviExportLockAR"=dword:00000001
"AviExportLoop"=dword:00000001
"AviExportPlay"=dword:00000000
"AviExportPrompt"=dword:00000000
"AviExportWidth"=dword:00000140
"BrowserHome"=""
"DefaultTemplate"="C:/Program Files/Google/Google SketchUp 7/Resources/en-US/Templates/Temp02b - Arch.skp"
"DisplayTabs"=dword:00000001
"LengthFormat"=dword:00000001
"LengthPrecision"=dword:00000001
"LengthSnapping"=dword:00000001
"LengthUnit"=dword:00000000
"MaxUndo"=dword:00000064
"MinSnapPixels"=dword:00000002
"ShowInferenceTips"=dword:00000001
"SnapAngle"="15.000000"
"SnapLength"="1\""
"UpdateDefaultColorOn"=dword:00000001
"UpdateDefaultOn"=dword:00000001
"VCBShowTypedInputBackground"=dword:00000001
"VCBTimoutSeconds"=dword:00000005

[HKEY_CURRENT_USER\Software\Google\SketchUp7\PrefsPS]
"curPage"=dword:00000008
"x"=dword:000002d9
"y"=dword:0000017d

[HKEY_CURRENT_USER\Software\Google\SketchUp7\PrintOptions]
"ComputeSizeFromScale"=dword:00000000
"FitToPage"=dword:00000001
"LineWeight"="0.5"
"ModelExtents"=dword:00000001
"NumberOfPages"=dword:00000001
"PixelsPerInch"="150"
"PrintHeight"="11"
"PrintQuality"=dword:00000000
"PrintWidth"="8.5"
"QualityAdjustment"="1"
"ScaleAdjustment"="1"
"SectionSlice"=dword:00000000
"SizeInModel"="1"
"SizeInPrint"="1"
"VectorMode"=dword:00000000

[HKEY_CURRENT_USER\Software\Google\SketchUp7\QA]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\Settings]
"Num_Shortcuts"=dword:00000012
"Shortcut_1"="0 0 0 Space selectSelectionTool:"
"Shortcut_10"="0 0 0 P selectPushPullTool:"
"Shortcut_11"="0 0 0 M selectMoveTool:"
"Shortcut_12"="0 0 0 Q selectRotateTool:"
"Shortcut_13"="0 0 0 S selectScaleTool:"
"Shortcut_14"="0 0 0 F selectOffsetTool:"
"Shortcut_15"="0 0 0 O selectOrbitTool:"
"Shortcut_16"="0 0 0 H selectDollyTool:"
"Shortcut_17"="0 0 0 Z selectZoomTool:"
"Shortcut_18"="0 0 1 Z viewZoomExtents:"
"Shortcut_2"="0 0 0 G Edit/Make Component..."
"Shortcut_3"="0 0 0 L selectLineTool:"
"Shortcut_4"="0 0 0 E selectEraseTool:"
"Shortcut_5"="0 0 0 T selectMeasureTool:"
"Shortcut_6"="0 0 0 B selectPaintTool:"
"Shortcut_7"="0 0 0 R selectRectangleTool:"
"Shortcut_8"="0 0 0 C selectCircleTool:"
"Shortcut_9"="0 0 0 A selectArcTool:"

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SlideshowOptions]
"LoopSlideshow"=dword:00000001
"SlideTime"="1"

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappyBackgroundImage]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappyComponents]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappyEntityInfo]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappyFogDlg]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappyInstructor]
"cx"=dword:00000179
"cy"=dword:0000020d
"show"=dword:00000000

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappyLayers]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappyMaterials]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappyNavigator]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappyPages]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappyShadows]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappySoftenEdges]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\SnappyStyles]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\TextStyle]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\Textures]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar0]
"BarID"=dword:0000007f
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000040
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000000
"MRUDockRightPos"=dword:00000178
"MRUDockTopPos"=dword:0000001e
"MRUFloatStyle"=dword:00002004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"Visible"=dword:00000000
"XPos"=dword:fffffffe
"YPos"=dword:0000001e

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar1]
"BarID"=dword:00000089
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000047
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:0000003e
"MRUDockRightPos"=dword:00000080
"MRUDockTopPos"=dword:00000000
"MRUFloatStyle"=dword:00000004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"Visible"=dword:00000000
"XPos"=dword:0000003e
"YPos"=dword:fffffffe

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar10]
"BarID"=dword:000000d3
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000209
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000000
"MRUDockRightPos"=dword:00000042
"MRUDockTopPos"=dword:00000000
"MRUFloatStyle"=dword:00000004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:ffd9d9d9
"MRUWidth"=dword:0000003e
"XPos"=dword:fffffffe
"YPos"=dword:fffffffe

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar11]
"BarID"=dword:00002979
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000022
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:000002d5
"MRUDockRightPos"=dword:00000381
"MRUDockTopPos"=dword:00000000
"MRUFloatStyle"=dword:00002004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"Visible"=dword:00000000
"XPos"=dword:000002d5
"YPos"=dword:fffffffe

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar12]
"BarID"=dword:000055e8
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000022
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000000
"MRUDockRightPos"=dword:000002d9
"MRUDockTopPos"=dword:00000000
"MRUFloatStyle"=dword:00002004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:fc00ffff
"XPos"=dword:fffffffe
"YPos"=dword:fffffffe

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar13]
"BarID"=dword:0000e801

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar14]
"BarID"=dword:00000067
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:69e9e9d0
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000000
"MRUDockRightPos"=dword:21f8b8b8
"MRUDockTopPos"=dword:00000000
"MRUFloatStyle"=dword:00002000
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000408
"Visible"=dword:00000000
"XPos"=dword:00000175
"YPos"=dword:0000001f

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar15]
"BarID"=dword:000000dc
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:ffe2e2e2
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000000
"MRUDockRightPos"=dword:ffb7b7b7
"MRUDockTopPos"=dword:00000000
"MRUFloatStyle"=dword:00002000
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:ffafafaf
"Visible"=dword:00000000
"XPos"=dword:00000238
"YPos"=dword:0000001f

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar16]
"BarID"=dword:000000dd
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000022
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000000
"MRUDockRightPos"=dword:000000f0
"MRUDockTopPos"=dword:00000000
"MRUFloatStyle"=dword:00002000
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:a04a3ad2
"Visible"=dword:00000000
"XPos"=dword:fffffffe
"YPos"=dword:fffffffe

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar17]
"Bar#0"=dword:00000000
"Bar#1"=dword:000055e8
"Bar#10"=dword:0000e900
"Bar#11"=dword:00000000
"Bar#2"=dword:00002979
"Bar#3"=dword:00000000
"Bar#4"=dword:0000007f
"Bar#5"=dword:0000016a
"Bar#6"=dword:00000067
"Bar#7"=dword:00000163
"Bar#8"=dword:000000dc
"Bar#9"=dword:00000000
"BarID"=dword:0000e81b
"Bars"=dword:0000000c

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar18]
"Bar#0"=dword:00000000
"Bar#1"=dword:000000dd
"Bar#2"=dword:00000000
"BarID"=dword:0000e81e
"Bars"=dword:00000003

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar19]
"Bar#0"=dword:00000000
"Bar#1"=dword:000000d3
"Bar#10"=dword:00000000
"Bar#2"=dword:00000000
"Bar#3"=dword:00000089
"Bar#4"=dword:000001f5
"Bar#5"=dword:000001f3
"Bar#6"=dword:000001db
"Bar#7"=dword:00000168
"Bar#8"=dword:00000088
"Bar#9"=dword:000001dd
"BarID"=dword:0000e81c
"Bars"=dword:0000000b

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar2]
"BarID"=dword:00000168
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:000001ef
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:0000003e
"MRUDockRightPos"=dword:00000080
"MRUDockTopPos"=dword:0000016c
"MRUFloatStyle"=dword:00000004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"Visible"=dword:00000000
"XPos"=dword:0000003e
"YPos"=dword:0000016c

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar20]
"BarID"=dword:0000e80a
"Visible"=dword:00000000

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar21]
"BarID"=dword:0000e900
"BarName"="Dynamic Components"
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:005c0073
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000000
"MRUDockRightPos"=dword:006e0069
"MRUDockTopPos"=dword:00000000
"MRUFloatStyle"=dword:00002004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000408
"Visible"=dword:00000000
"XPos"=dword:fffffffe
"YPos"=dword:fffffffe

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar3]
"BarID"=dword:000001f5
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:000000a8
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:0000003e
"MRUDockRightPos"=dword:00000080
"MRUDockTopPos"=dword:00000043
"MRUFloatStyle"=dword:00000004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"Visible"=dword:00000000
"XPos"=dword:0000003e
"YPos"=dword:00000043

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar4]
"BarID"=dword:000001f3
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:0000010b
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:0000003e
"MRUDockRightPos"=dword:00000080
"MRUDockTopPos"=dword:000000a6
"MRUFloatStyle"=dword:00000004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"Visible"=dword:00000000
"XPos"=dword:0000003e
"YPos"=dword:000000a6

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar5]
"BarID"=dword:000001db
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:0000016e
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:0000003e
"MRUDockRightPos"=dword:00000080
"MRUDockTopPos"=dword:00000109
"MRUFloatStyle"=dword:00000004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:ffababab
"Visible"=dword:00000000
"XPos"=dword:0000003e
"YPos"=dword:00000109

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar6]
"BarID"=dword:00000088
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000234
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:0000003e
"MRUDockRightPos"=dword:00000080
"MRUDockTopPos"=dword:000001ed
"MRUFloatStyle"=dword:00000004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:ff4f4f4f
"Visible"=dword:00000000
"XPos"=dword:0000003e
"YPos"=dword:000001ed

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar7]
"BarID"=dword:00000163
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000040
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000237
"MRUDockRightPos"=dword:00000302
"MRUDockTopPos"=dword:0000001e
"MRUFloatStyle"=dword:00000004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:ff212121
"Visible"=dword:00000000
"XPos"=dword:00000237
"YPos"=dword:0000001e

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar8]
"BarID"=dword:0000016a
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000040
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:00000174
"MRUDockRightPos"=dword:00000239
"MRUDockTopPos"=dword:0000001e
"MRUFloatStyle"=dword:00002004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:00000000
"Visible"=dword:00000000
"XPos"=dword:00000174
"YPos"=dword:0000001e

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Bar9]
"BarID"=dword:000001dd
"Docking"=dword:00000001
"MRUDockBottomPos"=dword:00000279
"MRUDockID"=dword:00000000
"MRUDockLeftPos"=dword:0000003e
"MRUDockRightPos"=dword:00000080
"MRUDockTopPos"=dword:00000232
"MRUFloatStyle"=dword:00000004
"MRUFloatXPos"=dword:80000000
"MRUFloatYPos"=dword:ff7d7d7d
"Visible"=dword:00000000
"XPos"=dword:0000003e
"YPos"=dword:00000232

[HKEY_CURRENT_USER\Software\Google\SketchUp7\ToolbarsUser-Summary]
"Bars"=dword:00000016
"IconSize"=dword:00000000
"ScreenCX"=dword:00000780
"ScreenCY"=dword:00000438

[HKEY_CURRENT_USER\Software\Google\SketchUp7\Undo]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\UpdateService]
"LastChecked"="12/09/2008"

[HKEY_CURRENT_USER\Software\Google\SketchUp7\WebDialog]

[HKEY_CURRENT_USER\Software\Google\SketchUp7\WebDialog_]
"Height"=dword:000001f5
"Left"=dword:00000000
"Top"=dword:00000000
"Width"=dword:00000171

[HKEY_CURRENT_USER\Software\Google\SketchUp7\WelcomeDialog]
"ShowOnStartup"=dword:00000000 

***SECOND STEP***
Open a terminal session and enter:
wine regedit
from menu Registry.....Import Registry File    select the file Sketchup7.reg

***THIRD STEP***

I used google_sketchup.png is from Jose Maliel at DeviantArt.com
[http://hosaem.deviantart.com/art/Google-Sketchup-38630870](http://hosaem.deviantart.com/art/Google-Sketchup-38630870)

and place  icon into [IMG]file:///home/briand/Desktop/google_sketchup.png[/IMG]/usr/share/pixmaps/  (use Nautilus)

Open terminal and:
sudo chown root [IMG]file:///home/briand/Desktop/google_sketchup.png[/IMG]/usr/share/pixmaps/google_sketchup.png
sudo chgrp [IMG]file:///home/briand/Desktop/google_sketchup.png[/IMG]root /usr/share/pixmaps/google_sketchup.png

***CLEANUP***
Delete Desktop of:  google_sketchup.png,  GoogleSketchUpWEN.exe and Sketch7.reg

and you should be good to go.:popcorn:

$Note: the template is for metric as I use metric not imperial
):P


Edit: for some reason the wine regedit export somehow inserted a dummy space in the Key strings. No idea why. The version here is fine now.

---

### Post by BGFG on 2008-12-09
Good info, before i read the post i jumped to google thinking there was a linux version....

---

