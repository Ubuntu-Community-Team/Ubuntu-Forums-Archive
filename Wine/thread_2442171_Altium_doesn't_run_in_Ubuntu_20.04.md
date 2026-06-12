---
title: "Altium doesn't run in Ubuntu 20.04"
date: 2020-04-30
forum: Wine
---

### Post by TimmyPage on 2020-04-30
I've been using Altium Designer under wine for many years. But since  yesterday that I have upgraded my Ubuntu from 19.10 to 20.04 it has  stopped working.
I've tried PlayOnLinux to use lower versions of wine, but it is not a  wine issue. I've used other flavours of ubuntu 20.04, tried reinstalling  Altium Designer inside a fresh wine environment, tried installing  different versions of it but it didn't work.
It's seems that this problem is not directly related to wine, but  probably something has been changed in Ubuntu 20.04 that is generating  this problem which is preventing DXP.EXE from starting.
I've tried Altium Designer version 14, 16 and 17 and also Altium CircuitStudio. All of them have same  issue. Program stops loading at loading integratedlibrary.dll  (integrated library server) and integrated debugger reports: 
```
Access violation at address 0DD8600E in module 'IntegratedLibrary.DLL'. Read of address 00000008 at 0DD8600E.
Failed to load IntegratedLibrary.
```

Here's an output of running Altium Designer 16 inside wine 3.0.1
```
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d2b0, (nil) 0x32d2d8
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d2b0 (nil) 0x32d2d8) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d2b0, 0x1aca680 0x32d2d8
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d2b0 0x1aca680 0x32d2d8) returning a dummy value (current locale)
00aa:err:winediag:SQLDrivers No ODBC drivers could be found. Check the settings for your libodbc provider.
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d734, (nil) 0x32d75c
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d734 (nil) 0x32d75c) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d734, 0x1f3a680 0x32d75c
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d734 0x1f3a680 0x32d75c) returning a dummy value (current locale)
reg: Unable to open the registry key '%s'.
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:uxtheme:BufferedPaintInit Stub ()
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d2d8, (nil) 0x32d300
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d2d8 (nil) 0x32d300) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d2d8, 0x2753350 0x32d300
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d2d8 0x2753350 0x32d300) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d238, (nil) 0x32d260
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d238 (nil) 0x32d260) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d238, 0x3253350 0x32d260
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d238 0x3253350 0x32d260) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:dwmapi:DwmIsCompositionEnabled 0x32f858
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, (nil) 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 (nil) 0x32d130) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, 0x7d33350 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 0x7d33350 0x32d130) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, (nil) 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 (nil) 0x32d130) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, 0x8743350 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 0x8743350 0x32d130) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, (nil) 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 (nil) 0x32d130) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, 0x8dc3350 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 0x8dc3350 0x32d130) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, (nil) 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 (nil) 0x32d130) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, 0x9bd3350 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 0x9bd3350 0x32d130) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:mscoree:get_runtime_info unsupported startup flags 4
00aa:err:mscoree:CLRRuntimeInfo_GetRuntimeHost Wine Mono is not installed
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, (nil) 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 (nil) 0x32d130) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, 0xa0a3350 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 0xa0a3350 0x32d130) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, (nil) 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 (nil) 0x32d130) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, 0xba33350 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 0xba33350 0x32d130) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, (nil) 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 (nil) 0x32d130) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, 0xc773350 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 0xc773350 0x32d130) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, (nil) 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 (nil) 0x32d130) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, 0xcf63350 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 0xcf63350 0x32d130) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, (nil) 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 (nil) 0x32d130) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32d108, 0xde23350 0x32d130
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32d108 0xde23350 0x32d130) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:thread:GetThreadUILanguage : stub, returning default language.
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32cc98, (nil) 0x32ccc0
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32cc98 (nil) 0x32ccc0) returning a dummy value (current locale)
00aa:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x32cc98, 0xe583350 0x32ccc0
00aa:fixme:nls:get_dummy_preferred_ui_language (0x38 0x32cc98 0xe583350 0x32ccc0) returning a dummy value (current locale)
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:err:ole:create_server class {00000507-0000-0010-8000-00aa006d2ea4} not registered
00aa:err:ole:CoGetClassObject no class object {00000507-0000-0010-8000-00aa006d2ea4} could be created for context 0x5
00aa:fixme:win:DisableProcessWindowsGhosting : stub
00aa:fixme:shell:SetCurrentProcessExplicitAppUserModelID L"Altium Designer": stub

```

 Dunno what to do  [IMG]https://forum.winehq.org/images/smilies/icon_sad.gif[/IMG]

---

### Post by QIII on 2020-04-30
Hello!

I don't know, but you might find [this]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=2799") interesting.  You might also want to visit [WineHQ's forums]("https://forum.winehq.org/").

While it is possible that Someone will be able to give you an answer, please bear in mind that it is not the responsibility of Linux distro developers to make sure applications work under Wine in new releases.  It's the responsibility of those who maintain the Wine environment and applications to keep up.  That being the case, your best bet may be to make that community aware of the issues you are facing.

Cheers!

---

### Post by TimmyPage on 2020-04-30
> **QIII said:**
> Hello!

Hello and thanks for replying to my question.

> **QIII said:**
> I don't know, but you might find [this]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=2799") interesting.  You might also want to visit [WineHQ's forums]("https://forum.winehq.org/").
I've already asked this question [there]("https://forum.winehq.org/viewtopic.php?f=2&t=33811") too. 

> **QIII said:**
> While it is possible that Someone will be able to give you an answer,  please bear in mind that it is not the responsibility of Linux distro  developers to make sure applications work under Wine in new releases.   It's the responsibility of those who maintain the Wine environment and  applications to keep up.  That being the case, your best bet may be to  make that community aware of the issues you are facing.
I'm not accusing distro developers to take responsibility of this incident. I'm just saying this problem has been created and I'm looking for a solution to solve it. I'm saying this should be something related to ubuntu because changing wine versions didn't solve the problem and this is a common problem between different versions of this application running on newest version of ubuntu which were working without problem in the past.
I'm just saying there might be something new in the latest version of ubuntu which came in as an improvement but has affected running this wine application.

---

### Post by TimmyPage on 2020-04-30
Problem solved by installing jet40 and overriding 'msado15' to native, builtin.

---

### Post by trungpc97 on 2020-11-19
> **TimmyPage said:**
> Problem solved by installing jet40 and overriding 'msado15' to native, builtin.


Can you install successfully AD17 on Unbuntu? If can, please help me!

---

