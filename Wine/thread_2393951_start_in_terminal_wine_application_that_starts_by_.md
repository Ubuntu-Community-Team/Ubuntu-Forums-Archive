---
title: "start in terminal wine application that starts by invoking .ink"
date: 2018-06-10
forum: Wine
---

### Post by arapaho on 2018-06-10
How to start in terminal wine application that normally is started by .ink?

In SumatraPDF.desktop there is entry:

```
Exec=env WINEPREFIX="/home/user_name/.wine" wine C:\\windows\\command\\start.exe /Unix /home/user_name/.wine/dosdevices/c:/users/Public/Start\ Menu/Programs/SumatraPDF.lnk
```

But just pasting it to terminal gives back error:
```
fixme:exec:SHELL_execute flags ignored: 0x00000100Couldn't run application or there is no application linked to the file
ShellExecuteEx failed
```

I want to know this because I want to be able to run it in firejail sandbox.

---

### Post by mc4man on 2018-06-10
Exec= whatever is not useful in the terminal.
You could just go 
wine C:\\windows\\command\\start.exe /Unix /home/user_name/.wine/dosdevices/c:/users/Public/Start\ Menu/Programs/SumatraPDF.lnk

or using ' around actual linux path to the .exe
wine 'path/to/the/.exe'

Ex.  here with ImgBurn
wine '.wine/drive_c/Program Files (x86)/ImgBurn/ImgBurn.exe'

or
wine 'C:\\Program Files (x86)/ImgBurn/ImgBurn.exe'

---

