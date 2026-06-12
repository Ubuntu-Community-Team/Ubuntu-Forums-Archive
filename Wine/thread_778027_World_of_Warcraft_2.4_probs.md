---
title: "World of Warcraft 2.4 probs"
date: 2008-05-01
forum: Wine
---

### Post by carmaster01 on 2008-05-01
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




:confused: Im a Noob

---

### Post by Grishka on 2008-05-01
perhaps this will help: [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by carmaster01 on 2008-05-01
nope, still flickers (showing the background).

---

### Post by thisismalhotra on 2008-05-02
> **carmaster01 said:**
> nope, still flickers (showing the background).

Can you post a screenshot please.
Also post your config.wtf and xorg.conf files.

Thanks

---

### Post by situz on 2008-05-02
disable your visual effects: right click your desktop-> Appearance Preferences-> Visual Effects-> check "None".

install correct display drivers with this program:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

and add this to your config.wtf file:
> SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET UIFaster "2"
SET M2UseShaders "0"

hope this helps you ;)

---

### Post by carmaster01 on 2008-05-05
srry about the delay, heres the scrreenie of what happens (it flickers into the background),the config.wtf and xorg file in the atts.

[ATTACH]68891[/ATTACH]

[ATTACH]68892[/ATTACH]

[ATTACH]68893[/ATTACH]

thanks

---

### Post by thisismalhotra on 2008-05-05
> **carmaster01 said:**
> srry about the delay, heres the scrreenie of what happens (it flickers into the background),the config.wtf and xorg file in the atts.

[ATTACH]68891[/ATTACH]

[ATTACH]68892[/ATTACH]

[ATTACH]68893[/ATTACH]

thanks

Is you compiz/special effects turned on when this happens .... also, there seem to be something missing in your xorg.conf in the device section I just dont remember what??

---

### Post by carmaster01 on 2008-05-05
i have now turned off desktop effects, and it works smoothly, but in game it gives some different coloured triangles moving from the bottom of the screen, chk the att:


[ATTACH]68928[/ATTACH]

when i saved this screenie, it was about 20 secs into the game, when i pressed ok, the comptuer just froze so i had to turn of the switch and restart.

what happened there?
thanks

---

### Post by situz on 2008-05-05
looks like the mage on the screenshot blinked into your computer and aoe'd it to **** :P

well that's a known bug with ati cards, and I don't know of anything that can fix it. (the text go all buggy bug)

---

### Post by sadris on 2008-05-05
Is your video card overclocked?

Has it ever been?

---

### Post by carmaster01 on 2008-05-05
nope, never been overclocked
fresh out of the box a few months ago

---

### Post by thisismalhotra on 2008-05-06
> **carmaster01 said:**
> nope, never been overclocked
fresh out of the box a few months ago

IDK what to tell you I have an ATi card and I have tried head over heels anything I can find on the internet to fix it but it is still there ... so dont know what to say. Last thing,

what version of WINE you have ... what I did on my PC is subscribed to trunk/subversion for wine so that I can get the latest builds before they even came on the repos and hope some version fixed it.

I am now on wine 0.9.61 i think...

you can get the instructions to do that here .....

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Hope they fix something in WINE 1.0 or ATi start supporting there cards better for linux ... I am all for nvidia right now

---

