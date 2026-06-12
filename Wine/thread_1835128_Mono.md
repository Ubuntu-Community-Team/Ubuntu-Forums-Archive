---
title: "Mono"
date: 2011-08-28
forum: Wine
---

### Post by Kodeine on 2011-08-28
Salutations!

So I'm trying to execute a executable file with wine. However I received this error.
```
install the Windows version of Mono to run .NET executables
```

I then tried to execute the file with native to Ubuntu mono via 'mono file.exe' but that was also to no avail as I received this.

```
** (Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe:5229): WARNING **: Method '<Module>:_WinMainCRTStartup ()' in assembly '/home/zack/Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe' contains native code that cannot be executed by Mono on this platform. The assembly was probably created using C++/CLI.


** (Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe:5229): WARNING **: Method '<Module>:<CrtImplementationDetails>.DoDllLanguageSupportValidation ()' in assembly '/home/zack/Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe' contains native code that cannot be executed by Mono on this platform. The assembly was probably created using C++/CLI.


** (Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe:5229): WARNING **: Method '<Module>:_decode_pointer (void*)' in assembly '/home/zack/Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe' contains native code that cannot be executed by Mono on this platform. The assembly was probably created using C++/CLI.


** (Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe:5229): WARNING **: Method '<Module>:<CrtImplementationDetails>.ThrowNestedModuleLoadException (System.Exception,System.Exception)' in assembly '/home/zack/Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe' contains native code that cannot be executed by Mono on this platform. The assembly was probably created using C++/CLI.


Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for <Module> ---> System.MissingMethodException: Method contains unsupported native code
  at (wrapper managed-to-native) <Module>:<CrtImplementationDetails>.ThrowNestedModuleLoadException (System.Exception,System.Exception)
  at <Module>.<CrtImplementationDetails>.LanguageSupport.Cleanup (<CrtImplementationDetails>.LanguageSupport* , System.Exception innerException) [0x00000] in <filename unknown>:0 
  at <Module>.<CrtImplementationDetails>.LanguageSupport.Initialize (<CrtImplementationDetails>.LanguageSupport* ) [0x00000] in <filename unknown>:0 
  at <Module>..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---

```

It says 'contains native code that cannot be executed by Mono on this platform.' So why have they used mono if it's not entirely cross platform? Does anyone know how I can run this file?

Thanks bye!

---

### Post by directhex on 2011-08-28
> **Kodeine said:**
> Salutations!

So I'm trying to execute a executable file with wine. However I received this error.
```
install the Windows version of Mono to run .NET executables
```

I then tried to execute the file with native to Ubuntu mono via 'mono file.exe' but that was also to no avail as I received this.

```
** (Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe:5229): WARNING **: Method '<Module>:_WinMainCRTStartup ()' in assembly '/home/zack/Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe' contains native code that cannot be executed by Mono on this platform. The assembly was probably created using C++/CLI.


** (Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe:5229): WARNING **: Method '<Module>:<CrtImplementationDetails>.DoDllLanguageSupportValidation ()' in assembly '/home/zack/Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe' contains native code that cannot be executed by Mono on this platform. The assembly was probably created using C++/CLI.


** (Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe:5229): WARNING **: Method '<Module>:_decode_pointer (void*)' in assembly '/home/zack/Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe' contains native code that cannot be executed by Mono on this platform. The assembly was probably created using C++/CLI.


** (Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe:5229): WARNING **: Method '<Module>:<CrtImplementationDetails>.ThrowNestedModuleLoadException (System.Exception,System.Exception)' in assembly '/home/zack/Desktop/FFOW_EFIS_PATCH_V1.2.0_TO_V1.3.0.exe' contains native code that cannot be executed by Mono on this platform. The assembly was probably created using C++/CLI.


Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for <Module> ---> System.MissingMethodException: Method contains unsupported native code
  at (wrapper managed-to-native) <Module>:<CrtImplementationDetails>.ThrowNestedModuleLoadException (System.Exception,System.Exception)
  at <Module>.<CrtImplementationDetails>.LanguageSupport.Cleanup (<CrtImplementationDetails>.LanguageSupport* , System.Exception innerException) [0x00000] in <filename unknown>:0 
  at <Module>.<CrtImplementationDetails>.LanguageSupport.Initialize (<CrtImplementationDetails>.LanguageSupport* ) [0x00000] in <filename unknown>:0 
  at <Module>..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---

```

It says 'contains native code that cannot be executed by Mono on this platform.' So why have they used mono if it's not entirely cross platform? Does anyone know how I can run this file?

Thanks bye!

They've used C++/CLI by the look of it, which is the .NET version of C++. It't not true .NET (it's more of a regular C++ with .NET wrapped around it) and is therefore not cross-platform.

It might run with the Windows version of Mono, in Wine - since then it's running Windows C++ code in "Windows"

---

### Post by Tweak42 on 2011-08-29
I did have some success getting .NET up to 4.0 installed in wine using latest winetricks at [http://winetricks.org]("http://winetricks.org").  There is a certain order you needed to install different packages (forgot where I found the guide).  Highly recommend using a clean PREFIX if you trying this because I had to start from scratch many times till I got it right.

Unfortunately, in the end I still wasn't able to get the .NET program I wanted running, and had to acquiesce to WinXP in a VirtualBox instance. :-(

---

