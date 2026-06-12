---
title: "C&amp;C Generals Zero Hour + Wine"
date: 2007-08-19
forum: Wine
---

### Post by Fittersman on 2007-08-19
i was trying to install generals and i get this error:

```
[root@Christopher-PC media]# cd GENERALS1/
[root@Christopher-PC GENERALS1]# wine setup
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:advapi:LookupAccountNameW (null) L"root" (nil) 0x33b740 (nil) 0x33b744 0x33b738 - stub
fixme:advapi:LookupAccountNameW (null) L"root" 0x1732f0 0x33b740 0x173620 0x33b744 0x33b738 - stub
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
err:msi:ACTION_CallDllFunction Custom action (L"C:\\windows\\temp\\msi16f8.tmp":L"RegisterISDriverFiles") caused a page fault: c0000005
err:ntdll:RtlpWaitForCriticalSection section 0x7efec6e4 "loader.c: loader_section" wait timed out in thread 0009, blocked by 000d, retrying (60 sec)
wine: Critical section 7efec6e4 wait failed at address 0x7ef98c20 (thread 0009), starting debugger...
Unhandled exception: wait failed on critical section 0x7efec6e4 loader_section
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7ef98c20
[root@Christopher-PC GENERALS1]# Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0


```

the installer kinda hangs for a while then crashes/exits. o yeah, and by the way im on fedora 7, but it cant be that much different can it?

---

