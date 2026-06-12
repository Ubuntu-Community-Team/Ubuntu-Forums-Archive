---
title: "Urgent : Age of mythology garbled video"
date: 2008-02-10
forum: Wine
---

### Post by darthshak on 2008-02-10
Hi everyone

      I seem to be having a rather unique issue which no one seems to be having. I installed Age of Mythology yesterday, and it ran well. Now, I found that in the main menu, the position over which the cursor was hovering did not correspond to the menu item being highlighted (ie if the cursor was over 'Save Game', 'Single Player' was highlighted).

I remedied this by changing the game resolution to 1280x1024x32. I asked Wine to simulate a virtual desktop of 1280 x 1024. And it seemed to solve the mouse issue and the game was working FINE. However, the game seemed a bit laggy. Then, I recalled from a forum that the WINEDEBUG command is known to speed things up for age of mythology.

So I entered : WINEDEBUG=-all wine aom.exe

And poof! At start up, this is what would happen in stages. Here are the screenshots : 

Screenshot 1 : The screen I get on just clicking run
Screenshot 2 : The screen after the opening cinematic

(More importantly, the game crashed. I had to do a Ctrl + Alt + Backspace and restart X.)
As you can see, the background is absolute garbage.

This is the output of the wine command :
darthshak@T61:~/Age of Mythology$ wine aom.exe
fixme:imm:ImmGetDefaultIMEWnd ((nil) - (nil) 0x11fd40 ): semi-stub
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmReleaseContext (0x10024, 0x11fd40): stub
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x11fd40): semi-stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34f4d8, 260): stub
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed60,0x00000000), stub!
fixme:imm:ImmGetDefaultIMEWnd (0x1002a - (nil) 0x11f300 ): semi-stub
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x34dae4,0x00000000), stub!
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message WM_NCPAINT hdc packing not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
wine: Unhandled page fault on write access to 0x00a995e4 at address 0x300016ad (thread 0013), starting debugger...
Unhandled exception: page fault on write access to 0x00a995e4 in 32-bit code (0x300016ad).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:300016ad ESP:0034df1c EBP:00960de4 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000de4 EBX:ffffffff ECX:00138800 EDX:00000000
 ESI:00188db4 EDI:00020030
Stack dump:
0x0034df1c:  0034e0d8 00000001 04000003 00188db4
0x0034df2c:  ffffffff 00000010 00000010 00000379
0x0034df3c:  000001f4 00000000 00400000 00000200
0x0034df4c:  30001410 00000000 00000000 00400000
0x0034df5c:  00000000 000010de 00000000 00000000
0x0034df6c:  30047274 0000006c 0000100f 000001e0
Backtrace:
=>1 0x300016ad in binkw32 (+0x16ad) (0x00960de4)
  2 0x00000000 (0x00000000)
0x300016ad: movb        %dl,0x0(%ecx,%ebp,1)
Modules:
Module  Address                 Debug info      Name (68 modules)
PE        400000-  40f000       Deferred        movieplayer
PE      30000000-3006d000       Export          binkw32
ELF     7b800000-7b928000       Deferred        kernel32<elf>
  \-PE  7b820000-7b928000       \               kernel32
ELF     7bc00000-7bca3000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca3000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d15f000-7d252000       Deferred        wined3d<elf>
  \-PE  7d170000-7d252000       \               wined3d
ELF     7d252000-7d2a8000       Deferred        ddraw<elf>
  \-PE  7d260000-7d2a8000       \               ddraw
ELF     7d62b000-7d63e000       Deferred        libresolv.so.2
ELF     7d651000-7d66f000       Deferred        iphlpapi<elf>
  \-PE  7d660000-7d66f000       \               iphlpapi
ELF     7d66f000-7d6ce000       Deferred        rpcrt4<elf>
  \-PE  7d680000-7d6ce000       \               rpcrt4
ELF     7d6ce000-7d770000       Deferred        ole32<elf>
  \-PE  7d6e0000-7d770000       \               ole32
ELF     7d770000-7d7bb000       Deferred        dsound<elf>
  \-PE  7d780000-7d7bb000       \               dsound
ELF     7d7cb000-7d7f1000       Deferred        msacm32<elf>
  \-PE  7d7d0000-7d7f1000       \               msacm32
ELF     7d7f1000-7d8b7000       Deferred        libasound.so.2
ELF     7dc47000-7dc5c000       Deferred        midimap<elf>
  \-PE  7dc50000-7dc5c000       \               midimap
ELF     7dc5c000-7dc74000       Deferred        msacm32<elf>
  \-PE  7dc60000-7dc74000       \               msacm32
ELF     7dc74000-7dcaa000       Deferred        winealsa<elf>
  \-PE  7dc80000-7dcaa000       \               winealsa
ELF     7dcaa000-7dcb3000       Deferred        libxcursor.so.1
ELF     7dcb3000-7dcb8000       Deferred        libxfixes.so.3
ELF     7dcb8000-7dcbb000       Deferred        libxcomposite.so.1
ELF     7dcbb000-7dcc1000       Deferred        libxrandr.so.2
ELF     7dcc1000-7dcc9000       Deferred        libxrender.so.1
ELF     7dcc9000-7dccc000       Deferred        libxinerama.so.1
ELF     7dd7f000-7dd81000       Deferred        libnvidia-tls.so.1
ELF     7dd81000-7e834000       Deferred        libglcore.so.1
ELF     7e834000-7e8d8000       Deferred        libgl.so.1
ELF     7e8d8000-7e8dd000       Deferred        libxdmcp.so.6
ELF     7e8dd000-7e8e0000       Deferred        libxau.so.6
ELF     7e8e0000-7e9d1000       Deferred        libx11.so.6
ELF     7e9d1000-7e9df000       Deferred        libxext.so.6
ELF     7e9f2000-7ea82000       Deferred        winex11<elf>
  \-PE  7ea00000-7ea82000       \               winex11
