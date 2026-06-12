---
title: "Lord of the Rings Online Patching Error"
date: 2011-12-22
forum: Wine
---

### Post by SirDakkalot on 2011-12-22
So I'm trying to patch Lord of the Rings Online through PyLotRO and I'm getting this error:

```
Connecting to patch.lotro.com:80

Checking files...
files to patch: 43 bytes to download: 96663104
Patching files:

Downloading de/Licenses/LUA/LUA License.txtFailed!

 Failed!
```I have no idea how to fix this, and can't seem to find anyone else having this problem (I've been trying to figure it out for almost two hours now). Could anyone please deign to offer assistance?

---

### Post by Faffin on 2011-12-23
Have you got that file already in /de/Licenses/LUA/? You could try renaming it to 
LUA License.bak & try patching again. I have it if you want it emailed, but I would need an email address to send it to.

---

### Post by SirDakkalot on 2011-12-23
> **Faffin said:**
> Have you got that file already in /de/Licenses/LUA/? You could try renaming it to 
LUA License.bak & try patching again. I have it if you want it emailed, but I would need an email address to send it to.

I checked for it and yes, I have it. I tried renaming it, but that didn't help. I suppose we could try emailing it. My email is REDACTED.

EDIT: I realized I had the wrong folder, and renamed the right file. However, when I renamed it, it simply added in a new LUA License.txt but still said it failed.

EDIT 2: I think I've managed to fix it, with a bit of help from your own suggestions.

Edit 3: I have not, and in fact determined that your suggested method didn't work. Still trying my damnedest.

---

### Post by Eisdiele on 2011-12-25
Hey,

Have you been able to solve this problem? I had the same here. I copied the LUA file from the /en/licenses folder. That worked so far but now I'm stuck  at "Downloading de/LOTRO TOS.rtfFailed". If I try to start Pylotro via Terminal I can't start patching at all.

I'm using wine 1.3.35 and have just downloaded and installed Lotro...

Any ideas how to solve that?

Thanks

edit: probably somebody can upload the hole /de /fr /en folders if they aren't to big?
edit2. changed back to the last stable wine version 1.2.3 and now there are no troubles while patching , at least none you can see. But if I try to run it nothing happens...

---

### Post by Eisdiele on 2011-12-27
Used the pando downloader for another try. Now installing and patching worked fine but I didn't get it  to start...

---

