---
title: "WINE Problem with TurboTax 2014"
date: 2015-02-04
forum: Wine
---

### Post by leong2 on 2015-02-04
hi. I am completely new to Ubuntu. I just spent all day trying to fix this problem without success. I don't know much about Ubuntu so hopefully you can help me out.

I have wine 1.17.18 installed. Also installed TurboTax 2014. I can run some .exe files without problem using wine. But I get errors/warnings when I run this

=====================================================

Satellite-A70:~/.wine/drive_c/Program Files/TurboTax 2014$ wine tt2014.exe 

fixme:thread:GetThreadPreferredUILanguages 56, 0x32fa64, 0x32fa78 0x32fa6c
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x32f640 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x32f4cc 1 C) semi-stub

Unhandled Exception:
System.TypeInitializationException: An exception was thrown by the type initializer for <Module> ---> <CrtImplementationDetails>.ModuleLoadException: The C++ module failed to load during process initialization.
 ---> System.InvalidProgramException: Invalid IL code in <Module>:CActivationManager.{ctor} (CActivationManager*): IL_009b: ldc.i4.s  14


  at <Module>.?A0xe382785e.??__EgActivationManager@@YMXXZ () [0x00000] in <filename unknown>:0 
  at <Module>._initterm_m (System.MonoFNPtrFakeClass* pfbegin, System.MonoFNPtrFakeClass* pfend) [0x00000] in <filename unknown>:0 
  at <Module>.<CrtImplementationDetails>.LanguageSupport.InitializePerProcess (<CrtImplementationDetails>.LanguageSupport* ) [0x00000] in <filename unknown>:0 
  at <Module>.<CrtImplementationDetails>.LanguageSupport._Initialize (<CrtImplementationDetails>.LanguageSupport* ) [0x00000] in <filename unknown>:0 
  at <Module>.<CrtImplementationDetails>.LanguageSupport.Initialize (<CrtImplementationDetails>.LanguageSupport* ) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at <Module>.<CrtImplementationDetails>.ThrowModuleLoadException (System.String errorMessage, System.Exception innerException) [0x00000] in <filename unknown>:0 
  at <Module>.<CrtImplementationDetails>.LanguageSupport.Initialize (<CrtImplementationDetails>.LanguageSupport* ) [0x00000] in <filename unknown>:0 
  at <Module>..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeInitializationException: An exception was thrown by the type initializer for <Module> ---> <CrtImplementationDetails>.ModuleLoadException: The C++ module failed to load during process initialization.
 ---> System.InvalidProgramException: Invalid IL code in <Module>:CActivationManager.{ctor} (CActivationManager*): IL_009b: ldc.i4.s  14


  at <Module>.?A0xe382785e.??__EgActivationManager@@YMXXZ () [0x00000] in <filename unknown>:0 
  at <Module>._initterm_m (System.MonoFNPtrFakeClass* pfbegin, System.MonoFNPtrFakeClass* pfend) [0x00000] in <filename unknown>:0 
  at <Module>.<CrtImplementationDetails>.LanguageSupport.InitializePerProcess (<CrtImplementationDetails>.LanguageSupport* ) [0x00000] in <filename unknown>:0 
  at <Module>.<CrtImplementationDetails>.LanguageSupport._Initialize (<CrtImplementationDetails>.LanguageSupport* ) [0x00000] in <filename unknown>:0 
  at <Module>.<CrtImplementationDetails>.LanguageSupport.Initialize (<CrtImplementationDetails>.LanguageSupport* ) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at <Module>.<CrtImplementationDetails>.ThrowModuleLoadException (System.String errorMessage, System.Exception innerException) [0x00000] in <filename unknown>:0 
  at <Module>.<CrtImplementationDetails>.LanguageSupport.Initialize (<CrtImplementationDetails>.LanguageSupport* ) [0x00000] in <filename unknown>:0 
  at <Module>..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
fixme:msvcrt:__clean_type_info_names_internal (0x1b5e6b4) stub
fixme:msvcrt:__clean_type_info_names_internal (0x19af8fc) stub
fixme:msvcrt:__clean_type_info_names_internal (0x157dee0) stub
fixme:msvcrt:__clean_type_info_names_internal (0x3f8334) stub
fixme:msvcrt:__clean_type_info_names_internal (0x16ee03c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x1e25012c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x121a83fc) stub
fixme:msvcrt:__clean_type_info_names_internal (0x4a91223c) stub

==================================================

All these alien messages came out. I already did some research on multiple forums but seems the problems are not the same.

Would you please give me some clues?

Thanks.

---

### Post by TheFu on 2015-02-05
From the appdb: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=623](https://appdb.winehq.org/objectManager.php?sClass=application&iId=623)
> 
WARN*ING: the latest versions add DRM (Digital Rights Management) to the software, which is even said to mess with your hard disk*'s first sectors! (sector 33, to be exact) Given this information, decide on your own whether to use it or not... [030216] Oh, and alternative packages are: TaxCut, TaxAct.

Basically - take it back and let Intuit know why. Buy Taxcut from H&Rb

The last report is for 2012 version: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=27491](https://appdb.winehq.org/objectManager.php?sClass=version&iId=27491) - following those instructions might help. It is only bronze level support, however. I switched to Taxcut the first year Intuit added DRM and never looked back.

---

### Post by leong2 on 2015-02-05
> **TheFu said:**
> From the appdb: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=623](https://appdb.winehq.org/objectManager.php?sClass=application&iId=623)


Basically - take it back and let Intuit know why. Buy Taxcut from H&Rb

The last report is for 2012 version: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=27491](https://appdb.winehq.org/objectManager.php?sClass=version&iId=27491) - following those instructions might help. It is only bronze level support, however. I switched to Taxcut the first year Intuit added DRM and never looked back.

Thanks for the reply. I uninstalled TurboTax 2014 and then I attempted to follow the two commands in that winehq page. But now i can't get TurboTax installed again. I get the following messages. It appears some dll is not found?

wine: Call from 0x7b83be75 to unimplemented function msvcr110.dll.__CxxExceptionFilter, aborting
wine: Call from 0x7b83be75 to unimplemented function msvcr110.dll.__CxxExceptionFilter, aborting


Sigh.. it is so frustrating.  

Thanks!

---

### Post by TheFu on 2015-02-05
If there are any issues, it will be frustrating - this applies even if you aren't a C/C++ developer.  I see that error above, looked in the WINE directory and found msvcr110.dll - since I don't do Windows development anymore, can't really look at the DLL internals to see if those methods exist in this specific version. They seem like extremely standard calls, based on the name alone. 

The winehq instructions are very specific - run the first, do the install, change the machine type, then run the program.  If you don't follow the order exactly .... 

BTW, if you need to start over - either **rm -rf ~/.wine/** or just move it do  a different name or set your WINE_PREFIX variable to some other directory and start over.  It is common to have a different WINE_PREFIX for every Windows program running.  Winetricks are cached locally, so there won't be a new download every time.

Follow the instructions, carefully.

Or you can install Windows into a VM and be done (assuming a modern CPU/RAM). If you don't have a license that will install, you can use a 30 day trial for stuff like this. Just be certain you file the taxes before the trial ends. Or you will be reinstalling everything again for another 30 day trial (assuming you don't just pay MSFT) just to add a few things and print.

Wish it wasn't so hard, but it is hard for the Intuit team to bother testing on Linux at all too.

---

