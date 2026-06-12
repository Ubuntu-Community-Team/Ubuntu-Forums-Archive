---
title: "WoW frame rate?"
date: 2008-05-27
forum: Wine
---

### Post by MemoryDump on 2008-05-27
just curious what some of you have as frame rate for WoW running under Wine?

I'm running the latest version of Wine (wine-1.0-rc2) and I noticed I was just getting over 23 fps! Now I know I have the latest Nvidia drivers installed for my GeForce 7800 GS so I'm not really sure why my fps is so low. I know I'm comparing.. but it was never this low under that "other" OS :)
or perhaps this is normal or expected?

---

### Post by tigerplug on 2008-05-27
> **MemoryDump said:**
> just curious what some of you have as frame rate for WoW running under Wine?

I'm running the latest version of Wine (wine-1.0-rc2) and I noticed I was just getting over 23 fps! Now I know I have the latest Nvidia drivers installed for my GeForce 7800 GS so I'm not really sure why my fps is so low. I know I'm comparing.. but it was never this low under that "other" OS :)
or perhaps this is normal or expected?



Network Latency issue ?

---

### Post by MemoryDump on 2008-05-27
> **tigerplug said:**
> Network Latency issue ?

that was my guess too, however I can download off sites at almost 600 KB/ps.. so I don't know


edit:
Download Speed: 5581 kbps (697.6 KB/sec transfer rate)
Upload Speed: 521 kbps (65.1 KB/sec transfer rate)

---

### Post by karth on 2008-05-27
Did you try the tweaks listed under the WOW entry in WineHQ's AppDB?

See here, "Registry tweak"

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

Also, try disabling the ingame advanced fog and brilliance effects. 
Here with an old P4@2,8GHz, 3GB of RAM and an Nvidia 7600 GS, I get over an average of 60fps.

---

### Post by MemoryDump on 2008-05-27
> **karth said:**
> Did you try the tweaks listed under the WOW entry in WineHQ's AppDB?

See here, "Registry tweak"

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

Also, try disabling the ingame advanced fog and brilliance effects. 
Here with an old P4@2,8GHz, 3GB of RAM and an Nvidia 7600 GS, I get over an average of 60fps.
yeah I have all those settings in the registry too. I'm really baffled by this :(

here's my config files for those wondering how I'm setup:

my Config.wtf file:

```
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET locale "enUS"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1680x1050"
SET gxRefresh "50"
SET gxMultisample "1"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "48"
SET farclip "657"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET showToolsUI "0"
SET Sound_OutputDriverName "System Default"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET gxCursor "0"
SET anisotropic "4"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "PulseAudio Virtual OSS"
SET ChatMusicVolume "0.20000000298023"
SET ChatSoundVolume "0.20000000298023"
SET ChatAmbienceVolume "0.10000000149012"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET weatherDensity "3"
SET ffxGlow "0"
SET realmName ""
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET gameTip "46"
SET autoDismountFlying "1"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET statusBarText "1"
SET uiScale "0.76999998092651"
SET useUiScale "1"
SET autoSelfCast "1"
SET guildMemberNotify "1"
SET videoOptionsVersion "1"
SET profanityFilter "0"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET checkAddonVersion "0"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET assistAttack "1"
SET questFadingDisable "1"
SET guildRecruitmentChannel "0"
SET fctCombatState "1"
SET fctLowManaHealth "1"
SET fctHonorGains "1"
SET hidePartyInRaid "1"
SET showPartyDebuffs "0"
SET fctAuras "1"
SET cameraSmoothStyle "0"
SET displayFreeBagSlots "1"
SET cameraPivot "0"
SET UnitNameNPC "1"
SET secureAbilityToggle "0"
SET SlideBarConfig "anchor=right;position=157.83299137537"
SET groundEffectDist "110"
SET lastCharacterIndex "9"
SET minimapInsideZoom "0"
SET groundEffectDensity "48"
SET textureFilteringMode "4"
SET shadowLevel "0"
SET Sound_VoiceChatOutputDriverIndex "1"
SET EnableMicrophone "0"
SET minimapZoom "0"
SET xpBarText "1"
SET playerStatusText "1"
SET partyStatusText "1"
SET petStatusText "1"
SET targetStatusText "1"
SET lockActionBars "1"
SET alwaysShowActionBars "1"
SET combatTextFloatMode "3"
SET showRaidRange "1"
SET accountName ""
SET CombatHealing "0"

```

