---
title: "Winetricks vcrun2010 installation problem"
date: 2017-07-27
forum: Wine
---

### Post by lordcorvin2 on 2017-07-27
Hello all,

I'm heaving trouble installing VC redist 2010
I have installed latest wine-staging with winetricks

VC redist 2005 and 2008 installed fine Anything later than 2010 doesn't install, no idea why.

Can someone help a newb out?

```

ubuntu@Ubuntu:~$ winetricks vcrun2010
Using winetricks 20170614-next - sha256sum: cf3126ae45052eba3a2586da03dd65bf2b38a8193da8f27ff3878cc23be77f07 with wine-2.13 (Staging) and WINEARCH=win32
Executing w_do_call vcrun2010
Executing load_vcrun2010 
Using native,builtin override for following DLLs: msvcp100 msvcr100 vcomp100 atl100
Executing winetricks_early_wine regedit C:\windows\Temp\_vcrun2010\override-dll.reg
Executing cd /home/ubuntu/.cache/winetricks/vcrun2010
Executing wine vcredist_x86.exe
fixme:clusapi:GetNodeClusterState ((null),0x32eb14) stub!
fixme:advapi:DecryptFileA ("c:\\9d9c2edce4d6405054eae0cac8cb\\", 00000000): stub
fixme:ntdll:EtwRegisterTraceGuidsW (0x6cd15f38, 0x6cd20180, {e2821408-c59d-418f-ad3f-aa4e792aeb79}, 1, 0x33fcf0, (null), (null), 0x6cd20188): stub
fixme:ntdll:EtwRegisterTraceGuidsW   register trace class {e2821408-c59d-418f-ad3f-aa4e792aeb79}
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:thread:SetThreadStackGuarantee (0x33faf8): stub
fixme:msxml:domdoc_putref_schemas (0x15dca0)->(0x33f340 {VT_DISPATCH: 0x15de4c}): semi-stub
fixme:msxml:domdoc_get_readyState stub! (0x15dca0)->(0x33f328)
fixme:wintrust:SOFTPUB_VerifyImageHash Cannot verify hash for pszObjId="1.3.6.1.4.1.311.2.1.25"
fixme:ole:NdrCorrelationInitialize (0xcdb65c, 0xcdb7ec, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0xcdb60c, 0xcdb79c, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0xcdb62c, 0xcdb7bc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0xcdb5ec, 0xcdb77c, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0xcdb62c, 0xcdb7bc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0xcdb5ec, 0xcdb77c, 1024, 0x0): semi-stub
fixme:wer:WerReportCreate build report information from scratch for 0xba3838
fixme:wer:WerReportAddDump (0xba3838, 0x88, (nil), 2, 0xcdb118, (nil), 0) :stub
fixme:wer:WerReportSetParameter (0xba3838, 0, (null), L"Microsoft Visual C++ 2010  x86 Redistributable Setup") :stub
fixme:wer:WerReportSetParameter (0xba3838, 1, (null), L"10.0.30319") :stub
fixme:wer:WerReportSetParameter (0xba3838, 2, (null), L"10.0.30319.1") :stub
fixme:wer:WerReportSetParameter (0xba3838, 3, (null), L"1") :stub
fixme:wer:WerReportSetParameter (0xba3838, 4, (null), L" ") :stub
fixme:wer:WerReportSetParameter (0xba3838, 5, (null), L"None_UI_Interactive_Crash") :stub
fixme:wer:WerReportSetParameter (0xba3838, 6, (null), L"0xc0000005") :stub
fixme:wer:WerReportSetParameter (0xba3838, 7, (null), L"0") :stub
fixme:wer:WerReportSetParameter (0xba3838, 8, (null), L" ") :stub
fixme:wer:WerReportAddFile (0xba3838, L"C:\\users\\ubuntu\\Temp\\Setup_20170727_045522509.html", 5, 0x0) :stub
fixme:wer:WerReportAddFile (0xba3838, L"C:\\users\\ubuntu\\Temp\\Microsoft Visual C++ 2010  x86 Redistributable Setup_20170727_045522609.html", 5, 0x0) :stub
fixme:wer:WerReportSetUIOption (0xba3838, 3, L"Microsoft Visual C++ 2010 Redistributable Setup has failed") :stub
fixme:wer:WerReportSetUIOption (0xba3838, 8, L"Microsoft Visual C++ 2010 Redistributable Setup has failed") :stub
fixme:wer:WerReportSubmit (0xba3838, 1, 0x10, 0xcdb124) :stub
fixme:ntdll:EtwUnregisterTraceGuids deadbeef: stub
------------------------------------------------------
Note: command wine vcredist_x86.exe returned status 1. Aborting.
------------------------------------------------------



```

