---
title: "Can't play Smite on Ubuntu Gnome, any solution?"
date: 2017-05-22
forum: Wine
---

### Post by linon2 on 2017-05-22
Hello fellows,

I just installed Ubuntu Gnome 17.04.

I would really like to install Smite on my new distribution. So I followed the steps showed in this tutorial, which work for the youtuber :

[https://www.youtube.com/watch?v=elZoUNCMNF0](https://www.youtube.com/watch?v=elZoUNCMNF0)

What I did :

- Installed WIne 2.8 on POL
- Created a new virtual WIndows installing Adobe Air, Corefont, d3dx11, 10 & 9, d3dx9.43, dotnet 20 and dotnet 40, dxfullsetup, PhysX, vbrun6, vcrun2005 to 2013, vcrun6
- Used the .exe file downloaded on official website [https://www.smitegame.com/download/](https://www.smitegame.com/download/)
- Launcher started, updated it
- Downloaded the game
- Installed pre-requisites (needed several attempts)
- Clicked on "Play", the game started then crashed

Now I can't even open the launcher, which worked at first. 

This is what the PlayOnLinux debugger tells me :

```
[05/22/17 19:44:17] - Running wine-2.8 start.exe /wait /unix $WINEPREFIX/drive_c/./users/Public/Bureau/Smite.lnk 
(Working directory : /home/clm/.PlayOnLinux/wineprefix/Smite/dosdevices/c:/Program Filep11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: Can't open the shared object file No file or folder dep11-kit: 
couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: 
Can't open the shared object file: No file[05/22/17 19:44:42] - Running wine-2.8 start.exe /wait /unix $WINEPREFIX/drive_c/./users/Public/Bureau/Smite.lnk 
(Working directory : /home/clm/.PlayOnLinux/wineprefix/Smite/dosdevices/c:/Program Filefixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:thread:SetThreadStackGuarantee (0x33fbf4): stub
fixme:ole:CoGetApartmentType (0x2e1e6dc, 0x2e1e6d8): semi-stub
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceProcess"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:ole:CoGetApartmentType (0x3dde73c, 0x3dde738): semi-stub
fixme:ole:CoGetApartmentType (0x3cde66c, 0x3cde668): semi-stub
fixme:shell:URL_ParseUrl failed to parse L"PatcherEngine"
fixme:ole:CoGetApartmentType (0x3ede6bc, 0x3ede6b8): semi-stub
fixme:shell:URL_ParseUrl failed to parse L"HirezUtils"
fixme:shell:URL_ParseUrl failed to parse L"HirezUtils"
err:module:load_builtin_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.0: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type
err:winedevice:async_create_driver failed to create driver L"WineBus": c0000142
fixme:nls:get_dummy_preferred_ui_language (0x0 0x3ddd488 (nil) 0x3ddd484) returning a dummy value (current locale)
fixme:nls:get_dummy_preferred_ui_language (0x0 0x3ddd488 0x158fc0 0x3ddd484) returning a dummy value (current locale)
fixme:shell:URL_ParseUrl failed to parse L"PatcherData"
fixme:exec:SHELL_execute flags ignored: 0x00000100
err:exec:shellex_load_object_and_run failed to get data object
fixme:shell:URL_ParseUrl failed to parse L"PatcherMisc"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:process:FlushProcessWriteBuffers : stub
fixme:ntdll:EtwRegisterTraceGuidsW (0x9607c2, (nil), {8e9f5090-2d75-4d03-8a81-e5afbf85daf1}, 1, 0x3ddbd1c, (null), (null), 0xcc1040): stub
fixme:ntdll:EtwRegisterTraceGuidsW   register trace class {8e9f5090-2d75-4d03-8a81-e5afbf85daf1}
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Management"
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier dep11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichiererr:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:shell:URL_ParseUrl failed to parse L"PatcherEngine.resources"
fixme:shell:URL_ParseUrl failed to parse L"PatcherEngine.resources"
fixme:advapi:LsaOpenPolicy ((null),0x3ddd554,0x00000800,0x3ddd52c) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:shell:URL_ParseUrl failed to parse L"System.Runtime.Remoting"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:ole:CoGetApartmentType (0x4dfe3bc, 0x4dfe3b8): semi-stub
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceProcess.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceProcess.resources"
fixme:advapi:RegisterEventSourceW (L".",L"HiRezSoftwareManagerSvc"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x104c680,0x104c588): stub
fixme:ole:CoGetApartmentType (0x4f0cc74, 0x4f0cbdc): semi-stub
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:ole:CoGetApartmentType (0x4f0aabc, 0x4f0aa1c): semi-stub
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:ole:CoGetApartmentType (0x4f0cb80, 0x4f0cadc): semi-stub
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:ole:CoGetApartmentType (0x4f0cba8, 0x4f0cb0c): semi-stub
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:wbemprox:wbemprox_cf_QueryInterface interface {b196b28f-bab4-101a-b69c-00aa00341d07} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {00000144-0000-0000-c000-000000000046} not implemented
fixme:wbemprox:wbem_locator_ConnectServer authentication not supported
fixme:wbemprox:wbem_locator_ConnectServer specific locale not supported
fixme:wbemprox:wbem_locator_ConnectServer unsupported flags
fixme:wbemprox:client_security_QueryBlanket 
fixme:wbemprox:client_security_Release 0x7d4f7c54
fixme:wbemprox:client_security_SetBlanket 0x7d4f7c54, 0x18c758, 4294967295, 0, L"<COLE_DEFAULT_PRINCIPAL>", 2, 3, (nil), 0x00000020
fixme:wbemprox:client_security_Release 0x7d4f7c54
fixme:wbemprox:wbem_services_QueryInterface interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4} not implemented
fixme:wbemprox:wbem_services_QueryInterface interface {b196b283-bab4-101a-b69c-00aa00341d07} not implemented
fixme:wbemprox:wbem_services_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
fixme:wbemprox:wbem_services_QueryInterface interface {00000144-0000-0000-c000-000000000046} not implemented
err:wbemprox:wql_error syntax error, unexpected TK_ID, expecting TK_SELECT
err:ntdll:RtlLeaveCriticalSection section 0x110b08 is not acquired
```

I'm pretty new to Linux, so I have no idea what to do.

Thanks by advance!

---

### Post by Oby on 2017-06-20
Seems as if the new anti-cheat tools they implemented broke Wine compatibility: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=34969](https://appdb.winehq.org/objectManager.php?sClass=version&iId=34969)

---

### Post by sccman on 2017-07-08
Looks like missing dependencies. Try installing them:

```
[COLOR=#111111][FONT=Consolas]sudo apt-get install p11-kit-modules:i386

[/FONT][/COLOR]wget https://raw.github.com/spaetzlecode/getlibs/master/getlibs
sudo chown root:root getlibs
sudo chmod +x getlibs
sudo mv -n getlibs /usr/local/bin
sudo /usr/local/bin/getlibs -p gnome-keyring:i386



```

Sources:
[[COLOR=#111111][FONT=Consolas]p11-kit-modules:i386[/FONT][/COLOR]]("https://askubuntu.com/questions/370737/p11-kit-typical-problem-with-wine")
[getlibs]("https://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so")

---

