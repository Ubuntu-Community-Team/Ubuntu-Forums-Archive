---
title: "Can't install Visual C++ 2008 Redist."
date: 2015-04-14
forum: Wine
---

### Post by stretch4 on 2015-04-14
I can't install vcrun2008. It seems like it's trying to install the 32-bit, even though I'm on a 64-bit system. That's just a guess though, I don't really know what I'm looking at. Here's the output, any ideas?

```

$$ winetricks vcrun2008
------------------------------------------------------
You are using a 64-bit WINEPREFIX. If you encounter problems, please retest in a clean 32-bit WINEPREFIX before reporting a bug.
------------------------------------------------------
Executing w_do_call vcrun2008
Executing load_vcrun2008
Using native,builtin override for following DLLs: atl90 msvcm90 msvcp90 msvcr90 vcomp90
Executing winetricks_early_wine regedit C:\windows\Temp\_vcrun2008\override-dll.reg
Executing wine vcredist_x86.exe
fixme:clusapi:GetNodeClusterState ((null),0x33ebe4) stub!
fixme:advapi:DecryptFileA ("g:\\2c0a44f69e9258188f02cef30f\\", 00000000): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:secur32:SECUR32_initSchannelSP TLS library not found, SSL connections will fail
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:advapi:LsaOpenPolicy ((null),0x33f2c4,0x00000001,0x33f2b0) stub
fixme:advapi:LsaClose (0xcafe) stub
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
------------------------------------------------------
Note: command 'wine vcredist_x86.exe' returned status 84.  Aborting.
------------------------------------------------------

```

---

### Post by stretch4 on 2015-04-14
I was trying to play Skyrim. I got it to work by using playonlinux and installing it to a 32-bit environment.

---

