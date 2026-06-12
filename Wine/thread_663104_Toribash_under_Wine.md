---
title: "Toribash under Wine"
date: 2008-01-09
forum: Wine
---

### Post by Zeranamu on 2008-01-09
I've just recently got back into Linux, and am using Ubuntu (which is wonderful!), and I'm trying to run Toribash 3.06 under Wine, since the linux distro isn't out yet... I fixed the missing DLL problems, but now I'm running into this:

[email]zeranamu@zeranamu-laptop:~/.wine[/email]/drive_c/Program Files/Toribash-3.06$ wine toribash.exe

err:reg:SCSI_getprocentry SCSI type line scan count error (fscanf returns 1, expected 2)

fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fdb79a8)->((nil),00000008)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - (nil) 0x7fdcd578 ): semi-stub 
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x1002c 0x7fdcd578 ): semi-stub
fixme:wgl:wglChoosePixelFormatARB unused pfAttribFList

It opens an invisible window (shows up on the task bar) with the name SDL_app, but no window actually shows up. 

I do also have the ddraw and dinput dlls, as well as having tried switching both graphics and sound from hardware to emulation and back. Still no go!

Also my Wine is the latest version I could get as of last night, and I've tried emulating almost every Windows OS in the config when trying to run the program, if I remember right I get the exact same errors.

Can anybody help me fix this?

---

