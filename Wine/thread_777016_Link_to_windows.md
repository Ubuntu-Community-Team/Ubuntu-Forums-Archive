---
title: "Link to windows"
date: 2008-05-01
forum: Wine
---

### Post by talsemgeest on 2008-05-01
Is there an easy way to link everything to an existing windows partition to give it entirely native dlls?

---

### Post by ajmorris on 2008-05-01
well, yes, however, it is not advised, you could have ~/.wine/drive_c linking to your windows partition, however, lots of things probably would not run, and when you use a native dll in wine, you have to set a native dll override in winecfg, which would just be a pain, if all dlls were native.

AJ

---

### Post by talsemgeest on 2008-05-01
Mmmm, thanks. So there is no way to automate the process?

---

### Post by ajmorris on 2008-05-01
not that i know of... you could get a list of all the windows system dlls, and make a bash script that automatically adds them to the wine config... but why are you wanting to do this? i think most things wont work if you try and use all native dlls.

---

### Post by talsemgeest on 2008-05-01
I think it would give better compatibility for some of the more complicated programs that I use.

Do you think otherwise?

---

### Post by aphirst on 2008-05-01
In principle you're almost on the right track. However, you must NOT override ALL the DLLs, im particular kernel.dll . DO RESEARCH for every single DLL you intend to override before you do it, as some will NOT play nicely with wine, trying to access basic hardware and system processes for Windows, which obviously don't run in Linux (!).
So, basically, only replace DLLs WHEN YOU KNOW YOU NEED TO, because 99% of the time a lack of compatibility/functionality is down to wine being ALPHA, or the Windows APP being written poorly, not necessarily down to the need for a native DLL.

---

### Post by talsemgeest on 2008-05-01
Ok, thanks for the info.

---

