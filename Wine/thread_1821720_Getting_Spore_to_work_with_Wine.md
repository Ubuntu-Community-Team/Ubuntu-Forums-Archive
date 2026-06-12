---
title: "Getting Spore to work with Wine"
date: 2011-08-09
forum: Wine
---

### Post by sabersong on 2011-08-09
I'm using Ubuntu 11.04, and I'm trying to run a game called Spore. According to WineHQ, Spore works just fine, but it doesn't. Everything I've found online says to install DCOM98 using Winetricks, but DCOM98 isn't available through winetricks anymore.

When I try to run it from the command line, I get the following output:

```
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x2928e40,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x29289c0,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x1de88d0, 0x2909814) stub
fixme:psapi:EnumPageFilesA (0x1de88d0, 0x28d4130) stub
fixme:win:EnumDisplayDevicesW ((null),0,0x28701c0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x286fd40,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x287004c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x286fbcc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x287004c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x286fbcc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x286f648,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x286f1c8,0x00000000), stub!
wine: Unhandled page fault on write access to 0x00200000 at address 0xf74a80a6 (thread 0009), starting debugger...

```

I should note that as far as I can tell, no debugger ever starts.

---

