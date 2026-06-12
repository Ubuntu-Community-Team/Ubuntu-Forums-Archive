---
title: "[SOLVED] dell d410 + wine 1.1.2+ wow = video intro and then nothing"
date: 2008-08-02
forum: Wine
---

### Post by jlhs1971 on 2008-08-02
Hi

I am running Wine 1.1.2 with Hardy on a Dell D410 which has the following specs:

2Ghz
1G Ram
Graphics card: Intel Corporation Mobile 915GM/GMS/910GML

Running the command: 
> 
glxinfo | grep rendering

gives me the correct response of: 

> direct rendering: Yes


However, when I run WOW, I get the video intro but then it just stops altogether after this and returns me to my desktop.

I get the following output when I run from the command line:

[HTML]julian@julian-laptop:~$ wine "C:\Program Files\World of Warcraft\Launcher.exe"
fixme:shdocvw:PersistStreamInit_Load (0x131198)->(0x32e328)
fixme:shdocvw:OleControl_FreezeEvents (0x131198)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x131198)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x131728): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x131728): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x131708): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x131708): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x132068): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x132068): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x132068): WIN32_FIND_DATA is not yet filled.
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d8ada08, overlapped 0x7d8ad9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x131234)->((null) 1 0x32bcf4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x131234)->((null) 25 2 0x32bd08 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x131234)->((null) 26 2 0x32bd08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x131234)->(0x32bd44)
fixme:shdocvw:ClOleCommandTarget_Exec (0x131234)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32be08 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x132068)->(L"" L"" 0 0x32be40)
fixme:shdocvw:ClOleCommandTarget_Exec (0x131234)->((null) 29 2 0x32ea0c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x131234)
fixme:shdocvw:ClientSite_GetContainer (0x131234)->(0x32e84c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x131234)->(0xb7eac6b1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x131234)->((null) 25 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x131234)->((null) 26 2 0x32e780 (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:shdocvw:ClOleCommandTarget_Exec (0x131234)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x131234)->((null) 28 2 0x32e9ac (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x131198)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14a420)->((nil))
fixme:shdocvw:OleObject_Close (0x131198)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
julian@julian-laptop:~$ fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\common.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f298,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x1378f8) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x139468) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22[/HTML]


Any feedback is welcome.

---

### Post by Floridor on 2008-08-02
I wish I could help you with this, but I'm having the exact same problem. So I hope someone answers us soon.

Like you, I've got a dell computer, I don't know if that's a factor in it. I hope not! I'm running ubuntu 7.10 rather than Hardy.

---

### Post by jlhs1971 on 2008-08-03
well, misery loves company....:)

---

### Post by aoanla on 2008-08-03
Fundamentally, the problem you both have is that the Intel Corporation Mobile 915GM graphics chipset is *horrible*. I imagine that this isn't much consolation for you, though, so heres some things you could try to get it to work:

add 
SET gxApi "opengl" to your config.wtf file.

This is in the config subdirectory of the WoW directory. That /might/ work.

Another thing that might work would be turning off pixel shaders using winecfg.

Try these two fixes separately and together, and tell us what happens.

---

### Post by jlhs1971 on 2008-08-03
Hi Aoanla


Many thanks! Success!

I have not actually managed to play the game yet, but I did get into the login screen (and login) and now it is downloading a mammoth patch. It should work thereafter (I hope!).

With respect to Aoanla's suggestions:

1) I could not alter the config.wtf file since I understand that this is created by the game after the first time you login. However, I was not even able to get to the login screen.

2) Opening up a terminal window and typing the command "winecfg" and changing the pixel shaders option (in the graphics tab) seemed to work.


Many thanks for your help Aoanla and I hope that this solves the same problem for Floridor and others. 

I'll write a brief update post after I manage to put in the recommended performance tweaks ([https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)) and play the game.

best
julian

---

### Post by RefleXX on 2008-08-03
Also experiencing a similar problem.

