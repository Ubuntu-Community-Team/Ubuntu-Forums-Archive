---
title: "World of Warcraft - Cannot play in OpenGL mode."
date: 2008-07-02
forum: Wine
---

### Post by TheHatter on 2008-07-02
Hi all,

I have the following system:

Ubuntu 8.04 (Xubuntu, AMD64)
AMD X2 4800+
2GB DDR RAM
ATI HD4850

If I try to play World of Warcraft in OpenGL it's totally unplayable. When starting the game the initial character menus are drawn incorrectly, then when I enter the game I have no button bars and any movement results in screen corruption (see attached images). 

If I run the game in d3d mode everything looks fine but FPS is poor ~6-10FPS. 

I've followed the howto's for installing and troubleshooting with no luck. I used method 2 from this guide to install the latest Catalyst drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide"). Everything checks out okay with glxgears, fglrxinfo etc...

My Xorg config:

```

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Option      "XAANoOffscreenPixmaps"     "true"
        Option      "TexturedVideo"             "on"
        Option      "VideoOverlay"              "off"
        Option      "OpenGLOverlay"             "off"
        Option      "UseFastTLS"                "2"
        Option      "Capabilities"              "0x00000800"
        Option      "KernelModuleParm"          "locked-userpages=0"
        Option      "Textured2D"                "on"
        Option      "TexturedXRender"           "on"
        Option      "BackingStore"              "on"
EndSection

```

World of Warcraft Config.wtf:
```

SET locale "enGB"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET expansionMovie "0"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET farclip "777"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "64"
SET gxApi "opengl"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET gxWindow "1"
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET realmName "Aggramar"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "2"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_EnableMusic "0"
SET Sound_MasterVolume "0.69999998807907"
SET Sound_SFXVolume "0.40000000596046"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0.30000001192093"
SET groundEffectDist "140"
SET showGameTips "0"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET uiScale "0.78999996185303"
SET useUiScale "1"
SET questFadingDisable "1"
SET showNewbieTips "0"
SET UberTooltips "0"
SET M2UsePixelShaders "1"
SET M2UseShaders "0"
SET UIFaster "2"
SET gxCursor "0"
SET gxMultisample "4"
SET textureFilteringMode "5"
SET shadowLevel "0"
SET weatherDensity "3"

```

Thanks in advance for any suggestions.

---

### Post by starcannon on 2008-07-02
nevermind, just re-read your post, I don't know why your d3d fps is so low, but I'd fix that and get your game on that way.

---

### Post by thisismalhotra on 2008-07-03
Which driver have you installed and how did you install it??
Was compiz/desktop effects turned off when you were trying to play wow??

---

### Post by TheHatter on 2008-07-03
I used the very latest cats from the ATi (AMD) website, so Catalyst 8.6.

All effects are turned off, compiz and AIGLX are specifically disabled in my Xorg configuration:

```

Section "Extensions"
        Option "Composite" "false"
EndSection

```

And: 

```

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

```

As mentioned before, installation was using these instructions: 
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

---

