---
title: "SecuROM has detected 'SoftICE'"
date: 2012-07-10
forum: Wine
---

### Post by circlemaster on 2012-07-10
Hello everybody ):P

I'm trying to install Oblivion GOTY through Wine but when I load either the main title screen or start the installer directly, I get an error message that refers me to: [http://www.securom.com/message.asp?m=module&c=3000+&l=en](http://www.securom.com/message.asp?m=module&c=3000+&l=en)
I also get some error messages in the terminal:
```
wine OblivionLauncher.exe 
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
```

```
wine setup.exe 
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0xed9184,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0xed8d04,0x00000000), stub!
fixme:file:K32EnumPageFilesA (0x7d2030, 0xeb9c84) stub
fixme:file:K32EnumPageFilesA (0x7d2030, 0xe845a0) stub
fixme:win:EnumDisplayDevicesW ((null),0,0xe2803c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0xe27bbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0xe28040,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0xe27bc0,0x00000000), stub!
fixme:cdrom:CDROM_GetMediaType : faking success
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation (0x00000007,0xeb1ef0,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:cursor:SetSystemCursor (0x10054,00007f00),stub!
fixme:cursor:SetSystemCursor (0x10080,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1008e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1009c,00007f03),stub!
fixme:cursor:SetSystemCursor (0x100aa,00007f01),stub!
fixme:cursor:SetSystemCursor (0x100b8,00007f88),stub!
fixme:cursor:SetSystemCursor (0x100c6,00007f86),stub!
fixme:cursor:SetSystemCursor (0x100d4,00007f83),stub!
fixme:cursor:SetSystemCursor (0x100e2,00007f82),stub!
fixme:cursor:SetSystemCursor (0x100f0,00007f84),stub!
fixme:cursor:SetSystemCursor (0x100fe,00007f04),stub!
fixme:cursor:SetSystemCursor (0x1010c,00007f02),stub!
fixme:cursor:SetSystemCursor (0x10054,00007f00),stub!
fixme:cursor:SetSystemCursor (0x80022,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x80020,00007f00),stub!
fixme:cursor:SetSystemCursor (0x20026,00007f03),stub!
fixme:cursor:SetSystemCursor (0x20024,00007f01),stub!
fixme:cursor:SetSystemCursor (0x50062,00007f88),stub!
fixme:cursor:SetSystemCursor (0x10066,00007f86),stub!
fixme:cursor:SetSystemCursor (0x1006a,00007f83),stub!
fixme:cursor:SetSystemCursor (0x1006e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x10072,00007f82),stub!
fixme:cursor:SetSystemCursor (0x10076,00007f84),stub!
fixme:cursor:SetSystemCursor (0x1007a,00007f04),stub!
fixme:cursor:SetSystemCursor (0x1007e,00007f02),stub!
fixme:process:GetLogicalProcessorInformation ((nil),0xed5ab8): stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:file:GetLongPathNameW UNC pathname L"\\\\.\\pipe\\svcctl"
err:rpc:I_RpcGetBuffer no binding
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
```

Now the appDB for this game states Platinum and Gold ratings, so why does this happen? The game runs fine in Windows 7.

```
wine --version
wine-1.4
```

Thankful for any help!:popcorn:

---

### Post by circlemaster on 2012-07-13
Here is a screenshot of the message. It's in swedish and roughly translated means: A mandatory security module cannot be started (3000).
[ATTACH]221188[/ATTACH]

---

### Post by bnice7 on 2012-07-24
I had the exact same issue w/ Oblivion GOTY.  Upgrading Wine to the latest version worked for me.  Add the Wine PPA to your software sources as described here:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by bnice7 on 2012-07-24
This bug report seems to describe the issue:

[http://bugs.winehq.org/show_bug.cgi?id=30410](http://bugs.winehq.org/show_bug.cgi?id=30410)

---

### Post by circlemaster on 2012-07-24
Thanks, that worked wonderfully!

---

### Post by bnice7 on 2012-07-24
> **circlemaster said:**
> Thanks, that worked wonderfully!

Glad to help :P

I'm having another issue though myself, every time I launch the game it asks me to re-enter the activation key.  Shouldn't I only have to do that once?  It activates every time, but it's annoying to have to re-enter it every single time I want to launch the game.  Any ideas?

---

