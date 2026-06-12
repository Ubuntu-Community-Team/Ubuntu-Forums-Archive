---
title: "WoW doesn't start with Wine"
date: 2007-08-03
forum: Wine
---

### Post by LeifEricson on 2007-08-03
I just started using Ubuntu when I got my new laptop on wednesday and I have been trying to get WoW to work.  I followed the directions on this website:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

the launcher will run, but when I try to run the game from the launcher, I am prompted to change my screen resolution and nothing happens.  When I try to run the game directly from WoW.exe, my computer freezes, and I can't do anything but move my mouse.  When trying to start from terminal, the following happens:

reid@dell:~$ wine "C:\program files\world of warcraft\wow.exe"
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c800000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c800000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x198af8) : stub, simulating 64MB for now, returning 64MB left
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

---

### Post by hikaricore on 2007-08-03
Video hardware?

+ How did you install your video drivers?

---

### Post by cryogenics on 2009-01-25
Install the video driver through the operating system.
Make sure you OpenGL Screen savers work
AND

Type in a terminal the command to make sure your 3d Sh*t wrks
Command

glxinfo | grep rendering

and see if that works.;)
install maybe trial of cedega and run it's diagnostic.

Wine vr= 1.1.13 and 8.10 ibex using 1024x768 and fire it off from the shortcut from desktop ,because your installed it through wine right ?
;)

---

