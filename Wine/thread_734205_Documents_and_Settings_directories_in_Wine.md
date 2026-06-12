---
title: "Documents and Settings directories in Wine?"
date: 2008-03-24
forum: Wine
---

### Post by needhelpplease on 2008-03-24
I'm installing an application which needs to put a license key in:

```
C:\Documents and Settings\[username]\Application Data\Caphyon\Advanced Installer
```

(that's what their instructions say)

I can't figure out where that maps to within Wine.  I ran wineconfig and saw that there is a mapping for "My Documents", but is that the same as "Documents and Settings"?  This must be a simple thing to fix.  It looks like the app will run well if I can figure this out.

Thanks

:???:

---

### Post by needhelpplease on 2008-03-24
with more Googling, I think the answer is:

```
~/.wine/drive_c/windows/profiles/user_name
```

I'm trying this out.

---

