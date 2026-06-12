---
title: "Installing DirectX 9.0c with Wine"
date: 2008-02-06
forum: Wine
---

### Post by masterofthemelee on 2008-02-06
Well I'm trying to follow the tutorial [here.]("http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html")

I have no idea what the problem is.  I copied the list of .dlls to the user.reg file after backing user.reg up, opened the self-executable, and opened DXSETUP.EXE but when I go to the system32 folder no new files have been created.  I'm stuck at the part where its asking me to run dxdiag, since DXSETUP.EXE didn't create it (or anything, as far as I can tell).

What am I doing wrong?  This is my first experience with Wine.

---

### Post by Ferrat on 2008-02-06
installing DirectX in wine is not needed, wine has it's own "version" of it that works pretty good and to install DirectX on wine you need to fix alot with native windows dlls ect and even then it might not work since wine changes with every update, also Im not sure that installing it would actually help with game preformance

---

### Post by cogadh on 2008-02-06
It doesn't help. If the install actually worked correctly, the only "advantage" that you would end up with is a working DXDiag app, which is relatively useless in Wine anyway. You can accomplish the same functionality by simply copying and overriding the native DLLs **when needed** (some Wine DLLs will actually work better than native ones), without messing with a broken DX installation.

---

### Post by gsmanners on 2008-02-06
FWIW, you have to run DXSETUP twice. If you don't, it seems it doesn't really install anything.

Of course, as noted above, it's virtually useless since you won't be able to replace D3D.

---

