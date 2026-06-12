---
title: "Installing MS Office 2010 with Wine 1.5"
date: 2012-12-27
forum: Wine
---

### Post by sarel29 on 2012-12-27
Hi,

I'm trying to install MS Office with wine1.5 on 32bit Ubuntu 12.04. I've followed the instructions here [http://ubuntuforums.org/showthread.php?t=1885051](http://ubuntuforums.org/showthread.php?t=1885051) and everything worked fine setting it all up, but now that I come to try and install the .exe file nothing is happening. When I try to install it this is the output I get:

```
sarah@sarah-VirtualBox:~$ wine 805fdeb1cf864fbfbfa947e0977cbe06_Pod14_en-gb.exe fixme:service:QueryServiceConfig2W Level 6 not implemented
fixme:service:QueryServiceConfig2W Level 6 not implemented
fixme:winhttp:request_query_option unimplemented option 93
fixme:winhttp:request_query_option unimplemented option 93
fixme:winhttp:request_query_option unimplemented option 93
fixme:winhttp:request_query_option unimplemented option 93
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:dwmapi:DwmIsCompositionEnabled 0x6ad0f77c
fixme:iphlpapi:NotifyAddrChange (Handle 0x1f2e8d0, overlapped 0x1f2e8dc): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ba48,0x00000000), stub!
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of CGID_ShellDocView
fixme:ieframe:ClOleCommandTarget_QueryStatus (0x1a4764)->((null) 1 0x32c9dc (nil))
fixme:ieframe:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 37 of CGID_ShellDocView
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of CGID_ShellDocView
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x1d86348)->()
fixme:ieframe:ClientSite_GetContainer (0x1a4764)->(0x32c9fc)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentDisposition (0x1d86348)->(0x32c10c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x1d86348)->(0x32bdbb)
fixme:ieframe:DocHostUIHandler_GetDropTarget (0x1a4764)
fixme:ieframe:ClientSite_GetContainer (0x1a4764)->(0x32ce2c)
fixme:imm:ImmReleaseContext (0x10076, 0x1d30dc8): stub
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x1c9fb18)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x1e2ef50)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x1ca00a8)->()
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1d4d330)->(0x32cefc 0x32ced4 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1ca19a0)->(0x32cefc 0x32ced4 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1d4fcb8)->(0x32cefc 0x32ced4 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2f111f8)->(0x32cefc 0x32ced4 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1ca14a8)->(0x32cefc 0x32ced4 0)
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000001
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000002
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2f20200)->(0x32cb5c 0x32cb34 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3043ce0)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3047b20)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x30483d0)->()
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x1ca00a8)->(0x32bb44)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x1ca00a8)->(0x32bb08)
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:jscript:to_object unsupported undefined
fixme:msxml:ClassFactory_QueryInterface interface {342d1ea0-ae25-11d1-89c5-006008c3fbfc} not implemented
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3044220)->(0x32cadc 0x32cab4 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3047f78)->(0x32cadc 0x32cab4 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x30487a0)->(0x32cadc 0x32cab4 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3094938)->(0x32cb5c 0x32cb34 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x30483d0)->(0x32bb44)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x30483d0)->(0x32bb08)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3047b20)->(0x32bb44)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x3047b20)->(0x32bb08)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3043ce0)->(0x32bb44)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x3043ce0)->(0x32bb08)
fixme:wininet:InternetLockRequestFile STUB
fixme:msxml:ClassFactory_QueryInterface interface {342d1ea0-ae25-11d1-89c5-006008c3fbfc} not implemented
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2f2a868)->(0x32cb5c 0x32cb34 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x457c3f0)->(0x32cb5c 0x32cb34 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:jscript:cc_token @if not implemented
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x457c588)->(0x32cb5c 0x32cb34 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x4726498)->(0x32cb5c 0x32cb34 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2f245e8)->(0x32cb5c 0x32cb34 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:ieframe:ControlSite_OnFocus (0x1a4764)->(0)
fixme:ieframe:InPlaceSite_OnInPlaceDeactivateEx fNoRedraw (1) ignored
fixme:mshtml:HlinkTarget_SetBrowseContext (0x147b78)->((nil))
fixme:mshtml:nsChannel_IsNoCacheResponse (0x1d86348)->(0x32cbbb)
```

Any suggestions on how I could get this working would be much appreciated.

---

