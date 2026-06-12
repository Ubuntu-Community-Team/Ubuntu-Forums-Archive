---
title: "Starcraft 2 Installer crash"
date: 2011-09-11
forum: Wine
---

### Post by sir.sargento on 2011-09-11
Hello all, I am currently running Xubuntu 11.04 as of right now. I have had Starcraft 2 installed on my old Ubuntu 11.04 install that was running unity. I never had as much trouble before as I have installing it now. Everytime i start the installation the installer crashes and says that the runtime asked it to close in an unusual way.

I got this to run before just using wine and since I haven't been able to get that to work even tried using Play On Linux but that didn't help either. Anybody have some ideas? 

If needed I can post the terminal output of what it says when it crashed but I cannot make any sense of it.

Thanks,
Tony

---

### Post by sir.sargento on 2011-09-11
Just thought id include the terminal output for anybody interested in helping. This is the last bit of it:

fixme:shdocvw:ClientSite_GetContainer (0x1b12e8)->(0x33ecc8)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1b12e8)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1b12e8)->(L"Done")
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 21
fixme:shdocvw:OleObject_Close (0x1b1240)->(1)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
err:wininet:NETCON_secure_connect SSL_connect failed: 12038
wine: Unhandled exception 0x40000015 at address 0x54b11d (thread 0034), starting debugger...
err:mmtime:TIME_MMTimeStop Timer still active?!
Process of pid=001a has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000002a    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000017    0
    00000013    0
    00000012    0
0000001c explorer.exe
    0000001d    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'

---

