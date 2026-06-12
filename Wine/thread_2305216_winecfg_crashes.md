---
title: "winecfg crashes"
date: 2015-12-03
forum: Wine
---

### Post by danielsender on 2015-12-03
I was running wine1.6 on a Ubuntu 14.04.3 on a Macbook Pro. In the past I installed the Microsoft Office 2007 that runs well. However a few days ago when trying to click on the Libraries tab of winecfg it crashed. I decided to upgrade to wine1.7 but the problem is now that winecfg crashes from the start, so I don't even see the gui. Here is what I get on the screen:
```
winecfg
err:module:DelayLoadFailureHook failed to delay load usp10.dll.ScriptBreak
wine: Call from 0x7b83c3de to unimplemented function usp10.dll.ScriptBreak, aborting
wine: Unimplemented function usp10.dll.ScriptBreak called at address 0x7b83c3de (thread 0009), starting debugger...
err:module:DelayLoadFailureHook failed to delay load usp10.dll.ScriptBreak
wine: Call from 0x7b83c3de to unimplemented function usp10.dll.ScriptBreak, aborting
winedbg: Internal crash at 0x7b83c3de

```

Thanks in advance for your help.

Daniel

---

### Post by danielsender on 2015-12-04
> **danielsender said:**
> I was running wine1.6 on a Ubuntu 14.04.3 on a Macbook Pro. In the past I installed the Microsoft Office 2007 that runs well. However a few days ago when trying to click on the Libraries tab of winecfg it crashed. I decided to upgrade to wine1.7 but the problem is now that winecfg crashes from the start, so I don't even see the gui. Here is what I get on the screen:
```
winecfg
err:module:DelayLoadFailureHook failed to delay load usp10.dll.ScriptBreak
wine: Call from 0x7b83c3de to unimplemented function usp10.dll.ScriptBreak, aborting
wine: Unimplemented function usp10.dll.ScriptBreak called at address 0x7b83c3de (thread 0009), starting debugger...
err:module:DelayLoadFailureHook failed to delay load usp10.dll.ScriptBreak
wine: Call from 0x7b83c3de to unimplemented function usp10.dll.ScriptBreak, aborting
winedbg: Internal crash at 0x7b83c3de

```

Thanks in advance for your help.

Daniel

Bump

---

### Post by r2rX on 2015-12-06
This doesn't answer what the exact problem you have is but i'd suggest uninstalling the version of Wine you currently have installed and try out wine-staging.

[https://github.com/wine-compholio/wine-staging/wiki/Installation#-ubuntulinux-mint](https://github.com/wine-compholio/wine-staging/wiki/Installation#-ubuntulinux-mint)

---

