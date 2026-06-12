---
title: "Steam: Blacklight Retribution error"
date: 2012-07-29
forum: Wine
---

### Post by ngrieb on 2012-07-29
Hi all,

I am trying to get a Steam game Blacklight Retribution to work under WINE. I have looked through the winehq app db and seen that there are a few people who claim to have it working. I think my problem is with MS .NET framework: I get a launch screen where I am under the impression one is supposed to log-in, but I see no log-in prompt or enter button. I am simply stuck at this screen. Is anyone having a similar issue? Has anyone been able to resolve it? Is there a trick that I am missing?

Thanks

---

### Post by javajames79 on 2012-08-07
Hi, i'm experiencing a similar issue here, i will come back and update if i find anything. Similarly if you do, could i request you do too?

---

### Post by javajames79 on 2012-08-07
Just for some information this is what wine actually says:

```
~/.wine/drive_c/Program Files (x86)/Steam/steamapps/common/blacklightretribution$ wine Blacklight\ Retribution.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0xf4e000 0 0x32fc9c 4
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32dc94,0x00000000), stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x15f9b0, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32e1d4)
WMI: pIWbemLocator->ConnectServer failed: 0x80041001
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
Ready.
Connecting to patchserver.blacklight.crypticstudios.com:7255
fixme:thread:SetThreadIdealProcessor (0x9c): stub
PatchClientLib: connecting to patchserver.blacklight.crypticstudios.com:7255
PatchClientLib: redirecting to 208.95.184.178:7255
PatchClientLib: skipping unneeded autoupdate CrypticLauncherBL
PatchClientLib: successfully connected
AutopatchDialog thread shutting down
fixme:thread:SetThreadIdealProcessor (0x98): stub
fixme:urlmon:URLMoniker_BindToObject use running object table
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:dwmapi:DwmIsCompositionEnabled 0x6abae480
fixme:iphlpapi:NotifyAddrChange (Handle 0x421ee8cc, overlapped 0x421ee8b0): stub
fixme:ieframe:ClOleCommandTarget_QueryStatus (0x186f24)->((null) 1 0x32b234 (nil))
fixme:ieframe:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 37 of group {000214d1-0000-0000-c000-000000000046}
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ieframe:ClientSite_GetContainer (0x186f24)->(0x32b244)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClientSite_GetContainer (0x186f24)->(0x32c0b4)
fixme:imm:ImmReleaseContext (0x1014e, 0x423b4330): stub
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:navigate_url Unsupported args (Flags 0x32d5bc:3; TargetFrameName (nil):-1)
fixme:win:EnumDisplayDevicesW ((null),0,0x32d330,0x00000000), stub!
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:ieframe:DocHostUIHandler_GetDropTarget (0x186f24)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:ieframe:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 67 of group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 63 of group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 103 of group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 2315 of group {de4ba900-59ca-11cf-9592-444553540000}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x433130a8)->()
fixme:ieframe:ClientSite_GetContainer (0x186f24)->(0x32dd88)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of group {000214d1-0000-0000-c000-000000000046}
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x43315bf0)->(0x32d858 0x32d830 0)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:ieframe:DocHostUIHandler_GetDropTarget (0x186f24)
fixme:ras:RasEnumConnectionsA (0x630607a8,0x4393e7e0,0x6305f610),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:service:EnumServicesStatusW resume handle not supported
fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
fixme:mshtml:nsChannel_IsNoCacheResponse (0x433130a8)->(0x32ca10)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x4334d860)->(0x32d468 0x32d440 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x4334e1b8)->(0x32d468 0x32d440 0)
fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x4334e700)->(0x32d468 0x32d440 0)
fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x4334eb68)->(0x32d468 0x32d440 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x4334efd8)->(0x32d468 0x32d440 0)
fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
fixme:urlmon:SecManagerImpl_ProcessUrlAction Unsupported arguments
fixme:mshtml:nsChannel_GetContentLength (0x4334e390)->(0x32cf74)

```

According to a friend it's supposed to take some time. But no more code gets spewed out for the next half hour, so i usually just quit it, because of these fixmes and also thqat my friend say's it usually only takes 10 minutes. It stays on 0% CPU usage also. So it's pretty blatantly crashed.

---

### Post by ngrieb on 2012-08-18
Ok, thanks for the update. I'll see if I leave mine for a few minutes if anything happens. What version of .NET do you have installed?

---