ELF     7ead2000-7eaf2000       Deferred        libexpat.so.1
ELF     7eaf2000-7eb1d000       Deferred        libfontconfig.so.1
ELF     7eb1d000-7eb32000       Deferred        libz.so.1
ELF     7eb32000-7eba2000       Deferred        libfreetype.so.6
ELF     7eba2000-7ec2f000       Deferred        winmm<elf>
  \-PE  7ebb0000-7ec2f000       \               winmm
ELF     7ec2f000-7ec7a000       Deferred        advapi32<elf>
  \-PE  7ec40000-7ec7a000       \               advapi32
ELF     7ec7a000-7ed12000       Deferred        gdi32<elf>
  \-PE  7ec90000-7ed12000       \               gdi32
ELF     7ed12000-7ee4d000       Deferred        user32<elf>
  \-PE  7ed30000-7ee4d000       \               user32
ELF     7ee4d000-7ee6a000       Deferred        imm32<elf>
  \-PE  7ee50000-7ee6a000       \               imm32
ELF     7ee6a000-7ee75000       Deferred        libnss_files.so.2
ELF     7ee75000-7ee8d000       Deferred        libnsl.so.1
ELF     7ee8d000-7ee96000       Deferred        libnss_compat.so.2
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     f7d03000-f7d07000       Deferred        libdl.so.2
ELF     f7d07000-f7e51000       Deferred        libc.so.6
ELF     f7e52000-f7e6a000       Deferred        libpthread.so.0
ELF     f7e7d000-f7f91000       Deferred        libwine.so.1
ELF     f7f93000-f7fb1000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
        00000009    0
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
00000010 
        00000011    0
00000012 (D) Z:\home\darthshak\Age of Mythology\movieplayer.exe
        00000016    0
        00000015    0
        00000014   15
        00000013    0 <==
Backtrace:
=>1 0x300016ad in binkw32 (+0x16ad) (0x00960de4)
  2 0x00000000 (0x00000000)
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4e4,0x00000000), stub!
darthshak@T61:~/Age of Mythology$ winecfg
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

Output of wine command for wine gfxinfo.exe:
fixme:imm:ImmGetDefaultIMEWnd ((nil) - (nil) 0x11fd40 ): semi-stub
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmReleaseContext (0x10024, 0x11fd40): stub
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x11fd40): semi-stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34f4d8, 260): stub
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed60,0x00000000), stub!
fixme:imm:ImmGetDefaultIMEWnd (0x1002a - (nil) 0x11f300 ): semi-stub
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x34dae4,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x32 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x24 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x16 @0! (XRandR)
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x16 @0! (XRandR)
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
^[^[err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1

Also, here are the contents of the gfxinfo.exe file : 
INFO : Opening vendor file gfxconfig/0x10DE_*.gfx
INFO : Querying graphics file gfxconfig\0x10de_nvidia.gfx
Looking for driver entry(0x014F)
Driver Entry not found

Interestingly, this is the output of the wine command for gfxinfo.exe


I also checked that my graphics card (nVidia Quadro NVS 140M) is supported for Age of Mythology.

I am a programmer and (forgive me if I'm wrong. I'm a newbie to linux), I noticed that this this is the first time I'm getting the fixme about ERASEBKGND. I did a bit of research on this and found that it is a function to erase the background, and if that function is not working, there will be garbage in the background.

Also, I was a bit worried about the "Deferred" status on all those libraries. I did a check on each one of them to see that they were installed. 

After encountering this error, here is all the antics that I tried out : 
 Antic 1 : Tried removing the Virtual  Desktop setting of 1280 x 1024
Result : Game worked. But mouse pointer issue persisted

Antic 2 : I reinstalled MSXML Parser.
Result : No change from Garbled graphics

Antic 3 : I reinstalled wine and Age of mythology and the parser
Result : No change

Antic 4 : I tried a manual override of DirectX files
Result : Game did not run. Said that it requires DirectX 8.1 or higher

Antic 5 : Tried running it on Vista. Said Rockalldll.dll is corrupt. At that point, I thought the same issue might have existed in wine as well. So i copied a good version of rockalldll.dll to both the system32 folder of wine and the AOM folder.
Result : No change

Also, guys, one important note about the ERASEBKGND fixme. I was not getting that message when I successfully ran AOM on the 1280x1024 background. It popped up after I ran the DEBUG command.

The first main problem is : Why is the Wine virtual desktop resizing itself from 1280 x 1024 to the size shown in the screenshot?

Secondly, what exactly did the WINEDEBUG command do? Also, did restarting X while wine was running screw it?

Lastly, why did ERASEBKGND suddenly start whining?

---

### Post by darthshak on 2008-02-10
Also, I got a d3draw error when I tried running it without a virtual desktop.

---

### Post by pcjunkie on 2008-02-11
Its a wine bug, Still can't work it out..
Googeling lots of reports but no fixes or solutions. Tried re-installing wine with no luck, as if it was going to learn anything by doing that anyway....

---

### Post by happyhamster on 2008-02-11
Which wine version are you guys using? I use wine 0.9.52 for most applications, because the newer versions seem to have quite some issues. (installation problems with 54/53 and screendepth/resolution/windowed-nonwindowed/stability issues with 55/54/53)

I guess the development of wine  is too fast for me to keep up :lolflag:

---

### Post by darthshak on 2008-02-12
I am using wine 0.9.54

I'm guessing that the problem I had was that there was no directx on it. I'm certain of opengl because i seemed to be able to run quake 3.

As of now, I will be giving 0.9.55 a shot. WineHQ claims to have fixed some direct3d issues with it.

---

