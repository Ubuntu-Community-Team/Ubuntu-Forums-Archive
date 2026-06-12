---
title: "Problems printing in Wine - C#.NET program"
date: 2015-10-17
forum: Wine
---

### Post by mr-good555 on 2015-10-17
Lubuntu 15.04, Wine 1.7.50

Except for a "msxml3", and a "dotnet40" install using winetricks, everything is default.
[LIST]
[*]Microsoft .Net Framework 4 Client Profile (4.0.30319) 
[*]Microsoft .Net Framework 4 Extended (4.0.30319) 
[/LIST]

This long list of fixme lines is when I run the AMP.exe program where I log in, chose a text file, read and formatted it, printed it, and closed my program. During this time, I was also trying to see what was being written in the terminal, so changing focus is also inserted in there. (Just saying you can probably skip everything until the last few lines then read it backwards)

```
bigaisdgood1@HP-Aaron:~/AMP-Truck$ wine AMP.exe
fixme:thread:SetThreadStackGuarantee (0x32fc04): stub
err:ole:CoGetContextToken apartment not initialised
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"System.Data"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:nls:GetUserPreferredUILanguages stub: 0 0x32e23c (nil) 0x32e238
fixme:thread:GetThreadPreferredUILanguages 0, 0x32e23c, (nil) 0x32e238
fixme:shell:URL_ParseUrl failed to parse L"Accessibility"
fixme:advapi:RegisterTraceGuidsW (0xa005d2, (nil), {8e9f5090-2d75-4d03-8a81-e5afbf85daf1}, 1, 0x32e110, (null), (null), 0xd3a898): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {8e9f5090-2d75-4d03-8a81-e5afbf85daf1}
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:shell:URL_ParseUrl failed to parse L"AMP.resources"
fixme:shell:URL_ParseUrl failed to parse L"AMP.resources"
fixme:shell:URL_ParseUrl failed to parse L"MySql.Data"
fixme:shell:URL_ParseUrl failed to parse L"System.Data"
fixme:shell:URL_ParseUrl failed to parse L"System.Transactions"
fixme:shell:URL_ParseUrl failed to parse L"System.Transactions"
fixme:shell:URL_ParseUrl failed to parse L"System.Numerics"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.Data.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Data.resources"
fixme:shell:URL_ParseUrl failed to parse L"MySql.Data.resources"
fixme:shell:URL_ParseUrl failed to parse L"MySql.Data.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.EnterpriseServices"
fixme:ole:CoGetDefaultContext -1 {000001c6-0000-0000-c000-000000000046} 0x32f150 stub
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:shell:URL_ParseUrl failed to parse L"AMP.resources"
fixme:shell:URL_ParseUrl failed to parse L"AMP.resources"
fixme:gdiplus:GdipCreateHalftonePalette stub
fixme:gdiplus:GdipGetNearestColor (0x1feae0, 0x32eacc): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x2016a0, 0x32e9c8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x2016a0, 0x32e9c8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x2016a0, 0x32eaa4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x2016a0, 0x32eaa4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x2100d0, 0x32e7e8): Passing color unmodified
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:gdiplus:GdipGetNearestColor (0x17b458, 0x32e934): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x208ac0, 0x32ea20): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x208ac0, 0x32ea20): Passing color unmodified
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:gdiplus:GdipGetNearestColor (0x1ad0d8, 0x32df64): Passing color unmodified
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:gdiplus:GdipGetNearestColor (0x1ad0d8, 0x32eae4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1ad0d8, 0x32ea20): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1ad0d8, 0x32e564): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x20df80, 0x32ea90): Passing color unmodified
fixme:process:FlushProcessWriteBuffers : stub
fixme:gdiplus:GdipGetNearestColor (0x15d508, 0x32e884): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x20a710, 0x32e064): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x20a710, 0x32e884): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x20a710, 0x32e500): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1ad018, 0x32e884): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x20a710, 0x32e500): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x20a710, 0x32ea90): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x20a710, 0x32e480): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1323d0, 0x32e330): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x20a710, 0x32e1b4): Passing color unmodified
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms.resources"
fixme:ole:CoGetDefaultContext -1 {000001c6-0000-0000-c000-000000000046} 0x32ea08 stub
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:ole:CoGetDefaultContext -1 {000001c6-0000-0000-c000-000000000046} 0x32e92c stub
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:gdiplus:GdipGetNearestColor (0x20d8a8, 0x32ea20): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1bea28, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1b4230, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1bea28, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1ca340, 0x32eb18): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1ca340, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1ca340, 0x32ebf4): Passing color unmodified
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:gdiplus:GdipGetNearestColor (0x1bf008, 0x32e0a4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1bf008, 0x32e0a4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1bee90, 0x32e884): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1bff78, 0x32e5a8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1fc9b0, 0x32e684): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1bff78, 0x32e5a8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1fc9b0, 0x32e5a8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1fc9b0, 0x32e5a8): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x208f40, 0x32e59c): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x208f40, 0x32e5a8): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:gdiplus:GdipGetNearestColor (0x208f40, 0x32e09c): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:gdiplus:GdipGetNearestColor (0x1f2ac8, 0x32dc6c): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1f2ac8, 0x32dc78): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32dfc8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32dfc8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e684): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e59c): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e09c): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32dff8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32dfec): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e684): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e59c): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e684): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e59c): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e59c): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e5a8): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1e2918, 0x32e09c): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:winspool:SetJobW Ignoring everything other than document title
fixme:gdiplus:GdipGetNearestColor (0x1c1dd8, 0x9d4da84): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1da618, 0x9d4d9a8): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1f1c40, 0x32e884): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1f1c40, 0x32ea20): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1f1c40, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1f1c40, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1f1c40, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1f1c00, 0x32eb18): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1f1c00, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1f1c00, 0x32ebf4): Passing color unmodified
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:gdiplus:GdipGetNearestColor (0x1f1c00, 0x32e884): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1f1c00, 0x32ea20): Passing color unmodified
fixme:gdiplus:create_gdi_logbrush unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:get_gdi_brush_color unhandled brush type 2
fixme:gdiplus:GdipGetNearestColor (0x1f1c40, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1f1c40, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1f1c40, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1aca70, 0x32eb18): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1aca70, 0x32ebf4): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x1aca70, 0x32ebf4): Passing color unmodified
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:thread:NtQueryInformationThread info class 16 not supported yet
fixme:advapi:UnregisterTraceGuids deadbeef: stub

```

The problem here is that in Windows, the output is supposed to contain the account details and the transactions. Here in Ubuntu, it's just a mess of number fragments that don't even resemble the numbers or values in the transactions.

I also noticed that the more lines are expected, the more it prints. Maybe it's a size or font issue.

I should also mention that it prints a really tiny amount only (not even 1/20 of the full document) and it's always printed at the very bottom of the page.

Note that the printer test pages and other example documents print fine, so this shouldn't be a driver problem.

UPDATE: 2015 OCT 19
Just adding that installing the font did not change the result. I also  tried changing the paper size through the printer, but all it did was  change the location of the print. At least I can see more of the  document.

Now I've noticed that it seems to squeeze everything into 2-3 character lengths, then cuts off like 3/4th of the bottom of each character.

---

