---
title: "Wow + vent in wine"
date: 2008-06-02
forum: Wine
---

### Post by bl4ck32 on 2008-06-02
Hi, 

Just got Ubuntu up and running, and have installed Wine, WoW and Ventrilo

All are working great. WoW works with sound + fullscreen, ventrilo works (i can talk to people and they can hear me etc).

However, when i start ventrilo, then move to the other desktop to start wow, it seems the Push to talk option in vent disables once im in WoW.

I can hear ppl on vent, and all the sounds in wow, but i cant use Push to talk...BTW im using a logitech USB headset with attached mic.

If i start up wow in the terminal i get the following :

```

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
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
fixme:win:EnumDisplayDevicesW ((null),0,0x32eda4,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec94,0x00000000), stub!
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
fixme:imm:ImmAssociateContextEx (0x90084, (nil), 16): stub
darren@darren-desktop:~/Games/WoW$ aoss wine /home/darren/Games/WoW/Launcher.exe
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
darren@darren-desktop:~/Games/WoW$ err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
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
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x37402b24) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d200,0x00000000), stub!
failed to open H:/Games/WoW/Data/Interface/Icons
failed to open H:/Games/WoW/Interface/Icons
fixme:imm:ImmReleaseContext (0x30024, 0x136b10): stub
fixme:imm:ImmAssociateContextEx (0x30024, (nil), 16): stub


```

can someone decipher the first three lines for me, and tell me what to do to get my mic working?

thanks :)

---

### Post by MemoryDump on 2008-06-02
Unfortunately VENT doesn't work the same way as it does in Windows. Once you select another application it looses its focus and ignores the keyboard commands. Luckily some people have had success with a script a member wrote called "ventriloctrl". You can try searching these forums for the script.
Good luck!

---

### Post by TimothyLuke on 2008-06-03
> Unfortunately VENT doesn't work the same way as it does in Windows. Once you select another application it looses its focus and ignores the keyboard commands.

While the bulk of this is correct, I have found that if I launch both WOW and Vent from the same 'instance' that PPT works when either the WOW window or the Vent window has focus.  In my case I put both WOW and Vent into my GNOME menu but use the exact same wine install and prefix.  In my case Vent is installed to ```
~/.wine/drive_c/Program\ Files/Ventrilo
```  where WOW is at ```
~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
```  They both use the same "registry" / Windows and System32 directories etc and are both launched using the exact same prefix.  eg:```
wine ~/.wine/drive_c/Program\ Files/Ventrilo/Ventrilo.exe
wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
``` or ```
aoss wine ~/.wine/drive_c/Program\ Files/Ventrilo/Ventrilo.exe
aoss wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
```

if however i try a combination like ```
aoss wine ~/.wine/drive_c/Program\ Files/Ventrilo/Ventrilo.exe
wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
```
the PPT only works when Vent is in focus.

The easiest way is to let the apps install themselves into GNOME's(/KDE?) WINE menu and launch from there.

---

### Post by MemoryDump on 2008-06-03
> **TimothyLuke said:**
> While the bulk of this is correct, I have found that if I launch both WOW and Vent from the same 'instance' that PPT works when either the WOW window or the Vent window has focus.  In my case I put both WOW and Vent into my GNOME menu but use the exact same wine install and prefix.  In my case Vent is installed to ```
~/.wine/drive_c/Program\ Files/Ventrilo
```  where WOW is at ```
~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
```  They both use the same "registry" / Windows and System32 directories etc and are both launched using the exact same prefix.  eg:```
wine ~/.wine/drive_c/Program\ Files/Ventrilo/Ventrilo.exe
wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
``` or ```
aoss wine ~/.wine/drive_c/Program\ Files/Ventrilo/Ventrilo.exe
aoss wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
```

if however i try a combination like ```
aoss wine ~/.wine/drive_c/Program\ Files/Ventrilo/Ventrilo.exe
wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
```
the PPT only works when Vent is in focus.

The easiest way is to let the apps install themselves into GNOME's(/KDE?) WINE menu and launch from there.

interesting! I'll have to test this out! thanks for the info :D

---

### Post by BlahMan_of.Doom on 2008-06-04
So all you're trying to say is that when you use two wine apps, you can use PTT (not PPT...) in both apps. Err...thanks?

---

### Post by TimothyLuke on 2008-06-04
> So all you're trying to say is that when you use two wine apps, you can use PTT (not PPT...) in both apps.
Yes but only if both wine apps are installed into tthe same .wine folder and started the same way.  If you use a wrapper, like aoss, on one and not the other then PTT wont work on the other wine app.

---

