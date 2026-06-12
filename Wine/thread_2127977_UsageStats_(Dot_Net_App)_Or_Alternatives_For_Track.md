---
title: "UsageStats (Dot Net App) Or Alternatives For Tracking My Keyboard And Mouse Usage"
date: 2013-03-21
forum: Wine
---

### Post by user2037 on 2013-03-21
Looking for a way to study how I'm using keyboard and mouse to optimize my flow and reduce RSI. Objo's UsageStats from [https://usagestats.codeplex.com/](https://usagestats.codeplex.com/) looks interesting, but it fails in Wine and Mono. Anyone know how to fix it or any good alternatives?

Wine
```

fixme:mscoree:ConfigFileHandler_startElement Unknown element L"configSections" in state 1
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"sectionGroup" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"section" in state 3
fixme:mscoree:parse_supported_runtime sku=L".NETFramework,Version=v4.0,Profile=Client" not implemented
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"userSettings" in state 1
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"UsageStats.Properties.Settings" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
...
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:CLRMetaHost_GetRuntime Unrecognized version L"v4.0"
The entry point method could not be loaded

```

Mono
```

The entry point method could not be loaded

```

EDIT:
Mono JIT compiler version 2.10.8.1 (Debian 2.10.8.1-1ubuntu2.2)
Copyright (C) 2002-2011 Novell, Inc, Xamarin, Inc and Contributors. [www.mono-project.com](www.mono-project.com)
	TLS:           __thread
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  amd64
	Disabled:      none
	Misc:          softdebug 
	LLVM:          supported, not enabled.
	GC:            Included Boehm (with typed GC and Parallel Mark)

wine-1.5.26

---

