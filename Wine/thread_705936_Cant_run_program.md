---
title: "Cant run program"
date: 2008-02-23
forum: Wine
---

### Post by Cartilage on 2008-02-23
The program is Amplitube2.  Installed the program ok but trying to launch and quits here:

```
wine: Call from 0x7b840b64 to unimplemented function gdiplus.dll.GdipDrawLinesI, aborting

wine: Call from 0x7b840b64 to unimplemented function gdiplus.dll.GdipDrawPieI, aborting
```

Thanks for any help.

---

### Post by adam0509 on 2008-02-24
get gdi32.dll from a windows installation, mmight work...

---

### Post by happyhamster on 2008-02-24
Yes, get gdiplus.dll and gdi32.dll (from a windows pc or download it from somewhere) and put those files in your system32 folder. You can find it in the hidden .wine folder in your home dir (location is usually ~.wine/drive_c/windows/system32). To be able to see hidden files: press ctrl-h in your file-manager (nautilus).

- When that's done, run your program while trying to override one (or both) of those dll's. 

WINEDLLOVERRIDES="gdiplus.dll=n" wine program-name.exe

- or: 
WINEDLLOVERRIDES="gdi32.dll,gdiplus.dll=n"  wine ....

- etc.

---

