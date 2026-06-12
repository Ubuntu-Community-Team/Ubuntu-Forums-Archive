---
title: "VisualBoyAdvance.exe + wine"
date: 2008-07-04
forum: Wine
---

### Post by silverhammer on 2008-07-04
I reinstalled Hardy earlier today, and now VisualBoyAdvance won't work in wine. Before I reinstalled, it worked perfectly (way better than native, surprisingly -that's why I chose to emulate). When I open it up from terminal, this is the output:

```
jake@jake-desktop:~$ wine /home/jake/VBA/VisualBoyAdvance.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\jake\\VBA\\VisualBoyAdvance.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\jake\\VBA\\VisualBoyAdvance.exe" failed, status c0000135

```

Any ideas?

---

### Post by mister_k81 on 2008-07-04
Basically, you're missing a Windows .DLL file called MFC42.DLL. 

Try downloading this one from here: [http://www.driverskit.com/dll/mfc42.dll/1917.html](http://www.driverskit.com/dll/mfc42.dll/1917.html) . 
Then unzip it and drop it in the same directory as your VisualBoyAdvance.exe file, and try running wine again.

---

### Post by silverhammer on 2008-07-04
That worked perfectly.

Wow. I can't believe it was that simple. It worked without doing that before I reinstalled. I wonder why? Oh well, as long as it works now.

Thanks a lot.

---

### Post by wingnux on 2008-07-04
[http://ubuntuforums.org/showthread.php?t=624170](http://ubuntuforums.org/showthread.php?t=624170)

---

