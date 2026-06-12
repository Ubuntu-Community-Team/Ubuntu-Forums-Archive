---
title: "todolist in wine. how to make it work?"
date: 2015-03-15
forum: Wine
---

### Post by xtf on 2015-03-15
Hello, Ubuntu-experts, can you give advices how to make program todolist from abstractspoon work in in wine(ubuntu 14.04)? When I launch todolist in wine it doesn't show any reaction, but another program work in wine. On the wine site there is a comment to put dll-files and instal xml
> 
]1. Download and extract (I did to .wine/drive_c/Programs/ToDoList/)
 2. Obtain a copy of msvcrt.dll and mfc42.dll (Note: use windows XP versions, windows vista produces errors in msvcrt.dll: Call from 0x7bc62815 to unimplemented function msvcrt.dll.__CxxFrameHandler3)
 3. Instal msxml3. Fallow: [http://wiki.winehq.org/NativeMSXML 3]("http://wiki.winehq.org/NativeMSXML3"). Note: I did not install NativeDcom and NativeMsi, and application still works fine.
but google doesn't give links to download msvcrt.dll and mfc42.dll for windows XP and I cannot understand where to put these files even if I get dll's
[https://appdb.winehq.org/objectManager.php?sClass=version&iId=9654](https://appdb.winehq.org/objectManager.php?sClass=version&iId=9654)
Of course I understand there are task managers in Linux but programs I found were not very useful for me

---

