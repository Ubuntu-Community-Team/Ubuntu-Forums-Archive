---
title: "Photoshop stopped working"
date: 2014-12-06
forum: Wine
---

### Post by leunam12 on 2014-12-06
Hi, I have Ubuntu 14.04 and I am used to run Photoshop CS2 under WINE with no problems at all; however, a few days ago Photoshop stopped working. When I try to start it the splash screen comes up fine, but after a few seconds it turns dark and then shuts down. This is the error message:

```
err:shell:HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),1,3,(nil),0,(nil)) - stub!
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:wia:wiadevmgr_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
fixme:wia:wiadevmgr_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
fixme:wia:wiadevmgr_QueryInterface interface {00000019-0000-0000-c000-000000000046} not implemented
fixme:wintab32:X11DRV_WTInfoW Return proper size
fixme:thread:start_thread Started native thread 00000044
fixme:thread:start_thread Started native thread 00000045
err:ntdll:RtlpWaitForCriticalSection section 0x7bcc7be0 "loader.c: loader_section" wait timed out in thread 0045, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bcc7be0 "loader.c: loader_section" wait timed out in thread 0035, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bcc7be0 "loader.c: loader_section" wait timed out in thread 0039, blocked by 0009, retrying (60 sec)
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc367d1
```

Thanks for your help.

---