vcrun2012 error:

```

ubuntu@Ubuntu:~$ winetricks vcrun2012
Using winetricks 20170614-next - sha256sum: cf3126ae45052eba3a2586da03dd65bf2b38a8193da8f27ff3878cc23be77f07 with wine-2.13 (Staging) and WINEARCH=win32
Executing w_do_call vcrun2012
Executing load_vcrun2012 
Using native,builtin override for following DLLs: atl110 msvcp110 msvcr110 vcomp110
Executing winetricks_early_wine regedit C:\windows\Temp\_vcrun2012\override-dll.reg
Executing cd /home/ubuntu/.cache/winetricks/vcrun2012
Executing wine vcredist_x86.exe
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:advapi:DecryptFileW (L"C:\\users\\ubuntu\\Temp\\{33d1fd90-4274-48a1-9bc1-97e33d9c2d6f}\\", 00000000): stub
fixme:shell:SHAutoComplete stub
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
fixme:advapi:DecryptFileW (L"C:\\users\\ubuntu\\Temp\\{33d1fd90-4274-48a1-9bc1-97e33d9c2d6f}\\", 00000000): stub
fixme:wuapi:automatic_updates_Pause 
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:wintrust:SOFTPUB_VerifyImageHash Cannot verify hash for pszObjId="1.3.6.1.4.1.311.2.1.30"
fixme:ole:NdrCorrelationInitialize (0x97dc9c, 0x97de2c, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc4c, 0x97dddc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:wintrust:SOFTPUB_VerifyImageHash Cannot verify hash for pszObjId="1.3.6.1.4.1.311.2.1.30"
fixme:ole:NdrCorrelationInitialize (0x97dc9c, 0x97de2c, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc4c, 0x97dddc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:wintrust:SOFTPUB_VerifyImageHash Cannot verify hash for pszObjId="1.3.6.1.4.1.311.2.1.30"
fixme:ole:NdrCorrelationInitialize (0x97dc9c, 0x97de2c, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc4c, 0x97dddc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:wintrust:SOFTPUB_VerifyImageHash Cannot verify hash for pszObjId="1.3.6.1.4.1.311.2.1.30"
fixme:ole:NdrCorrelationInitialize (0x97dc9c, 0x97de2c, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc4c, 0x97dddc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:wintrust:SOFTPUB_VerifyImageHash Cannot verify hash for pszObjId="1.3.6.1.4.1.311.2.1.30"
fixme:ole:NdrCorrelationInitialize (0x97dc9c, 0x97de2c, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc4c, 0x97dddc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:wintrust:SOFTPUB_VerifyImageHash Cannot verify hash for pszObjId="1.3.6.1.4.1.311.2.1.30"
fixme:ole:NdrCorrelationInitialize (0x97dc9c, 0x97de2c, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc4c, 0x97dddc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc6c, 0x97ddfc, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x97dc2c, 0x97ddbc, 1024, 0x0): semi-stub
fixme:wuapi:automatic_updates_Resume 
------------------------------------------------------
Note: command wine vcredist_x86.exe returned status 4. Aborting.
------------------------------------------------------

```

---

### Post by sccman on 2017-07-29
You can ignore the fixme's. They are for developers in debugging.

Based on the messages from vcrun2010, there aren't any error messages, which is weird.

But for vcrun2012, fettouhi from ArchLinux seemed to have fixed the ReadStyleSheet error [here]("https://bbs.archlinux.org/viewtopic.php?id=139473"). Try installing directx9, which is required for vcrun2010 and 2012 on native Windows. You can do it through winetrick's GUI:

```
winetricks --gui
```

[B]1) Select the default wineprefix
2) Install a Windows DLL or component
3) [/B]Then install all of the **d3dx9'**s you see on there.

---

### Post by gordintoronto on 2017-07-30
It should work fine, according to this page:
[https://appdb.winehq.org/objectManager.php?sClass=version&iId=20406](https://appdb.winehq.org/objectManager.php?sClass=version&iId=20406)

---

### Post by lordcorvin2 on 2017-08-09
Thanks,

For some reason nothing worked. I had to nuke the Installation and Start from scratch. It works now. Not sure what was the problem.

---

