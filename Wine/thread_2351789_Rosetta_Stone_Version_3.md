---
title: "Rosetta Stone Version 3"
date: 2017-02-06
forum: Wine
---

### Post by curticegough on 2017-02-06
Hello.  I am using Ubuntu 16.04 and I am having a problem with Wine 1.6.2.  I am trying to install Rosetta Stone Version 3 Spanish Latin America from CD's.  Installation of the core program goes just fine.  However, when I try to add a language level, Rosetta Stone cannot find any language CD's.  When I run wine through the terminal, I get this.
```

curtice@LinuxLoverPC:~/.wine/drive_c/Program Files (x86)/Rosetta Stone/Rosetta Stone Version 3$ wine RosettaStoneVersion3.exe
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
fixme:win:EnumDisplayDevicesW ((null),0,0x33f634,0x00000000), stub!
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:client_security_SetBlanket 0x7bb502c4, 0x168b58, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7bb502c4
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:client_security_SetBlanket 0x7bb502c4, 0x168c10, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7bb502c4
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030



```
Any help would be appreciated.  Thanks. :)

---

