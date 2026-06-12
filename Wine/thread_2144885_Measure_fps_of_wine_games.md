---
title: "Measure fps of wine games"
date: 2013-05-13
forum: Wine
---

### Post by Chelidze on 2013-05-13
So I found this thread while searching.

[http://ubuntuforums.org/showthread.php?t=1847105&p=11270377#post11270377](http://ubuntuforums.org/showthread.php?t=1847105&p=11270377#post11270377)

In this thread I found this commend that should enable onscreen fps counter 

```
[COLOR=#000000][FONT=Ubuntu Mono]WINEDEBUG=fps wine [/FONT][/COLOR][COLOR=Red][FONT=Ubuntu Mono]YOURGAME.exe[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] 2>&1 | tee /dev/stderr | sed -u -n -e '/trace/ s/.*approx //p' | osd_cat --lines=1 --font="lucidasanstypewriter-bold-18" --color=yellow[/FONT][/COLOR]
```

But When I try to use it I get this error

```
ABORT: Requested font not found
fixme:msvcrt:__clean_type_info_names_internal (0x345500) stub
fixme:msvcrt:__clean_type_info_names_internal (0x1002d680) stub
fixme:msvcrt:__clean_type_info_names_internal (0x33b4a8) stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f0055a0, 0x3f036b40, 0x3f036b38
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f0055a0, 0x3f036b78, 0x3f036b70
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f0055a0, 0x3f036b08, 0x3f036b00
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f0055a0, 0x3f036bb0, 0x3f036ba8
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f0055a0, 0x3f036be8, 0x3f036be0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f0055a0, 0x3f036b40, 0x3f036b38
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f0055a0, 0x3f036b78, 0x3f036b70
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f0055a0, 0x3f036b08, 0x3f036b00
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f0055a0, 0x3f036bb0, 0x3f036ba8
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f0055a0, 0x3f036be8, 0x3f036be0
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:iphlpapi:NotifyAddrChange (Handle 0x5add6bc, overlapped 0x58eb040): stub
fixme:winsock:WSALookupServiceBeginW (0x5add7bc 0x00000ff0 0x5add804) Stub!
[0514/003020:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599
fixme:dwrite:dwritefactory_CreateGdiCompatibleTextLayout (L"Steam":5 0x1f3410 10000.000000 10000.000000 1.000000 (nil) 0 0x33e4f8): semi-stub
fixme:dwrite:dwritetextlayout_GetMetrics (0x1f34b8)->(0x33e518): stub
fixme:dwrite:dwritefactory_CreateGdiCompatibleTextLayout (L"Connecting Steam account: levan27...":36 0x1f3410 10000.000000 10000.000000 1.000000 (nil) 0 0x33e4f8): semi-stub
fixme:dwrite:dwritetextlayout_GetMetrics (0x1f3510)->(0x33e518): stub
fixme:dwrite:dwritetextlayout_GetMetrics (0x1f3510)->(0x33e500): stub
fixme:dwrite:dwritetextlayout_GetMetrics (0x1f34b8)->(0x33e6b0): stub
fixme:dwrite:dwritetextlayout_GetMetrics (0x1f3510)->(0x33e6b0): stub
fixme:dwrite:dwritetextlayout_GetMetrics (0x1f34b8)->(0x33e678): stub
fixme:dwrite:dwritetextlayout_GetMetrics (0x1f3510)->(0x33e678): stub
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dwrite:dwritetextlayout_GetMetrics (0x1f34b8)->(0x33e138): stub
fixme:dwrite:dwritetextlayout_GetMetrics (0x1f34b8)->(0x33da98): stub
fixme:dwrite:dwritefactory_CreateMonitorRenderingParams (0x1): monitor setting ignored
fixme:dwrite:dwritetextlayout_Draw (0x1f34b8)->((nil) 0x28e24c0 0.000000 0.000000): stub
fixme:dwrite:dwritetextlayout_GetMetrics (0x1f3510)->(0x33e138): stub
fixme:dwrite:dwritetextlayout_GetMetrics (0x1f3510)->(0x33da98): stub
fixme:dwrite:dwritetextlayout_Draw (0x1f3510)->((nil) 0x28e24c0 0.000000 0.000000): stub
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1



```

 Does any one knows how to fix this issue ??

Thank you in advanced

---

### Post by oldos2er on 2013-05-13
Moved to Wine.

---

### Post by Chelidze on 2013-05-22
bump

---

### Post by Mark Phelps on 2013-05-22
You should have read the second post in the thread you cited -- where the filename has to be in lower case.  Your example has it in CAPS.

Also, the thread is from 2011 and mentions a font style in "lucid".  That was Ubuntu 10.04.  IF you're running something else, you need to reference a font that is current in that version.

---

### Post by Chelidze on 2013-05-22
> **Mark Phelps said:**
> You should have read the second post in the thread you cited -- where the filename has to be in lower case.  Your example has it in CAPS.

Also, the thread is from 2011 and mentions a font style in "lucid".  That was Ubuntu 10.04.  IF you're running something else, you need to reference a font that is current in that version.

what file name ?? are you talking about .exe file ?? if yes I understand that but can you tell me what font is the shock for ubuntu 13.04 because I could not find what are real fonts names

---

