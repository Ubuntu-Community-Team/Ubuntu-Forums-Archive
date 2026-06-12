---
title: "Neverwinter Nights 2 : almost everything black on screen"
date: 2008-03-17
forum: Wine
---

### Post by didli on 2008-03-17
Hi everyone !
I installed NWN2 from DVD, with all updates (last 1.11.1153 FR) and face one big problem as I tried to play :
Almost everything, except for the game interface, is ***turned black*** when the game starts. **Please look here to see what I mean** :
------
[[IMG]http://designed2.free.fr/screenshots/t_missing.jpg[/IMG]]("http://designed2.free.fr/screenshots/missing.png")
------
Quite unplayable isn't it ?
It happens too on the Game Character Creation, I can create a character but almost can't see it (I can only see his armor). 
**Is there something I should try ? Did i miss something ? **
Now below you can find specs for my system, please report anything that should help me a bit :
Wine 0.9.57 running on Gutsy 7.10 /MSI K7D Master (Dual Athlon MP2800+) with Radeon X800SE /1024 DDR RAM
No significative terminal output ! Not even a clue, everything seems fine ...
Wine config : Windows XP / No virtual desktop / DLL Override :
```
[Software\\Wine\\Direct3D]
"OffscreenRenderingMode"="fbo"
"PixelShaderMode"="enabled"
"UseGLSL"="enabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="256"

[Software\\Wine\\DirectSound]
"EmulDriver"="N"
"HardwareAcceleration"="Standard"

[Software\\Wine\\DllOverrides]
"d3d8"="builtin"
"d3d9"="builtin"
"d3dim"="native"
"d3drm"="native"
"d3dx8"="native"
"d3dx9_30"="native,builtin"
"d3dxof"="native"
"dciman32"="native"
"ddrawex"="native"
"devenum"="native,builtin"
"dinput"="builtin"
"dinput8"="builtin"
"dmband"="native"
"dmcompos"="native"
"dmime"="native"
"dmloader"="native"
"dmscript"="native"
"dmstyle"="native"
"dmsynth"="native"
"dmusic"="native"
"dmusic32"="native"
"dnsapi"="native"
"dplay"="native"
"dplayx"="native"
"dpnaddr"="native"
"dpnet"="native"
"dpnhpast"="native"
"dpnlobby"="native"
"dsound"="builtin"
"dswave"="native"
"dxdiagn"="native,builtin"
"gdiplus"="native,builtin"
"mscoree"="native"
"msdmo"="native"
"qcap"="native"
"quartz"="native"
"streamci"="native"

[Software\\Wine\\Drivers]
"Audio"="alsa" 

``` **.INI files from NWN2 folder** :
```
[Game Options]
Memory Level=1
Memory Access=0
Debug Text=0
Object Selection Mode=3
DebugMode=1

[Sound Options]
Music Volume=0.85
Voice Volume=0.85
SoundFX Volume=0.85
Music Multiplier=0.60
Dialog2d Multiplier=0.80
DisableSound=0
3D Provider=RAD Game Tools RSX 3D Audio
;3D Provider=Miles Fast 2D Positional Audio
Environment Effects=0
Number 2D Voices=16
Number 3D Voices=16
2D3D Bias=1.70
Speaker Type=4
MaxCachedSounds=100

[Display Options]
FullScreen=1
UseLargeFont=0
ShowSTRREF=0
TexturePack=0
Width=1400
Height=1050
BitsPerPixels=32
RefreshRate=60
;Gamma=1.5
SafeMovie=0
ObjectFade Start=0.0
ObjectFade Length=0.5
ObjectFade Percentage=.15
Enable ObjectFade Companions=1
Enable ObjectFade Target=1

[Video Options]
;Enable HardwareMouse=1
Enable VSync=0
Enable Truform=1
Enable AnisotropicFiltering=0
;CreatureWindSetting=2
;CreatureShadowDetail=2

[Graphics Options]
SEFCacheTimeout=60
SEFCacheSize=20
Bloom=1
EnableVsync=0
Shadows=1
EnvironmentShadows=0
CharacterDropShadows=0
SoftShadows=0
PointLightShadows=0
UseHardwareShadowMapsIfAvailable=1
NormalMappedTerrain=0
NumberOfTextureMipLevelsToSkip=0
UseHDRIfAvailable=0
MultiSampleType=0
ScreenshotFormat=jpg
WaterReflections=0
WaterRefraction=0
RenderGrass=1
HiRezShadowMapSize=1024
LowRezShadowMapSize=1024
CharacterAndPointLightShadowMapSize=512
TextureMinFilterMode=2
TextureMagFilterMode=2
TextureMipFilterMode=2
TextureMaxAnisoTropy=1
FarClipPlaneOverride=50.000000
ATIWorkAroundForPointLightShadows=1
SoftwareSkinning=0
FirstRunAutoDetect=0
LightsPerObject=2 

[Config]
FirstRun=0
Connection=0
``` **Thanks in advance for your help ! **

---

### Post by didli on 2008-03-18
Well ... 'seems I'm all alone with this problem (I search for other references of it without success). So I copy a Win installation over my Ubuntu one, and ... no way, the same problem still there, which maybe means it's a wine problem ...
Maybe with dll overrides ...
Is there someone running NWN2 with success ? I would like to ask for the list of his dll overrides for comparison ... Thanks a lot !

---

### Post by rockorequin on 2008-06-01
You could try turning shadow effects off eg in options / game options / graphics or the ini file. This initially fixed the black screen for me when I didn't yet have the [Software\\Wine\\Direct3D] entry in user.reg. (After I added that entry, I can run it with shadows on and without the black screen.)

---

### Post by harvodan on 2008-06-17
In the game graphics settings, enable bloom, and see how that goes. Also, consider creating a new wine prefix with the needed dll overrides, your current wine looks pretty crowded as far as that goes.

---

### Post by didli on 2008-06-17
> **harvodan said:**
> In the game graphics settings, enable bloom, and see how that goes. Also, consider creating a new wine prefix with the needed dll overrides, your current wine looks pretty crowded as far as that goes.
I already tried and followed howtos with the same settings. And same thing keeps happening again and again. Almost everything on the screen game is black.
My guess is either my pc config is kinda too exotic or my xorg.conf is a total mess.
Maybe one of you can confirm if there's something wrong with my xorg.conf ? Here it comes for an (agp) ATI X800 :
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R420 JJ [Radeon X800SE]"
	Monitor		"HM903D/DT"
	SubSection "Display"
		Depth	16
		Modes		"1400x1050"	"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1400x1050"	"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R420 JJ [Radeon X800SE]"
	Driver		"fglrx"
	Option		"XAANoOffscreenPixmaps"	"on"
	Option		"TexturedVideo"	"off"
	Option		"Textured2D"	"on"
	Option		"TexturedXrender"	"on"
  	Option         	"AddARGBGLXVisuals" "true"
  	Option         	"TripleBuffer"      "true"
	Option		"Capabilities"	"0x00000800"
	Option		"UseFastTLS"	"off"
	Option		"KernelModuleParm"	"locked-userpages=0"
	Option		"BackingStore"	"on"
	Option		"DesktopSetup"	"Single"
	Option		"UseInternalAGPGART"	"no"
	Option		"AllowGLXWithComposite"	"true"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Busid		"PCI:1:5:0"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Option		"AIGLX"	"true"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Module"
        # Load "GLcore"
        Load "bitmap"
        Load "ddc"
        Load "dbe"
        Load "dri"
        Load "extmod"
        Load "freetype"
        Load "glx"
        Load "int10"
        Load "type1"
        Load "vbe"
EndSection


Section "Monitor"
	Identifier	"HM903D/DT"
	Option		"DPMS"
	Horizsync	30-130
	Vertrefresh	50-200
EndSection

Section "DRI"
	Group		"Video"
	Mode	0666
EndSection

Section "Extensions"
	Option		"XVideo"	"Enable"
	Option		"RENDER"	"Enable"
	Option		"DAMAGE"	"Enable"
	Option		"Composite"	"Enable"
EndSection

```
**Besides, thanks you all for your kind help** :)
PS : if i run the game without the "WINEDEBUG=-all wine blabla.exe", wine return me this :
```
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
```

---

### Post by harvodan on 2008-06-19
If you're having no difficulties with other wine or native games, then it's likely not your drivers giving you grief, but needing to set up wine properly. You need to follow a guide such as this one here. [http://illespal.googlepages.com/wine.html]("http://illespal.googlepages.com/wine.html")

Pay special attention to copying over devenum, dxdiagn, and d3dx9_30.dll from windows, and setting up overrides in winecfg. If you manage to get the game working with the minimap and everything, please let me know.

---

### Post by didli on 2008-06-19
Unfortunately, i had already tried this one too without success either. I have tried it again a few minutes ago, just to be sure : and it failed. Same effect & probably same cause.
Since Hardy, i get a lot of glitches and graphical artefacts on my desktop (even if the PC seems to run fine), that's why i was thinking it could be hardware related (or at least, a communication problem between hardware and Ubuntu :-k ). Well now I think i will stop searching. I must install hardy on another computer in a month or two, and will give it a try, once again, at the moment. 
Thanks again for your kind help. I really appreciate it. :)

---

