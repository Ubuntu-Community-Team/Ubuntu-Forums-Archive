---
title: "[SOLVED] TVAnts on 64-bit Hardy"
date: 2008-08-08
forum: Wine
---

### Post by coolbrook on 2008-08-08
I just did a clean install upgrade to Ubuntu 8.04.1 (64-bit) and I'm having trouble running TVAnts on Wine.  I had no problem running it before the upgrade and it's running fine on my 32-bit Hardy desktop.

I receive the following output when I attempt to run TVAnts in Terminal

```
 wine "c:\program files\tvants\tvants.exe"
err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\program files\\tvants\\tvants.exe" failed, status c0000005
```

Any help will be appreciated.

---

### Post by coolbrook on 2008-08-08
Just did a clean install of 32-bit Heron and it installs fine.  It has something to do with the 64-bit architecture in Heron because it was working ok in Gutsy.  I did some web searching and apparently there is a bug report filed for the error I received.

---

