---
title: "Unable to use Wine at all"
date: 2013-11-11
forum: Wine
---

### Post by osarusan on 2013-11-11
I'm using Ubuntu 13.10 x64, freshly installed, and I am having no luck at all getting wine to work. I don't even mean wine with a specific program, I mean wine itself. Even winecfg fails.

I have tried using the wine package from the repositories, as well as various wine versions within playonlinux, and I have even tried using the wine packages from the Ubuntu wine team PPA. Every one of them fails.

Each time I delete the .wine prefix, so I know it's not as simple as that. When I run winecfg on a fresh prefix, this is the output:

```
osarusan@GLaDOS:~$ winecfg
wine: created the configuration directory '/home/osarusan/.wine'
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:seh:RtlAddFunctionTable 0x61e45620 1 61e40000: stub
fixme:seh:RtlAddFunctionTable 0x61776ba0 1 61700000: stub
fixme:seh:RtlAddFunctionTable 0x64f69540 1 64f40000: stub
fixme:seh:RtlAddFunctionTable 0x622c6620 1 622c0000: stub
fixme:seh:RtlAddFunctionTable 0x6ce47620 1 6ce40000: stub
fixme:seh:RtlAddFunctionTable 0x682d4b20 1 682c0000: stub
fixme:seh:RtlAddFunctionTable 0x638d1dc0 1 63800000: stub
fixme:seh:RtlAddFunctionTable 0x6e6ea0 1 6c0000: stub
fixme:seh:RtlAddFunctionTable 0x68f5b6a0 1 68f40000: stub
fixme:seh:RtlAddFunctionTable 0x6b431bc0 1 69c40000: stub
fixme:iphlpapi:NotifyAddrChange (Handle 0xece278, overlapped 0xece240): stub
err:module:attach_process_dlls "user32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\rundll32.exe" failed, status c0000005
wine: configuration in '/home/osarusan/.wine' has been updated.
XIO:  fatal IO error 12 (Cannot allocate memory) on X server ":0"
      after 318 requests (318 known processed) with 0 events remaining.

```

I tried bringing this up on the wine forums as well, but the only advice I've gotten so far is to delete my wine prefix. I'm posting here as well in the hopes that someone might be able to help me figure out what is going on here.

---

### Post by QIII on 2013-11-11
*Moved to **&#8203;Wine***

---

