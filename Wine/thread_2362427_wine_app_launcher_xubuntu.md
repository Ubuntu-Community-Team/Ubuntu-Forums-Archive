---
title: "wine app launcher xubuntu"
date: 2017-05-28
forum: Wine
---

### Post by cmcanulty on 2017-05-28
I have tried many paths and read tutorials but I still can't get a launcher to work for a wine app in xubuntu 16.04 

the path is

 /home/librarian/.wine/drive_c/Program Files/Microsoft Office/Office14/EXCEL.EXE

I am trying for the launcher command

wine " \drive_c\Program Files\Microsoft Office\Office14\EXCEL.EXE"

I also tried right click and send shortcut to desktop and that didn't work either. I also tried it with the slashes reversed, is there a typo or a trick I am missing?

---

### Post by ajgreeny on 2017-05-28
Try the full path ```
wine "/home/librarian/drive_c/Program Files/Microsoft Office/Office14/EXCEL.EXE"
```
It is years since I used wine and I can not remember the command I used in a launcher to do what you are trying to get working, but it certainly worked for me many years ago so must be worth trying this simple edit of the launcher command.

---

### Post by cmcanulty on 2017-05-28
I actually found a really neat program just now wine launcher creator,that solves one issue but I still can't get powerpoint 2010 to open, excel and word do fine. I did set the winecfg libraries  to override gdiplus riched20 and usp20. Thank you

[http://www.ubuntugeek.com/wl-creator-creates-linux-desktop-launchers-for-windows-programs.html]("http://www.ubuntugeek.com/wl-creator-creates-linux-desktop-launchers-for-windows-programs.html")

---

