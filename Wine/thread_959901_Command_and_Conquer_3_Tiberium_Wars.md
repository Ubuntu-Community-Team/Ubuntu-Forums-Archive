---
title: "Command and Conquer 3 Tiberium Wars"
date: 2008-10-26
forum: Wine
---

### Post by Espryon on 2008-10-26
It always says No CD/DVD-ROM drive found 

heres the output from trying to run it in terminal 

najix@NaJiX-DeskToP-ProJecT-Nemesis:~$ env WINEPREFIX="/home/najix/.wine" wine "C:\Program Files\Electronic Arts\Command & Conquer 3\CNC3.exe"
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x17ba520,0x00000004,0x17ba51c) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x17b940c): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x17b9258,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x10218f0, 0x1799d1c) stub
fixme:psapi:EnumPageFilesA (0x10218f0, 0x1764638) stub
najix@NaJiX-DeskToP-ProJecT-Nemesis:~$ 



heres output from kanes in terminal 

najix@NaJiX-DeskToP-ProJecT-Nemesis:~$ env WINEPREFIX="/home/najix/.wine" wine "C:\Program Files\Electronic Arts\Command & Conquer 3 Kane's Wrath\cnc3ep1.exe"
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x1b9a3e0,0x00000004,0x1b9a3dc) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1b992cc): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x1b99118,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0xf4c7d0, 0x1b79bd4) stub
fixme:psapi:EnumPageFilesA (0xf4c7d0, 0x1b444f0) stub
najix@NaJiX-DeskToP-ProJecT-Nemesis:~$ 


anyone know any fixes?


like some registry mount fixes?

Kanes wrath is even like screw you i cant find a disk 

/cry 

anyone??

FIXED

Use the autodetect menu from inside wine and mount the cd rom drive everything works and its on a compiz cube too also i have cursors no editing

---

### Post by Gcentrex on 2008-10-27
Just use a no-cd crack that's what I did to play Command and Conquer 3 Tiberium Wars with a patched version of wine.

---

