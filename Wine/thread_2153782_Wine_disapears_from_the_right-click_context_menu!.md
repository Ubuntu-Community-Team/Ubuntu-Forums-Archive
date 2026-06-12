---
title: "Wine disapears from the right-click context menu!"
date: 2013-06-12
forum: Wine
---

### Post by mprswk on 2013-06-12
Help! Everything went fine until I've updated my Ubuntu. Wine has disapeared from the right-click context menu. I even cannot open *.exe files like before because Wine is absent in "Other applications..." as well.

How to fix it?
How to open .exe files through terminal?

---

### Post by mprswk on 2013-06-13
Okay, I've successfully used .exe files but I've noticed that "Create New File..." also disappeared from right-click context menu. Why?!

---

### Post by gordintoronto on 2013-06-13
What version of Ubuntu? Have you rebooted since this started happening?

---

### Post by xREDEMPTIONx on 2013-06-14
After upgrading to 13.04 I noticed wine is absent from the right click  menu. Also I was unable to set it as the default application for opening  .exe files as it was missing from the list, archive manager was somehow  set as default. To fix it I ran ```
gksu gedit /usr/share/applications/mimeinfo.cache
``` in a terminal and found the line- application/x-ms-dos-executable=file-roller.desktop;wine.desktop;mono-runtime.desktop;mono-runtime-terminal.desktop; I removed file-roller.desktop from the line and saved the file and it started working again. Wine was now set as the default application for opening .exe files. Now I noticed the issue has returned and I've had to remove file-roller.desktop a few times now so either this is a bug or there is something else I'm missing.

---

