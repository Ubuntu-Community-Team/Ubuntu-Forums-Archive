---
title: "World of Warcraft - Wine Assistance"
date: 2008-10-22
forum: Wine
---

### Post by saberz on 2008-10-22
Hello all,

I had followed the Wine tutorial located in the forums and the WoW ubuntu guide with success(initially). I was able to get the game up and running, but it was running in a window at 800x600 with the Nvidia Driver enabled. The moment I had attempted to switch the game to full-screen and 1280x800 resolution it provided an error.

Wow from this point on would error with an access violation(blizzard error). Per the searching of the forums I found that I could out put some of the Wine debugging and hope that someone can assist me in fully ditching Windows(Vista) so I can be free of it for good hopefully.

I had set the API to Open GL via the Config.wtf and WoW shortcut as well. Enabled OSS and Alsa in Winecfg. The Connection errors are due to me not being connected, as I am at work. But Wow should at least launch to the login screen which it does not.

System Specs:
Dell Vostro 1500
Intel C2D 1.6Ghz
Nvidia 8600M GT 256
2GB of RAM

The main error that stood out for me is:
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F


[I][COLOR="RoyalBlue"]fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x39ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f408,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
fixme:win:EnumDisplayDevicesW ((null),0,0x39f018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df0c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df34,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x374022e4) using GetSystemInfo()
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
saberz@saberz-laptop:/media/OS/World of Warcraft$ [/COLOR][/I]


Any assistance would be appreciated!

---

### Post by saberz on 2008-10-22
Just wanted to provide everyone an update incase someone experiences this in the future.

I went ahead and checked the folder permissions for the WoW folder as it was set as Root and everything was grayed out. Changing it under my restricted account would cause all settings to revert(ah bingo). So i went ahead and unlocked root and made the changes and reverted the lock back to the folder(as it is on my NTFS partition of Windows). Now after giving my limited account read/write access I am able to run the game FLAWLESSLY.

This Sunday i am going to perform a full all out format and use Linux soley as it now plays WoW. =)

---