First, I started up WoW in OpenGL mode and got nothing but a black screen with the sound playing. Then after installing the driver from ATI catalyst manually, and updating again, and reinstalling WINE, I now get a weird screen, quite f*cked up : x All this happened after running a biig update in Ubuntu Hardy.

Here's what the screen looks like:
[[IMG]http://img175.imageshack.us/img175/998/screenshot7hk1.th.png[/IMG]](http://img175.imageshack.us/my.php?image=screenshot7hk1.png)

I am using ATI x300, and I do not have Compiz running..

This is the WINE output:

sothe@sothe:~$ wine ~/.wine/drive_c/Program\ Files/WoW/World\ of\ Warcraft/WoW.exe -opengl

fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
fixme: powrprof: DllMain (0x7bf10000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme: powrprof: DllMain (0x7bf10000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec94,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3603
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x20026, 0x12fa10): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33eb0c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eb0c,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x20026, (nil), 16): stub

Note: I am NOT on a dell, I use a stationary HP.

---

### Post by RefleXX on 2008-08-03
Sorry for double post, but I managed to solve my problem here... After installing new ATI drivers from ATI Catalyst, and reinstalling WINE, I got some help from WineHQ's irc channel from a guy named db92, all thanks to him, changed my whole config.WTF file into this:

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "1"
SET locale "enGB"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxResolution "1440x900"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "48"
SET farclip "357"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET anisotropic "16"
SET M2UsePixelShaders "1"
SET movie "0"
SET expansionMovie "0"
SET Gamma "1.100000"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0"
SET ChatSoundVolume "0"
SET ChatAmbienceVolume "0"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET weatherDensity "0"
SET gameTip "1"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0"
SET uiScale "0.70999997854233"
SET useUiScale "1"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET Sound_EnableHardware "1"
SET groundEffectDist "70"
SET mouseSpeed "1"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1.5"
SET minimapInsideZoom "0"
SET UnitNameNPC "1"
SET SlideBarConfig "anchor=right;position=836.38528686237"
SET CombatLogRangeParty "200"
SET CombatLogRangePartyPet "200"
SET CombatLogRangeFriendlyPlayers "200"
SET CombatLogRangeFriendlyPlayersPets "200"
SET CombatLogRangeHostilePlayers "200"
SET CombatLogRangeHostilePlayersPets "200"
SET CombatLogRangeCreature "200"
SET CombatDeathLogRange "200"
SET autoSelfCast "1"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET questFadingDisable "1"
SET fctCombatState "1"
SET fctLowManaHealth "1"
SET fctHonorGains "1"
SET fctAuras "1"
SET showNewbieTips "0"
SET showPartyDebuffs "0"
SET minimapZoom "1"
SET profanityFilter "0"
SET secureAbilityToggle "0"
SET EnableVoiceChat "1"
SET checkAddonVersion "0"
SET gxApi "opengl"
SET ffxGlow "0"
SET M2UseShaders "0"
SET gxCursor "0"
SET baseMip "1"
SET gxDepthBits "24"
SET ffxDeath "0"
SET SoundOutputSystem "-1"
SET alwaysShowActionBars "1"
SET showClock "0"
SET Sound_OutputQuality "2"
SET Sound_MasterVolume "0.60000002384186"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "1"
SET Sound_AmbienceVolume "1"
SET realmName "Tarren Mill"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET Sound_NumChannels "64"
SET Sound_EnableMusic "0"
SET Sound_ZoneMusicNoDelay "1"
SET gxVSync "0"
SET lastCharacterIndex "1"
SET gxWindow "1"
SET DesktopGamma "1"
SET shadowLOD "0"

and voila it worked. Weird error..

---

### Post by jlhs1971 on 2008-08-04
WOW works for me now although the FPS is very slow (4-5 outside) and hence I am still looking at improving this through the various tweaks people suggest on this forum.

thanks

---

