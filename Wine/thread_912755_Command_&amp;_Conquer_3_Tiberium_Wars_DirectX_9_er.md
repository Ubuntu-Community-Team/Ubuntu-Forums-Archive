---
title: "Command &amp; Conquer 3: Tiberium Wars DirectX 9 error"
date: 2008-09-07
forum: Wine
---

### Post by Omega234 on 2008-09-07
Hello all.

I have successfully managed to install Command & Conquer 3: Tiberium Wars (Kane Edition) on Wine 1.1.0 as per the instructions at the Wine AppDB page [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7440").  When I run the game, the small start screen appears, and then I get an error:
[INDENT]Please make sure you have DirectX 9.0 or higher installed.  Also verify that your video card meets the minimum system requirements, and that you do not have hardware acceleration disabled in the Display control panel.[/INDENT]
While starting, the console displays all this:
[INDENT][FONT="Courier New"]fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x166ac2c,0x00000004,0x166ac28) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1669f20): Stub!
err:wgl:opengl_error No OpenGL support compiled in.
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
fixme:psapi:EnumPageFilesA (0xe52e10, 0x164aff4) stub
fixme:psapi:EnumPageFilesA (0xe52e10, 0x161951c) stub
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x1645a70,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:cursor:SetSystemCursor (0x10048,00007f00),stub!
fixme:cursor:SetSystemCursor (0x10086,00007f00),stub!
fixme:cursor:SetSystemCursor (0x10088,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1008a,00007f03),stub!
fixme:cursor:SetSystemCursor (0x1008c,00007f01),stub!
fixme:cursor:SetSystemCursor (0x1008e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x10090,00007f86),stub!
fixme:cursor:SetSystemCursor (0x10092,00007f83),stub!
fixme:cursor:SetSystemCursor (0x10094,00007f82),stub!
fixme:cursor:SetSystemCursor (0x10096,00007f84),stub!
fixme:cursor:SetSystemCursor (0x10098,00007f04),stub!
fixme:cursor:SetSystemCursor (0x1009a,00007f02),stub!
fixme:cursor:SetSystemCursor (0x10048,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1005c,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1005e,00007f00),stub!
fixme:cursor:SetSystemCursor (0x10062,00007f03),stub!
fixme:cursor:SetSystemCursor (0x10064,00007f01),stub!
fixme:cursor:SetSystemCursor (0x10068,00007f88),stub!
fixme:cursor:SetSystemCursor (0x1006c,00007f86),stub!
fixme:cursor:SetSystemCursor (0x10070,00007f83),stub!
fixme:cursor:SetSystemCursor (0x10074,00007f85),stub!
fixme:cursor:SetSystemCursor (0x10078,00007f82),stub!
fixme:cursor:SetSystemCursor (0x1007c,00007f84),stub!
fixme:cursor:SetSystemCursor (0x10080,00007f04),stub!
fixme:cursor:SetSystemCursor (0x10084,00007f02),stub!
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x167f948): Stub!
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x167f640): Stub!
fixme:thread:SetThreadIdealProcessor (0x704): stub
fixme:thread:SetThreadIdealProcessor (0x74c): stub
fixme:thread:SetThreadIdealProcessor (0x750): stub
fixme:d3d9:D3DPERF_GetStatus (void) : stub
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl[/FONT][/INDENT]

I know my machine meets the minimum requirements - I played the game when I had XP installed.  I'm still rather new to Wine, so any help would be greatly appreciated.

[EDIT]
I just tried using Wine-Doors to install C&C3 (different version of Wine in a different directory).  The game installed fine, and I can run it, but I am unable to use the keyboard (this is a problem for many reason, including that the game requires you to enter your name before doing anything else).  I cannot paste into the text box at all.  The keyboard still works as I am able to use other programs at the same time.

If anyone could please give me any information for either problem, that would be great!

---

