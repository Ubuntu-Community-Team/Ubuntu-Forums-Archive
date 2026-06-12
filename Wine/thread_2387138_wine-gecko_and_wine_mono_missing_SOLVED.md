---
title: "wine-gecko and wine mono missing SOLVED"
date: 2018-03-15
forum: Wine
---

### Post by royleith on 2018-03-15
It appears that both of these packages are now missing in Debian and Ubuntu repositories. That means that wine.org's iexplore and several wine help systems based on html will no longer render.
> 
Z:\home\roy>iexplore.exe

Z:\home\roy>Could not load wine-gecko. HTML rendering will be disabled.
err:mshtml:HTMLDocument_Create Failed to init Gecko, returning CLASS_E_CLASSNOTAVAILABLE
err:ole:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d

The workaround is to go to [https://wiki.winehq.org/Gecko](https://wiki.winehq.org/Gecko) and download the appropriate installation file and run,


> wine msiexec /i wine_gecko-2.47-x86_64.msi
or
wine msiexec /i wine_gecko-2.47-x86.msi

in Terminal, opened at the folder containing the downloaded installation file(s).

This problem was complicated by the failure of wine to use wifi connections. I could only get it to work via Ethernet.

If you are having problems with mono, then [https://wiki.winehq.org/Mono](https://wiki.winehq.org/Mono) may provide a solution.

---

