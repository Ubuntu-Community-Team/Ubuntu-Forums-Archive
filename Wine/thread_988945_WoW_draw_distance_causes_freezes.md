---
title: "WoW draw distance causes freezes"
date: 2008-11-21
forum: Wine
---

### Post by Ixonal on 2008-11-21
So yeah, finally got WoW working, but it seems that having a draw distance greater than the minimum causes it to crash. anyone else having this problem and/or have a solution?

running ubuntu 8.10, wine 1.1.8, wow 3.0.3
got a dual core pentium processor, 2gb of ddr2 ram, and a geforce 9800gt with the newest beta drivers

---

### Post by Ixonal on 2008-11-22
so yeah, bumpy

had been workin ok with draw distance set to maybe a half of normal, but then I got on a flightpath and it froze up again

---

### Post by Ixonal on 2008-11-22
ok, got some new data. ran wow from the console and got this...

```

ixonal@Reinverka-II:~/.wine/drive_c/Program Files/World of Warcraft$ wine Wow.exe -opengl
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x39ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f520,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df44,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x374025c4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x39dae4,0x00000000), stub!
E: shm.c: mmap() failed: Cannot allocate memory
W: pstream.c: Failed to import memory block.
fixme:wave:widRecorder Recovering from XRUN!
err:module:load_builtin_dll failed to load .so lib for builtin L"dbghelp.dll": /usr/bin/../lib/wine/dbghelp.dll.so: failed to map segment from shared object: Cannot allocate memory
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
err:module:load_builtin_dll failed to load .so lib for builtin L"dbghelp.dll": /usr/bin/../lib/wine/dbghelp.dll.so: failed to map segment from shared object: Cannot allocate memory

```

---

### Post by Ixonal on 2008-11-23
bump

anybody even looking at this?

---

