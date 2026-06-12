---
title: "[SOLVED] Wine (MSVCIRT.dll)"
date: 2006-08-19
forum: Wine
---

### Post by Cable on 2006-08-19
I have a (Windows) program that throws this error when I try to open it via Wine in the terminal:
```

caleb@Cable:~/.wine/drive_c/Program Files/Power Tab Software/Power Tab Editor 1.7$ wine PTEditor.exe 
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\Program Files\\Power Tab Software\\Power Tab Editor 1.7\\PTEditor.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Power Tab Software\\Power Tab Editor 1.7\\PTEditor.exe" failed, status c0000135

```
Is it possible to obtain the dll file which it requires in order to get this program to work in Linux?  If so, where do I put it?

---

### Post by derred on 2008-01-27
Late reply I know 
[http://www.dll-files.com/dllindex/dll-files.shtml?msvcirt](http://www.dll-files.com/dllindex/dll-files.shtml?msvcirt)

extract and copy to ~/.wine/drive_c/Windows/System/

Just happened to me and found the post in the forums :) better late then never

---

### Post by linuxd00 on 2008-01-27
I think its actually better to put it on 

~/.wine/drive_c/Windows/System32/

both might work though

---

### Post by derred on 2008-01-28
> **linuxd00 said:**
> I think its actually better to put it on 

~/.wine/drive_c/Windows/System32/

both might work though

I've used ../System version because under Windows that's where it would be. However in wine System is actually only a link to the System32 folder so you're right. It wouldn't be better, but it would be the same thing.

Anyway. I got MS Reader to work after yesterday's wine upgrade so I'm not complaining

---

### Post by p_quarles on 2008-01-28
I've moved this to the Wine forum (created long after the original post), and marked it solved. Hopefully, this will make it easier to find for anyone with a related question.

---