my xorg.conf file:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "compose:ralt"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "vmmouse"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
        BoardName      "GeForce 7800 GS"
        Option   "UseEdidDpi" "false"
        Option   "DPI" "96 x 96"

EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        ModelName       "Samsung SyncMaster"
        HorizSync       30.0 - 81.0
        VertRefresh     56.0 - 75.0
        DisplaySize     445 278 # 96 DPI @ 1680x1050
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        Option         "TwinView" "0"
        Option         "metamodes" "1680x1050_60 +0+0"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

---

### Post by tigerplug on 2008-05-28
Whats your ping value?

---

### Post by MemoryDump on 2008-05-28
> **tigerplug said:**
> Whats your ping value?
ping value to what? you can't ping the WoW login servers.

here's a ping to google.ca

```
ping www.google.ca
PING www.l.google.com (72.14.205.104) 56(84) bytes of data.
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=1 ttl=247 time=16.5 ms
64 bytes from qb-in-f104.google.com (72.14.205.104): icmp_seq=2 ttl=247 time=14.4 ms

```
I really doubt it's network latency causing this low frame rate.

---

### Post by Hairy_Palms on 2008-05-28
got the exam same GFX card as you, latest drivers too, had about 20fps untill i turned off Full Screen Glow Effect in Video options, now in silvermoon i get 75fps and shattrath 25fps whereas before in shatt it was 8fps

---

### Post by MemoryDump on 2008-05-28
> **Hairy_Palms said:**
> got the exam same GFX card as you, latest drivers too, had about 20fps untill i turned off Full Screen Glow Effect in Video options, now in silvermoon i get 75fps and shattrath 25fps whereas before in shatt it was 8fps
I'm pretty sure I've disabled that in the pass. Like I mentioned before, WoW worked flawlessly in the past. I'm not sure exactly what's causing this.. WoW itself, recent system updates, wine version, etc.. I see on the Wine appdb page that others are having the same issue.

---

### Post by nasvemos671 on 2008-05-28
Were you running a different os before? That was the primary reason I went back to Vista 64, I was losing an INSANE amount of FPS. I've got dual 8800 gt's and 8 gigs of ram, my fps was like 20-40 INSIDE, not really something I'm savvy with. Also, I've found out that when I upgraded my version of Wine, I was no longer able to shift+click anything so I just downgraded my version of wine and that fixed it. Hope this helps. Good Luck!

---

### Post by Faud on 2008-05-28
```

SET ffxGlow "0"

```
So the OP doesnt have full screen glow effects enabled.
I would say to downgrade your version of wine to .61. 
I noticed an fps drop when I upgraded to the newest version of wine as well.
Im on an older nvidia 6200se 256mb and my framerates in like 
SSC and Shat are between 20-25
and in IF I get up to 60. 
If Im in like Tek forest or Nagrand Im between 35 & 45 
using .61

---

### Post by MemoryDump on 2008-05-29
> **Faud said:**
> ```

SET ffxGlow "0"

```
So the OP doesnt have full screen glow effects enabled.
I would say to downgrade your version of wine to .61. 
I noticed an fps drop when I upgraded to the newest version of wine as well.
Im on an older nvidia 6200se 256mb and my framerates in like 
SSC and Shat are between 20-25
and in IF I get up to 60. 
If Im in like Tek forest or Nagrand Im between 35 & 45 
using .61

I think that's what I'll have to do for now.. is downgrade :(
now to figure out how to do that without loosing what I have installed right now under Wine. funfun

---

