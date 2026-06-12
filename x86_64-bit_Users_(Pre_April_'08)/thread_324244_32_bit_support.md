---
title: "32 bit support"
date: 2006-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by t4ggs on 2006-12-23
Hi, I installed Ubuntu 6.10 x64, i want to know how to install 32 bit programs like skype and google earth??

---

### Post by Pawel Stolowski on 2006-12-23
1. In general: you need to provide 32-bit libraries required by the application you wish to install. Some crucial libraries are packaged for 64-bit ubuntu and you may install them from official repos, e.g. ia32-libs, ia32-libs-gtk, ia32-libs-sdl, ia32-libs-kde etc. Sometimes you may need to unpack specific libraries (from 32-bit ubuntu debs, you need to download them by hand if needed) by yourself and place in /usr/lib32.
2. Read the thread "How to get specific programs to run under Dapper Drake 64-bit edition" (sticky thread on this forum).
3. Use Automatix ([http://www.getautomatix.com)](http://www.getautomatix.com)). It supports installation of popular 32-bit apps in 64-bit ubuntu (including GoogleEarth).

---

