---
title: "World of Warcraft 2.4 probs"
date: 2008-05-01
forum: Wine
---

### Post by carmaster01 on 2008-05-01
Question  World of Warcraft 2.4 probs
hi
im having problems with Wow 2.4 running with wine 9.60 on ubuntu 8.04.

i have looked around the forums and applied most of the fixes but still cannot fix this:
everytime wow starts, it 'flickers' blue randomly, but i can see everything else.

also here is whats displayed in the terminal when i run and close it:

> linux@linux-desktop:~$ wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
preloader: Warning: failed to reserve range 00000000-00010000
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
fixme:powrprof:DllMain (0x7bf10000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7bf10000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x32eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ecac,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3462
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x37402b24) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x20024, 0x133d88): stub
preloader: Warning: failed to reserve range 00000000-00010000
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub
linux@linux-desktop:~$ 




help me pls
thanks in advance
--------------------------------
im running:
AMD 64 3000+
1gb ddr ram
asus a8n-vm
ATI x2600 XT HD

restricted drivers enabled,
the ATI driver from the ati site won't work because it just boots into X and after login i get a white screen, thats y im on restricted drivers.




Im a Noob

---

### Post by Spydr4590 on 2008-05-01
Try this guide [http://ubuntuforums.org/showthread.php?t=752427](http://ubuntuforums.org/showthread.php?t=752427)

---

