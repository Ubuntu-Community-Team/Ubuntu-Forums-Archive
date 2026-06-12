---
title: "Running same script in Windows and wine under Linux"
date: 2008-01-19
forum: Wine
---

### Post by cisk4me on 2008-01-19
I want to write a script which detects whether the OS is Linux or Windows and then executes a Linux command or Windows batch file. Something like

```
if [ "$OSTYPE" = linux-gnu ]
then
  wine ~/.cxoffice/dotwine/fake_windows/winspice/wspice3.exe -n -b $1
else
  cmd /c "start /wait /min /low c:/WinSpice/wspice3.exe -b $1"
fi
```

Except this is a Linux script which won't work on Windows. Is there any way to do this?

---

